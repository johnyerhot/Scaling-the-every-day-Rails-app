!SLIDE bullets
# Hardware #
* (virtual)

!SLIDE bullets

# Current setup #
* one server: App + DB + Cron + Resque + Mongo
* 4 CPU, 8G memory
* gets crappy quick
* IO contention city

!SLIDE bullets

# Old faithful #
* 1 App + 1 DB + 1 Utility

!SLIDE bullets

* App = Nginx + Ruby Server + Memcached
* Utility = Resque, Mongo, Redis, Cron
* Database = MySQL, Postgres, whatever

!SLIDE bullets
# Specs #
* App - CPU is paramount.
* DB - CPU/Memory/IO.
* Utility - Save money here.

!SLIDE bullets
# 1 App master + _n_ App + DB + _n_ Utility

!SLIDE bullets

* Master = LB (HAProxy:80:443) + Nginx:81:444 + Ruby Server + (Memcached)
* App Nginx:81:444 + Ruby Server + (Memcached)
* Utility = Resque, Mongo, Redis, Cron

!SLIDE
# Take you a long way #

!SLIDE
# Out grow that? #

!SLIDE bullets
## 1 Master (Hardware LB?) + _n_ App + DB (writes) + DB Slave (reads) + _n_ Utility ##

!SLIDE bullets

## Out of scope ##

### _but_, DB slave can be useful for DB backups & reporting ###
