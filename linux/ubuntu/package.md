http://blog.csdn.net/michaelwubo/article/details/40588059

sudo apt-get install software-properties-common
sudo apt-get install apt-file && apt-file update
apt-file search add-apt-repository


sudo apt-file update
apt-file search filename
apt-file search /path/to/file
apt-file list package

apt-show-versions

dpkg -S /usr/bin/ls 查看某个文件属于哪个deb包
dpkg -r apt 
dpkg -X xxx.deb dirname
dpkg -e xxx.deb 

dpkg -c filename 显示一个Deb文件的目录
dpkg -L package-Name 显示一个包安装到系统里面的文件目录信息
dpkg -i <.deb file name> 安装软件
dpkg -R 安装一个目录下面所有的软件包
dpkg --unpack package_file 释放软件包，但是不进行配置,如果和-R一起使用，参数可以是一个目录
dpkg --configure package_file 重新配置和释放软件包,如果和-a一起使用，将配置所有没有配置的软件包
dpkg -r 删除软件包（保留其配置信息）
dpkg --update-avail <Packages-file> 替代软件包的信息
dpkg --merge-avail <Packages-file> 合并软件包信息
dpkg -A package_file 从软件包里面读取软件的信息
dpkg -P 删除一个包（包括配置信息）
dpkg --forget-old-unavail 丢失所有的Uninstall的软件包信息
dpkg --clear-avail 删除软件包的Avaliable信息
dpkg -C 查找只有部分安装的软件包信息
dpkg --compare-versions ver1 op ver2 比较同一个包的不同版本之间的差别
dpkg --help 显示帮助信息
dpkg --licence (or) dpkg --license 显示dpkg的Licence
dpkg --version 显示dpkg的版本号
dpkg -b direc×y [filename] 建立一个deb文件
dpkg -I filename [control-file] 显示一个Deb的说明
dpkg -l package-name-pattern 搜索Deb包
dpkg -l 显示所有已经安装的Deb包，同时显示版本号以及简短说明
dpkg -s package-name 报告指定包的状态信息
dpkg -S filename-search-pattern 搜索指定包里面的文件（模糊查询）
dpkg -p package-name 显示包的具体信息


dpkg-deb --build Cydia

apt-cache search package 搜索软件包
apt-cache show package  获取包的相关信息，如说明、大小、版本等
apt-cache depends package 了解使用该包依赖那些包
apt-cache rdepends package 查看该包被哪些包依赖

sudo apt-get install package 安装包
sudo apt-get install package --reinstall   重新安装包
sudo apt-get -f install   修复安装
sudo apt-get remove package 删除包
sudo apt-get remove package --purge 删除包，包括配置文件等
sudo apt-get update  更新源
sudo apt-get upgrade 更新已安装的包
sudo apt-get dist-upgrade 升级系统
sudo apt-get build-dep package 安装相关的编译环境
apt-get source package  下载该包的源代码
sudo apt-get clean && sudo apt-get autoclean 清理无用的包
sudo apt-get check 检查是否有损坏的依赖


sudo dpkg -i XXX.deb
sudo apt-get install -f
gdebi /root/flightgear_2.6.0-1.1_amd64.deb
