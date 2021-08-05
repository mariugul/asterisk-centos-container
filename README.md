# Setting up Asterisk in centOS container
This is a description for installing and setting up Asterisk as described in the book "Asterisk The Definitive Guide". The installation is done in a centOS docker container. Microsoft doesn't provide a devcontainer for centOS, so the official centOS image from Docker Hub was used.

## Download and run centOS
Downloads centOS 7 official image from docker hub and runs it in the background.

```docker
docker pull centos:7
docker run --name asterisk -it -d centos
```

## Attach vscode to centOS Container
Go into Remote Explorer in vscode and attach to the running centOS containerP. It's going to be called "centos asterisk". The extension "Remote - Containers" by Microsoft is needed for this.


-----------------------------------------------------------------------
### ⚠️ <span style="color:yellow"> All commands instructed to be entered and applications to be installed from here and down are going to be inside the centOS container.</span> 
-----------------------------------------------------------------------

## Install sudo, clear and which
For some reason these are missing from the image. Run this command to install them.
```bash
yum install -y sudo ncurses which
```

## Install Prerequisites
Run these commands in the command line or run the script *asterisk-prerequisites.sh*
```bash 
sudo yum -y update &&
sudo yum -y install epel-release &&
sudo yum -y install python3-pip &&
sudo yum -y install vim wget dnf &&
sudo pip3 install alembic ansible &&
sudo pip3 install --upgrade pip && 
sudo mkdir /etc/ansible &&
sudo chown root:root /etc/ansible &&
sudo echo "[starfish]" >> /etc/ansible/hosts &&
sudo echo "localhost ansible_connection=local" >> /etc/ansible/hosts &&
mkdir -p ~/ansible/playbooks
```

## Install Dependencies
.

## Install Asterisk
