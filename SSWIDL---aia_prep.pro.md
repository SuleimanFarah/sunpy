
PRO aia_prep, input1, input2, oindex, odata, index_ref=index_ref, use_ref=use_ref, $
  infil=infil, cutout=cutout, nearest=nearest, $
  interp=interp, cubic=cubic, $
  use_pnt_file=use_pnt_file, not_use_ssw=not_use_ssw, no_uncomp_delete=no_uncomp_delete, $
  do_write_fits=do_write_fits, outdir=outdir, outfile=outfile, scale_fac=scale_fac, _extra=_extra, $
  sign_mag=sign_mag, sign_x0=sign_x0, sign_y0=sign_y0, sign_angle=sign_angle, $
  qstop=qstop, quiet=quiet, verbose=verbose, run_time=run_time, progver=progver, prognam=prognam

;+
; NAME:
;   AIA_PREP
; PURPOSE:
;   Perform image registration (rotation, translation, scaling) of Level 1 AIA images, and update
;   the header information.
; CATEGORY:
;   Image alignment
; SAMPLE CALLS:
;   Inputing infil (in this case iindex and idata are returned with 
;   IDL> AIA_PREP, infil, [0,1,2], oindex, odata
;   Inputing iindex and idata: 
;   IDL> AIA_PREP, iindex, idata, oindex, odata
; INPUTS:
;   There are 2 basic usages for inputing the image and header data into AIA_PREP:
;   Case 1: References FITS file name on disk:
;           input1 - String array list of AIA FITS files
;           input2 - List of indices of FITS files to read 
;   Case 2. References index structure and data array in memory
;           (index, data already read from FITS file using, for example, READ_SDO.PRO):
;           input1 - index structure
;           input2 - data array
; OUTPUTS (OPTIONAL):
;   oindex - The updated index structure of the input image
;   odata - Registered output image.
; KEYWORDS:
;   USE_REF - If set then align all images to a reference index (if INDEX_REF is not supplied then
;             use the first index of the array as the reference index).
;             NOTE - If USE_REF is not set and if INDEX_REF is not supplied, then all images will
;             be aligned to sun center.
;   INDEX_REF - Reference index for alignment coordinates.
;   DO_WRITE_FITS - if set, write the registered image and updated header structure to disk
;   NEAREST - If set, use nearest neighbor interpolatipon
;   INTERP - If set, use bilinear interpolation
;   CUBIC - If set, use cubic convolution interpolation ith the specified value (in the range [-1,0]
;           as the interpolation parameter.  Cubic interpolation with this parameter equal -0.5
;           is the default.
; TODO:
;   Calculate NAXIS1, NAXIS2 as follows:
;     naxis1,2 = gt_tagval(oindex0, /znaxis1,2, missing=gt_tagval(oindex0, /naxis1,2))
;   Reference scale should be read from the database file.
;   Decide if CROTA1 should be added
; HISTORY:
;   2010 (circa), Created ab initio - GLS (slater@lmsal.com)
;   2010-12-07 - GLS - Corrected call to break_file - GLS
;   2011-02-10 - GLS - 1. Corrected sign error on roll (Thanks to Ralph Seguin)
;                      2. Corrections to tags CRPIX(1,2), CDELT(1,2, and CROT2A were not being 
;                         propagated to output header structure (OINDEX).  This was fixed
;                         (Thanks to Benjamin Mampaey)
;   2011-02-28 - GLS - 1. Added missing half pixel to output CRPIX1/2
;                      2. Defined LVL_NUM keyword to be 1.5 (should it be 1.51 to differentiate from
;                         real time?)
;                      3. Added _EXTRA in call for keyword inheritance
;                      4. Made UNCOMP_DELETE the default in call to READ_SDO.
;   2011-03-02 - GLS - 1. Corrected references to NAXIS1/2 in case of compressed file headers
;                      2. Changed default interpolation for ROT function from nearest neighbor to
;                         damped cubic.
;   2011-04-07 - GLS - Corrected 1 pixel error (both axes) in pivot point for ROT function due to
;                      discrepancy between FITS standard pixel numbering for CRPIX1,2 (starting from 1)
;                      and IDL array index referencing (starting from 0).  Thanks to Alberto Vasquez.
;   2011-04-08 - GLS - Added '/pivot' to ROT call for 'cutout' images.  Thanks to Marc DeRosa.
;   2011-04-20 - GLS - Checked for existence of tags 'RSUN_OBS', 'RSUN', and 'LVL_NUM' before attempting
;                      to update them, in order for code to work on HMI images.
;   2011-05-10 - GLS - Removed incorrect logic to correct for binning.
;   2011-05-18 - GLS - Corrected multiple errors in naming convention for output FITS files in HMI case
;   2011-05-19 - GLS - Added updating of header tags:
;                        DATAMIN, DATAMAX, DATAMEDN, DATAMEAN, DATARMS, DATASKEW, DATAKURT
;   2011-05-20 - GLS - Changed from inserting OINDEX0 into pre-defined OINDEX array back to concatenation
;                        cause I couldn't figger out a bonehead error.
;   2011-06-08 - GLS - Corrected error in usage of OUTFILE parameter.
;   2011-07-13 - GLS - Corrected errors in processing of 'cutout' images.
;   2011-12-19 - GLS - Corrected CRPIX error in HMI cutouts.
;   2011-12-20 - GLS - Further correction of CRPIX errors.
;-

; Define prognam, progver variables
prognam = 'AIA_PREP.PRO'

;progver = 'V4.00' ; 2011-02-10 (GLS)
;progver = 'V4.01' ; 2011-03-01 (GLS)
;progver = 'V4.02' ; 2011-03-02 (GLS)
;progver = 'V4.03' ; 2011-04-06 (GLS)
;progver = 'V4.04' ; 2011-04-07 (GLS)
;progver = 'V4.05' ; 2011-04-20 (GLS)
;progver = 'V4.06' ; 2011-05-10 (GLS)
;progver = 'V4.07' ; 2011-05-18 (GLS)
;progver = 'V4.08' ; 2011-05-18 (GLS)
;progver = 'V4.09' ; 2011-05-20 (GLS)
;progver = 'V4.10' ; 2011-06-08 (GLS)
;progver = 'V4.11' ; 2011-06-13 (GLS)
;progver = 'V4.12' ; 2011-12-19 (GLS)
progver = 'V4.13' ; 2011-12-22 (GLS)

; Start the clock running
t0 = systime(1)
t1 = t0	; Keep track of running time

; Define reference plate scale in arsec per pixel, if not already defined:
if not exist(scale_ref) then scale_ref = 0.6

; Define default signs for ROT parameters:
if not exist(sign_mag) then sign_mag = 1
if not exist(sign_x0) then sign_x0 = 1
if not exist(sign_y0) then sign_y0 = 1
if not exist(sign_angle) then sign_angle = 1

; Define constants:
wave_val_arr = [ 0094,   0131,   0171,   0193,   0211,   0304,   0335,   1600,   1700,   4500,   6173 ]
wave_str_arr = [ '094',  '131',  '171',  '193',  '211',  '304',  '335', '1600', '1700', '4500', '6173']

hmi_content_value = $
  ['dopplergram', 'magnetogram', 'level 1p image', 'linewidth', 'linedepth', 'contiuum intensity']
hmi_outfil_suffix = $
  ['dop','mag','img','wid','dep','cont']

; Process keywords:
loud = 1 - KEYWORD_SET(quiet)
verbose = KEYWORD_SET(verbose)
if (verbose eq 1) then loud = 1
if (loud) then PRINT, 'Running ', prognam, ' ', progver

if not exist(scale_ref) then scale_ref = 0.60
if ( (not exist(nearest)) and (not exist(interp)) and (not exist(cubic)) ) then cubic = -0.5

if keyword_set(no_uncomp_delete) then uncomp_delete = 0 else uncomp_delete = 1

input_err = 1
if ( (size(input1, /tname) eq 'STRING') and (size(input2, /n_dim) le 1) ) then begin
  input_err = 0
  do_read = 1
  infil_arr = input1
  ss_infil = input2
  if ss_infil[0] eq -1 then ss_infil = indgen(n_elements(infil_arr))
  n_img = n_elements(ss_infil)

  ss_not_exist = where(file_exist(infil_arr) ne 1, n_not_exist)
  if n_not_exist eq 0 then begin
    read_sdo, infil_arr[ss_infil[0]], iindex0, idata0, uncomp_delete=uncomp_delete, _extra=_extra
; Create template oindex structure array if output index structure is requested:
;    if n_params() ge 3 then begin
;      oindex = replicate(iindex0, n_img)
; Update history record(s) in output index array:
;      update_history, oindex, version=progver
;    endif
    data_type = size(idata0, /type)
    data_dim = size(idata0, /dim)
    data_ndim = size(idata0, /n_dim)
  endif else begin
    input_err = 2
    print, ' Input error: Not all files in file list found.  Returning.'
    return
  endelse
endif

if ( (size(input1, /tname) eq 'STRUCT') and ( (size(input2, /n_dim) eq 2) or (size(input2, /n_dim) eq 3) ) ) then begin
  input_err = 0
  do_read = 0
  iindex = input1
  idata = input2
; Create template oindex structure array if output index structure is requested:
;  if n_params() ge 3 then begin
;    oindex = iindex
; Update history record(s) in output index array:
;    update_history, oindex, version=progver
;  endif
  ss_infil = indgen(n_elements(iindex))
  n_img = n_elements(ss_infil)
  data_type = size(idata, /type)
  data_dim = size(idata, /dim)
  data_ndim = size(idata, /n_dim)
endif

if input_err eq 1 then begin
  print, ' Input error: INPUT1 and INPUT2 must be:'
  print, '   EITHER: FITS file list and indices list'
  print, '   OR:     INDEX array and DATA array.'
  print, ' Returning.'
  return
endif

; Create empty array for odata:
if n_params() ge 4 then odata = make_array([data_dim[0], data_dim[1], n_img], type=data_type)

for i=0, n_img-1 do begin  
  if do_read eq 1 then begin
    file0 = infil_arr[ss_infil[i]]
    read_sdo, file0, iindex0, idata0, uncomp_delete=uncomp_delete, /mixed
  endif else begin
    iindex0 = iindex[i]
    idata0 = idata[*,*,i]
  endelse

  oindex0 = iindex0
  instr_prefix = strupcase(strmid(iindex0.instrume,0,3))

; If use_ref is set and index_ref not passed, then set INDEX_REF equal to first index record:
  if ( (keyword_set(use_ref)) and (not exist(index_ref)) ) then $
    index_ref = iindex0

  if i eq 0 then begin
    if exist(index_ref) then begin
      cdelt1_ref = index_ref.cdelt1
      cdelt2_ref = index_ref.cdelt2
      crpix1_ref = index_ref.crpix1
      crpix2_ref = index_ref.crpix2
      if instr_prefix ne 'HMI' then begin
        xcen_ref   = index_ref.xcen
        ycen_ref   = index_ref.ycen
      endif
      crota2_ref = index_ref.crota2
    endif else begin
      cdelt1_ref = scale_ref
      cdelt2_ref = scale_ref
      crpix1_ref = (float(iindex0.naxis1)+1.)/2.
      crpix2_ref = (float(iindex0.naxis2)+1.)/2.
      xcen_ref   = 0.
      ycen_ref   = 0.
      crota2_ref = 0.
    endelse
  endif

; Update history record(s) in output index array:
  update_history, oindex0, version=progver

; Determine wavelength and other properties:
  if instr_prefix eq 'HMI' then wavelnth = '6173' else wavelnth = strtrim(fix(iindex0.wavelnth),2)
  ss_match_wave = where(wavelnth eq wave_val_arr, n_match_wave)
  wave_val = wave_val_arr[ss_match_wave]
  wave_string = wave_str_arr[ss_match_wave]

; Optionally use master pointing file for pointing parameters:
  if keyword_set(use_pnt_file) then begin

; Read master pointing file and find the nearest record to AIA image:
    pnt_struct = ssw_sdo_master_pointing(ssw=1-keyword_set(not_use_ssw))
    ss_close_pnt = tim2dset(anytim(pnt_struct.date_obs, /ints), anytim(iindex0.date_obs, /ints))
    pnt_str_match = pnt_struct[ss_close_pnt]

; Extract appropriate IMSCALE, X0, Y0, and INSTROT tags for wavelength:
    t_names_pnt = strlowcase(tag_names(pnt_str_match))
    ss_x0 = where(strpos(t_names_pnt, wave_string + '_x0') ne -1, n_match_x0)
    crpix10 = pnt_str_match.(ss_x0)
    ss_y0 = where(strpos(t_names_pnt, wave_string + '_y0') ne -1, n_match_x0)
    crpix20 = pnt_str_match.(ss_y0)
    ss_imscale = where(strpos(t_names_pnt, wave_string + '_imscale') ne -1, n_match_imscale)
    cdelt10 = pnt_str_match.(ss_imscale)
    cdelt20= pnt_str_match.(ss_imscale)
    ss_instrot = where(strpos(t_names_pnt, wave_string + '_instrot') ne -1, n_match_instrot)
    crota20 = pnt_str_match.(ss_instrot)  
  endif else begin
; REMOVE    scale_fac = iindex0.cdelt1/scale_ref
    crpix10 = iindex0.crpix1
    crpix20 = iindex0.crpix2
    cdelt10 = iindex0.cdelt1
    cdelt20 = iindex0.cdelt2
    crota20 = iindex0.crota2
  endelse

; Define deltas for rotation, translation, and scaling by subtracting the reference parameters from the
;   corresponding image parameters:
  scale_fac = cdelt10/cdelt1_ref
  if keyword_set(use_ref) then begin
    delta_crpix1 = crpix10 - crpix1_ref/scale_fac
    delta_crpix2 = crpix20 - crpix2_ref/scale_fac
  endif else begin
    delta_crpix1 = crpix10 - crpix1_ref
    delta_crpix2 = crpix20 - crpix2_ref
  endelse
  delta_crota2 = crota20 - crota2_ref
  mag = scale_fac ^(sign_mag)
  x0 = delta_crpix1 *sign_x0 + float(iindex0.naxis1-1)/2
  y0 = delta_crpix2 *sign_y0 + float(iindex0.naxis2-1)/2
;  x0 = delta_crpix1 *sign_x0 + (float(iindex0.naxis1)+1.)/2.
;  y0 = delta_crpix2 *sign_y0 + (float(iindex0.naxis2)+1.)/2.

  angle = -delta_crota2 *sign_angle

  if not exist(missing) then missing = min(idata0)
; Perform re-mapping:
;  odata0 = rot(idata0, -instrot, scale_fac, x0, y0, interp=interp, cubic=cubic, missing=missing)
  odata0 = rot(idata0, angle, mag, x0, y0, interp=interp, cubic=cubic, missing=missing)

; Update header tag values as needed:
  naxis1 = gt_tagval(oindex0, /znaxis1, missing=gt_tagval(oindex0, /naxis1))
  naxis2 = gt_tagval(oindex0, /znaxis2, missing=gt_tagval(oindex0, /naxis2))

; Update coordinates by calling WCS_REMAP.PRO:
;  oindex0 = wcs_remap(oindex0)

; Set coordinate tags equal to reference values:
  oindex0.cdelt1 = cdelt1_ref
  oindex0.cdelt2 = cdelt2_ref
  oindex0.crpix1 = crpix1_ref
  oindex0.crpix2 = crpix2_ref
  if instr_prefix ne 'HMI' then begin
    oindex0.xcen   = xcen_ref
    oindex0.ycen   = ycen_ref
  endif
  oindex0.crota2 = crota2_ref

; Update header tags for max, min, and moments of pixel values:
  if tag_exist(oindex0, 'DATAMIN') then oindex0.datamin = min(odata0)
  oindex0.datamax = max(odata0)
  oindex0.datamedn = median(odata0)
  moments_odata0 = moment(odata0)
  oindex0.datamean = moments_odata0[0]
  oindex0.datarms = moments_odata0[1]^2
  oindex0.dataskew = moments_odata0[2]
  oindex0.datakurt = moments_odata0[3]

  if ( tag_exist(oindex0, 'r_sun') and tag_exist(iindex0, 'rsun_obs') )then $
    oindex0.r_sun  = iindex0.rsun_obs/oindex0.cdelt1
  if tag_exist(oindex0, 'lvl_num') then $
    oindex0.lvl_num = 1.5

; If output index array or data cube is requested then update these:
;  if n_params() ge 3 then oindex[i] = oindex0
  if n_params() ge 3 then begin
    if i eq 0 then oindex = oindex0 else oindex = concat_struct(oindex, oindex0)
  endif
  if n_params() ge 4 then odata[0,0,i] = odata0

; Optionally write out new FITS file:
  if keyword_set(do_write_fits) then begin
    if not exist(outfile) then begin
      if not exist(outdir) then outdir = './'
      if instr_prefix eq 'HMI' then begin
        ss_match = where(hmi_content_value eq strlowcase(oindex0.content), n_match)
        if n_match gt 0 then $
          outfil_suffix = hmi_outfil_suffix[ss_match[0]] else $
          outfil_suffix = string(wave_val, format='$(i4.4)')
      endif
      if instr_prefix eq 'AIA' then begin
        outfil_suffix = string(wave_val, format='$(i4.4)')
      endif
      outfil = instr_prefix + time2file(oindex0.date_obs, /sec) + '_' + outfil_suffix + '.fits'
      outfile0 = concat_dir(outdir, outfil)
    endif else begin
      outfile0 = outfile
    endelse
    mwritefits, oindex0, odata0, outfile=outfile0
  endif

endfor

if keyword_set(qstop) then $
  stop,' Stopping on request.'

end
