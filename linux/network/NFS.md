=== server ===
sudo apt-get install nfs-kernel-server
sudo vi /etc/exports
/path/to/somewhere/to/expose *(rw,sync,no_root_squash,no_subtree_check)
sudo /etc/init.d/rpcbind restart
sudo /etc/init.d/nfs-kernel-server restart 

=== verification ===
sudo mount -t nfs 127.0.0.1:/path/to/somewhere/to/expose /path/to/mount/point

