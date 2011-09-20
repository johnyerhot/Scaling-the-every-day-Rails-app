!SLIDE bullets incremental
# Hardware #
* (virtual)

!SLIDE bullets incremental
# 1 App + 1 DB + 1 Utility
* App = Nginx + Ruby Server + Memcached
* Utility = Resque, Mongo, Redis, Cron

* works great

!SLIDE bullets incremental
# Specs #
* App - CPU is pretty much most important
* DB - CPU/Memory/IO
* Utility can get away with not so hot hardware usually. Save money here.

!SLIDE bullets incremental
# 1 App master + _n_ App + DB + _n_ Utility
* Master = LB (HAProxy:80:443) + Nginx:81:444 + Ruby Server + (Memcached)
* App Nginx:81:444 + Ruby Server + (Memcached)
* Utility = Resque, Mongo, Redis, Cron, (Memcached)

!SLIDE
# Take you a long way #

!SLIDE bullets incremental
# Out grow that? #
* 1 Master (Hardware LB?) + _n_ App + DB (writes) + DB Slave (reads) + _n_ Utility
* Out of scope
* _but_, DB slave can be useful for DB backups & reporting
