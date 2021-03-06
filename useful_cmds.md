useful commands
===============

Change default editor to vim on ubuntu:
sudo update-alternatives --config editor

Install java on ubuntu:
sudo add-apt-repository ppa:openjdk-r/ppa 
sudo apt update 
sudo apt install openjdk-11-jdk

install java on centos:

## Installing & setting Java12

curl -O https://download.oracle.com/java/GA/jdk12.0.1/69cfe15208a647278a19ef0990eea691/12/GPL/openjdk-12.0.1_linux-x64_bin.tar.gz
sudo tar -zxvf openjdk-12.0.1_linux-x64_bin.tar.gz -C /usr
sudo update-alternatives --install /usr/bin/java java /usr/jdk-12.0.1/bin/java 1
export PATH=$PATH:/usr/jdk-12.0.1/bin
export JAVA_HOME=/usr/jdk-12.0.1


## secure copy
scp -i allen_01.pem /path/to/odfe-es-0.8.0.tar ubuntu@ec2-34-232-63-30.compute-1.amazonaws.com:~

## check linux version
cat /etc/os-release

## Reverse package to folder
dpkg-deb -R package.deb tmp

#build package from folder
dpkg-deb -b tmp

## see all versions of a apt package
apt-cache policy package_name

## grow fs to ebs
sudo xfs_growfs /dev/nvme0n1p1

## No space left on device

1. Grow ebs
2. sudo growpart /dev/xvda 1 (for nvme: sudo growpart /dev/nvme0n1 1)
3. sudo resize2fs /dev/xvda1 (for nvme: sudo resize2fs /dev/nvme0n1p1)

Details see [here](https://stackoverflow.com/questions/52508038/how-to-increase-aws-ebs-nvme-size)


## Find dir with many files
sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n

## Find number of files in current directory
find -type f | wc -l

## Extract and see what's inside a rpm package

repoquery --installed -l pkg

rpm2cpio ./packagecloud-test-1.1-1.x86_64.rpm | cpio -idmv

