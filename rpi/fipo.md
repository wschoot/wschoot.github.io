---
title: 'Deliciously static: from WordPress to Jekyll'
date: 2013-07-05
published: true
expires: never
layout: post
tags:
 - Raspberry Pi
 - snmp
 ---
```bash
yum install net-snmp

vim /etc/snmp/snmpd.conf

Voeg wat execs toe

exec pitemp /opt/vc/bin/vcgencmd measure_temp | /bin/egrep -o ‘[0-9][0-9]\.[0-9]’
exec picorefreq /opt/vc/bin/vcgencmd measure_clock core | cut -d= -f2
exec picpufreq /opt/vc/bin/vcgencmd measure_clock arm | cut -d= -f2
exec picorevolt /opt/vc/bin/vcgencmd measure_volts core | /bin/egrep -o ‘[0-9]*\.[0-9]*’
```
