!SLIDE
# Know Yer App #

!SLIDE bullets incremental

# Understand it #
* New Relic
* Scout
* RIP FiveRuns

!SLIDE center

![New Relic](nr.jpg)

!SLIDE center
![New Relic](nr2.png)

!SLIDE bullets incremental

# Profile yer App #
* AB is not that great.
* Use a real tool like Apache JMeter

!SLIDE center
![Jmeter](jmeter.png)

!SLIDE 
# Huge learning curve, but very worth it #

!SLIDE bullets incremental small
* test plans and threads
* per worker (thread) cookies
* dynamic data
* conditions
* monitor servers, mysql, etc...
* plugins
* full of awesome

!SLIDE bullets incremental

# Found weak points, usually: #
* Not caches\_page’ing, caches\_action’ing, and fragment caching
* Shitty SQL 
* External Everything

!SLIDE bullets incremental

# Crazy things in views #
* ..like
* .each without using :include 

!SLIDE bullets incremental

* ActionMailering, Reporting, Processing inside an action
* Move to the background yo

!SLIDE bullets incremental small

# use Resque #
* emailing users
* rmagicking
* tarballing
* reporting
* gather external
* deleting, adding, updating
* _anything_ that would otherwise chew up a worker