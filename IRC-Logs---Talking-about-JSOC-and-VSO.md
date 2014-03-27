# 25/3/2014
```
[03:56:24] *** Joins: VaticanCameos (~pls@182.68.205.231)
[04:42:19] *** Quits: mefistofeles (~crush@unaffiliated/mefistofeles) (Quit: Hay the guachu!)
[06:04:58] *** Joins: livingstore (~livingsto@115.248.45.78)
[06:12:04] *** Joins: examon (~exo@ip-94-112-98-5.net.upcbroadband.cz)
[06:17:31] *** Joins: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230)
[06:51:12] *** Joins: AndChat|501 (~SVXX@182.68.205.231)
[07:19:59] *** Quits: AndChat|501 (~SVXX@182.68.205.231) (Quit: Bye)
[07:29:51] *** Joins: rishabh (uid26424@gateway/web/irccloud.com/x-ugsjgoomudvayvfl)
[07:35:16] *** Quits: livingstore (~livingsto@115.248.45.78) (Quit: BinPy-soc)
[07:35:36] *** Joins: livingstore (~livingsto@115.248.45.78)
[07:36:06] *** Quits: livingstore (~livingsto@115.248.45.78) (Read error: Connection reset by peer)
[07:36:52] *** Joins: sarwarc (~livingsto@115.248.45.78)
[08:51:03] *** Joins: astrofrog (~Adium@rt-mpia.mpia-hd.mpg.de)
[08:52:20] *** Quits: VaticanCameos (~pls@182.68.205.231) (Quit: Leaving)
[09:10:58] *** Joins: rajul_ (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230)
[09:22:57] <Cadair> Good morning
[09:24:11] <rajul_> Cadair: good morning
[09:24:41] <rajul_> Cadair: i have tried to to clean up my proposal....https://github.com/sunpy/sunpy/wiki/GSoC-2014-Rajul
[09:24:51] <rajul_> Cadair: please take a look...
[09:31:29] <Cadair> hey rajul I will take a look
[09:31:41] <Cadair> damn it where is joe when you need him?
[09:32:58] <rajul_> Cadair: thanks!!
[09:34:11] <Cadair> looks good
[09:35:40] <Cadair> pingy ping DavidPS 
[09:41:36] <Cadair> hey astrofrog more WCSAxes tweaks
[09:41:40] <Cadair> loving the deg symbol
[09:42:07] <astrofrog> Cadair - great!
[09:46:01] <Cadair> astrofrog, What can I do to help with WCSAxes?
[09:53:09] *** Joins: VaticanCameos (~SVXX@182.68.205.231)
[10:12:40] <Cadair> God save unit testing
[10:45:11] *** Quits: sarwarc (~livingsto@115.248.45.78) ()
[10:50:03] <Cadair> __name__, you around?
[11:09:42] <astrofrog> Cadair: about helping - first already testing it for many different cases is great, but if you're interested in developing, then I'll try and identify issues you can contribute to
[11:10:15] <Cadair> astrofrog, It needs to get finished, it is too awesome.
[11:11:05] <astrofrog> ok, will start planning the near-term development and create issues for everything that needs to be done - then take your pick :)
[11:11:17] <Cadair> Shiny
[11:11:26] <astrofrog> afk, back later
[11:55:46] <VaticanCameos> o.o
[11:57:59] <Cadair> astrofrog, http://imgur.com/a/5pPAH#0
[11:59:13] <astrofrog> pretty!!
[11:59:25] <astrofrog> I need to fix how the axis label position is determined
[11:59:40] <astrofrog> at the moment it puts it as close as possible without overlapping with tick labels
[11:59:45] <astrofrog> but clearly not a good choice
[12:01:33] <Cadair> astrofrog, what do you mean?
[12:02:18] <Cadair> you mean the lon labels are too close?
[12:03:08] <Cadair> astrofrog, you know you made those HI images with the dual WCS? Have you still got the code, I was trying to re-create
[12:03:21] <astrofrog> before we fix that in code, need to figure out what the 'ideal' behavior is
[12:03:21] <astrofrog> I think it should default to being a certain distance away from the axes, *then* move even further if it overlaps
[12:03:21] <astrofrog> in your 'cropped' plot
[12:03:21] <astrofrog> you can see the solar-x and solar-y labels are too close to the axes
[12:03:21] <astrofrog> yes
[12:03:21] <astrofrog> I need to make the default displacement larger
[12:03:32] <astrofrog> ah must have that
[12:03:33] <astrofrog> 2 sec
[12:04:08] <Cadair> astrofrog, the solar-xy labels are too close to the axes?
[12:04:14] <Cadair> I donno, I think they are ok
[12:04:43] <Cadair> I think a bigger problem is the solar lon labels in this image: http://i.imgur.com/lKKL6DF.png
[12:04:52] <Cadair> the -80 and -75 are way too close
[12:05:25] <astrofrog> I meant that in that plot the 'solar-x' and 'solar-y' labels are maybe too close - at least there should way to customize it
[12:05:38] <astrofrog> how would you improve the −80 and −75?
[12:05:45] <astrofrog> what would be the ideal output?
[12:05:47] <astrofrog> Cadair: https://gist.github.com/astrofrog/9760437
[12:06:44] <Cadair> astrofrog, either they need to be slightly further apart, or one of them not there
[12:08:16] <astrofrog> if you increase the font size one will disappear
[12:08:33] <astrofrog> but we could simply make the criterion for overlap more stringent
[12:09:38] *** Quits: renstar (~quassel@c-98-217-130-167.hsd1.ma.comcast.net) (Ping timeout: 265 seconds)
[12:22:43] *** Quits: VaticanCameos (~SVXX@182.68.205.231) (Quit: Bye)
[12:27:16] *** Joins: VaticanCameos (~pls@182.68.205.231)
[13:11:09] *** Joins: travis-ci (~travis-ci@ec2-54-221-152-237.compute-1.amazonaws.com)
[13:11:09] <travis-ci> [travis-ci] nabobalis/sunpy#99 (ana_cython - b5045c1 : Nabil Freij): The build was fixed.
[13:11:09] <travis-ci> [travis-ci] Change view : https://github.com/nabobalis/sunpy/compare/6da4dcbe08f7...b5045c1cf5c0
[13:11:09] <travis-ci> [travis-ci] Build details : http://travis-ci.org/nabobalis/sunpy/builds/21505475
[13:11:09] *** Parts: travis-ci (~travis-ci@ec2-54-221-152-237.compute-1.amazonaws.com) ()
[13:27:37] *** Joins: renstar (~quassel@18.155.7.137)
[13:53:30] *** Quits: VaticanCameos (~pls@182.68.205.231) (Quit: Leaving)
[14:11:23] *** Quits: rajul_ (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230) (Quit: Page closed)
[14:45:02] *** Quits: astrofrog (~Adium@rt-mpia.mpia-hd.mpg.de) (Quit: Leaving.)
[14:46:20] *** Joins: astrofrog (~Adium@rt-mpia.mpia-hd.mpg.de)
[14:48:40] *** Quits: examon (~exo@ip-94-112-98-5.net.upcbroadband.cz) (Ping timeout: 265 seconds)
[15:34:38] *** Joins: VaticanCameos (~SVXX@182.68.205.231)
[16:09:44] *** Joins: jhourcle (~Adium@c-76-106-20-159.hsd1.md.comcast.net)
[16:52:11] <Cadair> hey jhourcle
[16:52:15] <Cadair> just the man I need to talk to
[16:52:19] <jhourcle> I didn't do it.
[16:52:24] <Cadair> are you sure?
[16:52:29] <jhourcle> fairly certain
[16:52:32] <Cadair> lol
[16:53:05] <Cadair> firstly, what controls if you get RICE compressed data back?
[16:53:25] <Cadair> wrt to HMI/AIA data?
[16:53:28] <jhourcle> it's only an AIA & HMI thing...
[16:53:32] <Cadair> right
[16:53:52] <jhourcle> so after you do the vso 'search' part ...
[16:54:16] <jhourcle> you get back identifiers, but you can request those back different ways depending on the data provider
[16:54:50] <jhourcle> when you send a 'GetData' request to VSO, you tell it what methods you'd like to use
[16:55:12] <jhourcle> and by 'methods', I mean how you'd like to obtain the data
[16:55:37] <jhourcle> 'URL-FILE' is the default, as most data providers support that
[16:55:48] <Cadair> right yes
[16:55:51] <Cadair> I see
[16:55:53] <jhourcle> next most is 'PACKAGED-TAR_GZ'
[16:55:57] <Cadair> evil
[16:55:59] <jhourcle> anyway, we tied it into there.
[16:56:03] <Cadair> shiny
[16:56:09] <jhourcle> let me look up what the right string is to send
[16:56:58] <jhourcle> URL-FILE_Rice
[16:57:16] <jhourcle> it should be case insensitive .. 
[16:57:29] *** Parts: astrofrog (~Adium@rt-mpia.mpia-hd.mpg.de) ()
[16:58:08] *** Joins: examon1 (~exo@auth47-241.fi.muni.cz)
[16:58:18] <Cadair> thanks
[16:58:33] <Cadair> secondly, where is the limit at the point where JSOC will return tar files?
[16:59:02] <jhourcle> I think it's 5000 records … let me confirm
[16:59:27] <Cadair> that's odd, because I got tars and I only got ~4000 fits files out for a MDI query
[16:59:37] <jhourcle> might be 3k
[16:59:51] <jhourcle> we had to play w/ it based on time to process
[17:00:03] *** Joins: sarwarc (~livingsto@115.248.45.78)
[17:00:10] <Cadair> it is such a PITA
[17:00:21] <Cadair> I understand why, but it is still a PITA
[17:00:49] <jhourcle> sub limit { return 5000 }
[17:01:24] <Cadair> hmmm, I wonder if it is SunPy prefering tar over individual at a lower limit then?
[17:01:28] <jhourcle> the thing is — it's based on the query, not the retrieval
[17:01:37] <Cadair> yeah
[17:01:40] <jhourcle> well, there's two things ...
[17:01:53] <jhourcle> HMI.S_720s will *always* be tarballs
[17:02:03] <jhourcle> because they have a single identifier that maps to 24 files
[17:02:11] <Cadair> they are the vectorgrams right?
[17:02:19] <jhourcle> stokes parameter data
[17:02:24] <Cadair> yeah
[17:02:24] <jhourcle> I,Q,U,V
[17:03:04] <jhourcle> anyway, the limit is so that we can return the response in a reasonable amount of time (and not break UIs)
[17:03:37] <jhourcle> so if we switch over to the 'summary' mode, any of the IDs now map to multiple files ...
[17:03:44] <jhourcle> rather than discrete observations
[17:04:32] <Cadair> dear god this is so crazy
[17:04:41] <jhourcle> yeah, I know.
[17:05:11] <jhourcle> there was a proposal a long time ago to pass back the ID as a new 'search' to have it expand to individual files
[17:05:22] <jhourcle> but we've had too many distractions … mostly things breaking at the JSOC
[17:06:11] <Cadair> jhourcle, does VSO use VO tables anywhere?
[17:06:20] <jhourcle> nope, because IDL sucks at XML
[17:06:26] <Cadair> XD
[17:06:36] <Cadair> o.o
[17:06:39] <jhourcle> we've talked about using it for returning our search results
[17:06:45] <Cadair> yeah
[17:06:46] <jhourcle> rather than how we're serializing it now
[17:07:12] <jhourcle> there's also been talk about trying to make a way to 'peek' at the data, without getting a file back
[17:07:18] <jhourcle> just get back the FITS header ...
[17:07:22] <Cadair> how does the IDL client handle the tar thing?
[17:07:34] <jhourcle> it downloads a tarball.  
[17:07:37] <jhourcle> *grin*
[17:07:51] <Cadair> then leaves it to the user to untar it?
[17:08:10] <jhourcle> anyway, the FITS header stuff … VOTable would be great, but there's no good VOTable support in SolarSoft
[17:08:36] <Cadair> burn it
[17:08:52] <jhourcle> so I've got a proposal to just return the FITS headers w/ no data … just need to figure out if routines choke on 'em or not … or leave it to people to look at 'em on their own
[17:09:04] <jhourcle> burn SolarSoft ?  I wish
[17:09:10] <Cadair> yes, burn it
[17:09:30] <Cadair> it can't do this: http://imgur.com/a/5pPAH#0
[17:09:44] <jhourcle> the problem is, there's too many people wedded to it, and it'd take man years to replace it all, and test it sufficiently for mission support
[17:10:30] <jhourcle> it can't do what?  draw grid lines at the wrong Rsun ?
[17:10:54] <Cadair> jhourcle, it's not wrong, it is just based on the photosphere
[17:10:57] <jhourcle> or are you assuming the grid's at the ...
[17:11:02] <jhourcle> I was just going to say that
[17:11:14] <Cadair> it uses the WCS information
[17:11:23] <jhourcle> damned optically thin layers
[17:11:31] <Cadair> so if it is wrong then I blame JSOC
[17:11:56] <jhourcle> pretty sure the WCS stuff is right … 
[17:12:05] <jhourcle> I can't say I've ever personally checked it, though
[17:12:09] <Cadair> it bloody well better be
[17:12:27] <jhourcle> Jack Ireland found some questionable stuff in HEK, though
[17:12:41] <Cadair> I did something pretty funky with HEK yesterday
[17:12:53] <Cadair> the first time it has actually been useful for something I thought it should be
[17:12:57] <jhourcle> mostly, it seemed to be that they were inconsistent about if locations were at the start, middle or end of an event
[17:13:15] <jhourcle> yay, that only took … um … 4 years ?
[17:13:41] <Cadair> I used it to find all AR's that emerge on disk and not on limb
[17:13:58] <Cadair> then I queried the VSO to get the data
[17:14:09] <Cadair> it took 13 hours to download one event
[17:14:17] <Cadair> of HMI magnetogram data
[17:14:22] <Cadair> I found 53
[17:15:04] <jhourcle> ah … so you want the rice'd data, so it's faster to download ?
[17:15:21] <Cadair> jhourcle, as far as I can tell the tars that came back were piced
[17:15:23] <Cadair> *riced
[17:15:31] <Cadair> but I actually haven't confirmed that
[17:15:33] <jhourcle> it might default to that for tarballs … I can't remember
[17:15:43] <jhourcle> part of the goal is to keep the tarballs under 2GB each
[17:15:51] <Cadair> I am basing that on the fact the data wasn't in the primary HDU
[17:16:05] <jhourcle> yeah, that's likely compressed, then
[17:16:12] <jhourcle> look for 'ZNAXIS'
[17:16:21] <Cadair> I need to work out a way to speed this up
[17:16:23] <jhourcle> well, headers starting with a 'Z' in general
[17:16:33] <Cadair> the downloader in SunPy is already threaded
[17:16:36] <jhourcle> oh … fuck...
[17:16:40] <Cadair> I think I need mooorrrr threads
[17:16:44] <jhourcle> no, don't do that.
[17:16:44] <Cadair> jhourcle, ?
[17:16:51] <jhourcle> this was HMI/?
[17:16:54] <Cadair> yeah
[17:17:10] <jhourcle> so about 3 weeks ago, there was a whole bunch of crap that went wrong at the JSOC
[17:17:18] <Cadair> ^.o
[17:17:34] <Cadair> seriously who designed this?
[17:17:34] <jhourcle> one of which is that their system that manages the early HMI data went to hell
[17:17:46] <jhourcle> physicists.
[17:17:49] <Cadair> I saw something about that
[17:18:02] <jhourcle> so they're rate-limiting us
[17:18:02] <Cadair> this data was 2011-01-16 ish
[17:18:18] <jhourcle> I've heard different stories about what's affected
[17:18:26] <jhourcle> making me believe that there's more than one thing that went wrong.
[17:18:47] <jhourcle> one of the things that went wrong is that someone 'cleaned up' and deleted a ton of stuff on disk.
[17:18:54] <Cadair> o.o
[17:18:55] <jhourcle> like 200TB, I think it was
[17:19:00] <Cadair> O.O(
[17:19:01] <Cadair> O.O
[17:19:01] <jhourcle> which they've now got to restore from tape
[17:19:08] <Cadair> *facedesk*
[17:19:27] <jhourcle> and because of their complicated system ...
[17:19:36] <jhourcle> they can't just load all of the files from a given tape
[17:19:47] <Cadair> why not just stick it all in one massive-ass SQL databse?
[17:20:04] <jhourcle> and of course, these are tapes have to be manually loaded as it's older stuff
[17:20:06] <Cadair> or at least all the header info with links to the data
[17:20:16] <jhourcle> and if you get 6 tapes waiting to be loaded, NOTHING ELSE can process
[17:20:17] * Cadair jumps off a bridge
[17:20:21] <jhourcle> actually, it is.
[17:20:25] <Cadair> IT IS
[17:20:30] <jhourcle> but again, the scientists designed it.
[17:20:41] <Cadair> bnbnbn
[17:20:45] <VaticanCameos> Massive ass SQL database = data warehouse
[17:20:45] <jhourcle> the headers are, at least.
[17:20:52] * VaticanCameos fades back into obscurity
[17:20:55] <jhourcle> actually, that's part of the problem.
[17:21:00] <Cadair> what
[17:21:09] <jhourcle> the problem is … because all of the FITS headers are stored in the database ...
[17:21:36] <jhourcle> they've stripped all of the scientifically useful data out of the FITS files on disk
[17:21:55] <jhourcle> so you have to run this 'export_as_fits' process for everything that someone wants
[17:22:05] <jhourcle> every damned file, to reattach the headers
[17:22:12] <Cadair> what the hell
[17:22:15] <jhourcle> yes
[17:22:19] <Cadair> why
[17:22:20] <Cadair> why
[17:22:21] <Cadair> why
[17:22:23] *** VaticanCameos is now known as CaptainObvious
[17:22:32] <Cadair> +1 on Cadair 
[17:22:37] <CaptainObvious> can't believe this one isn't taken yet
[17:22:48] <jhourcle> because like I said … data system designed by the physicists
[17:22:50] <Cadair> s/Cadair/CaptainObvious 
[17:22:50] <SunPyBot> Cadair meant to say: +1 on CaptainObvious  
[17:22:59] <CaptainObvious> XD
[17:23:10] <Cadair> jhourcle, what was the thought process behind that?
[17:23:38] <jhourcle> http://xkcd.com/793/
[17:23:41] <Cadair> why not just have a parameter in the database that tells you the last time the FITS header on disk was updates?
[17:23:53] <jhourcle> because they NEVER update them on disk
[17:24:15] <Cadair> why?
[17:24:15] <jhourcle> so, back to the VOTable discussion ..
[17:24:31] <Cadair> oh please
[17:24:35] <jhourcle> because that could introduce errors in the archive
[17:24:45] <Cadair> jhourcle, but you just check the update
[17:24:48] <jhourcle> no, seriously … VOTable … it relates back
[17:25:01] <Cadair> go
[17:25:05] <jhourcle> oh .. did I mention that their giant SQL database never updates?
[17:25:10] <Cadair> WHAT
[17:25:12] <jhourcle> only inserts new records
[17:25:21] <Cadair> WHAT WHAT WHAT WHAT WHAT
[17:25:27] <jhourcle> so you have to try to figure out for a given observation which is the most recent one
[17:25:36] <Cadair> THEN WHAT IS THE ACTUAL POINT?!
[17:25:39] <CaptainObvious> That sounds suspiciously like a data warehouse.
[17:25:51] <jhourcle> it was designed for helioseismology
[17:25:53] <CaptainObvious> Those don't update.
[17:26:00] <Cadair> jhourcle, what?
[17:26:18] <jhourcle> it was designed for their specific scientific niche
[17:26:21] <Cadair> I will update you CaptainObvious is you are not careful
[17:26:28] <jhourcle> and they don't give a shit about anything else.
[17:26:31] <CaptainObvious> xD
[17:26:37] <Cadair> jhourcle, why does helioseismology not want the records to update?!
[17:27:15] <jhourcle> so they have transactional consistenency for long-running jobs, I think
[17:27:38] * Cadair cries
[17:27:46] <jhourcle> I mean, in theory, with their design, they could do some pretty cool stuff to say 'what would the result have been if I had run this in 2012?'
[17:28:13] <jhourcle> of course, that's not why they designed it that way … I know because when I was there ~2 weeks ago, they were talking about how they'd go about doing it.
[17:28:27] <Cadair> go about doing what?
[17:28:36] <jhourcle> trying to run a query as if it were in the past
[17:28:40] <Cadair> also why would you want to do that?!
[17:28:55] <Cadair> surely if you have updated the data then you did it for a good reason
[17:29:03] <jhourcle> if data's been updated since someone published a paper
[17:29:06] <Cadair> i.e. because it was *wrong*
[17:29:11] <jhourcle> see if the results differ
[17:29:17] <jhourcle> now vs. back when they got the data
[17:29:21] <Cadair> I suppose
[17:29:36] <Cadair> still never mind.
[17:29:42] <Cadair> jhourcle, VOTable?
[17:29:47] <jhourcle> yes, VOTable
[17:29:59] <jhourcle> VOTable has this great little feature where you can 'link' to a FITS file
[17:30:12] <jhourcle> so you can say 'here's the header info, but the data's over in this FITS file'
[17:30:21] <Cadair> +many
[17:30:40] <jhourcle> So, we could archive a FITS file … and then never need to update it...
[17:30:57] <jhourcle> we just make a new VOTable file that has the corrected info
[17:31:27] <Cadair> well that sounds like a very sensible idea
[17:31:30] <jhourcle>  tried proposing to the FITSBITS mailing list to do the same thing in FITS … but they acted like I had no idea what the hell I was talking about
[17:31:39] <jhourcle> so I'm guessing I didn't explain myself well enough
[17:31:44] <Cadair> FITSBITS?
[17:32:17] <jhourcle> it's a mailing list w/ lots of FITS contributors … Bill Pence, Bill Thompson, Arnold Rots, lots of europeans, etc.
[17:32:34] <Cadair> right
[17:33:11] <Cadair> Solar Physics is in for a shock in a decade or two if it dosen't start pulling it's head out of it's software arse
[17:34:08] <jhourcle> I would think that this would be one of those things that the Astronomy community would have to deal with.
[17:34:20] <Cadair> yeah they built VOTable?!
[17:34:28] <jhourcle> good point … 
[17:34:43] <jhourcle> they don't need to use FITS
[17:34:52] <Cadair> I have discovered so much stuff from working with the astropy folks
[17:34:52] <jhourcle> whereas the Solar community is tied to FITS
[17:34:56] *** Quits: sarwarc (~livingsto@115.248.45.78) (Ping timeout: 265 seconds)
[17:35:06] <Cadair> Astro uses FITS very heavily, as much if not more than us
[17:35:09] <jhourcle> there were a few proposals for FITS a few months ago ...
[17:35:19] <jhourcle> they use both FITS *and* VOTable
[17:35:23] <Cadair> true
[17:35:30] <Cadair> we should start using VOTable
[17:35:33] <jhourcle> they don't use FITS for stuff where it's the wrong thing to use.
[17:35:34] <jhourcle> well, they do.
[17:35:41] <jhourcle> but not 100% of the time.
[17:35:54] <jhourcle> although, they don't use IDL save files, so that's a plus to them
[17:36:02] <jhourcle> #$@$^$&#$ LMSAL
[17:36:11] <Cadair> anyone who uses an IDL save file I will personally slap with a cod
[17:36:16] <jhourcle> Sam Freeland
[17:36:23] <Cadair> pass me my cod of slapping
[17:36:28] *** Quits: examon1 (~exo@auth47-241.fi.muni.cz) (Quit: Leaving.)
[17:36:35] *** Joins: examon2 (~exo@auth47-241.fi.muni.cz)
[17:36:42] <jhourcle> although, there's a python IDL reader
[17:36:47] <Cadair> yeah
[17:36:54] <Cadair> that is saner than the one in IDL
[17:36:58] <jhourcle> that's been blessed by RSI / ITT
[17:37:09] <Cadair> indeed
[17:37:21] <jhourcle> I tried getting official blessing for the perl one … had to do a bit of an end-run on it.
[17:38:03] <jhourcle> and the perl one, although it only got added into PDL ~1 year ago, was actually written for IDL 4 … so it doesn't know about the changes in IDL7 save files
[17:38:20] <Cadair> oh ewww
[17:38:34] *** Joins: sarwarc (~livingsto@115.248.45.78)
[17:38:41] <jhourcle> I actually had a problem when LMSAL went to IDL7 ...
[17:38:59] <jhourcle> suddently, I couldn't read the TRACE and Hinode catalogs from the machine I use, as it was still on IDL6
[17:39:16] <Cadair> OH WHAT
[17:39:38] <jhourcle> yeah, because they were writing files that weren't backwards compatable
[17:39:45] <Cadair> XD
[17:39:59] <Cadair> I can't wait for IDL to die
[17:39:59] <jhourcle> one of the reasons of why not to use proprietary formats
[17:40:30] <jhourcle> it won't happen … to much code is written in IDL
[17:40:32] <Cadair> I will burn it, personally if I can afford it
[17:40:47] <jhourcle> the best thing you can do is re-write everything you need
[17:40:55] <Cadair> I will reduce it to a historical irrelevance
[17:40:59] <jhourcle> to make it easier for other people to migrate off.
[17:41:10] <Cadair> and make the alternative so good people want to re-write their code
[17:41:41] <jhourcle> don't re-write code.
[17:41:57] <jhourcle> that's something to avoid at all costs.
[17:42:03] <jhourcle> I've made that mistake way too many times.
[17:42:07] <jhourcle> look at Netscape
[17:42:11] <Cadair> write, new, better code
[17:42:24] <Cadair> with a replacement feature set
[17:42:30] <jhourcle> you think 'oh, my stuff's looking kinda ugly, I'll rewrite it all using (insert new technique/language here)'
[17:42:46] <jhourcle> and then you spend the week re-writing it … and then a month debugging it ...
[17:43:13] <jhourcle> https://xkcd.com/349/
[17:43:39] <Cadair> lol
[17:43:56] <Cadair> it must die jhourcle 
[17:44:45] <Cadair> it is the only way
[17:45:01] <Cadair> we must purge the demon, kill it with fire.
[17:46:47] <jhourcle> so long as there are missions that rely on it, you can't kill it.
[17:47:00] <jhourcle> and no one's going to re-write all of the stuff for past missions
[17:47:12] <Cadair> yes
[17:47:16] <jhourcle> so provided that there's useful data from past missions, you can't kill it.
[17:47:22] <Cadair> that is inescapable
[17:47:28] *** Quits: CaptainObvious (~SVXX@182.68.205.231) (Quit:  HydraIRC -> http://www.hydrairc.com <- Now with extra fish!)
[17:47:43] <Cadair> However you can provide some of the functionality
[17:47:52] <Cadair> i.e high level data processing
[17:48:34] <jhourcle> I think we need a concerted software development effort within solar physics
[17:48:43] <Cadair> yes
[17:48:45] <jhourcle> no so ad-hoc
[17:48:46] <Cadair> totally
[17:49:01] <Cadair> everyone should start contributing to SunPy obv
[17:49:16] <jhourcle> I think it shouldn't be tied to one language
[17:49:27] *** Quits: sarwarc (~livingsto@115.248.45.78) (Ping timeout: 265 seconds)
[17:49:32] <Cadair> you have to have a front-end language
[17:49:34] <jhourcle> we need a system where you could pick and choose bits from diff. languages, for whatever makes sense for you
[17:49:49] <Cadair> that just makes things ugly
[17:49:52] <jhourcle> okay, so we have a Perl front-end ...
[17:50:09] <Cadair> what kind of things are you talking about?
[17:50:09] <jhourcle> wait, no, Ruby
[17:50:27] <Cadair> applications?
[17:50:32] <Cadair> what applications?
[17:50:35] <jhourcle> both pipeline processing and ad-hoc
[17:50:45] <Cadair> you need to pick a data processing language
[17:50:52] <jhourcle> R?
[17:50:55] <Cadair> otherwise you have to repeat yourself
[17:51:00] <jhourcle> oh, wait, I know … IDL
[17:51:11] <jhourcle> it's got 'data language' right in the title.
[17:51:17] <Cadair> *facedesk*
[17:52:09] <jhourcle> oh, crap … I need to get back to trying to get my processes started ...
[17:52:10] <Cadair> The thing is that, most of the tools that you could happily abstract into C or something so they can be called from wherever are already like that 
[17:52:22] <Cadair> wcslib, fits, etc.
[17:52:33] <jhourcle> there's a fair bit of command line stuff … 
[17:52:55] <jhourcle> but we might want to think even grander ...
[17:53:04] <Cadair> like how?
[17:53:06] <jhourcle> for instance, there are a number of 'grid computing' platforms
[17:53:26] <jhourcle> so you can write your code, and then send it over to near the data to be run
[17:53:40] <Cadair> that would be nice
[17:53:40] <jhourcle> now, we'd run into issues with resource utilization ...
[17:53:58] <jhourcle> but if you didn't have to download all of the HMI data to do your analysis ...
[17:54:04] <jhourcle> if you could just run it at the JSOC ...
[17:54:18] <jhourcle> reduce it down to something manageable ...
[17:54:33] <Cadair> yep
[17:54:35] <jhourcle> what I hate is when someone goes and downloads 2TB of data ...
[17:54:42] <Cadair> yeah it's a PITA
[17:54:45] <jhourcle> and then goes 'nope, this wasn't what I wanted'
[17:54:56] <Cadair> that's even more retarded
[17:55:01] <jhourcle> we just wasted their time, and the bandwidth of so many places
[17:55:13] <jhourcle> I *hate* that one of the key metrics that people use is 'bytes downloaded'
[17:55:29] <jhourcle> oh, look, more people downloaded our data!
[17:55:45] <jhourcle> yeah, well, you only have 200GB total … so 10x the people downloading your data is a joke.
[17:55:57] <jhourcle> for us, it means that our bandwidth got saturated for days
[17:56:19] <jhourcle> we're still trying to figure out how we can get data to the Koreans so that they're not pounding on the JSOC so hard
[17:56:42] <Cadair> jhourcle, that is the other thing I wanted to ask
[17:56:45] <Cadair> the data mirrors
[17:57:07] <Cadair> we have this:https://github.com/sunpy/sunpy/blob/master/sunpy/net/vso/vso.py#L528
[17:57:18] <Cadair> that allows the user to add a 'site' flag
[17:57:35] <jhourcle> right now, we've got some issues at the SDAC
[17:57:50] <jhourcle> NSO and SAO have been serving all of the data
[17:58:08] <jhourcle> the problem is, that 'export_as_fits' command ...
[17:58:15] <jhourcle> it's been failing here at the SDAC for HMI data
[17:58:39] <jhourcle> so I've made it so that unless you expicitly ask for SDAC, we'll push you elsewhere
[17:58:55] <jhourcle> and the failing isn't a 100% thing … it's just … unreliable.
[17:59:14] <jhourcle> right … I was supposed to test to see if the updated code made a difference ...
[17:59:16] <Cadair> jhourcle, have you got some way I can test if our implementation of 'site' is doing what it should be
[17:59:28] <Cadair> a test query or sthg
[17:59:33] <jhourcle> check what the URLs you get back are
[17:59:41] <jhourcle> use 'nso' and 'sao' for the 'site'
[18:00:07] <jhourcle> when you run the 'vso.get' or whateer the method is … you should get back different URLs
[18:00:17] <jhourcle> nso should give you … um ...
[18:00:22] <jhourcle> vso2.tuc.noao.edu
[18:00:38] <jhourcle> sao is um … something.cfa.harvard.edu
[18:00:59] <jhourcle> sdac should give sdo4.nascom.nasa.gov
[18:01:28] <jhourcle> you don't need to actually download anything … just sent the 'GetData' SOAP call
[18:01:36] *** Joins: sarwarc (~livingsto@115.248.45.78)
[18:05:47] <Cadair> jhourcle, It does seem to be working
[18:06:23] <Cadair> jhourcle, it is defaulting to this:http://sao.virtualsolar.org/cgi-bin/VSO/drms_export.cgi?series=aia__lev1;record=171_1167609647-1167609647
[18:07:30] <jhourcle> that's SAO … that'd fine
[18:07:42] <jhourcle> I guess they're not using the 'whatever.cfa.harvard.edu' anymore
[18:07:59] <Cadair> jhourcle, if I request HMI data from say UCLAN, will I avoid the tape chaos?
[18:08:05] <jhourcle> nope
[18:08:12] * Cadair swears
[18:08:15] <Cadair> why not?
[18:08:25] <jhourcle> the 'sites' are actually caches
[18:08:50] <jhourcle> if one of the VSO sites has it, we pass it among ourselves … if not, we have to go to the JSOC
[18:09:07] <jhourcle> and for older data, odds are, we're going to have to go to the JSOC … no matter where you try
[18:09:24] <Cadair> so there is a chance it will make it faster
[18:09:35] <Cadair> but potentially unlikely?
[18:09:54] <jhourcle> well, the benefit of using something that's closer to you (internet wise)
[18:10:13] <jhourcle> is that they can pull it Rice compressed, then it's only traveling expanded a short distance
[18:10:34] <Cadair> I thought I was pulling it all RICE compressed anyway?
[18:10:34] <jhourcle> but I know that SAO has the best bandwidth to the JSOC … most of the time...
[18:10:44] <jhourcle> well, for tarballs … yes
[18:10:53] <jhourcle> here's something else you might want to do ...
[18:11:01] <jhourcle> you know what time ranges you care about, right ?
[18:11:04] <Cadair> yeah
[18:11:17] <jhourcle> do you know which 'series' of data it is?
[18:11:28] <Cadair> I don't know what that measn
[18:11:30] <Cadair> *means
[18:11:38] <jhourcle> that'd be a no, then.
[18:11:49] <jhourcle> so, the JSOC system is spread out across … well ...
[18:11:55] <jhourcle> they call 'em 'series'
[18:12:07] <jhourcle> basically, each one is a different type of processing that's been applied.
[18:12:25] <jhourcle> so there's the 'hmi.m_45s' is the LOS magnetic field
[18:12:33] <jhourcle> 'hmi.v_45s' are doppler
[18:12:44] <Cadair> it is all him._45s
[18:13:01] <Cadair> s/him._45s/hmi.m_45s
[18:13:02] <SunPyBot> Cadair meant to say: it is all hmi.m_45s
[18:13:02] <jhourcle> almost all are hmi.*_45s
[18:13:08] <jhourcle> okay then … 
[18:13:27] <Cadair> my CSO query is this:vsoq = [vso.attrs.Time(region['start_time']-datetime.timedelta(days=1), region['end_time']),
[18:13:27] <Cadair>             vso.attrs.Instrument('HMI'), vso.attrs.Physobs('LOS_magnetic_field')]
[18:13:42] <Cadair> s/CSO/VSO
[18:13:42] <SunPyBot> Cadair meant to say: my VSO query is this:vsoq = [vso.attrs.Time(region['start_time']-datetime.timedelta(days=1), region['end_time']),
[18:13:45] <jhourcle> we are going to make the JSOC to the work
[18:14:02] <jhourcle> go to : http://jsoc.stanford.edu/ajax/exportdata.html
[18:14:19] <Cadair> oh man I hate this web interface
[18:14:27] <jhourcle> give me a date range
[18:14:45] <Cadair> I love the warning on the top of that page
[18:14:55] <jhourcle> oh … right ...
[18:15:04] <jhourcle> is it before 2011?
[18:15:08] <Cadair> some of it
[18:15:15] <jhourcle> okay, let's try one that isn't .
[18:16:14] <Cadair> 2013-12-09 03:00:00 2013-12-11 08:00:00
[18:16:42] <Cadair> jhourcle, I want this whole set: http://bpaste.net/show/193555/
[18:17:10] <jhourcle> um … email address ?
[18:17:16] <Cadair> stuart@mumford.me.uk
[18:17:22] <jhourcle> I'm not 100% sure on the syntax … might have to try a few.
[18:17:27] <Cadair> I can do this
[18:17:34] <Cadair> but thanks
[18:17:46] <jhourcle> hmi.m_45s[2013-12-09T03:00:00TAI/53h]
[18:17:54] <jhourcle> says it's 4240 records
[18:18:10] <jhourcle> syntax is :
[18:18:24] <jhourcle> seriesname[dateTtime/duration]
[18:18:39] <Cadair> oh what
[18:19:02] <jhourcle> there's some other stuff you can do, but I have yet to find a simple guide to their syntax
[18:19:06] <Cadair> does this page have a simple web call or something I can script
[18:19:18] <jhourcle> yeah, it's all JSON backend
[18:19:30] <jhourcle> do you have firebugs or similar?
[18:19:44] <Cadair> I can do
[18:19:46] <jhourcle> if so, turn on the 'network' tab ...
[18:19:57] <jhourcle> submit a request, then look at what & where it's sending it.
[18:20:14] <Cadair> jhourcle, why is this going to be faster than VSO?
[18:20:28] <Cadair> also, I need to put "hmi.m_45s[2013-12-09T03:00:00TAI/53h]" in RecordSer?
[18:20:32] <jhourcle> yes
[18:20:43] <jhourcle> it's because the JSOC has the data
[18:20:49] <jhourcle> you cut out the middle man
[18:20:56] <jhourcle> of course, they have to stage it all first
[18:21:06] <jhourcle> the VSO tries to do it all without staging ...
[18:21:16] <jhourcle> so we run their 'export_as_fits' command as a CGI
[18:21:16] <Cadair> jhourcle, explain this pipeline?
[18:21:45] <jhourcle> and rather than write it to disk, we stream the output … but for tarballs, we have to wait for each file to transfer from the JSOC
[18:21:57] <jhourcle> and right now, they're rate-limiting us for some of the series
[18:22:23] <jhourcle> so we ask for a file, and they tell us to try back later … so our CGI hangs and dies
[18:22:38] <jhourcle> it's really, really awful
[18:23:00] <jhourcle> but we were told if we didn't use their software for returning the data, they wouldn't support the users who downloaded it
[18:23:33] *** Joins: VaticanCameos (~SVXX@182.68.205.231)
[18:24:16] <jhourcle> I think I have the recordset wrong
[18:24:17] <jhourcle> try :
[18:24:19] <Cadair> mother of god
[18:24:34] <jhourcle> hmi.m_45s[2013.12.09_03:00:00_TAI/53h]
[18:24:41] <jhourcle> looks like you can also do:
[18:25:22] <jhourcle> hmi.m_45s[2013.12.09_03:00:00_TAI-2013.12.11_08:00:00_TAI]
[18:25:41] <jhourcle> oh … one thing, though … the VSO uses UTC, not TAI
[18:25:51] <Cadair> what is the difference?
[18:26:00] <jhourcle> um … a few seconds
[18:26:10] <Cadair> oh I don't care about a few seconds
[18:26:16] <jhourcle> http://www.leapsecond.com/java/gpsclock.htm
[18:26:20] <Cadair> as long as the resultant header is right
[18:26:23] <VaticanCameos> http://www.quickmeme.com/img/15/1539173f8e749b71c51de6ef3d4db3d9be1da056197fc4297c5c77c53729feca.jpg
[18:26:33] <jhourcle> 35 leap seconds
[18:26:49] <Cadair> VaticanCameos, +1 to that
[18:26:55] <jhourcle> TAI = atomic clock time, no leap seconds
[18:27:01] *** Joins: derdon (~quassel@catv-89-132-224-69.catv.broadband.hu)
[18:27:04] <Cadair> jhourcle, how do you enable firebug 
[18:27:46] <jhourcle> um … there's a menu … one sec … I'm in Safari right now
[18:27:59] <jhourcle> Tools -> Web Developer
[18:28:55] <jhourcle> Tools -> Web Developer -> FireBug -> Open Firebug
[18:29:04] <jhourcle> then it'll split your screen ...
[18:29:10] <jhourcle> make sure to select the 'net' tab
[18:30:10] <Cadair> this is a PITA
[18:30:35] <jhourcle> VaticanCameos : so before SDO launched, there was a meeting at Stanford.  And we gave our little 10 min talk of 'we'll make data available via the VSO'
[18:30:52] <jhourcle> and then there was the talk from the JSOC … where they went and tried to explain how to query using their tools
[18:31:16] <jhourcle> and I shit you not, Phil (the HMI PI), said 'after 6 months you might be able to do something almost useful'
[18:31:21] <jhourcle> that quote has stuck with me.
[18:31:22] <VaticanCameos> jhourcle: you mean Cadair right o.o
[18:31:38] <jhourcle> re: your meme
[18:31:50] <VaticanCameos> Ah
[18:31:55] <jhourcle> so not understanding the syntax … 
[18:32:01] <Cadair> jhourcle, holy fuck, seriously who let these people loose with all the data from the most important solar satellite in 20 years
[18:32:05] <jhourcle> '6 months' 'almost useful'
[18:32:10] <VaticanCameos> Damn
[18:32:19] <jhourcle> not, you'd actually understand it after 6 months ...
[18:32:28] <Cadair> I am going to make JSOC bleed
[18:32:54] <jhourcle> the AGU meeting after SDO launched, Joe Gurman chaired a session on SDO data...
[18:33:07] <jhourcle> standing room only … it was PACKED
[18:33:08] <Cadair> I have decided that the easiest way of doing this is to get Python to write out a RecordSet file and then push it through this web interface
[18:33:35] <jhourcle> for the poster session, we had our VSO poster, and the little sheet w/ sample IDL commands to get SDO data ...
[18:34:25] <jhourcle> and I had my joke of a flowchart : http://vso1.nascom.nasa.gov/sdo/sdo_flowchart.pdf
[18:34:48] <jhourcle> the JSOC folks had a 24 page book on how to use their web interface
[18:35:37] <Cadair> holy crap that flowchart is terrifying
[18:35:49] <jhourcle> I should make a new one … add sunpy
[18:36:15] <jhourcle> the reason I say it's a joke as the first version had 'are you a masochist?' as the first question
[18:36:21] <Cadair> jhourcle, What is NetDRMS and what does it do?
[18:36:24] <Cadair> jhourcle, nice
[18:36:36] <jhourcle> NetDRMS is the software that the JSOC wrote
[18:36:44] <jhourcle> that we have to run at the VSO sites to serve the data
[18:36:55] <Cadair> they WROTE THEIR OWN NET SOFTWARE
[18:37:02] <Cadair> oh dear
[18:37:09] <jhourcle> they wrote their own tape drivers
[18:37:13] <jhourcle> single threaded.
[18:37:31] <jhourcle> they had to re-write 'em when they realized it was taking 15hrs to restore a day's worth of data
[18:37:47] <Cadair> AHAHAHAHHAHHAHAHAHAHAHAHAHHHAHAHAHAHHAHAHAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
[18:37:52] <jhourcle> and they had just deleted 2 months of data
[18:38:24] <Cadair> this timestamp makes no sense I am going to have to build it from the ground up
[18:38:51] <jhourcle> YYYY.MM.DD_HH:mm:ss_TAI
[18:38:56] <Cadair> yeah that
[18:38:56] <jhourcle> dots between date parts
[18:39:08] <jhourcle> underscore, time
[18:39:17] <jhourcle> underscore, 'TAI'
[18:40:24] <jhourcle> okay, the guide to how to write a JSOC query ...
[18:40:32] <jhourcle> it's kinda screwed up, because they don't call it a query
[18:40:41] <jhourcle> they call it a 'dataset name'
[18:41:07] <jhourcle> they came up with all sorts of new terms to describe things because they had no idea what they were doing.
[18:41:11] <jhourcle> http://jsoc.stanford.edu/jsocwiki/AllAboutJsocNames
[18:41:59] <jhourcle> the main document is http://hmi.stanford.edu/doc/JSOC/DRMS_dataset_names.pdf , but you'll want to slam your head against the wall repeatedly after reading it.
[18:42:06] <Cadair> this is why I use the VSO
[18:42:29] <jhourcle> I've actually thought about making a little VSO query to DRMS query tool.
[18:42:47] <jhourcle> specify the inputs in VSO terms, we tell you what to use for the JSOC
[18:42:48] <Cadair> sounds handy
[18:42:54] *** Quits: examon2 (~exo@auth47-241.fi.muni.cz) (Quit: Leaving.)
[18:42:57] *** Joins: 1JTAAVD9B (~exo@auth47-241.fi.muni.cz)
[18:43:05] <jhourcle> the problem is, one VSO query might require 10+ JSOC queries
[18:43:17] <jhourcle> as we don't have a 'one series at a time' limitation
[18:43:48] <jhourcle> oh … one warning if you read the JSOC documentation.
[18:43:49] <Cadair> jhourcle, is it easy to throw these queries to JSOC from a script?
[18:44:08] <jhourcle> 'prime key' is NOT a typo for 'primary key'
[18:44:16] <jhourcle> it's some other concept they came up with
[18:44:29] <jhourcle> I think you can … it's just a CGI
[18:44:43] <jhourcle> so you just have to form the URL to make the requests
[18:44:48] <jhourcle> then send 'em
[18:45:06] <jhourcle> you'll get back a JSON response if it was accepted or not
[18:47:09] <Cadair> if i have got this wrong JSOC are going to hate me
[18:47:24] <Cadair> I think I just asked them for:
[18:47:30] <Cadair> .py 53*60
[18:47:31] *** Quits: 1JTAAVD9B (~exo@auth47-241.fi.muni.cz) (Client Quit)
[18:47:31] <SunPyBot> 3180
[18:47:35] <Cadair> 3.1TB of data
[18:47:51] <jhourcle> heh
[18:47:58] <Cadair> jhourcle, it returned a 500
[18:48:07] <jhourcle> okay, then they didn't like it.
[18:48:35] <Cadair> no sensible error
[18:48:38] <Cadair> just a 500
[18:48:42] <jhourcle> blah
[18:48:50] <jhourcle> let me try …same time range.
[18:49:25] <Cadair> jhourcle, do you happen to know the format of the file they want if you upkoad a list of ranges?
[18:50:45] <jhourcle> ah, it's a POST
[18:50:47] <jhourcle> not a GET
[18:51:05] <Cadair> indeed
[18:51:08] <jhourcle> I don't know if you can upload a list
[18:51:19] <jhourcle> you'd have to each one as a seperate request
[18:51:27] <Cadair> it gives you the option
[18:51:30] <Cadair> the first tick box
[18:51:43] <Cadair> "{"requestid":"VOID","method":"url","protocol":"FITS,compress Rice","wait":0,"status":3,"count":12850,"size":194300,"error":"Request exceeds max byte limit of 100000MB"} "
[18:51:49] <jhourcle> oh … I have NO IDEA
[18:51:52] <jhourcle> op=exp_request&ds=hmi.m_45s%5B2013.12.09_03%3A00%3A00_TAI-2013.12.11_08%3A00%3A00_TAI%5D&process=n%3D0%7Cno_op&requestor=none&notify=stuart%40mumford.me.uk&method=url&filenamefmt=hmi.m_45s.%7BT_REC%3AA%7D.%7BCAMERA%7D.%7Bsegment%7D&format=json&protocol=FITS%2Ccompress%20Rice
[18:52:18] <jhourcle> response was :
[18:52:19] <jhourcle> {"status":2,"requestid":"JSOC_20140325_334","method":"url","protocol":"FITS,compress Rice","wait":10,"rcount":4241,"size":64080}
[18:52:54] <Cadair> thanks
[18:52:59] <Cadair> hey derdon 
[18:53:05] <Cadair> you about?
[18:53:07] <Cadair> and got 5?
[18:53:21] <derdon> hi Cadair
[18:53:28] <derdon> I got 5? 5 what?
[18:53:32] <Cadair> mins
[18:53:38] <derdon> ah, yes
[18:53:48] <Cadair> what is the quickest and dirtiest way to send a POST request from python
[18:54:05] <derdon> I can tell you the quickiest and best way!
[18:54:08] <derdon> use requests!
[18:54:15] <derdon> *quickest
[18:54:20] <Cadair> I am hoping here that between jhourcle understanding what I want to send and derdon telling me the python we might get somewhere
[18:54:28] <Cadair> derdon, I just loaded up requests
[18:54:32] <derdon> good
[18:54:41] <derdon> it's one of the best python libs if not the best
[18:54:45] <jhourcle> you'll be posting to : http://jsoc.stanford.edu/cgi-bin/ajax/jsoc_fetch
[18:55:05] <derdon> Cadair: do you need some scraping as well or just sending an HTTP request?
[18:55:21] <jhourcle> he just needs the return … it'll be JSON
[18:55:25] <derdon> ah
[18:55:25] <jhourcle> can probably just read it.
[18:55:27] <Cadair> what he said
[18:56:14] <jhourcle> the only field you need to screw with is 'ds=' bit : op=exp_request&ds=hmi.m_45s%5B2013.12.09_03%3A00%3A00_TAI-2013.12.11_08%3A00%3A00_TAI%5D&process=n%3D0%7Cno_op&requestor=none&notify=stuart%40mumford.me.uk&method=url&filenamefmt=hmi.m_45s.%7BT_REC%3AA%7D.%7BCAMERA%7D.%7Bsegment%7D&format=json&protocol=FITS%2Ccompress%20Rice
[18:56:22] <jhourcle> of course, it's URI encoded
[18:56:41] <jhourcle> basically, the bit between 'ds=' and '&process='
[18:58:20] <derdon> uhm, I hope you don't parse the URI yourself manually
[18:58:53] <derdon> there are functions out there to do that. either in requests as well (I'm not sure) or in urllib(2)
[18:59:05] <Cadair> derdon, I would rather build it
[18:59:39] <derdon> Cadair: "building" a URI is just passing a dict to requests.post
[18:59:42] *** Quits: VaticanCameos (~SVXX@182.68.205.231) (Ping timeout: 240 seconds)
[18:59:43] <Cadair> yes
[18:59:44] <Cadair> I see
[18:59:47] <derdon> I think the parameter is called payload
[19:00:10] <Cadair> jhourcle, what is contained in that string when it is not URI encoded?
[19:00:14] <Cadair> derdon, yep
[19:01:57] <jhourcle> ds	hmi.m_45s[2013.12.09_03:00:00_TAI-2013.12.11_08:00:00_TAI]
[19:01:58] <jhourcle> filenamefmt	hmi.m_45s.{T_REC:A}.{CAMERA}.{segment}
[19:01:58] <jhourcle> format	json
[19:01:58] <jhourcle> method
[19:01:58] <jhourcle> urlnotify
[19:01:58] <jhourcle> stuart@mumford.me.uk
[19:01:58] <jhourcle> op
[19:01:59] <jhourcle> exp_request
[19:01:59] <jhourcle> process
[19:02:00] <jhourcle> n=0|no_op
[19:02:00] <jhourcle> protocol
[19:02:01] <jhourcle> FITS,compress Rice
[19:02:13] <Cadair> jhourcle, is god-like
[19:02:38] <jhourcle> ds	hmi.m_45s[2013.12.09_03:00:00_TAI-2013.12.11_08:00:00_TAI]
[19:02:38] <jhourcle> filenamefmt	hmi.m_45s.{T_REC:A}.{CAMERA}.{segment}
[19:02:38] <jhourcle> format	json
[19:02:38] <jhourcle> method	url
[19:02:38] <jhourcle> notify	stuart@mumford.me.uk
[19:02:38] <jhourcle> op	exp_request
[19:02:39] <jhourcle> process	n=0|no_op
[19:02:39] <jhourcle> protocol	FITS,compress Rice
[19:02:40] <jhourcle> requestor	none
[19:03:15] <jhourcle> oh … the VSO uses a different 'filenamefmt' … one sec, I'll check what it is.
[19:05:11] <jhourcle> {seriesname}.{t_rec}.{segment}
[19:05:42] <jhourcle> I have no idea what '{T_REC:A}' means vs. '{T_REC}'
[19:06:59] <Cadair> BOOM!
[19:07:05] <Cadair> (<Response [200]>, {u'status': 2, u'protocol': u'FITS,compress Rice', u'rcount': 2, u'requestid': u'JSOC_20140325_336', u'size': 30, u'method': u'url', u'wait': 10})
[19:07:33] <Cadair> but how do I get the URLs?
[19:07:40] <jhourcle> they'll e-mail you
[19:07:49] <jhourcle> to let you know when it's ready 
[19:08:28] <Cadair> looks like you can GET to check
[19:08:56] <jhourcle> yes
[19:09:04] <jhourcle> there's um … u'JSOC_20140325_336
[19:09:26] *** Joins: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de)
[19:10:00] <jhourcle> down at the bottom of the page
[19:10:17] <jhourcle> 'RequestID'
[19:10:32] <jhourcle> it says that one's done.
[19:10:34] *** Quits: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de) (Client Quit)
[19:10:38] <Cadair> it is
[19:10:41] <Cadair> it was a 2 file job
[19:11:02] <jhourcle> the one I sent was a little bigger
[19:11:02] <jhourcle> JSOC_20140325_334
[19:11:08] <jhourcle> 64GB
[19:11:21] <Cadair> yeah
[19:11:25] <Cadair> why is this not working
[19:11:40] <Cadair> I am doing: GET http://jsoc.stanford.edu/cgi-bin/ajax/jsoc_fetch?op=exp_status&requestid=JSOC_20140325_336
[19:11:40] <Cadair> 	
[19:12:11] <Cadair> http://bpaste.net/show/193585/
[19:12:33] <Cadair> aghhhhh
[19:12:35] <Cadair> my bad
[19:12:47] <Cadair> boom
[19:13:28] <jhourcle> what was it?
[19:13:38] <Cadair> the JSON response dosen't give you the base URL
[19:13:41] <Cadair> I mean really
[19:13:49] <Cadair> jhourcle, Python syntax error
[19:13:53] <jhourcle> ah
[19:19:14] <Cadair> derdon, where is that url join method
[19:19:14] <Cadair> ?
[19:20:09] <derdon> Cadair: I googled for "python urljoin": http://docs.python.org/2/library/urlparse.html#urlparse.urljoin
[19:20:14] <derdon> this was the first result for me
[19:20:29] <derdon> well, technically it was without the anchor
[19:21:04] <Cadair> thanks
[19:21:18] <Cadair> derdon is faster than goofle
[19:21:24] <Cadair> it's like multiprocessing
[19:23:47] <Cadair> jhourcle / derdon : JSOC_20140325_336
[19:23:49] <Cadair> http://bpaste.net/show/193593/
[19:23:54] <Cadair> wrong buffer
[19:29:35] <Cadair> boom!
[19:34:02] <Cadair> jhourcle, will this tarball?
[19:36:18] <Cadair> I made be making JSOC bleed here
[19:36:54] <derdon> I recently discovered "numberwang", it's awesome :D https://www.youtube.com/watch?v=ZH-cXBhkl-E
[19:36:54] <SunPyBot> [YouTube] Title: Number Wang Season One, Episode 1 | Uploader: biggeidea | Uploaded: 08/12/2009, 00:22 | Duration: 1mins 58secs | Views: 8,757 | Comments: 8 | Likes: 44 | Dislikes: 0
[19:37:08] <Cadair> lol numberwang is great
[19:37:13] <Cadair> derdon, requests is bitchin
[19:37:34] <derdon> everything involving mitchell and web is worth watching
[19:37:39] <derdon> Cadair: indeed it is
[19:40:30] <Cadair> damn it
[19:40:35] <Cadair> my request is too big :(
[19:50:23] <Cadair> derdon, finished: http://bpaste.net/show/193600/
[19:50:32] <Cadair> it saves the request ids to a file
[19:51:00] <Cadair> so I can have another script parse the file and check to see if they are done
[19:52:08] <derdon> lines 15/16 look a bit weird to me. you overwrite the value of piks in each iteration without any conditional statement before
[19:52:38] <Cadair> if pik.find(str(ar)) == -1
[19:52:43] <Cadair> it's at the end of the list comp
[19:52:51] <derdon> so basically you could have left out the for loop and just use the last value of complete_ARs directly
[19:53:11] <Cadair> erm
[19:53:23] <Cadair> it does the purge once for each value of ar
[19:53:32] <derdon> piks = [pik for pik in piks if pik.find(str(complete_ARs[-1])) == -1]
[19:53:42] <derdon> isn't that the same? ^
[19:53:49] <Cadair> no
[19:53:52] <Cadair> don't think so
[19:54:04] <Cadair> I am not changing the ars list
[19:55:24] <derdon> that doesn't change anything. I'm still very sure that the for-loop around the LC is unnecessary
[19:55:46] <derdon> because effectively only the last value will be used because the intermediate values will be "forgotten|
[19:56:13] <derdon> and well, use the with-statement for closing files
[19:56:27] <derdon> and never-ever pass open(...) as a parameter
[19:56:58] *** Joins: examon1 (~exo@ip-94-112-98-5.net.upcbroadband.cz)
[19:57:26] <derdon> Cadair: in line 47, couldn't you use ', '.join(foo) + '\n' there?
[19:57:34] <derdon> instead of calling the format method
[19:57:53] * Cadair wonders why I showed my code to derdon 
[19:58:10] <derdon> to get constructive feedback and be happy :)
[19:58:11] <derdon> sorry
[19:58:20] <Cadair> it's ok
[19:58:25] <Cadair> i was joking
[19:59:11] <derdon> why do you call the flush method? is it required?
[19:59:28] <Cadair> no, but it forces a write to file once the loop i sdone
[19:59:36] <derdon> I know what it does ;)
[19:59:46] *** Quits: rishabh (uid26424@gateway/web/irccloud.com/x-ugsjgoomudvayvfl) (Quit: Connection closed for inactivity)
[20:00:00] <Cadair> that's why i do it
[20:00:05] <Cadair> I am watching the file
[20:00:38] <derdon> ah
[20:00:56] <derdon> line 23 should be outside the loop, I think
[20:01:13] <derdon> maybe CPython is clever enough to do that optimization, but who knows
[20:01:17] <jhourcle> cadair : I don't think it tarballs
[20:01:26] <derdon> ah no, forget it
[20:01:52] <derdon> oversaw that it depends on pik. but anyway: with should be used to close files properly
[20:02:20] <derdon> hi jhourcle
[20:02:42] <derdon> jhourcle: have you talked with Cadair about issue #913? https://github.com/sunpy/sunpy/issues/913 haven't read the backlog
[20:02:55] <Cadair> a little
[20:03:26] <jhourcle> actually … does SunPy return warnings?
[20:03:41] <jhourcle> there's a warning message in one of the responses about 'switching to summary mode' or something like that
[20:04:06] <jhourcle> which is one of the indications that it's happened
[20:04:34] <jhourcle> the other is that the 'no_records_returned' or whatever that field is higher than the items in the array
[20:08:38] <Cadair> IT WORKS
[20:08:40] <Cadair> I AM AWESOME
[20:08:46] <Cadair> thanks a lot jhourcle and derdon 
[20:09:13] <derdon> it was your work :)
[20:09:20] <derdon> and thank Kenneth Reitz!
[20:09:24] <Cadair> indeed
[20:09:30] <Cadair> so many of these requests are too big
[20:10:03] <Cadair> derdon, this is the downloader:
[20:10:05] <derdon> so if VSO (the SunPy package) detects too big requests, it should divide it into smaller chunks?
[20:10:08] <Cadair> http://bpaste.net/show/193607/
[20:10:28] <Cadair> derdon, I don't think jhourcle would like us if we did that
[20:10:43] <derdon> what's jhourcle's idea?
[20:10:58] <jhourcle> actually, that's the right approach
[20:11:02] <Cadair> oh, ok
[20:11:07] <Cadair> do that then!
[20:11:08] <derdon> Cadair: +1 for using partial! :)
[20:11:12] <jhourcle> that's the workaround most people do
[20:11:21] <jhourcle> but it'd be NICE if you warned someone about it
[20:11:22] <Cadair> derdon, internet told me to
[20:11:29] <Cadair> jhourcle, like who?
[20:11:30] <derdon> I like internet
[20:11:44] <jhourcle> 'that seems to be 2billion records … are you sure you want to expand that?'
[20:11:46] <jhourcle> the user
[20:11:49] <Cadair> haha
[20:12:50] <jhourcle> (I'm okay with running the queries … looks good in our metrics if you call us 50k times per day)
[20:13:03] <Cadair> sweet
[20:13:15] <Cadair> right
[20:13:19] <Cadair> it is late
[20:13:25] <Cadair> I am going home to my wife and my dinner
[20:13:28] <Cadair> I will ttyl
[20:13:38] <Cadair> thanks once again for your help, this data is coming in much quicker
[20:14:01] <Cadair> it's pulling just over
[20:14:32] <Cadair> .py 959/(7.5*60)
[20:14:33] <SunPyBot> 2.13111111111
[20:14:39] <Cadair> that many MB/s
[20:14:44] <Cadair> which means that
[20:14:52] <jhourcle> it might be done by next week?
[20:15:00] <Cadair> .py 60000/2.13
[20:15:00] <SunPyBot> 28169.0140845
[20:15:07] <Cadair> it will take that many sec to download
[20:15:15] <Cadair> .py 60000/2.13/60/60
[20:15:15] <SunPyBot> 7.82472613459
[20:15:20] <Cadair> or 7 hours
[20:15:24] <jhourcle> .py 64000 / 2.13 / 3600
[20:15:24] <SunPyBot> 8.34637454356
[20:15:31] <Cadair> or 8
[20:15:32] <jhourcle> it was 64000MB
[20:15:48] <jhourcle> sounds like a good time to go for a sandwich, then
[20:15:53] *** Joins: VaticanCameos (~SVXX@182.68.174.22)
[20:16:05] <Cadair> jhourcle, I am going to have to go through all my requests tomorrow and break up the ones that breach their 100GB limit
[20:16:20] <jhourcle> oh … blah
[20:16:30] <jhourcle> break 'em into maybe 3 day chunks
[20:16:36] <Cadair> I will split em in half
[20:16:40] <Cadair> and then in half again
[20:16:44] <Cadair> as required :p
[20:16:50] <jhourcle> that works, too
[20:16:59] <jhourcle> just avoid the pre-2011 ones
[20:17:01] <Cadair> probably only need the one splitting
[20:17:02] <jhourcle> whtever the date is
[20:17:09] <Cadair> jhourcle, nah i sent em anyway :p
[20:17:26] <jhourcle> that's not good.
[20:17:36] <Cadair> I think there was only 1 or 2
[20:17:46] <Cadair> I think
[20:17:47] <jhourcle> okay, okay
[20:17:52] <jhourcle> 6 is where they hit the problem
[20:18:11] <jhourcle> if there's 6 processes waiting for tapes to be manually loaded, it blocks EVERYTHING tape related
[20:18:24] <jhourcle> ie, the tape robot won't process ones already has available to it
[20:18:26] <Cadair> there was 3
[20:18:36] <Cadair> oh no
[20:18:37] <Cadair> only 2
[20:18:43] <Cadair> one in March 2 before
[20:18:56] <Cadair> one was the one I dled yesterday
[20:19:04] <Cadair> so that leaves one I posted today
[20:19:18] <Cadair> which was too big so it didn't go anyway
[20:19:26] <Cadair> so I did none before 2011-03
[20:19:30] <jhourcle> oh, okay.
[20:19:37] <Cadair> right I am actually leaving now
[20:19:49] <Cadair> thanks a *lot* jhourcle 
[20:19:51] <Cadair> ttyl
[20:23:07] <derdon> jhourcle: so if someone requests a lot of data at once from VSO, there is no kind of DOS attack prevention and VSO will be down?
[20:29:16] <jhourcle> there are some precautions
[20:29:44] <jhourcle> for instance, if you try to open up more than 4 HTTP connections to the NetDRMS system at SAO or SDAC, it'll drop 'em
[20:29:53] <jhourcle> so you can't have it making more than 4 tarballs per site
[20:30:13] <jhourcle> I don't know if NSO has installed that fix yet … Igor's been away
[20:31:38] <jhourcle> we have assorted other stuff, as we regularly get ponded by China
[20:31:42] <jhourcle> pounded, even
[21:00:01] *** Quits: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230) (Quit: Page closed)
[21:04:49] *** Quits: VaticanCameos (~SVXX@182.68.174.22) (Ping timeout: 252 seconds)
[21:07:46] <derdon> ah, interesting info!
[21:20:24] *** Quits: examon1 (~exo@ip-94-112-98-5.net.upcbroadband.cz) (Quit: Leaving.)
[21:21:21] *** Joins: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de)
[21:52:24] *** Quits: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de) (Quit: Leaving.)
[22:24:48] *** Quits: renstar (~quassel@18.155.7.137) (Ping timeout: 268 seconds)
[22:26:49] *** Joins: amras1 (328ba9f3@gateway/web/freenode/ip.50.139.169.243)
[23:29:54] *** Joins: renstar (~quassel@c-98-217-130-167.hsd1.ma.comcast.net)
[23:33:38] *** Quits: amras1 (328ba9f3@gateway/web/freenode/ip.50.139.169.243) (Ping timeout: 245 seconds)
[23:49:00] *** Joins: amras1 (328ba9f3@gateway/web/freenode/ip.50.139.169.243)
```
# 26/3/2014
```
[00:27:36] *** Quits: derdon (~quassel@catv-89-132-224-69.catv.broadband.hu) (Ping timeout: 246 seconds)
[01:44:47] *** Joins: rishabh (uid26424@gateway/web/irccloud.com/x-qfzhtptjbsteambp)
[03:03:13] *** Quits: amras1 (328ba9f3@gateway/web/freenode/ip.50.139.169.243) (Ping timeout: 245 seconds)
[03:54:20] *** Joins: VaticanCameos (~SVXX@182.68.191.132)
[03:56:21] *** Joins: mefistofeles (~crush@unaffiliated/mefistofeles)
[04:36:30] *** Quits: VaticanCameos (~SVXX@182.68.191.132) (Read error: Connection reset by peer)
[04:36:44] *** Joins: VaticanCameos (~pls@182.68.3.194)
[04:49:47] *** Quits: rishabh (uid26424@gateway/web/irccloud.com/x-qfzhtptjbsteambp) (Quit: Connection closed for inactivity)
[05:41:13] *** Quits: mefistofeles (~crush@unaffiliated/mefistofeles) (Quit: Hay the guachu!)
[05:41:39] *** Joins: mefistofeles (~crush@unaffiliated/mefistofeles)
[05:41:49] *** Quits: mefistofeles (~crush@unaffiliated/mefistofeles) (Client Quit)
[05:48:55] *** Joins: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230)
[06:46:27] <VaticanCameos> #gsoc is so quiet for now...until April 21st.
[06:51:08] *** Quits: VaticanCameos (~pls@182.68.3.194) (Quit: Leaving)
[07:39:46] *** Parts: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230) ()
[08:34:28] *** Joins: rajul (cb6ef6e6@gateway/web/freenode/session)
[08:35:01] *** Quits: rajul (cb6ef6e6@gateway/web/freenode/session) (Changing host)
[08:35:01] *** Joins: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230)
[10:16:58] <Cadair> Good morning
[10:35:41] *** Joins: VaticanCameos (~SVXX@182.68.172.229)
[10:40:23] *** Quits: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230) (Quit: Page closed)
[11:44:51] *** Joins: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230)
[12:19:50] <Cadair> hey rajul 
[12:25:28] *** Quits: renstar (~quassel@c-98-217-130-167.hsd1.ma.comcast.net) (Ping timeout: 246 seconds)
[12:25:35] <rajul> Cadair: hey
[12:27:16] <Cadair> how are you?
[12:27:30] <rajul> Cadair: i am good....how are you??
[12:27:37] <Cadair> alright
[12:27:44] <rajul> Cadair: did you get a chance to take alook at the proposal??
[12:28:11] <Cadair> I had a quick look
[12:29:00] <rajul> ohh....how did you like it??
[12:31:31] <Cadair> It looks pretty good!
[12:31:31] <rajul> Cadair: i have tried to imrpove the formatting....but still i think the "Project Implementation and tasks" heading looks a bit cluttered...
[12:31:58] <rajul> Cadair: but i could not figure out how to go about writing it...in a better way...
[12:32:44] <rajul> Cadair: what can i do next??
[12:34:05] <Cadair> rajul, I think the text for your "community bonding period" needs updating
[12:34:39] <rajul> Cadair: ohh...right!!
[12:35:47] <rajul> Cadair: done!!
[12:36:10] <Cadair> If you want a bit of code to work on, I would take a look at the astropy.wcs submodule
[12:37:06] <Cadair> you can see how I created one from a Map here: https://gist.github.com/Cadair/9763278#file-solarwcsaxes-py-L46
[12:37:31] <rajul> Cadair: okay....
[12:38:06] <Cadair> Then once you have an idea about those objects I would take a peek in Ginga and work out how it uses them to calculate and display coordinates
[12:38:43] <rajul> Cadair: gereat i shall take alook at these....
[12:38:54] <Cadair> so WCS in case you don't know, is a horrifically complex system that converts pixel coordinates (i.e. array indexes) into world or physical coordinates
[12:38:57] <rajul> i shall start with astropy.wcs...
[12:39:08] <rajul> Cadair: okay....
[12:39:22] <Cadair> However, in general for Solar data we only use a tiny fraction of the whole scope of WCS
[12:39:31] <Cadair> so it's actually not *that* complex
[12:39:38] <Cadair> although still a bit alien
[12:39:51] <rajul> Cadair: hmm....okay!!
[12:41:06] <rajul> Cadair: i also looked into Issue #221 that you suggested to me
[12:41:12] <Cadair> ah yes
[12:41:26] <rajul> there in the file it contains pixel_to_data
[12:41:31] <Cadair> indeed
[12:41:44] <rajul> so it does use wcs for that
[12:41:47] <Cadair> That uses the sunpy.wcs module
[12:42:07] <Cadair> which I found a huge bug in the other day ;)
[12:42:25] <rajul> Cadair: yeah...right!!
[12:42:55] <Cadair> sunpy.wcs seems to ignore the rotation of the data when calculating the coordinate transforms
[12:43:04] <rajul> Cadair: so sunpy.wcs is a subset of astropy.wcs??
[12:43:13] <Cadair> No it is totally seperate
[12:43:19] <Cadair> sunpy.wcs is a bit shit
[12:43:26] <rajul> Cadair: okay....i shall take a look at it too,,,,
[12:43:27] * Cadair checks that ehsteve isn't about
[12:43:37] <rajul> Cadair: ohh...
[12:43:45] <Cadair> However, sunpy.wcs does the job more or less
[12:44:10] <Cadair> In concert with the astropy.coordinates GSOC project I plan to re-work all the WCS handling in SunPy
[12:44:23] <Cadair> to totally replace sunpy.wcs
[12:44:32] <Cadair> if not the API at least all the underlying stuff
[12:44:40] <rajul> Cadair: okay....
[12:46:53] <Cadair> Ginga will undestand a astropy.wcs.WCS object to do the transforms, so that is another good reason to look into using that
[12:47:16] <VaticanCameos> .seen amras1
[12:47:16] <SunPyBot> VaticanCameos: I last saw amras1 at 2014-03-23 13:07:37 UTC on #SunPy, saying It's going well! Glad it's the weekend
[12:47:33] <rajul> VaticanCameos: hey
[12:47:34] <VaticanCameos> He hasn't been a round a lot
[12:47:43] <VaticanCameos> Hello rajul, Cadair 
[12:47:45] <Cadair> rajul, I would be interested to know if it would be possible to loada FITS file in Ginga into a SunPy Map and use that inside Ginga
[12:48:32] <Cadair> because among many other things, Map provides a standard interface to the WCS information in the different types of Solar Data
[12:48:41] <Cadair> hey VaticanCameos how are you
[12:48:45] <rajul> Cadair: okay....i shall take a look at it....
[12:49:12] <rajul> Cadair: in fact i am currently reading up the Ginga documentation only.....
[12:49:18] <Cadair> rajul, that's fine
[12:49:25] <rajul> Cadair: i thought it was needed....
[12:49:26] <Cadair> I am just thinking aloud really
[12:49:32] <Cadair> rajul, indeed!!
[12:49:53] <rajul> Cadair: no its fine...it is helping me get a hang of what need be done :)
[12:50:33] <Cadair> rajul, Nabobalis and I don't actually have any real understanding of the inner workings of Ginga, so it will be important for you to understand them so you can do things in the most sensible way
[12:51:16] <Cadair> rajul, I know the guy who wrote Ginga, so in the community bonding period if the project goes ahead I will try and set up a meeting or two with him to work a few things out
[12:51:21] <rajul> Cadair: yes...i am working on it!!
[12:51:48] <rajul> Cadair: that shall be great!!
[12:53:30] <VaticanCameos> Cadair: pretty good
[12:53:49] <VaticanCameos> Minor stomach blips but otherwise fine lol
[12:54:38] <rajul> Cadair: great....so i shall look into the WCS.....and then Ginga....
[12:55:28] <rajul> Cadair: i am right now reading up on the project idea of astropy's that you mentioned....
[12:56:37] *** Joins: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de)
[12:56:47] *** Quits: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de) (Client Quit)
[12:57:07] <rajul> Cadair: it would be "Implement IAU2000 celestial coordinate transformations", right??
[13:03:11] *** Quits: VaticanCameos (~SVXX@182.68.172.229) (Read error: Connection reset by peer)
[13:04:24] *** Joins: VaticanCameos (~SVXX@182.68.189.10)
[13:04:49] <VaticanCameos> My modem is poppy.
[13:04:51] <Cadair> rajul, no I meant our coordinates project that uses astropy
[13:04:54] <VaticanCameos> Poopy*
[13:05:46] <rajul> Cadair: ohkay....right!!
[13:06:33] <rajul> Cadair: great i shall take a look at it....
[13:07:18] <VaticanCameos> Cadair: how's the slot allocation thingy going
[13:09:10] <rajul> VaticanCameos: for the thompson paper that is mentioned in the project idea for sunpy.coordinates project....
[13:09:16] <rajul> VaticanCameos: i am able to find http://secchi.nrl.navy.mil/wiki/uploads/Main/coordinates.pdf
[13:09:46] <VaticanCameos> rajul: yes, that is the very same
[13:10:12] <rajul> VaticanCameos: ohh thanks.....but this is dated 2005....but in the project description it is mentioned thompson 2009...that why i got confused!!
[13:10:19] <VaticanCameos> The one cadair and co have is slightly abridged I think
[13:10:54] <rajul> VaticanCameos: Cadair and co got??
[13:11:27] <rajul> Cadair: VaticanCameos: can you please send me that.....i shall be glad to take a look just to see what it is about!!
[13:11:38] <VaticanCameos> Yes, if I recall correctly, the sunpy website or wiki has a link to NASA's version if coordinates. Pdf
[13:12:10] <rajul> VaticanCameos: okay....great...i shall look there...thanks!!
[13:12:50] <VaticanCameos> http://fits.gsfc.nasa.gov/wcs/coordinates.pdf
[13:12:56] <VaticanCameos> Of*
[13:14:27] <rajul> VaticanCameos: great....thanks!!
[13:25:27] <Cadair> jhourcle, I have requested 6.82TB of data from JSOC :D
[13:25:51] *** Joins: renstar (~quassel@18.155.7.137)
[13:27:27] <jhourcle> do you have space to hold it?
[13:27:31] <Cadair> yep
[13:27:37] <jhourcle> okay, then not a problem
[13:27:56] <Cadair> I wrote a recursive function to split up the larger queries
[13:28:16] <Cadair> I then realised that this would be an excellent way to DOS JSOC :p
[13:28:20] <jhourcle> I mean, i wish the VSO got credit for the downloads, but the really big jobs are more efficient this way
[13:28:43] <Cadair> jhourcle, I was thinking about using the VSo to return the jsoc series
[13:29:13] <Cadair> basically writing that VSO -> JSOC translator
[13:32:26] <Cadair> __name__, !!!
[13:33:24] <Cadair> __name__, why the hell dosen't the Downloader release it's lock after it has downloaded all the files in it's que?
[13:35:33] <jhourcle> you might get more than one name … but there's a trick.
[13:35:43] <jhourcle> if you use the 'near' logic, it's set so it'll return one per series
[13:36:00] <Cadair> jhourcle, say waht
[13:36:02] <jhourcle> provided there's something in the time span at all
[13:36:25] <jhourcle> because each JSOC 'series' is … well, let's just pretend it's a table
[13:37:10] <Cadair> the near logic is in what? Time?
[13:37:11] <jhourcle> if you ask for  instrument='HMI' and a time 'near'=>'2012-01-01'
[13:37:15] <jhourcle> yeah.
[13:37:29] <jhourcle> you still need to give it bounds (start & end)
[13:37:45] <Cadair> what if I make those bounds very very large?
[13:37:54] <jhourcle> it'll take longer to return
[13:38:04] <Cadair> is there a way to say can I only have the first result please?
[13:38:17] <jhourcle> 'near' is the closest thing to that
[13:38:27] <Cadair> hmmm
[13:38:49] <Cadair> I suppose it doesn't matter about the time range
[13:39:01] <jhourcle> don't go too early in the mission
[13:39:14] <Cadair> if I am trying to go from a instrument + wave etc. search to a JSOC request it is only SDO anyway
[13:39:15] <jhourcle> and as some products take a little time to generate, you want a week back or so
[13:39:28] <Cadair> so if I go mid 2013 it should be sane enough
[13:39:32] <jhourcle> wave doesn't matter for HMI
[13:39:34] <jhourcle> it's all the same
[13:39:36] <Cadair> sure
[13:39:41] <jhourcle> wave matters for AIA, but it's all in one table
[13:39:44] <jhourcle> series
[13:40:08] <Cadair> jhourcle, so it is only PhysObs and instrument that map to jsoc series?
[13:40:37] <jhourcle> pretty much … there are some other series they want us to add
[13:40:42] <Cadair> like
[13:40:43] <Cadair> ?
[13:40:47] <jhourcle> but we need some additional discriminators ...
[13:41:05] <jhourcle> so there's hmi.m_45s and hmi.m_720s
[13:41:13] <Cadair> where the latter is/
[13:41:14] <Cadair> ?
[13:41:21] <Cadair> what the difference?
[13:41:36] <jhourcle> both are magnetic field data … but they use different observing sequences
[13:41:43] <Cadair> say what now
[13:41:54] <jhourcle> actually, those two might be discernable … I think the m_720s might be vector magnetic field
[13:42:07] <jhourcle> m_45s is a series of ~100 images over 45 seconds
[13:42:19] <jhourcle> m_720s uses a lot more images over a 720s second period
[13:42:23] <Cadair> jhourcle, is there a list of all the series that are available?
[13:42:25] <jhourcle> HMI is actually two cameras
[13:42:37] <jhourcle> yes … let me find it
[13:43:04] <jhourcle> it seems it's not on a single page
[13:43:09] <Cadair> o.o
[13:43:10] <jhourcle> http://jsoc.stanford.edu/
[13:43:21] <jhourcle> look on the left side, there's an 'HMI data products'
[13:43:41] <Cadair> lol! http://jsoc.stanford.edu/HMI/HMI_observables.png
[13:43:56] <jhourcle> 	•	http://jsoc.stanford.edu/ajax/lookdata.html?ds=hmi.M_720smagnetograms are computed every 12 minutes (720 seconds) by combining registered filtergrams obtained over a 1260 second time interval. The images provide a full-disk low-noise image of the Sun.
[13:43:56] <jhourcle> 	•	http://jsoc.stanford.edu/ajax/lookdata.html?ds=hmi.M_45smagnetograms are derived every 45 seconds. They provide a full disk image of the magnetic field and are best used to investigate rapidlly evolving field structures.
[13:44:26] <jhourcle> that's incomplete
[13:44:53] <jhourcle> no mention of Lw (line width) or Me (magnetic field … radial, I think)
[13:45:15] <Cadair> what the hell does this mean:
[13:45:17] <Cadair> "Any combination of FITS header keywords FSN and T_REC is unique for the DRMS series aia.lev1. "
[13:45:45] <jhourcle> remember how I mentioned that 'prime key' isn't a primary key?
[13:46:12] <jhourcle> each SQL table has multiple calibrations of a given observation in it.
[13:46:50] <jhourcle> so to determine what are the 'same' observation, you need to use a … well, it'd be a foreign key if there were another table it was referencing
[13:46:56] <jhourcle> they call it the 'prime key'
[13:47:08] <Cadair> soab
[13:47:45] <jhourcle> and for AIA.lev1, it's FSN (filtergram sequence number) + T_rec (observation time, rounded to the nearest second)
[13:48:14] <Cadair> jhourcle, how the hell do I progmatically generate that?
[13:48:21] <Cadair> do I need it for the series?
[13:48:27] <Cadair> or does it have a default
[13:48:29] <jhourcle> for aia ?  you don't.
[13:48:32] <Cadair> good
[13:48:42] <jhourcle> use um … let me get my cheat sheet
[13:49:46] <jhourcle> oh … crap.
[13:49:47] <jhourcle> <getdata_drms_query>aia.lev1[? wavelnth = '%i' and T_REC_index between %d and %d ?]{image_lev1}</getdata_drms_query>
[13:50:03] <jhourcle> you'd have to compute T_rec for that
[13:50:24] <jhourcle> wait, we can use VSO for this ...
[13:50:44] <jhourcle> ask for an AIA image closest to the start, then another one closest to the end.
[13:51:06] <jhourcle> you'll get back fileids that look like :
[13:51:15] <jhourcle> aia__lev1:%i:%i:%i
[13:51:20] <Cadair> oh ffs
[13:51:29] <jhourcle> the first value is the wavelength, next two are t_rec
[13:51:43] <jhourcle> it's doubled because we use the same pattern for tarballs
[13:51:50] <jhourcle> just it's the first & last value
[13:51:58] <Cadair> what is T-REC?
[13:52:16] <jhourcle> number of seconds since 15 seconds before January 1st, 1968
[13:52:50] <jhourcle> or at least, that's what they store in their database
[13:53:05] <Cadair> O.O
[13:53:23] <jhourcle> they write it back out to a string when they make the FITS file
[13:53:51] <jhourcle> but that's how they store it internally … the problem is that their system is so complicated that they can specify different epochs for each date field
[13:54:46] <jhourcle> because they decided that getting the maximum space savings was so much more important than actually being able to use the system in a useful manner
[13:54:54] <jhourcle> also, they didn't want leap seconds
[13:55:18] <Cadair> but but why
[13:55:35] <jhourcle> http://xkcd.com/793/
[13:55:43] <Cadair> yeah yeah
[13:56:06] <jhourcle> did I mention that they wrote their own software for tracking files on disk, pushing it between tape and disk, etc?
[13:56:14] <Cadair> no
[13:56:19] <jhourcle> which would effectively be a SOLVED PROBLEM
[13:56:25] <Cadair> erm YEAH
[13:57:07] <jhourcle> when I heard that IRIS data was also going to be put into DRMS, I told my boss I quit.
[13:57:37] <Cadair> you are shitting me
[13:57:41] <jhourcle> nope
[13:57:53] <Cadair> that is going to be available else where tho right
[13:58:01] <jhourcle> LMSAL was so unhappy with IRIS, they're only putting in the level 0 data
[13:58:12] <Cadair> eh?
[13:58:16] <jhourcle>  they're managing the other data themselves … of course, their only catalog into it is the HEK
[13:58:23] <jhourcle> erm ...
[13:58:29] <jhourcle> LMSAL was so unhappy w/ DRMS 
[13:58:37] <jhourcle> from their experiences with AIA
[13:58:42] <Cadair> right
[13:58:45] <Cadair> yeah
[13:58:52] <jhourcle> but the PDMP had already been approved for IRIS
[13:58:56] <Cadair> PDMP?
[13:58:59] <jhourcle> PDMP = project data management plan
[13:59:04] <Cadair> XD
[13:59:12] <Cadair> who was responsible for approving that?
[13:59:13] <jhourcle> which interestingly … I've never seen
[13:59:28] <jhourcle> Aaron Roberts, NASA"s Heliphysics Data Scientist
[13:59:34] * Cadair FETCH me my cod of slapping
[13:59:36] <jhourcle> he actually appologized to me
[13:59:39] <Cadair> HA!
[14:00:10] <jhourcle> because of the change in the Heliophysics Data Policy, SDAC was designated as a 'final archive'
[14:00:18] <jhourcle> which Joe G. isn't too thrilled about ...
[14:00:31] <Cadair> .me os very confused
[14:00:50] <jhourcle> but one of the duties of the 'final archive' is to be a stakeholder in the review of the PDMP
[14:01:14] <jhourcle> Joe G. was involved in the review of the SDO PDMP review … he's apologizes for that one, too.
[14:01:18] <jhourcle> apologized.
[14:01:38] <jhourcle> he said that they had Rasmus and Karen, and that the two of them would figure out what needed to be done, and do it.
[14:01:46] <jhourcle> (they were two programmers who weren't physicists)
[14:01:58] <jhourcle> Karen got pissed off and left … not sure what happened to Rasmus
[14:02:11] <Cadair> dear god
[14:02:19] <Cadair> jhourcle, What is your role?
[14:02:25] <Cadair> like officially?
[14:02:30] <jhourcle> 'programmer/analyst'
[14:02:35] <Cadair> where?
[14:02:40] <jhourcle> for the Solar Data Analysis Center, Goddard
[14:02:50] <Cadair> what is the role of SDAC?
[14:03:15] <jhourcle> repository for NASA's heliophysics data
[14:03:31] <Cadair> repo as in store all the data?
[14:03:47] <jhourcle> we're the mission archive for SMM, SOHO, STEREO … now TRACE and Yohkoh
[14:03:53] <jhourcle> yes
[14:04:06] <Cadair> but not SDO
[14:04:11] <jhourcle> we're also a mirror for Hinode
[14:04:21] <jhourcle> nope, don't have the funding for that much data
[14:04:25] <Cadair> indeed
[14:04:42] <jhourcle> so the way NASA handles archives ...
[14:04:42] <Cadair> and what is JSOC?
[14:05:00] <jhourcle> JSOC is a 'resident archive'
[14:05:17] <jhourcle> basically, you have three main classes of NASA archives :
[14:05:29] <jhourcle> resident archive -> managed by the people who collected the data
[14:05:44] <jhourcle> final archive -> NASA site that the data goes to after the mission is done
[14:06:10] <jhourcle> permanent archive -> NASA site that the data goes to after no one's really using the data any more
[14:06:24] <Cadair> you used "mission archive" above
[14:06:31] <Cadair> is that "resident archive"?
[14:06:37] <jhourcle> not exactly.
[14:06:42] <Cadair> XD
[14:06:44] <jhourcle> you can then divide them up other ways
[14:06:59] <jhourcle> 'instrument archive' 'mission archive' 'discipline archive'
[14:07:05] <jhourcle> with what the scope of a given archive is.
[14:07:23] <jhourcle> one sec.
[14:07:45] <jhourcle> http://virtualsolar.org/vocab
[14:07:58] <jhourcle> read the section 'Types of Archives'
[14:10:38] <Cadair> riiiighhht
[14:11:15] <sunpy-gitbot> [13sunpy] 15dpshelio pushed 4 new commits to 06master: 02http://git.io/ih8AKA
[14:11:15] <sunpy-gitbot> 13sunpy/06master 14c851c1f 15VaticanCameos: Changed angle_units flag to take 'degrees' and not 'deg' in wcs.py.
[14:11:15] <sunpy-gitbot> 13sunpy/06master 14504d62e 15Pritish Chakraborty: Update test_wcs.py...
[14:11:15] <sunpy-gitbot> 13sunpy/06master 14d246d3d 15VaticanCameos: Made some changes in sunpy.wcs....
[14:12:00] <jhourcle> I had to put that together after too many times talking to people, and realizing we were using the same words to mean different things
[14:12:18] <jhourcle> 'dataset' and 'data product'  … a dataset is a collection of data products, right?
[14:12:35] <Cadair> sure
[14:12:42] <jhourcle> not in the earth sciences
[14:12:54] <jhourcle> they've swapped the meanings of those two terms
[14:13:04] <jhourcle> for them, a dataset is an individual file
[14:13:12] <jhourcle> and a data product is a collection of similar files
[14:14:06] <renstar> jhourcle: depends on the earth science you are talking about
[14:14:40] <renstar> in geophysics a data set is the same as you describe above
[14:21:36] <jhourcle> the NASA EOS folks were the ones I had the issue with
[14:22:22] <jhourcle> we were having a discussion of what level of description we should share between archives … and we were all saying 'the collection level, not the file level'
[14:22:37] <jhourcle> but they kept saying 'data product' and I kept saying 'data set'
[14:23:10] <jhourcle> and no way in hell was I going to index at the 'data product' level, nor them at the 'data set' level
[14:23:21] <jhourcle> at least, not for sharing purposes
[14:24:30] <renstar> that is such a pita
[14:24:42] <renstar> i have similar issues in my current work
[14:24:53] <renstar> there are literally 5 different uses for the word "model"
[14:25:01] *** Joins: rishabh (uid26424@gateway/web/irccloud.com/x-lgwoqgxxwvifdzcv)
[14:25:11] <renstar> makes me want to punch a hobo
[14:25:41] <Cadair> haha
[14:26:05] <renstar> this is why i despise astropy's model module
[14:26:11] <Cadair> ahhh
[14:26:33] *** Quits: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230) (Ping timeout: 245 seconds)
[14:26:44] <renstar> the content is nice, the namespace makes me stabby
[14:26:51] <Cadair> anyone in here have any idea about Python threads
[14:27:25] <Cadair> specifically any idea how to use the callbacks in this: https://github.com/sunpy/sunpy/blob/master/sunpy/net/download.py#L26
[14:27:28] <jhourcle> model ?  there's a whole document on that from the Brits
[14:27:40] <Cadair> to wait until the dl is finished and then stop
[14:27:55] <renstar> Cadair, python multiprocessing is a minefield
[14:28:05] <Cadair> renstar, threading is even worse
[14:28:14] <Cadair> I need a Florain
[14:28:24] <Cadair> but he is busy doing useful things
[14:28:31] <renstar> the only time i use it is when i can call external programs
[14:28:36] <Cadair> damn it __name__ why you write crazy code?
[14:28:41] <renstar> because otherwise navigating the GIL is bonkers
[14:29:13] <renstar> cadair, what is your question
[14:29:56] <Cadair> give me a min to try and work this out
[14:36:19] *** Joins: mefistofeles (~crush@unaffiliated/mefistofeles)
[14:39:57] *** Joins: travis-ci (~travis-ci@ec2-23-22-92-190.compute-1.amazonaws.com)
[14:39:57] <travis-ci> [travis-ci] sunpy/sunpy#1314 (master - 1e8e20d : dpshelio): The build has errored.
[14:39:57] <travis-ci> [travis-ci] Change view : https://github.com/sunpy/sunpy/compare/9e34c2c6486b...1e8e20d56e8d
[14:39:57] <travis-ci> [travis-ci] Build details : http://travis-ci.org/sunpy/sunpy/builds/21594004
[14:39:57] *** Parts: travis-ci (~travis-ci@ec2-23-22-92-190.compute-1.amazonaws.com) ()
[14:48:17] *** Joins: derdon (~quassel@catv-89-132-224-69.catv.broadband.hu)
[14:49:09] <Cadair> hey derdon 
[14:50:17] <derdon> ho
[14:51:02] <Cadair> derdon, you don't happen to understand wtf is going on in __name__'s Downloader class / the VSO downloadin routines?
[14:51:47] <Cadair> If I call Downloader.wait() it never releases it's lock
[14:51:53] <Cadair> I can't work out how to make it
[14:51:57] <derdon> Cadair: didn't need to take a closer look at it yet
[14:52:06] <Cadair> damn ok
[14:54:04] <derdon> Cadair: maybe you have to call Downloader.stop manually after having completed the download?
[14:54:26] <Cadair> derdon, but if Downloader has the lock, how?!
[14:54:34] <derdon> wait is just a synonym for acquiring the lock and stop is just a synonym for releasing it again
[14:55:31] <derdon> hm
[14:55:50] <derdon> __name__ has too much RL in last time ^^
[14:55:58] <derdon> doesn't show up on irc anymore
[14:56:54] <derdon> Cadair: I can ask him this evening/tonight if you want to, he's more often online on jabber than on irc
[14:57:51] <Cadair> hot damn this is annoying
[14:57:54] *** Joins: travis-ci (~travis-ci@ec2-23-22-92-190.compute-1.amazonaws.com)
[14:57:54] <travis-ci> [travis-ci] sunpy/sunpy#1314 (master - 1e8e20d : dpshelio): The build passed.
[14:57:54] <travis-ci> [travis-ci] Change view : https://github.com/sunpy/sunpy/compare/9e34c2c6486b...1e8e20d56e8d
[14:57:54] <travis-ci> [travis-ci] Build details : http://travis-ci.org/sunpy/sunpy/builds/21594004
[14:57:54] *** Parts: travis-ci (~travis-ci@ec2-23-22-92-190.compute-1.amazonaws.com) ()
[14:58:13] <Cadair> he has done it in vso somehow but the code is totally opaque to me
[14:58:21] <Cadair> derdon, if you could that would be good
[14:59:17] <derdon> he's a genius! that's how you should do it in the enterprise: make code unreadable so that you're the only one who can maintain and extend it. this way the company will depend on you and you reached your final goal
[14:59:36] <Cadair> yep
[14:59:56] <jhourcle> derdon : and it means you can never be promoted
[15:00:05] <jhourcle> as you'll always have that pulling you back.
[15:00:56] <jhourcle> 4 years of hell trying to support the JSOC stuff, but even hiring someone who used to work for the JSOC, they can't understand it well enough for me to pass off my tasks to them
[15:01:13] <Cadair> dear god
[15:01:15] <jhourcle> so the fun tasks that I thought I was going to get to do this year?  nope, I'm stuck supporting NetDRMS
[15:01:32] <jhourcle> I blame the way the code's written at Stanford … a bunch of silos.
[15:01:48] <Cadair> eh?
[15:01:54] <jhourcle> shortly after launch, we had a problem, and were told that Jim was out of town for a couple of weeks, and we'd have to wait
[15:02:08] <jhourcle> as he was the only one who knew that part of the system
[15:02:25] <derdon> *cough* bus factor
[15:02:29] <jhourcle> yep
[15:03:01] <jhourcle> when it first got handed to us, I recommended forking the code, when they wouldn't make the changes we wanted
[15:03:15] <jhourcle> and that was when I was told that if we did that, they wouldn't support the users.
[15:03:43] <jhourcle> but there's a whole lot of people who now say we need to just break away .. but we don't have the man hours we did near the SDO launch
[15:03:58] <jhourcle> we barely have enough to keep it on life support
[15:04:24] <Cadair> jhourcle, what would you do if you did break away?
[15:10:53] *** Quits: mefistofeles (~crush@unaffiliated/mefistofeles) (Quit: Hay the guachu!)
[15:22:13] *** Joins: astrofrog (~Adium@rt-mpia.mpia-hd.mpg.de)
[15:22:24] <VaticanCameos> Cadair: should I directly push my patchbranch on to remote 0.4x branch?
[15:24:13] <Cadair> VaticanCameos, you will need to rebase the commits onto 0.4
[15:25:21] <VaticanCameos> Rebase..I recall Thats a risky thing to do
[15:27:14] <Cadair> with great power
[15:27:19] <Cadair> create a new branch off 0.4
[15:28:05] <Cadair> then do rebase <branchname> 
[15:28:18] <Cadair> where branchname is the branch of the original PR
[15:32:00] <VaticanCameos> So I create a new branch named 0.4?
[15:32:18] <Cadair> no named something else
[15:32:26] <Cadair> but you branch it from 0.4
[15:32:37] <Cadair> so git checkout -b my04patch 0.4
[15:32:47] <Cadair> git rebase mymasterpatch
[15:32:52] <VaticanCameos> I dont have 0.4 as a branch locally ;_;
[15:34:02] <VaticanCameos> How would I branch off from 0.4  in that case
[15:34:19] <Cadair> git checkout 0.4
[15:34:22] <Cadair> should do it
[15:34:36] <Cadair> otherwise git checkout -b 0.4 upstream/0,4
[15:34:38] <VaticanCameos> Ah it did
[15:34:57] <VaticanCameos> It wasn't there earlier but its now tracking from remote
[15:35:00] <Cadair> yes
[15:36:07] <VaticanCameos> Rebase complete
[15:36:32] <VaticanCameos> Do I push now?
[15:39:52] <Cadair> yep
[15:39:58] <Cadair> then open a new PR
[15:52:50] <VaticanCameos> Er Cadair 
[15:53:08] <VaticanCameos> Pr from 0.4patch to remote/0.4?
[15:54:16] <VaticanCameos> It says branches can't be merged lol
[15:57:33] <Cadair> oh what
[15:58:45] <VaticanCameos> Sunpy:0.4 from VaticanCameos: 0.4patch not automatically merge able
[16:01:36] <VaticanCameos> Brb coming on comp
[16:01:42] *** Quits: VaticanCameos (~SVXX@182.68.189.10) (Quit: Bye)
[16:02:02] *** Joins: VaticanCameos (~pls@182.68.189.10)
[16:21:24] *** Quits: sarwarc (~livingsto@115.248.45.78) (Read error: Connection reset by peer)
[16:30:16] <VaticanCameos> Cadair: What now?
[16:30:33] <Cadair> panic and run
[16:32:51] <VaticanCameos> lul
[16:32:57] <VaticanCameos> Should I submit the PR anyway?
[16:35:22] <DavidPS> Hello all! I'm back!
[16:37:59] <VaticanCameos> Welcome back DavidPS 
[16:41:21] <Cadair> hey DavidPS 
[16:44:01] <DavidPS> Cadair, lot of information jhourcle gave to you eh!
[16:44:05] <Cadair> oh yeh
[16:44:06] <DavidPS> VaticanCameos: how are you?
[16:44:15] <Cadair> DavidPS, I have basically written a JSOC client
[16:45:30] <DavidPS> I saw you asked for the slots. The thing is we don't really know anything till 17 of April (or so)
[16:45:38] <DavidPS> VaticanCameos ^^
[16:45:42] *** Joins: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230)
[16:45:47] <DavidPS> Cadair, that's a good thing?
[16:46:09] <Cadair> yeah, sure
[16:46:14] <DavidPS> cool then :)
[16:46:32] <DavidPS> so we can then query jsoc independently of VSO
[16:46:52] <DavidPS> jsoc is the one that provides cut-offs of SDO?
[16:47:32] <Cadair> it provides all the SDO data
[16:47:42] <Cadair> you can also do cut-out
[16:47:50] <Cadair> tho I haven't written that in
[16:47:51] <Cadair> at all
[16:48:02] <Cadair> it also enables you to get the HMI vector magnetograms
[16:48:08] <DavidPS> yeah, and VSO queries it when SDO data is requested, right?
[16:48:13] <Cadair> yeah
[16:48:16] <DavidPS> nice!!
[16:48:33] <DavidPS> I remember we had some year that as an idea for SoC
[16:48:56] <Cadair> it works, but for it to be SunPy ready it will take quite a while
[16:49:39] <DavidPS> Feature branch!!! :-P
[16:49:44] *** Joins: sarwarc (~livingsto@115.248.45.78)
[16:49:45] <Cadair> another one!
[16:49:56] <Cadair> I think we need to close one or two that are currently open!
[16:50:09] <Cadair> I think we need to be stricter on what gets a feature branch
[16:50:28] <Cadair> i.e. things that many other people are *actually* going to contribute to
[16:50:42] <Cadair> nobody has lent a hand with LC factory yet
[16:50:46] <Cadair> tho rishabh did offer
[16:51:30] <VaticanCameos> DavidPS: I'm good, just finished dinner ^^
[16:56:55] <DavidPS> Cadair, you are right, we should set some limits on feature branches... what about infinity?
[16:57:06] <Cadair> no
[16:57:28] <DavidPS> :-P
[16:57:31] <Cadair> I am not suggesting we have a limit, I am just suggesting we shouldn't pepper ourselves with them
[16:57:49] <DavidPS> Cadair, that's right too.
[16:57:58] <Cadair> Also the JSOC client shouldn't be a feature branch as it can get mainlined and then other people can help
[16:58:06] <Cadair> feature branches are good for API changes
[16:58:20] <Cadair> where you can't merge into master until it works
[16:58:41] <DavidPS> so jsoc client works???!! why didn't you tell it before!
[16:58:42] <Cadair> afterall you can PR to other peoples fork for smaller contributions
[16:59:02] <DavidPS> Cadair, yes, I'm very much up for that approach
[16:59:04] <Cadair> DavidPS, yes and no
[17:03:21] <DavidPS> Cadair, if I use logic that's no
[17:03:28] <Cadair> exactly
[17:09:29] *** Quits: rajul (cb6ef6e6@gateway/web/freenode/ip.203.110.246.230) (Ping timeout: 245 seconds)
[17:20:08] *** Joins: rajul (~rajul@203.110.246.111)
[17:25:36] *** Quits: rajul (~rajul@203.110.246.111) (Quit: Leaving)
[17:35:13] *** Joins: rajul (~rajul@203.110.246.111)
[17:36:30] *** Quits: rajul (~rajul@203.110.246.111) (Client Quit)
[17:36:51] *** Joins: rajul (~rajul@203.110.246.111)
[17:42:56] *** Quits: astrofrog (~Adium@rt-mpia.mpia-hd.mpg.de) (Read error: Operation timed out)
[18:15:10] *** Joins: sarwarc_ (~livingsto@115.248.45.78)
[18:18:36] *** Quits: sarwarc (~livingsto@115.248.45.78) (Ping timeout: 264 seconds)
[18:20:24] *** Quits: sarwarc_ (~livingsto@115.248.45.78) (Ping timeout: 264 seconds)
[18:35:15] <Cadair> jhourcle, derdon, DavidPS and anyone else who cares: https://gist.github.com/Cadair/9790147
[18:36:34] <derdon> Cadair: looks cool, a new SunPy module or package?
[18:36:34] *** Joins: sarwarc_ (~livingsto@115.248.45.78)
[18:36:47] <derdon> the __init__ definition is not necessary btw
[18:37:09] <Cadair> derdon, true, I put it there expecting to write something in it
[18:37:13] <Cadair> then didn't
[18:38:17] <derdon> ``map(get_file, urls)`` :O
[18:38:34] <derdon> using map just for the side-effects is not a good style
[18:38:45] <derdon> you create a list and throw it away
[18:38:56] <derdon> better use a for loop explicitly
[18:39:14] <Cadair> thought map could be fatser
[18:39:16] <Cadair> *faster
[18:39:46] <derdon> instead of doing X you do X *and* create a list of the return values you don't need. what is faster?
[18:40:24] <Cadair> true
[18:40:30] <Cadair> http://bpaste.net/show/194063/
[18:40:35] <Cadair> that's better?
[18:40:40] <derdon> lists have a boolean value, so instead of ``if len(urls):`` you can just say ``if urls:``
[18:40:59] <Cadair> derdon, so if []: returns False?
[18:41:06] <Cadair> .py if []
[18:41:06] <SunPyBot> SyntaxError: unexpected EOF while parsing (<string>, line 1)
[18:41:14] <Cadair> .py if []: print 'False'
[18:41:23] <Cadair> .py if []: print('False')
[18:41:31] <Cadair> .py if [] print('False')
[18:41:31] <SunPyBot> SyntaxError: invalid syntax (<string>, line 1)
[18:41:32] <derdon> .py bool([])
[18:41:32] <SunPyBot> False
[18:41:35] <derdon> :)
[18:41:43] <Cadair> shniny
[18:41:47] <Cadair> shiny
[18:42:45] <derdon> and in the next version, you want to use a real progress bar, I assume? :)
[18:43:07] <Cadair> derdon, yeah I want a progressbar but I have to work out __name__'s threading nonsense first :p
[18:43:12] * Cadair has not done threads before
[18:43:24] * derdon neither, only in theory
[18:43:40] <derdon> they are way too hard to use in most languages!
[18:43:42] <Cadair> that's one theory better than me
[18:52:13] <derdon> the ``dlers = []`` within the outer loop still looks weird to me. why is there no ``result.extend(dlers)`` at the end of the outer loop and then ``return result``?
[18:52:41] <derdon> it looks as if only the last generated list will be remembered
[18:53:06] <Cadair> that should be outside, good spot
[18:53:45] <derdon> :)
[18:57:50] <derdon> Cadair: in what way does JSOC relate to VSO? are they comparable?
[18:58:56] <Cadair> derdon, the VSO queries JSOC for some of it's data
[19:00:23] <derdon> ah, so VSO just passes on the query in case the data can be found at JSOC?
[19:00:36] <Cadair> derdon, yes, if only it were that simple
[19:00:38] <Cadair> but teag
[19:00:40] <Cadair> *yeah
[19:00:55] <derdon> I'm too optimistic :P
[19:00:59] <Cadair> yeah
[19:01:06] <Cadair> get jhourcle going about JSOC sometime
[19:01:10] <Cadair> It is really fun
[19:01:15] <derdon> I already fear a rant :D
[19:01:15] <Cadair> or read last nights logs
[19:01:22] <derdon> read it a bit
[19:01:38] <Cadair> it will make you want to cry
[19:05:32] <derdon> Cadair: the docstring says there's a compression parameter but jsoc_query doesn't receive it directly and you don't read it from kwargs either
[19:05:47] <Cadair> derdon, it gets put into protocol
[19:07:10] <derdon> protocol isn't used either
[19:07:16] <derdon> or I fail to see it
[19:07:34] <Cadair> it gets passed to _make_jsoc_request
[19:07:57] <VaticanCameos> .py print('u wot m8')
[19:07:58] <SunPyBot> u wot m8
[19:08:02] <Cadair> lol
[19:08:02] <VaticanCameos> noice
[19:08:35] <derdon> Cadair: can you give me the link to the latest version, please? I think I have an older version
[19:09:09] <Cadair> derdon, https://gist.github.com/Cadair/9790147
[19:09:47] *** Quits: rishabh (uid26424@gateway/web/irccloud.com/x-lgwoqgxxwvifdzcv) (Quit: Connection closed for inactivity)
[19:10:07] <derdon> Cadair: and now you show me where jsoc_query uses the parameters compression and protocol ;)
[19:10:28] <Cadair> https://gist.github.com/Cadair/9790147#file-jsocclient-py-L103
[19:11:07] <Cadair> jsoc_query -> _multi_request -> _make_jsoc_request
[19:11:20] <derdon> ah
[19:11:22] <Cadair> in kwargs
[19:11:24] <derdon> but line 134 ...
[19:11:32] <Cadair> yes
[19:11:35] <derdon> **kwargs -> *kwargs
[19:11:39] <derdon> intentional?
[19:11:43] <Cadair> ooops nope
[19:11:52] <Cadair> danke
[19:12:11] <derdon> bitte sehr, gern geschehen!
[19:12:22] <Cadair> .tr bitte sehr, gern geschehen!
[19:12:22] <SunPyBot> Cadair: "if you please , you're welcome !" (de to en, translate.google.com)
[19:12:34] <derdon> what a great translation :D
[19:12:37] <Cadair> oh yeah
[19:12:55] <derdon> more like "you're welcome, it was a pleasure"
[19:13:29] <VaticanCameos> I wonder if I can make SunPyBot issue a command on itself
[19:13:37] <VaticanCameos> .py print('.seen derdon')
[19:13:37] <SunPyBot> .seen derdon
[19:13:40] <VaticanCameos> dang
[19:13:55] <derdon> meta bot controlling
[19:13:56] <Cadair> VaticanCameos, recursive bot
[19:13:58] <jhourcle> derdon : JSOC hosts a bunch of data … they're just one of the many places that the VSO can query.
[19:14:14] <derdon> jhourcle: I see
[19:14:51] <jhourcle> but they have the ability to stage data … we've talked about trying to work out how to handle it for their data, but um … 
[19:14:53] <derdon> jhourcle: how does VSO decide which server to query is the best choice? I guess there can be overlaps, e.g. server A and server B offer data for query X, but yield different results
[19:15:06] <jhourcle> … there was a death involved.
[19:15:24] <jhourcle> oaky, there's two VSO methods — Search and GetData
[19:15:41] <jhourcle> for search, we try to make sure there's no duplication.
[19:15:53] <jhourcle> it's actually caused a bit of headaches over the years.
[19:16:10] <jhourcle> (NRL wanted us to serve THEIR version of the EIT and LASCO data)
[19:16:13] <derdon> I can imagine, doesn't sound trivial
[19:16:23] <jhourcle>  … but it had all of the engineering data in it, didn't have the scientific headers ...
[19:16:34] <jhourcle> so we went with the more universally useful files from the SDAC
[19:17:07] <jhourcle> so anyway, for Search, we have a registry of what each provider has
[19:17:23] <jhourcle> so if you ask for data from the 1980s … it's only going to talk to the Mt. Wilson archive
[19:18:09] <jhourcle> so we try to only ask the providers that are going to have a chance at returning results
[19:18:24] <jhourcle> for 'GetData' … it used to always be just one site for each one
[19:18:57] <Cadair> jhourcle, I made a pretty: https://gist.github.com/Cadair/9790147#file-jsocclient-py
[19:19:00] <jhourcle> but with SDO, Stanford said they didn't have the bandwidth to support everyone … so they wrote into their PDMP (project data management plan), that they'd give access to the VSO
[19:19:15] <jhourcle> and we'd serve it to the public
[19:19:50] <jhourcle> the problem was, the way that they store the data isn't useful to anyone.
[19:20:17] <jhourcle> so we have to run software to insert headers onto the files…. and had to set up this big, huge caching network.
[19:20:30] <jhourcle> in some cases, there were groups that wanted the data anyway … like SAO
[19:20:43] <jhourcle> I think they have a few hundred TB of space
[19:21:17] *** Quits: VaticanCameos (~pls@182.68.189.10) (Quit: Leaving)
[19:21:30] <jhourcle> other places like um … one of the european groups … could only hold about 14 days of data
[19:22:15] <Cadair> jhourcle, hang on, netDRMS only serves headers?
[19:22:28] <Cadair> you cache the data and build the headers on the fly?
[19:22:33] <jhourcle> 'NetDRMS' is actually two things ...
[19:22:35] <jhourcle> maybe three ...
[19:22:46] <jhourcle> the package as distributed by stanford
[19:23:19] <jhourcle> 'DRMS' : Data Record Management System … is a bunch of logic to deal with the metadata … and a big postgres database
[19:23:36] <jhourcle> 'SUMS' : Storage Unit Management System … handles pushing the files around
[19:23:46] <jhourcle> … and also uses a postgres database
[19:24:03] <jhourcle> then there's the VSO supplied code
[19:24:31] <jhourcle> 'JMD' : Java Mirroring Daemon  … handles parallel retrieval of data when there isn't a copy local
[19:24:55] <jhourcle> Cadair : yes, sort of.
[19:25:05] <jhourcle> so, we have a few processes running at all of the sites ...
[19:25:26] <jhourcle> first, the JSOC is running Slony-I replication of some of their database tables
[19:26:05] <jhourcle> the VSO sites pull the Slony logs every few minutes, and apply them to our databases, so we know what the metadata is (FITS headers)
[19:26:53] <jhourcle> each site then has database triggers on the tables for the data they want, that writes a record to a table that basically signifies 'please download this'
[19:27:16] <jhourcle> so we attempt to keep up-to-date on the most recent data, rather than waiting for someone to request it
[19:27:43] <jhourcle> the JMD reads that table, and tries to pull the data from the other VSO nodes … if not, it pulls it from the JSOC
[19:28:36] <jhourcle> when soemone wants to actually download the data … it gets messy. ..
[19:28:57] <Cadair> ^.o
[19:29:19] <jhourcle> I have a CGI that does some simple sanity checks (we know about that series, how do you build requests for that given series, etc.)
[19:30:03] <jhourcle> if then calls something that the JSOC folks wrote called 'export_as_fits'
[19:30:32] <jhourcle> that we've hacked up slightly, so it streams the response w/ MIME headers, rather than trying to write out to disk
[19:30:40] <jhourcle> and will generate tarballs on the fly.
[19:31:32] <jhourcle> export_as_fits goes to DRMS to get the FITS headers … 
[19:31:52] <jhourcle> and then tells SUMS what files it needs … but if SUMS doesn't know about the file, it has to load it from tape.
[19:32:11] <Cadair> load it from TAPE
[19:32:26] <jhourcle> but the JMD sits in place of the tape retrieval code, an instead goes and contacts the caching nodes
[19:32:27] <Cadair> I suppose they can only store so much on disks
[19:32:44] <jhourcle> if none of them have it, then it asks the JSOC for it.
[19:32:55] <Cadair> who then gets it from tape?
[19:32:59] <jhourcle> if the JSOC has it online, we start transfering it immediately
[19:33:02] <jhourcle> the JSOC
[19:33:19] <jhourcle> if they don't have it online, then they have to load tapes
[19:33:31] <jhourcle> I have no idea how much their tape robot holds
[19:33:35] <Cadair> what if SUMS knows about it, are the mirrors still checked?
[19:33:47] <jhourcle> no, then we return it immediately
[19:33:55] <Cadair> from JSOC?
[19:34:12] <jhourcle> there's a SUMS running at the JSOC and each of the caching nodes
[19:34:23] <jhourcle> I'd say 'VSO  sites', but it's more than just VSO
[19:34:30] <Cadair> right
[19:34:32] <jhourcle> ROB, UCLAN, etc.
[19:34:51] <jhourcle> if the local SUMS has is, then it doesn't try 'going to tape' (which we've bypassed)
[19:34:51] <Cadair> and each of those sites SUMS knows about it's local data
[19:34:55] <jhourcle> yes
[19:35:04] <Cadair> right
[19:35:05] <Cadair> ok
[19:35:12] <jhourcle> this is one of those cases where any of the 'data grid' infrastructures could've been used
[19:35:19] <Cadair> yes
[19:35:38] <jhourcle> but DRMS/SUMS was never meant for distribution
[19:35:44] <Cadair> jhourcle, I presume that export_as_fits has to do some processing on the raw data?
[19:35:47] <jhourcle> it just got foisted on us
[19:35:51] <Cadair> jhourcle, wtf
[19:35:55] <Cadair> it was in their damn plan
[19:36:11] <Cadair> what lang is DRMS/SUMS written in?
[19:36:35] <jhourcle> export_as_fits determines the FITS headers, then hands off to cfitsio
[19:36:49] <jhourcle> language?  um … C, some perl, some shell ...
[19:36:54] <Cadair> XD
[19:37:03] <jhourcle> in some really bad cases, C that generates perl that calls out to the shell
[19:37:38] <jhourcle> in other bad cases, shell script CGIs that call C that generates perl that calls out to the shell to call other shell scripts
[19:37:58] <Cadair> jhourcle, I am confused as to the reason for the metadata / data seperation
[19:38:17] <jhourcle> the folks at Stanford never reassemble the files
[19:38:25] <jhourcle> DRMS is their whole world
[19:38:38] <Cadair> if no calibration happens on the fly, the data is presumably stored as lvl 1, why not save the metadata with the data
[19:38:43] <Cadair> and in the databse
[19:38:54] <Cadair> surely to go this would be easier
[19:38:59] <Cadair> *God
[19:39:03] <jhourcle> all of the pipeline processing uses this stuff, so it never needs to write files
[19:39:12] <Cadair> eh?
[19:39:26] <jhourcle> after enough bitching by the LMSAL folks, AIA.lev1 *is* written out with the headers
[19:39:29] <jhourcle> but they're never updated
[19:39:40] <Cadair> the pipeline must have to modify the data
[19:39:57] <Cadair> so where is the data kept as it goes through the pipeline?
[19:39:59] <jhourcle> so it's like with TRACE — the files were distributed with known bad headers
[19:40:14] <jhourcle> okay, I over simplified … nothing is ever updated ...
[19:40:37] <jhourcle> everything in SUMS has a 'sunum' (storage unit number)
[19:40:55] <jhourcle> you just link your updated record to the new sunum ...
[19:41:44] <jhourcle> want to work on some temporary calculations ?  then you make a 'link table', where you can add extra fields, but it then also pulls values from the original table
[19:42:15] <jhourcle> oh … and storage units aren't necessarily one per record … HMI data is actually stored w/ 30 records per storage unit.
[19:42:33] <jhourcle> so that one file you want to download ?  we have to retrieve 30 of 'em to serve you that one file.
[19:42:40] <Cadair> jhourcle, so instead of updating the data as it goes through the pipeline it copies it
[19:42:57] <Cadair> jhourcle, WHAT THE BANDWIDTH EATING WHAT
[19:43:00] <jhourcle> it never makes copies … they've done everything they could to minimize storage
[19:43:40] <Cadair> jhourcle, but the pipeline has to modify the pixel data
[19:44:02] <jhourcle> well, they're separate series
[19:44:12] <jhourcle> so there's the 'level 0' series
[19:44:21] <jhourcle> and then the various processed series
[19:44:40] <jhourcle> really, the system is built around scratch space for their pipeline, as best I can tell
[19:45:13] <jhourcle> there is some reprocessing done, but it's pretty rare … trust me.
[19:45:43] <jhourcle> I know that they're supposed to reprocess the AIA data at 6 months in, but I'm not sure if they generate new level1 or just level1.5
[19:46:10] <jhourcle> (we've got some logic that stops us from automatically downloading new records if they're for observatons more than 2 weeks old)
[19:46:47] <jhourcle> anyway … on the wasted bandwidth front … 
[19:47:17] <jhourcle> for AIA, they originally wanted to store 'em as on SUNUM per timestep … so 8 exposures per storage unit
[19:47:34] <jhourcle> we fought for them to not do that.
[19:47:56] <jhourcle> I said no big deal, I'll just cherry-pick the files, and just download the individual files I need
[19:48:11] <jhourcle> they had a fucking hissy fit over it
[19:48:33] <jhourcle> that's when I was told that if I forked their software, they's not support any users who downloaded data through us
[19:48:49] <jhourcle> so we talked the AIA folks into writing out one file per observation
[19:49:14] <jhourcle> of course, the system … if it was ever stress tested … assumed a record every 45 secs, max
[19:49:33] <jhourcle> per time step, they would've had one every 10 sec for AIA (as designed … now one every 12)
[19:50:05] <jhourcle> instead, I got 'em to write the files individually … so SUMS has to track 8x as many units, and DRMS is tracking a new record every 1.5 sec
[19:50:11] <jhourcle> needless to say … it didn't scale
[19:50:46] <jhourcle> but it was all so that when soemone wanted to download a day of AIA 171 images, I didn't have to go and download 2TB and throw away 7/8 of it
[19:51:30] *** Joins: derdon_ (~quassel@catv-89-132-224-69.catv.broadband.hu)
[19:52:12] *** Quits: derdon (~quassel@catv-89-132-224-69.catv.broadband.hu) (Ping timeout: 264 seconds)
[19:54:22] *** Joins: VaticanCameos (~SVXX@182.68.189.10)
[20:47:02] *** Quits: renstar (~quassel@18.155.7.137) (Ping timeout: 240 seconds)
[21:03:56] *** Quits: VaticanCameos (~SVXX@182.68.189.10) (Ping timeout: 268 seconds)
[21:09:02] *** Quits: rajul (~rajul@203.110.246.111) (Ping timeout: 240 seconds)
[21:23:22] *** Quits: jhourcle (~Adium@c-76-106-20-159.hsd1.md.comcast.net) (Quit: Leaving.)
[21:47:55] *** Joins: jhourcle (~Adium@pool-108-56-191-209.washdc.fios.verizon.net)
[22:28:15] *** Joins: renstar (~quassel@c-98-217-130-167.hsd1.ma.comcast.net)
[22:34:32] *** Joins: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de)
[23:32:18] *** Quits: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de) (Quit: Leaving.)
[23:39:34] *** Joins: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de)
[23:42:29] *** Quits: astrofrog (~Adium@pD9528420.dip0.t-ipconnect.de) (Client Quit)
```