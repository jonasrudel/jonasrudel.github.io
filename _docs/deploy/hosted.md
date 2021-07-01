- TOC
{:toc}

# Hosted mode
{:.no_toc}

Trustm3 containers can also be run natively on your host, using the hosted mode.
This section describes how to run the hosted mode.
These instructions have been tested and work on Debian 10 stable. 

## Requirements
Have a prebuilt container image or build one yourself as described in build ready as described in [Build]({{ "/" | absolute_url }}build/build).

### Required packages
Install all required packages with the following command: 
```
    apt install git build-essential unzip re2c pkg-config check lxcfs \ 
                libprotobuf-c-dev automake libtool libselinux1-dev \
                libcap-dev protobuf-c-compiler libssl-dev udhcpd udhcpd
```
### Protobuf-c-text
To install protobuf-c-text, run the following commands:
```
git clone https://github.com/trustm3/external_protobuf-c-text
cd external_protobuf-c-text/
./autogen.sh
./configure --enable-static=yes
make 
make install
ldconfig
```

## Installation
1. Clone  https://github.com/trustm3/device_fraunhofer_common_cml 
2. Compile and install the neccesary components with 
```
make -f Makefile_lsb 
sudo make -f Makefile_lsb install
```


## Setup
1. Run scd once to initialize /var/lib/cml/tokens 
3. You can either push your own certificate by using cml-control push_ca or copy the ssig_rootca.cert from your build to /var/lib/cml/tokens
4. Run scd again, this time it will start a loop and keep running
5. Run cmld and keep it running
2. Install your guestos as described in [GuestOS configuration]({{ "/" | absolute_url }}operate/guestos_config)
6. You can now use control as described in [Basic Operation]({{ "/" | absolute_url }}operate/control)

