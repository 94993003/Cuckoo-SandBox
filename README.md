# Cuckoo-SandBox
Shell Script to install Cuckoo sandbox

#1 st -> Enable VT-X in the Machine's Proccessor ->Very Important

#!/bin/sh
echo "----------------------------------------------------------"
echo "Hello To My Special Inistallition"
echo "It is made By Naser Al Abdali"
echo "Enjoy the sandbox"
echo "----------------------------------------------------------"
yes "" |  apt-get update
yes "" |  apt-get upgrade
yes "" |  apt install python2	
python2 -V
yes "" |  apt install curl 
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
yes "" |  python2 get-pip.py
yes "" | echo "10% Proccessed"
yes "" |  apt-get install libffi-dev libssl-dev 
yes "" |  apt-get install python-dev 
apt-get install software-properties-common
yes "" |  add-apt-repository universe
yes "" |  apt-get update
yes "" |  apt-get install libjpeg-dev zlib1g-dev swig 

yes "" |  apt install virtualenv 

echo "30% Proccessed"
yes "" |  apt-get install libjpeg-dev zlib1g-dev swig
yes "" |  apt-get install mongodb
yes "" |  apt-get install postgresql libpq-dev
yes "" |  apt-get install virtualbox
yes "" |  apt-get install tcpdump apparmor-utils
echo "50% Proccessed"
 groupadd pcap
 usermod -a -G pcap cuckoo
 chgrp pcap /usr/sbin/tcpdump
 setcap cap_net_raw,cap_net_admin=eip /usr/sbin/tcpdump
getcap /usr/sbin/tcpdump
 aa-disable /usr/sbin/tcpdump
echo "70% Proccessed"
yes "" |  apt-get install git
git clone https://github.com/volatilityfoundation/volatility.git 
cd volatility 
 python setup.py build
 python setup.py install
 pip2 install yara-python ujson
 usermod -a -G vboxusers cuckoo
virtualenv --python=python2.7 venv
 virtualenv venv
. venv/bin/activate
 pip2 install -U pip setuptools
#install vmcloak
git clone git://github.com/jbremer/vmcloak
cd vmcloak
 python setup.py develop
#install other tools

 pip2 install -U cuckoo
 pip3 install psycopg2
echo "90% Proccessed"
 pip2 download cuckoo
 pip2 install openpyxl
 pip2 install ujson
 pip2 install pycrypto
 pip2 install distorm3==3.4.4
 pip2 install pytz
 pip2 install *.tar.gz
yes "" |  apt install yara

 wget http://sourceforge.net/projects/ssdeep/files/ssdeep-2.13/ssdeep-2.13.tar.gz/download -O ssdeep-2.13.tar.gz
 tar -zxf ssdeep-2.13.tar.gz
cd ssdeep-2.13
./configure
make
 make install
ssdeep -V
 pip2 install pydeep
wget https://cuckoo.sh/win7ultimate.iso
 mkdir /mnt/win7
 chown cuckoo:cuckoo /mnt/win7
 mount -o ro,loop win7ultimate.iso /mnt/win7
yes "" |  apt-get -y install build-essential libssl-dev libffi-dev python-dev genisoimage
yes "" |  apt-get -y install zlib1g-dev libjpeg-dev



vmcloak-vboxnet0
vmcloak init --verbose --win7x64 win7x64base --cpus 2 --ramsize 2048
vmcloak clone win7x64base win7x64cuckoo
vmcloak install win7x64cuckoo adobepdf pillow dotnet flash vcredist vcredist.version=2015u3 wallpaper
vmcloak install win7x64cuckoo ie11
vmcloak snapshot --count 4 win7x64cuckoo 192.168.56.101
vmcloak list vms

vboxmanage modifyvm 192.168.56.1011 --name win7x64
vboxmanage startvm "win7x64"
sleep 30
vboxmanage snapshot "win7x64" take "snapshot1" --pause
vboxmanage controlvm "win7x64" poweroff
vboxmanage snapshot "win7x64" restorecurrent
