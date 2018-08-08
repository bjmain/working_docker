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


### C++ compiler install
sudo apt-get install build-essential
### boost install
cd /home/ubuntu/bin/arcs
        wget https://sourceforge.net/projects/boost/files/boost/1.58.0/boost_1_58_0.tar.gz
        tar -zxvf boost_1_58_0.tar.gz
        cd boost
        ./bootstrap.sh 
        ./b2 install
### Configure arcs        
./configure --with-boost=/home/ubuntu/bin/arcs/boost_1_58_0/

sudo apt-get install libz-dev
git clone https://github.com/bcgsc/LINKS.git

### add dependencies to path (.bashrc + source):
export PATH=$PATH:/home/bradmain/gambiae/malphigs/Acol/BitSeq/


sudo make install

### run arcs + tigmint:
/home/ubuntu/bin/arcs/Examples/arcs-make arcs-tigmint draft=scaffolds_5k reads=barcoded

/home/ubuntu/bin/arcs/Examples/pipeline_example.sh scaffolds_5k barcoded

## Note: If the stop an AWS instance, screens are terminated with its running docker container

### copy files to and from aws
scp -i .pem knwr_F_spades.fa.gz ubuntu@XXXXamazonaws.com:~
scp -i .pem ubuntu@XXXXamazonaws.com:~ knwr_F_spades.fa.gz 

### Initially the pipeline was breaking because of an old version of samtools!
### update samtools on aws
Read the ubuntu section of the INSTALL file and it gives a list of all dependencies and how to install
$ sudo apt remove samtools
$ sudo ln -s /usr/local/bin/bin/samtools /usr/bin/samtools

