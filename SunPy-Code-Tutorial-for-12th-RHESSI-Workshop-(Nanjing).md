```
# SunPy Demo given on 17-Oct-2011

# plotting a fits file image
import sunpy
aia = sunpy.Map(sunpy.AIA_171_IMAGE)
aia.show()

from matplotlib import colors
aia.show(norm=colors.Normalize(1, 2048))

from sunpy.cm import cm as cm
cm.show_colormaps
aia.show(cmap=cm.sdoaia94)

type(aia)
aia.header
aia.max()
aia.mean()

sub_aia = aia.submap([-500,500], [-500,500])
sub_aia.show()

from sunpy.net import vso

# create a new VSOClient instance
client = vso.VSOClient()

result = client.query( vso.attrs.Time((2006, 9, 20), 
  (2006, 9, 21,1)), vso.attrs.Instrument('eit') )
result.no_records
result = client.query( vso.attrs.Time((2006, 9, 20), 
  (2006, 9, 21,1)), vso.attrs.Instrument('eit') | vso.attrs.Instrument('trace'))

# now download the data
res = client.get(result[:1]).wait()

from sunpy.sun import constants as con

con.volume
con.value('volume')
con.unit('volume')
con.print_all()

solar_constants = con.physical_constants
solar_constants.keys()
solar_constants.get('volume')

from sunpy.util import util as util
util.anytim('2003/04/01 01:03:00')

import pidly
idl = pidly.IDL('myidl')
idl('a = dist(10)')
idl.a

from pylab import *
imshow(idl.a)

idl.x = 2 ** 2
idl.x

idl.interact()
# now in IDL> shell
# print, x
# x = 12
# now type ^D to escape the IDL shell and get back to the python shell
idl.x

#if time permits
from sunpy.instr import rhessi
image = rhessi.backprojection(sunpy.RHESSI_EVENT_LIST)
imshow(image)

```