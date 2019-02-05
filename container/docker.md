sudo apt-get install docker.io
sudo docker -d -H unix:///var/run/docker.sock -H tcp://0.0.0.0:2375
sudo service docker start

[general]
docker version
docker info

[register]
docker search [...]
docker pull [image]

[image]
docker images
docker push [image_name]
docker run [image] [cmd]
docker run -i -t [imag] [cmd]
docker run -d [image] [cmd]

[container]
docker ps -a
docker ps -l
docker inspect [container_id]
docker rm [container_id]
docker start [container_id]
docker logs [container_id]
docker attach [container_id]
docker stop [container_id]
docker commit [container_id] [image_name]

