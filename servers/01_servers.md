!SLIDE bullets incremental

# Bit on Ruby web servers #
* Unicorn
* Passenger
* <strike>Mongrel</strike>
* thin, ebb

!SLIDE bullets incremental small

# Passenger - Good #
* Built in worker management.  Can require memory monitoring.
* Attached at the hip to Nginx.  "Less moving parts"
* Zero Downtime Deploy &#x2122;	
* Easier to debug when shit hits the fan. 

!SLIDE bullets incremental small

# Passenger - Bad #
* Shit will hit the fan.
* hardcoded backlog, doesn't respect /proc/sys/net/core/somaxconn.  Shit hits fan.
* No Nginx proxy directives <http://blog.phusion.nl/2011/08/03/phusion-passenger-3-0-8-released>
* Shit hits fan with _lots_ of apps
* Spawns workers as needed.  min_instances is your friend

!SLIDE bullets incremental small
# Unicorn - Good
* Still not that complicated
* More like Mongrel - can use Nginx proxy directives & Unix sockets
* Doesn't seem to break quite as much
* Zero Downtime Deploy &#x2122;	
* Unicorn master does a good job

!SLIDE bullets incremental
# Uncicorn - Bad
* Sporadic issues reloading workers at times (USR2)
* Need to manage Unicorn master process to an extent

!SLIDE 
# Preference, really. #

!SLIDE
# Nginx #

!SLIDE bullets incremental
# Cache everything #

!SLIDE bullets incremental
# Nginx should serve _all_ static content 
* (that isn't being served by a CDN or S3)
* try_files  $uri $uri/index.html $uri.html @passenger-or-uniorn

!SLIDE bullets incremental

# HAProxy #
* super efficient and really doesn’t need a server all to it’s own.   
* Just run a few less workers on app master
* Never seen it be first piece to break