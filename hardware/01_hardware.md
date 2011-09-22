!SLIDE bullets incremental
# Hardware #
* (virtual)

!SLIDE bullets incremental

# Current setup #
* 1 server: App + DB + Cron + Resque + Mongo
* 4 CPU, 8G memory
* gets crappy quick
* IO contention city

!SLIDE bullets incremental

# Old faithful #
* 1 App + 1 DB + 1 Utility
* App = Nginx + Ruby Server + Memcached
* Utility = Resque, Mongo, Redis, Cron
* Database = MySQL, Postgres, whatever

* works great

!SLIDE bullets incremental
# Specs #
* App - CPU is paramount.
* DB - CPU/Memory/IO.
* Utility - Save money here.

!SLIDE bullets incremental
# 1 App master + _n_ App + DB + _n_ Utility
* Master = LB (HAProxy:80:443) + Nginx:81:444 + Ruby Server + (Memcached)
* App Nginx:81:444 + Ruby Server + (Memcached)
* Utility = Resque, Mongo, Redis, Cron

!SLIDE
# Take you a long way #

!SLIDE bullets incremental
# Out grow that? #
* 1 Master (Hardware LB?) + _n_ App + DB (writes) + DB Slave (reads) + _n_ Utility
* Out of scope
* _but_, DB slave can be useful for DB backups & reporting
