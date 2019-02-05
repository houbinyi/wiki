Ubuntu 使用 AppArmor 作为程序权限限制， Fedora 使用 selinux 作为程序权限限制.在linux中，以往的权限管理，是通过用户绑定的，现在还有一种权限机制，设置程序的访问权限，如：

sudo mysqldump --T db;如果不起动程序权限管理，mysqldump获得root权限，可以在任何文件中进行操作。

sudo mysqldump -T db;如果ubuntu中启用apparmor，即使是root权限，他也会根据程序的访问权限进行限定。

所以我们可以将需要访问的目录添加到AppArmor的配置文件中:

sudo gedit /etc/apparmor.d/usr.sbin.mysqld

添加下面内容

/data/* rw,

然后,sudo /etc/init.d/apparmor restart
