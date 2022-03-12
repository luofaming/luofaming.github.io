---
layout: default
---

Install of geant4 and root on ubuntu 20.04.

[back](https://luofaming.github.io/)

参考至北大物院吴鸿毅博士：https://github.com/wuhongyi/BasicConfiguration

使用方法：将以下代码分别保存到脚本文件，根据官网实际情况修改相应的版本号，然后依次以管理员权限执行。

* 脚本1：修改镜像源
```
if [ `whoami` = "root" ];then 
    echo "当前为root用户，能够执行此脚本！" 
else 
    echo "请在ROOT权限下执行此脚本！！！"
    exit 1
fi

VERSION=`lsb_release -r`
echo "$VERSION"
if [ "$VERSION" = "Release:	20.04" ] ; then 
    echo "当前为Ubuntu 20.04"
    ## Ubuntu2004
    echo 'deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse' >> /etc/apt/sources.list
    echo 'deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse' >> /etc/apt/sources.list
else 
    echo "暂时不支持当前版本Ubuntu。"
    exit 1
fi
```

* 脚本2：apt安装依赖
``` bash
if [ `whoami` = "root" ];then 
    echo "当前为root用户，能够执行此脚本！" 
else 
    echo "请在ROOT权限下执行此脚本！！！"
    exit 1
fi

apt-get update
apt --fix-broken install
apt -y autoremove

apt -y install net-tools openssh-server iotop iftop htop rar minicom git shc screen environment-modules apache2
apt -y install emacs gcc gfortran g++ cmake qt5-default qtcreator gnuplot texlive texlive-xetex python3-pip jupyter libminizip1 ipython3 openjdk-8-jdk

#source error
apt -y install kate
apt -y install dpkg-dev binutils libx11-dev libxpm-dev libxft-dev libxext-dev python libssl-dev openssl doxygen doxygen-latex doxygen-gui graphviz

#source error
apt -y install libftgl-dev
apt -y install libpcre3-dev xlibmesa-glu-dev libglew-dev  libmysqlclient-dev libfftw3-dev libcfitsio-dev libgraphviz-dev libavahi-compat-libdnssd-dev libldap2-dev python-dev libxml2-dev libkrb5-dev libgsl-dev mysql-server libmysqlclient-dev libfcgi-bin libfcgi-dev libsqlite3-dev libqt5webkit5-dev libqt5webengine5 qtwebengine5-dev libqt5webenginecore5 libqt5webenginewidgets5 libqt5webengine-data libqt5webchannel5-dev libqt5websockets5-dev libqt5websockets5 libqt5webview5-dev libqt5webview5 davix-dev davix
apt -y install python3-numpy
apt -y install libxerces-c3.2 libxerces-c-dev libxmu-headers libxmu-dev libmotif-dev
apt -y install libreadline-dev libgtk-3-dev libgtk2.0-dev xfonts-75dpi xfonts-100dpi

#source error
apt -y install freeglut3-dev freeglut3
apt -y install  libsdl2-dev libsdl2-image-dev libglm-dev
apt -y install libncurses5 libncurses5-dev libcanberra-gtk-module

#source error
apt -y install ffmpeg libsdl1.2-dev

##DAQ
apt -y install libboost-dev libzmq3-dev
apt -y install libminizip1
apt --fix-broken install

wget http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_amd64.deb
dpkg -i multiarch-support_2.27-3ubuntu1.2_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/libx/libxp/libxp6_1.0.2-1ubuntu1_amd64.deb
dpkg -i libxp6_1.0.2-1ubuntu1_amd64.deb
ln -s /usr/lib/x86_64-linux-gnu/libXp.so.6 /usr/lib/x86_64-linux-gnu/libXp.so

apt --fix-broken install
wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
dpkg -i teamviewer_amd64.deb

VERSION=`lsb_release -r`
echo "$VERSION"
if [ "$VERSION" = "Release:	20.04" ] ; then 
    echo "当前为Ubuntu 20.04"
    ## Ubuntu2004
    pip install metakernel zmq Markdown voila jupyterlab jupyter
    pip install sphinx sphinx-intl sphinx-autobuild recommonmark sphinx_rtd_theme mkdocs
else 
    echo "暂时不支持当前版本Ubuntu。"
    exit 1
fi
```

* 脚本3：pip安装
``` bash
if [ `whoami` = "root" ];then 
    echo "当前为root用户，能够执行此脚本！" 
else 
    echo "请在ROOT权限下执行此脚本！！！"
    exit 1
fi

## ROOT jupyter 依赖版本
VERSION=`lsb_release -r`
echo "$VERSION"
if [ "$VERSION" = "Release:	20.04" ] ; then 
    echo "当前为Ubuntu 20.04"
    ## Ubuntu2004
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com ipykernel==6.4.1
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com ipython==7.27.0
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com jupyter-client==7.0.2
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com jupyter-console==6.4.0
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com jupyter-core==4.7.1
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com notebook==6.4.4
    pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com voila==0.2.13
else 
    echo "暂时不支持当前版本Ubuntu。"
    exit 1
fi
```

* 脚本4：geant4安装
``` bash
pathinstall="/opt/Geant4"
filename="geant4.10.07.p02" ##根据自己实际下载的版本修改

urllink="http://cern.ch/geant4-data/releases/"
urllinkdata="http://cern.ch/geant4-data/datasets/"

if [ `whoami` = "root" ];then 
    echo "当前为root用户，能够执行此脚本！" 
else 
    echo "请在ROOT权限下执行此脚本！！！"
    exit 1
fi

wget ${urllink}${filename}.tar.gz
## 以下版本号均要根据官网实际修改
wget ${urllinkdata}G4NDL.4.6.tar.gz
wget ${urllinkdata}G4EMLOW.7.13.tar.gz
wget ${urllinkdata}G4PhotonEvaporation.5.7.tar.gz
wget ${urllinkdata}G4RadioactiveDecay.5.6.tar.gz
wget ${urllinkdata}G4SAIDDATA.2.0.tar.gz
wget ${urllinkdata}G4PARTICLEXS.3.1.1.tar.gz
wget ${urllinkdata}G4ABLA.3.1.tar.gz
wget ${urllinkdata}G4INCL.1.0.tar.gz
wget ${urllinkdata}G4PII.1.3.tar.gz
wget ${urllinkdata}G4ENSDFSTATE.2.3.tar.gz
wget ${urllinkdata}G4RealSurface.2.2.tar.gz
wget ${urllinkdata}G4TENDL.1.3.2.tar.gz

# wget ftp://gdo-nuclear.ucllnl.org/LEND_GND1.3/LEND_GND1.3_ENDF.BVII.1.tar.gz

if [ ! -f "${filename}.tar.gz" ]; then
    echo "文件 ${filename}.tar.gz 未下载成功"
    exit 1
fi

name=`expr $filename | sed 's/\.//g'` #去除.
buildname="build$name"
datafilename=`expr $filename | sed 's/geant4./Geant4-/g' | sed 's/\.0/./g' | sed 's/p0//g'`
datadir="${pathinstall}/${name}/share/${datafilename}/data"


num=`cat /proc/cpuinfo | grep processor | wc -l`

tar -xvf ${filename}.tar.gz
mkdir $buildname
cd $buildname

# Release/Debug
cmake -DCMAKE_INSTALL_PREFIX=${pathinstall}/$name -DCMAKE_BUILD_TYPE=Release  -DGEANT4_USE_SYSTEM_CLHEP=OFF -DGEANT4_USE_SYSTEM_ZLIB=OFF -DGEANT4_USE_SYSTEM_EXPAT=OFF -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_USE_RAYTRACER_X11=ON -DGEANT4_USE_QT=ON -DGEANT4_BUILD_MULTITHREADED=ON -DGEANT4_USE_GDML=ON  -DGEANT4_USE_XM=ON -DGEANT4_BUILD_TLS_MODEL=global-dynamic -DGEANT4_USE_FREETYPE=ON -DGEANT4_BUILD_PHP_AS_HP=ON -DGEANT4_USE_SMARTSTACK=ON  ../${filename}
# -DGEANT4_USE_PYTHON=ON
make -j$num
make install
cd ../
rm -rf $filename
rm -rf $buildname

mkdir ${datadir}
tar -zxvf G4NDL.4.6.tar.gz  -C ${datadir}
tar -zxvf G4EMLOW.7.13.tar.gz -C  ${datadir}
tar -zxvf G4PhotonEvaporation.5.7.tar.gz -C  ${datadir}
tar -zxvf G4RadioactiveDecay.5.6.tar.gz -C  ${datadir}
tar -zxvf G4SAIDDATA.2.0.tar.gz -C  ${datadir}
tar -zxvf G4PARTICLEXS.3.1.1.tar.gz -C  ${datadir}
tar -zxvf G4ABLA.3.1.tar.gz -C  ${datadir}
tar -zxvf G4INCL.1.0.tar.gz -C  ${datadir}
tar -zxvf G4PII.1.3.tar.gz -C  ${datadir}
tar -zxvf G4ENSDFSTATE.2.3.tar.gz -C  ${datadir}
tar -zxvf G4RealSurface.2.2.tar.gz -C  ${datadir}
tar -zxvf G4TENDL.1.3.2.tar.gz -C  ${datadir}

# tar -zxvf LEND_GND1.3_ENDF.BVII.1.tar.gz -C  ${datadir}

echo ""
echo "如欲启用该版本Geant4请将 source ${pathinstall}/$name/bin/geant4.sh  添加进 .bashrc "
```

* 脚本5：安装root
``` bash
filename="root_v6.24.02" #根据实际下载的版本修改
pathinstall="/opt/ROOT"
if [ `whoami` = "root" ];then 
    echo "当前为root用户，能够执行此脚本！" 
else 
    echo "请在ROOT权限下执行此脚本！！！"
    exit 1
fi

name=`expr $filename | sed 's/_v//g' | sed 's/\.//g'` #去除_v .
filename2=`expr $filename | sed 's/_v/-/g'`
buildname="build$name"

rm -f ${filename}.source.tar.gz
wget https://root.cern.ch/download/${filename}.source.tar.gz

if [ ! -f "${filename}.source.tar.gz" ]; then
    echo "文件 ${filename}.source.tar.gz 未下载成功"
    exit 1
fi

num=`cat /proc/cpuinfo | grep processor | wc -l`

tar -zxvf ${filename}.source.tar.gz
mkdir $buildname
cd $buildname

VERSION=`lsb_release -r`
echo "$VERSION"
if [ "$VERSION" = "Release:	20.04" ] ; then 
    echo "当前为Ubuntu 20.04"
    ## Ubuntu2004
    cmake -DCMAKE_INSTALL_PREFIX=${pathinstall}/${name} -Dqt5web=ON -Dwebgui=ON -Droot7=ON -Dfcgi=ON -Dgviz=ON -Dminuit2=ON -Dxrootd=OFF ../$filename2
else 
    echo "暂时不支持当前版本Ubuntu。"
    exit 1
fi
make -j$num
make install
cd ../
rm -rf $buildname
rm -rf $filename2
echo "如欲启用该版本ROOT请将 source ${pathinstall}/$name/bin/thisroot.sh  添加进 .bashrc "
```
