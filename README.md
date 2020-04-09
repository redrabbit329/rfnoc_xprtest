https://kb.ettus.com/Software_Development_on_the_E3xx_USRP_-_Building_RFNoC_UHD_/_GNU_Radio_/_gr-ettus_from_Source

https://kb.ettus.com/Getting_Started_with_RFNoC_Development#Verify_Environment




# system update
------------------------------------

sudo dpkg-reconfigure dash
ll /bin/sh

$ sudo apt-get update
$ sudo apt install cmake
$ cmake --version 
  >> cmake version 3.10.2



# install the required dependencies  (getting started with RFNoC -> manually instal application note)
------------------------------------
$ sudo apt-get -y install git swig cmake doxygen build-essential libboost-all-dev libtool libusb-1.0-0 libusb-1.0-0-dev libudev-dev libncurses5-dev libfftw3-bin libfftw3-dev libfftw3-doc libcppunit-1.14-0 libcppunit-dev libcppunit-doc ncurses-bin cpufrequtils python-numpy python-numpy-doc python-numpy-dbg python-scipy python-docutils qt4-bin-dbg qt4-default qt4-doc libqt4-dev libqt4-dev-bin python-qt4 python-qt4-dbg python-qt4-dev python-qt4-doc python-qt4-doc libqwt6abi1 libfftw3-bin libfftw3-dev libfftw3-doc ncurses-bin libncurses5 libncurses5-dev libncurses5-dbg libfontconfig1-dev libxrender-dev libpulse-dev swig g++ automake autoconf libtool python-dev libfftw3-dev libcppunit-dev libboost-all-dev libusb-dev libusb-1.0-0-dev fort77 libsdl1.2-dev python-wxgtk3.0 git libqt4-dev python-numpy ccache python-opengl libgsl-dev python-cheetah python-mako python-lxml doxygen qt4-default qt4-dev-tools libusb-1.0-0-dev libqwtplot3d-qt5-dev pyqt4-dev-tools python-qwt5-qt4 cmake git wget libxi-dev gtk2-engines-pixbuf r-base-dev python-tk liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq3-dev libzmq5 python-requests python-sphinx libcomedi-dev python-zmq libqwt-dev libqwt6abi1 python-six libgps-dev libgps23 gpsd gpsd-clients python-gps python-setuptools

------------------------------------
sudo apt -y install git swig cmake doxygen build-essential libboost-all-dev libtool libusb-1.0-0 libusb-1.0-0-dev libudev-dev libncurses5-dev libfftw3-bin libfftw3-dev libfftw3-doc libcppunit-1.14-0 libcppunit-dev libcppunit-doc ncurses-bin cpufrequtils python-numpy python-numpy-doc python-numpy-dbg python-scipy python-docutils qt4-bin-dbg qt4-default qt4-doc libqt4-dev libqt4-dev-bin python-qt4 python-qt4-dbg python-qt4-dev python-qt4-doc python-qt4-doc libqwt6abi1 libfftw3-bin libfftw3-dev libfftw3-doc ncurses-bin libncurses5 libncurses5-dev libncurses5-dbg libfontconfig1-dev libxrender-dev libpulse-dev swig g++ automake autoconf libtool python-dev libfftw3-dev libcppunit-dev libboost-all-dev libusb-dev libusb-1.0-0-dev fort77 libsdl1.2-dev python-wxgtk3.0 git libqt4-dev python-numpy ccache python-opengl libgsl-dev python-cheetah python-mako python-lxml doxygen qt4-default qt4-dev-tools libusb-1.0-0-dev libqwtplot3d-qt5-dev pyqt4-dev-tools python-qwt5-qt4 cmake git wget libxi-dev gtk2-engines-pixbuf r-base-dev python-tk liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq3-dev libzmq5 python-requests python-sphinx libcomedi-dev python-zmq libqwt-dev libqwt6abi1 python-six libgps-dev libgps23 gpsd gpsd-clients python-gps python-setuptools python3-pyqt5 dnsmasq sshfs

[Result]
Setting up dnsmasq (2.79-1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/dnsmasq.service → /lib/systemd/system/dnsmasq.service.
Job for dnsmasq.service failed because the control process exited with error code.
See "systemctl status dnsmasq.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dnsmasq, action "start" failed.
● dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server
   Loaded: loaded (/lib/systemd/system/dnsmasq.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2020-04-09 17:44:01 KST; 5ms ago
  Process: 18776 ExecStart=/etc/init.d/dnsmasq systemd-exec (code=exited, status=2)
  Process: 18775 ExecStartPre=/usr/sbin/dnsmasq --test (code=exited, status=0/SUCCESS)

 4월 09 17:44:01 rr systemd[1]: Starting dnsmasq - A lightweight DHCP and caching DNS server...
 4월 09 17:44:01 rr dnsmasq[18775]: dnsmasq: syntax check OK.
 4월 09 17:44:01 rr dnsmasq[18776]: dnsmasq: failed to create listening socket for port 53: Address already in use
 4월 09 17:44:01 rr dnsmasq[18776]: failed to create listening socket for port 53: Address already in use
 4월 09 17:44:01 rr systemd[1]: dnsmasq.service: Control process exited, code=exited status=2
 4월 09 17:44:01 rr dnsmasq[18776]: FAILED to start up
 4월 09 17:44:01 rr systemd[1]: dnsmasq.service: Failed with result 'exit-code'.
 4월 09 17:44:01 rr systemd[1]: Failed to start dnsmasq - A lightweight DHCP and caching DNS server.
------------------------------------





$ sudo apt update
$ sudo apt upgrade

reboot

## Create Working Directory

   $ mkdir -p ~/rfnoc
   $ mkdir -p ~/rfnoc/src
   $ mkdir -p ~/rfnoc/oe
   $ mkdir -p ~/rfnoc/e300


## Building UHD

   $ cd ~/rfnoc/src    
   $ git clone --recursive https://github.com/EttusResearch/uhd
   $ cd uhd
   $ git checkout v3.14.1.1
   $ git submodule update --init --recursive
   $ cd host
   $ mkdir build-host
   $ cd build-host
   $ cmake -DENABLE_E300=ON -DENABLE_GPSD=ON -DENABLE_RFNOC=ON ..
   $ make -j4
   $ sudo make install
   $ sudo ldconfig


## Download UHD FPGA Images

   $ sudo uhd_images_downloader


## Building GNU Radio

   $ cd ~/rfnoc/src 
   $ git clone --recursive https://github.com/gnuradio/gnuradio
   $ cd gnuradio/
   $ git checkout maint-3.7
   $ git submodule update --init --recursive
   $ mkdir build-host
   $ cd build-host
   $ cmake ..
   $ make -j4
   $ sudo make install
   $ sudo ldconfig


## Building gr-ettus

   $ cd ~/rfnoc/src 
   $ git clone https://github.com/EttusResearch/gr-ettus.git
   $ cd gr-ettus
   $ mkdir build-host
   $ cd build-host
   $ cmake ..
   $ make -j4
   $ sudo make install
   $ sudo ldconfig
   
  
Verify Installation

Run the following command to verify UHD was installed properly.

   $ uhd_usrp_probe --version
  
  Expected Output:

   3.14.1.HEAD-0-g0347a6d8
   
   
Run the following command to verify GNU Radio was installed properly.

   $ gnuradio-config-info --version

Expected Output:

   3.7.13.5



# Cross-Compiling UHD / GNU Radio / gr-ettus for the E3xx USRP 

## SDK Setup

Download the OE SDK for the E31x release into the ~/rfnoc/src/ directory:

   $ cd ~/rfnoc/src
   $ wget http://files.ettus.com/e3xx_images/e3xx-release-4/oecore-x86_64-armv7ahf-vfp-neon-toolchain-nodistro.0.sh



  
   $ bash oecore-x86_64-armv7ahf-vfp-neon-toolchain-nodistro.0.sh 
   


# rfnocmodtool installation
------------------------------------
$ rfnocmodtool newmod xprtest
$ cd rfnoc-xprtest
$ rfnocmodtool add gain
Enter all argument setting "No = N" except of Device ID (1111222233334444).
Default Skeletone code is generated. Refer to follow tree structure.
There is no *.xpr and vivado related files.


rr@rr:~/rfnoc/src/rfnoc-xprtest$ tree -L 4
.
├── apps
│   └── CMakeLists.txt
├── cmake
│   ├── cmake_uninstall.cmake.in
│   └── Modules
│       ├── CMakeParseArgumentsCopy.cmake
│       ├── ettusConfig.cmake
│       ├── FindCppUnit.cmake
│       ├── Findfpga.cmake
│       ├── FindGnuradioRuntime.cmake
│       ├── GrMiscUtils.cmake
│       ├── GrPlatform.cmake
│       ├── GrPython.cmake
│       ├── GrSwig.cmake
│       ├── GrTest.cmake
│       ├── UseSWIG.cmake
│       └── xprtestConfig.cmake
├── CMakeLists.txt
├── docs
│   ├── CMakeLists.txt
│   ├── doxygen
│   │   ├── CMakeLists.txt
│   │   ├── Doxyfile.in
│   │   ├── Doxyfile.swig_doc.in
│   │   ├── doxyxml
│   │   │   ├── base.py
│   │   │   ├── doxyindex.py
│   │   │   ├── generated
│   │   │   ├── __init__.py
│   │   │   └── text.py
│   │   ├── other
│   │   │   ├── group_defs.dox
│   │   │   └── main_page.dox
│   │   └── swig_doc.py
│   └── README.xprtest
├── examples
│   └── README
├── grc
│   ├── CMakeLists.txt
│   └── xprtest_gain.xml
├── include
│   └── xprtest
│       ├── api.h
│       ├── CMakeLists.txt
│       ├── gain_block_ctrl.hpp
│       └── gain.h
├── lib
│   ├── CMakeLists.txt
│   ├── gain_block_ctrl_impl.cpp
│   ├── gain_impl.cc
│   ├── gain_impl.h
│   ├── qa_xprtest.cc
│   ├── qa_xprtest.h
│   └── test_xprtest.cc
├── MANIFEST.md
├── python
│   ├── build_utils_codes.py
│   ├── build_utils.py
│   ├── CMakeLists.txt
│   └── __init__.py
├── README.md
├── rfnoc
│   ├── blocks
│   │   ├── CMakeLists.txt
│   │   └── gain.xml
│   ├── fpga-src
│   │   ├── Makefile.srcs
│   │   └── noc_block_gain.v
│   └── testbenches
│       ├── CMakeLists.txt
│       └── noc_block_gain_tb
│           ├── CMakeLists.txt
│           ├── Makefile
│           └── noc_block_gain_tb.sv
└── swig
    ├── CMakeLists.txt
    └── xprtest_swig.i

20 directories, 57 files
# rfnoc_xprtest
vivado project source tree check
