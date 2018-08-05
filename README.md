# working_docker

From host server: docker ps    # gives you container ids
  
docker cp knwr_F_spades.fa.gz 30face09e8f8:/home/linuxbrew/tigmint/spades


inside container:
sudo apt-get update
#install vi
sudo apt-get install vim

#get linuxbrew
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"


test -d ~/.linuxbrew && PATH="$HOME/.linuxbrew/bin:$HOME/.linuxbrew/sbin:$PATH"
test -d /home/linuxbrew/.linuxbrew && PATH="/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH"
test -r ~/.bash_profile && echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.bash_profile
echo "export PATH='$(brew --prefix)/bin:$(brew --prefix)/sbin'":'"$PATH"' >>~/.profile


docker login --username=yourhubusername --email=youremail@company.com
bjmain
@

docker images
docker tag 632ce8e46b32 bjmain/arcs:firsttry

docker pull bjmain/arcs:firsttry
