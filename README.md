Why?
====

Unix world needs a CLI based CC monitoring tool that can accept various inputs. While piping MPEG-TS packets into dvbsnoop works, dvbsnoop does lots of other unnecessary processing using valuable CPU time. Using non-unix tools doesn't work either should you want to run headless. So CCmon was born.


Examples
========

$ CCmon 

Default socket mode:
  CCmon -group 239.3.1.1 -dev eth0

Using pcap capture:
  CCmon -group 239.3.1.1 -mode pcap -dev mirror

Using pcap capture with vlan and different port number:
  CCmon -group 239.3.1.1 -mode pcap -dev mirror -vlan 4 -port 666

Reading from file:
  CCmon -group myfilename -mode file

Additional parameters:
  -pidfilter X        Run only on specific PID, ignore others
  -stats              Report every 100000 packets received
  -cache              Cache last 5 packets for every PID, display on CC error
  -debug              Display all packets processed

$ sudo CCmon -group 239.3.1.1 -dev mirror -mode pcap -vlan 4
Fri Jan  6 13:09:41 2012: Starting with mode:pcap dev:mirror vlan:4 group:239.3.1.1 port:1234
Fri Jan  6 13:09:41 2012: Found PID: 0x2c0
Fri Jan  6 13:09:41 2012: Found PID: 0x324
Fri Jan  6 13:09:41 2012: Found PID: 0x0
Fri Jan  6 13:09:41 2012: Found PID: 0xcc
Fri Jan  6 13:09:41 2012: Found PID: 0x1f69
Fri Jan  6 13:09:41 2012: Found PID: 0x11
Fri Jan  6 13:09:41 2012: Found PID: 0x1
Fri Jan  6 13:09:46 2012: Found PID: 0x14
Fri Jan  6 13:09:52 2012: CC error! PID: 0x324 Expected: 14, is 8
Fri Jan  6 13:09:52 2012: CC error! PID: 0x1f69 Expected: 2, is 9
Fri Jan  6 13:09:52 2012: CC error! PID: 0x0 Expected: 5, is 10
Fri Jan  6 13:09:52 2012: CC error! PID: 0xcc Expected: 7, is 12
Fri Jan  6 13:09:52 2012: CC error! PID: 0x1 Expected: 5, is 7
Fri Jan  6 13:09:52 2012: CC error! PID: 0x11 Expected: 15, is 0
^C
exiting...
Fri Jan  6 13:10:06 2012: PCAP: recv:10691, drop:0, ifdrop:0
Fri Jan  6 13:10:06 2012: PID: 0x14, packets: 2
Fri Jan  6 13:10:06 2012: PID: 0x11, packets: 23
Fri Jan  6 13:10:06 2012: PID: 0x1, packets: 45
Fri Jan  6 13:10:06 2012: PID: 0xcc, packets: 113
Fri Jan  6 13:10:06 2012: PID: 0x0, packets: 113
Fri Jan  6 13:10:06 2012: PID: 0x1f69, packets: 574
Fri Jan  6 13:10:06 2012: PID: 0x324, packets: 3110
Fri Jan  6 13:10:06 2012: PID: 0x2c0, packets: 67483


License
=======
MIT License.  Copyright 2012 Tarko Tikan.
