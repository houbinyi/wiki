=== client ===
sudo vi /etc/default/tftp-hpa

=== server ===
sudo vi /etc/default/tftpd-hpa
sudo vim
# /etc/default/tftpd-hpa
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftpboot" # 这里是你的tftpd-hpa的服务目录,这个想建立在哪里都行
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="-l -c -s" # 这里是选项,-c是可以上传文件的参数，-s是指定tftpd-hpa服务目录，上面已经指定 
sudo service tftpd-hpa restart

=== verification ===
tftp 127.0.0.1
tftp>get test.txt
tftp>put test1.txt
tftp>q 

