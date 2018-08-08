###############################################################################
# Working with docker
###############################################################################

### Installation
curl -sSL https://get.docker.com/ | sh


[cheatsheet](https://github.com/wsargent/docker-cheat-sheet)
  
### attach and detach from running contatiner
docker excec -it 26fe6d658472 /bin/bash

cntrl + p + q # detach

### kill container
docker kill ##id##

### You _can_ copy files from host to container:
docker cp knwr_F_spades.fa.gz 30face09e8f8:/home/linuxbrew/tigmint/spades
### but probably always preferable to just mount your host folder to /mnt with -v:
docker run -it -v /home/ubuntu/reads:/mnt bjmain/arcs:firsttry

### To update tools inside an instance or image:
sudo apt-get update
### install automake & aclocal for installing arcs (autogen.sh)
sudo apt-get install autotools-dev

sudo apt-get install automake

#### install vi
sudo apt-get install vim

### get [linuxbrew](http://linuxbrew.sh/)

### If you want to pull a private docker image:
docker login # insert sudo if non-root
bjmain
@
docker pull bjmain/arcs:firsttry  # insert sudo if non-root

### To run both [Tigmint](https://hub.docker.com/r/bcgsc/tigmint/) and scaffold the corrected assembly with ARCS : 
/home/linuxbrew/tigmint/bin/tigmint-make arcs draft=knwr_F_spades reads=barcoded  #you need to be in the same directory as reads

## Note: If the stop an AWS instance, screens are terminated with its running docker container

### copy files to and from aws
scp -i .pem knwr_F_spades.fa.gz ubuntu@XXXXamazonaws.com:~
scp -i .pem ubuntu@XXXXamazonaws.com:~ knwr_F_spades.fa.gz 
