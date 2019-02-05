=== /etc/bind/named.conf.local ===

zone "binyi.hou" in {
		type master;
		file "/etc/bind/db.binyi.hou";
};

zone "56.168.192.in-addr.arpa" in {
		type master;
		file "/etc/bind/db.192.168.56";
};

=== /etc/bind/db.binyi.hou ===

$TTL 10800
binyi.hou. IN SOA u01.binyi.hou. root.localhost. (
		1       ; Serial
		10800   ; Refresh after 3 hours
		3600    ; Retry after 1 hour
		86400   ; Expire after 1 week
		3600 )  ; Negative caching TTL of 1 hour

binyi.hou. IN NS u01.binyi.hou.

u01.binyi.hou. IN A 192.168.56.101
u02.binyi.hou. IN A 192.168.56.102
u03.binyi.hou. IN A 192.168.56.103

u1.binyi.hou. IN CNAME u01.binyi.hou.
u2.binyi.hou. IN CNAME u02.binyi.hou.
u3.binyi.hou. IN CNAME u03.binyi.hou.

=== /etc/bind/db.192.168.56 ===

$TTL 10800
56.168.192.in-addr.arpa. IN SOA u01.binyi.hou. root.localhost. (
		1       ; Serial
		10800      ; Refresh after 3 hours
		3600      ; Retry after 1 hour
		86400      ; Expire after 1 week
		3600 )    ; Negative caching TTL of 1 hour

56.168.192.in-addr.arpa. IN NS u01.binyi.hou.

101.56.168.192.in-addr.arpa. IN PTR u01.binyi.hou.
102.56.168.192.in-addr.arpa. IN PTR u02.binyi.hou.
103.56.168.192.in-addr.arpa. IN PTR u03.binyi.hou.




