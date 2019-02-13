---
title: Monitoring your Raspberry Pi with SNMP
#permalink: /pi/monitoring-your-raspberry-pi-with-snmp/
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
#header:
#  teaser: /assets/images/math/statistical-sampling/sampling-header.jpg
#  image: /assets/images/math/statistical-sampling/sampling-header.jpg
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
