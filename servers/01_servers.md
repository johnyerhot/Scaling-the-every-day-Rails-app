!SLIDE bullets

# Part III #
## Ruby Servers ##

!SLIDE bullets

* Unicorn
* Passenger
* <strike>Mongrel</strike>
* thin, ebb

!SLIDE bullets small incremental

# Passenger #
* the good

!SLIDE bullets small

* Built in worker management.  Can require memory monitoring.
* Attached at the hip to Nginx.  "Less moving parts"
* Zero Downtime Deploy &#x2122;
* (Passegner 3 only)
* Easier to debug when shit hits the fan. 

!SLIDE bullets small incremental

# Passenger #
* the bad

!SLIDE bullets small

* Shit _will_ hit the fan.
* hardcoded backlog, doesn't respect /proc/sys/net/core/somaxconn.  Shit hits fan.
* No Nginx proxy directives (timeouts, header size, etc..)
* <http://blog.phusion.nl/2011/08/03/phusion-passenger-3-0-8-released>
* _lots_ of app on an instances tends to be problems.
* Spawns workers as needed.  min_instances is your friend.
* Restarting under high load. Shit hits fan.

!SLIDE bullets small incremental

# Unicorn #
* the good

!SLIDE bullets small

* Still not that complicated
* More like Mongrel - proxy directives FTW
* Doesn't seem to break quite as much
* Zero Downtime Deploy &#x2122;	
* Unicorn master does a good job

!SLIDE bullets incremental

# Uncicorn #
* the bad

!SLIDE bullets

* Sporadic issues reloading workers at times (USR2)
* Need to manage Unicorn master process to an extent.

!SLIDE 
# Preference, really. #

!SLIDE
# Nginx #

!SLIDE bullets
# Cache everything #

!SLIDE bullets
# Nginx should serve _all_ static content .
* (that isn't being served by a CDN or S3).
* `try_files  $uri $uri/index.html $uri.html @passenger-or-uniorn`

!SLIDE 

## If your provider doesn't provide a LB... ##

!SLIDE bullets

# HAProxy #
* Super efficient - really doesn’t need a server all to it’s own.   
* Just run a few less workers on app master.
* Never seen it be first piece to break.