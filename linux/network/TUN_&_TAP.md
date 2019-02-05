=== Install tools (tunctl) ===
sudo apt-get install uml-utilities
sudo gpasswd -a <username> uml-net

=== Create a virtual NIC ===
sudo tunctl -b
ip link set tap0 up

ifconfig tap0 192.168.0.1  netmask 255.255.255.0 promisc

