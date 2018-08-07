# working with docker

docker image ls # all pulled containers
docker ps # all running containers with ids
  
### You _can_ copy files from host to container:
docker cp knwr_F_spades.fa.gz 30face09e8f8:/home/linuxbrew/tigmint/spades
### but probably always preferable to just mount your host folder to /mnt with -v:
docker run -it -v /home/ubuntu/reads:/mnt bjmain/arcs:firsttry

### To update tools inside an instance or image:
sudo apt-get update
#### install vi
sudo apt-get install vim

### get [linuxbrew](http://linuxbrew.sh/)

### If you want to pull a private docker image:
docker login 
bjmain
@
docker pull bjmain/arcs:firsttry

### To run both [Tigmint](https://hub.docker.com/r/bcgsc/tigmint/) and scaffold the corrected assembly with ARCS : 
/home/linuxbrew/tigmint/bin/tigmint-make arcs draft=knwr_F_spades reads=barcoded  #you need to be in the same directory as reads

### copy files to and from aws
scp -i .pem knwr_F_spades.fa.gz ubuntu@XXXXamazonaws.com:~
scp -i .pem ubuntu@XXXXamazonaws.com:~ knwr_F_spades.fa.gz 
