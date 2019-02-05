Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-03-01T10:19:24+08:00

====== remote shell ======
'''

pdsh -R ssh -l user -w host1,host2 "some command"
dsh -r ssh -m user@host1 -m user@host2 -- ls -a

pdcp 
p./-w m./-w mdcp -R ssh -w vm[2-5] -r ~/m

mussh
cssh

pssh 
pssh -P -h test.txt uptime
pscp -h test.txt /etc/sysconfig/network /tmp/network

dsh [-m machinename | -a | -g groupname] [-f machinefile] [-M] [-q] [--wait-shell]--commandline
'''


scp local_file remote_username@remote_ip:remote_folder
scp local_file remote_username@remote_ip:remote_file
scp local_file remote_ip:remote_folder
scp local_file remote_ip:remote_file


