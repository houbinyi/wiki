=== wireshark ===

=== TCPDump ===
tcpdump host 192.168.56.1
tcpdump host 192.168.56.1 and \(192.168.56.2 or 192.168.56.3\)
tcpdump ip host 192.168.56.1 and ! 192.168.56.103
tcpdump icmp -n -i eth0
tcpdump tcp port 25 and host 192.168.56.103

=== NMap ===
sudo apt install nmap
nmap -sT ***.***.***.***
nmap -sU ***.***.***.***
nmap -sS 192.168.56.1 -255 -p 80,25-30 --v
-sT : tcp
-sU : udp
-sP : connect by Ping ICMP
-sS : tcp SYN
-sA : tcp ACK

=== hping ===
hping3 -1 -a 192.168.1.101 192.168.1.255
