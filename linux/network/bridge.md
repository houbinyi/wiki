=== All things you should know about bridge ===
http://www.tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html
http://www.cnblogs.com/morphling/p/3458546.html

=== Install tools ===
$ sudo apt-get install bridge-utils

=== List all bridges ===
sudo brctl show    

=== Create new virtual bridge ===
$ sudo brctl addbr <bridge>
$ sudo brctl stp <bridge> off
ip link set <bridge> up

=== Add/Remove new interface to the bridge ===
$ sudo brctl addif <bridge> <eth0>
$ sudo brctl delif virb1 eth5


=== Setup IP address for the interface attached to the bridge ===
$ sudo ifconfig eth0  0.0.0.0
$ sudo ifconfig bridge 10.0.0.1 netmask 255.255.255.0 up

