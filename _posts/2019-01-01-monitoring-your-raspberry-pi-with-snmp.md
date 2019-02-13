---
title: Monitoring your Raspberry Pi with SNMP
permalink: /blog/monitoring-your-raspberry-pi-with-snmp/
#author: "Wouter Schoot"

categories:
  - pi
tags:
  - pi
  - snmp
  - a
  - b
  - bc
  - asd
  - zxc
header:
  teaser: /assets/images/posts/RPi-Logo-Reg-SCREEN.png
  #image: /assets/images/posts/RPi-Logo-Reg-SCREEN.png
---

```bash
yum install net-snmp
vim /etc/snmp/snmpd.conf
```
Voeg wat execs toe
```bash
exec pitemp /opt/vc/bin/vcgencmd measure_temp | /bin/egrep -o ‘[0-9][0-9]\.[0-9]’
exec picorefreq /opt/vc/bin/vcgencmd measure_clock core | cut -d= -f2
exec picpufreq /opt/vc/bin/vcgencmd measure_clock arm | cut -d= -f2
exec picorevolt /opt/vc/bin/vcgencmd measure_volts core | /bin/egrep -o ‘[0-9]*\.[0-9]*’
```
