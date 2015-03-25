```
[14:41:50] <jhourcle> URI encoding kinda sucks
[14:41:52] <jhourcle> but :
[14:41:52] <jhourcle> curl 'http://vso1.nascom.nasa.gov//cgi-bin/registry_json.cgi?fields=%5b%22method%22%5d'
[14:45:06] <Cadair> rajul, those damn callisto tests failed:
[14:45:06] <Cadair> https://travis-ci.org/sunpy/sunpy/jobs/55784758#L1308
[14:45:11] <Cadair> the new ones anyway
[14:45:32] <rajul> Cadair, yeah saw that!!
[14:45:53] <rajul> feel like burning the world!! :P :P
[14:46:05] <jhourcle> and to get the expanded names
[14:46:06] <jhourcle> curl 'http://vso1.nascom.nasa.gov//cgi-bi?fields=%5b%22%2binstrument%22%5d'
[14:46:07] <rajul> how has our codebase become so non-deterministic
[14:46:12] <jhourcle> which is :
[14:46:26] <jhourcle> fields=["+instrument"]
[14:46:30] <jhourcle> once you decode it
[14:46:32] <rajul> any thing breaks whenever it feels like :P
[14:46:41] <jhourcle> you can also pass an argument of :
[14:46:45] <jhourcle> query={ … }
[14:46:59] <jhourcle> where … is a VSO formatted query.  (but 'time' is not required)
[14:47:05] <Cadair> https://youtu.be/PwuXVTNpWDk?t=1m50s
[14:47:06] <SunPyBot> [YouTube] Title: Family Guy Stewie Wants His Money | Uploader: TheTitansman1 | Uploaded: 07/01/2012, 22:02 | Duration: 2mins | Views: 214,667 | Comments: 75 | Likes: 524 | Dislikes: 35
[14:51:29] *** Joins: coder006 (~quassel@103.225.100.51)
[14:51:31] <jhourcle> so, to find the sources & instruments available from the JSOC data provider : 
[14:51:40] <jhourcle> curl 'http://vso1.nascom.nasa.gov//cgi-bin/registry_json.cgi?fields=%5b%22%2binstrument%22,%22%2bsource%22%5d;query=%7b%22provider%22:%22JSOC%22%7d'
[14:53:01] <Cadair> holy moly
[14:53:09] <Cadair> sweet
[14:53:16] <Cadair> this will have to go in the log
```