**Client**
Gmond (Ganglia monitoring daemon): a small service that collects information about a node. This is installed on every server you want monitored.

apt-get install ganglia-monitor



**Server**
Gmetad (Ganglia meta daemon): a daemon on the master node that collects data from all the Gmond daemons (and other Gmetad daemons, if applicable).

RRD (Round Robin Database) tool: a tool on the master node used to store data and visualizations for Ganglia in time series.

PHP web front-end: a web interface on the master node that displays graphs and metrics from data in the RRD tool.

sudo apt-get install rrdtool gmetad ganglia-webfrontend

sudo cp /etc/ganglia-webfrontend/apache.conf /etc/apache2/sites-enabled/ganglia.conf
