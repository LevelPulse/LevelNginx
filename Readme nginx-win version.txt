
=== Transforming nginx for Windows ===

Note: Should you need support or report anything please use the nginx forums at
http://forum.nginx.org/ or post an issue at http://forums.ecsystems.nl/ or by email
support@ecsystems.nl (where we maintain the package builds)

Builds can be found here:
  http://nginx-win.ecsds.eu/

Todo:
- nginx-1.4.x_proxy_protocol_patch_v2.patch, looking into merging this one.
- pagespeed
- drizzle
- dynamic loading of add-ons
- ldap / ntlm
- allow multiple instances to run on the same machine
- installation and upgrade package

Feature list (* nginx_basic only):
=* All current nginx features (see with nginx.exe -V)
=* Consistent with original nginx code
=* FD_SETSIZE = 16384 (modded kernel), allows one worker to handle c250k
   (with optimization registry file)
=* Multiple workers supported ! use no more than 2 workers for 1 core (cpu)
=* SPDY 3.1
=  LuaJIT compiled in (lua-nginx-module)
=  Streaming with nginx-rtmp-module
=  Naxsi WAF - Web Application Firewall
=  Array-var-nginx-module
=  HttpSubsModule
=  echo-nginx-module
=  ngx_http_lower_upper_case
=  headers-more-nginx-module
=  set-misc-nginx-module
=  ngx_http_auth_ldap (experimental)
=* Additional custom 503 error handler via 513
=  lua-upstream-nginx-module (Manipulate upstream dynamically)
=* Select-boost
=* Fully ASLR and DEP compliant for shared memory
=  encrypted-session-nginx-module
=  Nginx-limit-traffic-rate-module
=  RDNS (reverse DNS lookup for incoming connection)
=  AJP - tomcat backend support


*** Installation instructions;
* New: unzip this version with folder structure
* Old: overwrite with this version
* Check nginx.conf, nginx-org.conf and nginx-win.conf
* Windows optimization registry file: check your current values BEFORE setting the new ones


Upgrade Assessment Matrix
-------------------------
I am using               Security Stability Performance Existing_Features New_Features
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.5.12.2 Cheshire  High     Medium    High        High              High
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.5.13.1 Snowman   High     Medium    Low         High              High
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.5.13.2 Snowman   None     None      None        Low               Low
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.5.14.1 Snowman   None     Low       None        Low               None
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.7.1.1  Snowman   None     None      None        Low               Medium
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.7.1.2  Snowman   None     Low       None        Low               None
------------------------ -------- --------- ----------- ----------------- ------------
nginx 1.7.1.3  RedKnight -        -         -           -                 -
------------------------ -------- --------- ----------- ----------------- ------------


17:21 17-5-2014 nginx 1.7.1.3 RedKnight

Go ask Alice, I think she'll know, When logic and proportion have
fallen dead And the white knight is talking backwards And the red
queen's lost her head Remember what the dormouse said Feed your head,
feed your head, as the RedKnight rizes again from the dead !
The nginx RedKnight release is here /->
             ,      ,  /
        ____/~\    ~O
    ,;~( )_  )'' /~()'-{---
       )/  |(     /~)
       ~    ~     ~ ~
     Phil/sb/Donovan/mbfh

Based on nginx 1.7.1 (16-5-2014) with;
+ Openssl fix for out-of-bounds write in SSL_get_shared_ciphers (#3317)
+ integration of Mercurial and Git into our crosscompiler
  this reduces diff sets import and cross checks from 12 to 1 hour
+ lua-nginx-module v0.9.7 (upgraded 15-5-2014)
+ Select-boost is out of beta and is now the default
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


13:56 2-5-2014 nginx 1.7.1.2 Snowman

Based on nginx 1.7.1 (30-4-2014) with;
+ lua-nginx-module v0.9.7 (upgraded 1-5-2014)
+ Openssl fix for CVE-2010-5298
+ AJP tomcat backend support (https://github.com/yaoweibin/nginx_ajp_module)
  Note: a folder '.\nginx\ajp_temp' will be created, when running nginx jailed
  create it yourself and set additional rights for the service user who runs
  nginx to allow access
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


21:28 24-4-2014 nginx 1.7.1.1 Snowman

Based on nginx 1.7.1 (24-4-2014) with;
+ lua-upstream-nginx-module v0.1 (upgraded 24-4-2014)
+ Streaming with nginx-rtmp-module, v1.1.4 (upgraded 24-4-2014)
+ New development tree nginx export 1.7
+ Naxsi WAF v0.53-1 (upgraded 17-4-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


23:55 12-4-2014 nginx 1.5.14.1 Snowman

Based on nginx 1.5.14 (11-4-2014) with;
+ echo-nginx-module v0.53 (upgraded 12-4-2014)
+ Should I upgrade? (Upgrade Assessment Matrix)
+ lua-nginx-module v0.9.7 (upgraded 11-4-2014)
+ Streaming with nginx-rtmp-module, v1.1.4 (upgraded 11-4-2014)
+ set-misc-nginx-module (upgraded 11-4-2014)
+ RDNS (https://github.com/flant/nginx-http-rdns) (upgraded 11-4-2014, it's back!)
+ pcre-8.35 (upgraded)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


CVE-2014-0160 (heartbleed / heartbeat) statement: as of version 'nginx 1.5.13.2 Snowman'
nginx for Windows is not affected by CVE-2014-0160, this version uses openssl-1.0.1g, any
previous version can be vulnerable.


10:30 8-4-2014 nginx 1.5.13.2 Snowman

Based on nginx 1.5.13 (8-4-2014) with;
+ CVE fix CVE-2014-0160
+ openssl-1.0.1g (upgraded 8-4-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications are like 0:18 5-4-2014 nginx 1.5.13.1 Snowman


0:18 5-4-2014 nginx 1.5.13.1 Snowman

.-= This Is Snowman =-.
Here's a little snowman fast and fat, here's it's power as fast as a cat
When you run Windows you can hear it shout, take me in try me out!
The nginx Snowman release is here!

Based on nginx 1.5.13 (3-4-2014) with;
+ A fix for ssl_session_cache via trac ticket #528, thanks to Maxim!
+ Stability fixes, more performance tuning
+ multiple workers now use an api (efficiency and control)
+ Streaming with nginx-rtmp-module, v1.1.4 (upgraded 3-4-2014)
+ Naxsi WAF v0.53-1 (upgraded 3-4-2014, conf\naxsi_core.rules id 15+16)
+ LuaJIT-2.0.3 (upgraded 31-3-2014) Tnx to Mike Pall for his hard work!
+ lua51.dll (upgraded 31-3-2014) DO NOT FORGET TO REPLACE THIS FILE !
+ lua-nginx-module v0.9.7 (upgraded 3-4-2014)
+ FAQ included in archive
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications are like 20:29 18-3-2014 nginx 1.5.12.2 Cheshire


20:29 18-3-2014 nginx 1.5.12.2 Cheshire

Based on nginx 1.5.12 (release 18-3-2014) with;
+ nginx security advisory (CVE-2014-0133)
+ echo-nginx-module v0.51 (upgraded 18-3-2014)
+ Nginx-limit-traffic-rate-module (https://github.com/bigplum/Nginx-limit-traffic-rate-module)
+ lua-nginx-module v0.9.6 (upgraded 18-3-2014)
+ changed compile order (openresty)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications are like 13:58 9-3-2014 nginx 1.5.12.1 Cheshire


13:58 9-3-2014 nginx 1.5.12.1 Cheshire

Based on nginx 1.5.12 (9-3-2014) with;
+ Fixed a c99 logging issue in naxsi
+ Now includes nginx_basic. Need a simple powerful Windows webserver without all the
  bling of it's big brother ? then nginx_basic is for you, other custom builds are
  available upon request
+ nginx security advisory (CVE-2014-0088)
+ encrypted-session-nginx-module (https://github.com/agentzh/encrypted-session-nginx-module)
+ Fully ASLR and DEP compliant for shared memory (ea. limit_conn_zone, limit_req_zone, etc.)
+ lua-upstream-nginx-module (https://github.com/agentzh/lua-upstream-nginx-module)
+ lua-nginx-module v0.9.5rc2 (upgraded 8-3-2014)
+ Streaming with nginx-rtmp-module, v1.1.3 (upgraded 8-3-2014)
+ echo-nginx-module v0.51 (upgraded 21-2-2014)
+ headers-more-nginx-module v0.25 (upgraded 17-1-2014)
+ nginx-auth-ldap (upgraded 21-2-2014)
+ HttpSubsModule (upgraded 21-2-2014)
+ Additional custom 503 error handler via 513 (see onsite readme for example)
  Issue: a "return 503" can only be used once in a location block, when a custom 503
         is used for example with limit_req_zone you can't have a second custom 503
	 for a maintenance page
  example:
    server {
        listen  80;
        server_name  www.any.nl;
        root    '/webroot/www.any.nl';
        error_page 503 @floodnotice;
        error_page 513 @maintenance;
        location / {
            if (-f $document_root/maintenance_mode.html) { return 513; }
            # Or with a local IP check
            # set $maintmode S; if ($remote_addr ~ "^(10.10.*.*)$") { set $maintmode L; }
            # if (-f $document_root/maintenance_mode.html) { set $maintmode "${maintmode}M"; }
            # if ($maintmode = SM) { return 513; }
            # Yes we all know by now, ifisevil so put a sock in it
            try_files $uri $uri/ =404;
            index  index.html index.htm;
            limit_req zone=floodh burst=32 nodelay;
            # generates a 503 when triggered
            # see limit_req_zone directive how limit_req works
        }
        location @floodnotice {
            root html
            rewrite ^(.*)$ /floodnotice.html break;
        }
        location @maintenance {
            rewrite ^(.*)$ /maintenance_mode.html break;
            # process a 513 but return a 503 to client !
        }
    }
  The normal behavior would be (if the file exists) to return the contents 
  of "/maintenance_mode.html" with a "HTTP/1.1 200 OK", or when the 503 error_page
  is used a 503, however a 503 is often used for other things, With this new 513
  error_page the same thing can be done but the 513 is replaced with a 503 when
  the headers are compiled which allows you to use the real 503 for other things
+ Select-boost: event driven, non-blocking API select() replacement, Beta
  No need to enable anything, it is fully automatic and won't be used if certain
  conditions do not pass internal tests
+ Source changes back ported
+ Source changes add-on's back ported
* Additional specifications are like 14:05 10-1-2014: nginx 1.5.9.1 Cheshire


14:05 10-1-2014: nginx 1.5.9.1 Cheshire

When she sleeps she gently purrs, you hardly know she's there, but when she wakes
you're gonna hear her roar. nginx Cheshire release is here !
This native build runs on Windows XP SP3 and higher, both 32 and 64 bit.

Based on nginx 1.5.9 (4-1-2014) with;
+ changed compile order
+ prove01.zip (onsite), a Windows Test_Suite way to show/prove it all really works
+ ngx_http_auth_ldap2 (experimental, https://github.com/kvspb/nginx-auth-ldap)
  follow examples on github site, not the site example in example.conf, this is an
  experimental build addition ! (when not used it won't affect anything else)
+ set-misc-nginx-module (https://github.com/agentzh/set-misc-nginx-module)
+ headers-more-nginx-module (https://github.com/agentzh/headers-more-nginx-module)
+ openssl-1.0.1f (upgraded 8-1-2014)
+ lua-nginx-module v0.9.4 (upgraded 9-1-2014)
+ Streaming with nginx-rtmp-module, v1.1.1 (upgraded 10-1-2014)
+ echo-nginx-module v0.50 (upgraded 8-1-2014)
- RDNS has been removed until a blocking issue has been resolved
+ added http_auth_request_module
+ Source changes back ported
+ Source changes add-on's back ported
* Additional specifications are like 19:46 18-12-2013: nginx 1.5.8.3 Caterpillar


19:46 18-12-2013: nginx 1.5.8.3 Caterpillar

Based on nginx 1.5.8 (release) with;
+ prove.zip (onsite), a Windows Test_Suite way to show/prove it all really works
  with at the moment a limited amount of tests which will grow over time
+ Streaming with nginx-rtmp-module, v1.0.8 (upgraded 16-12)
+ pcre-8.34 (upgraded)
+ lua-nginx-module v0.9.3 (upgraded)
+ echo-nginx-module v0.50 (upgraded)
+ Source changes back ported (including fixes for the changed resolver API)
+ Source changes add-on's back ported (including fixes for the changed resolver API)
* More compiler optimizations
* Additional specifications are like 15:34 6-12-2013: nginx 1.5.8.2 Caterpillar


15:34 6-12-2013: nginx 1.5.8.2 Caterpillar

Based on nginx 1.5.8 (5-12-2013) with;
+ Fix for nginx -t 'Assertion failed' issue
+ HttpSubsModule (https://github.com/yaoweibin/ngx_http_substitutions_filter_module)
+ echo-nginx-module (https://github.com/agentzh/echo-nginx-module)
+ ngx_http_lower_upper_case (https://github.com/replay/ngx_http_lower_upper_case)
+ Naxsi WAF (Web Application Firewall) v0.53-1 (upgraded 5-12-2013)
+ lua-nginx-module v0.9.2 (upgraded 6-12)
+ Streaming with nginx-rtmp-module, v1.0.8 (upgraded 6-12)
+ Source changes back ported
+ Source changes add-on's back ported
* The debug version is no longer needed, Intel static profiler data is used
  nginx crash info/logging or event dump info is all that is needed
* Intel static profiler "the need for speed" compiler optimization
* Additional specifications are like 19:18 30-11-2013: nginx 1.5.8.1 Caterpillar


19:18 30-11-2013: nginx 1.5.8.1 Caterpillar

Based on nginx 1.5.8 (29-11-2013) with (mainly bugfixes in add-on's);
+ Naxsi WAF (Web Application Firewall) v0.53-1 (upgraded)
+ lua-nginx-module v0.9.2 (upgraded 30-11)
+ Streaming with nginx-rtmp-module, v1.0.8 (upgraded 29-11)
+ Source changes back ported
+ Source changes add-on's back ported
* Additional specifications are like 20:32 19-11-2013: nginx 1.5.7.2 Caterpillar


20:32 19-11-2013: nginx 1.5.7.2 Caterpillar

Based on nginx 1.5.7 (19-11-2013) with;
+ nginx fix for CVE-2013-4547 (nginx 1.5.7.1 Caterpillar removed from download)
+ Source changes back ported
+ Simplified new installations
* Additional specifications are like 12:22 16-11-2013: nginx 1.5.7.1 Caterpillar


12:22 16-11-2013: nginx 1.5.7.1 Caterpillar

The nginx 'Caterpillar' is a "you are no longer in Kansas Alice" *MONSTER* release bringing
to Windows full scalability with multiple workers!
This native build runs on Windows XP SP3 and higher, both 32 and 64 bit.

Based on nginx 1.5.7 (9-11-2013 + spdy hang fix) with;
+ A solution for the multiple worker(shm_) issue, commercially sponsored solution by ITPP
  with a HUGE thanks to Vittorio Francesco Digilio from Italy for his relentless debugging,
  analysis and solution !
+ Naxsi WAF (Web Application Firewall) v0.53 (https://github.com/nbs-system/naxsi)
  see https://github.com/nbs-system/naxsi/wiki how to use it and also see the conf/ folder
+ lua-nginx-module v0.9.2 (upgraded)
+ Streaming with nginx-rtmp-module, v1.0.6 (http://nginx-rtmp.blogspot.nl/) (upgraded)
* Additional specifications are like 12:38 2-10-2013: nginx 1.5.6.4 Butterfly


12:38 2-10-2013: nginx 1.5.6.4 Butterfly

The Nginx 'Butterfly' release brings to Windows stable and unleashed power of Nginx, Lua, 
Streaming feature, Reverse DNS, SPDY, easy c250k in a non-blocking and event driven build 
which runs on Windows XP SP3 or higher, both 32 and 64 bit.

Based on nginx 1.5.6 (release) with;
+ RDNS (https://github.com/flant/nginx-http-rdns)
+ Array-var-nginx-module (https://github.com/agentzh/array-var-nginx-module)
+ ngx_devel_kit v0.2.19
+ lua-nginx-module v0.9.0
* Additional specifications are like 13:46 25-9-2013: nginx 1.5.6.3 Alice


13:46 25-9-2013: nginx 1.5.6.3 Alice

Based on nginx 1.5.6 (25-9-2013) with;
+ Bug fixes in lua-nginx-module(master 25-9-2013) and ngx_devel_kit(master 25-9-2013) by agentzh
+ Both debug and non-debug versions, the non-debug version is production use ready ! 
* vcredist_x86 is required, get it here (http://www.microsoft.com/en-us/download/details.aspx?id=5555)
* Additional specifications are like 10:37 23-9-2013: nginx 1.5.6.1 Alice
* 1.5.6.2 was skipped for public release


10:37 23-9-2013: nginx 1.5.6.1 Alice

Based on nginx 1.5.6 (22-9-2013) with;
+ Streaming with nginx-rtmp-module, v1.0.4 (http://nginx-rtmp.blogspot.nl/)
+ lua-nginx-module v0.8.9 (tnx to agentzh about precompiled headers!)
+ LuaJIT-2.0.2 => (lua51.dll include / lua51.lib build)
+ Added lua51.dll (is required)
+ ngx_devel_kit v0.2.15
* Additional specifications are like 10:27 10-9-2013: B02 build


10:27 10-9-2013: B02 build

Based on nginx 1.4.2 with;
  pcre-8.32
  zlib-1.2.8
  openssl-1.0.1e
+ Compiled with: FD_SETSIZE = 16384 (original Windows source files modified)
+ Now capable to handle C250K ! (with optimization registry file)
+ Added Windows optimization registry file, check your current values BEFORE setting the new ones
+ Added debug symbols file (let us know where it went wrong when you have a crash)
+ Added adjusted nginx(-win).conf for Windows
+ Added SPDY
* Runs on Windows XP SP3 or higher, both 32 and 64 bit
* Set priority to High for both nginx.exe processes
* When nginx is running as a service: My computer -> Properties -> Advanced -> Performance -> 
  Advanced -> Processor scheduling, Adjust for best performance set to background services
* Website created for easy download: http://nginx-win.ecsds.eu/


19:40 2-9-2013: B01 build

Hello,

If you are following this thread (Transforming nginx for Windows):
http://forum.nginx.org/read.php?2,242426

Then this is the experimental binary you are looking for.

Compiled with:
FD_SETSIZE = 8192 (due to a recycle system in nginx you will be able to get
more than 16k concurrent connections with 4096 worker_connections, but feel free to
try out values all the way up to 8192)
This value has been compiled from scratch (original Windows source files modified
to accommodate a larger FD table)


				  DISCLAIMER

Use of this program acknowledges this disclaimer of warranty:
"This program is supplied as is. The author(s) and associated companies disclaims all warranties,
express or implied, including, without limitation, the warranties of merchantability and of fitness
of this program for any purpose. The author(s) and associated companies assumes no liability for
damages direct or consequential, which may result from the use of or inability to use this program.
Even if author(s) and associated companies has been advised of the possibility of such damages or
any claim by any other party."
