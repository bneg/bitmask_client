#### Quickstart build of dev environment
Assumptions: These instructions were made on a clean Ubuntu 12.04.3 system.
Goal: With minimal effort or reading install the necessary packages to build and develop on bitmask_client
Outcome: At the end of these instructions, you should be able to run the bitmask client GUI in debug mode and connect to a LEAP node (bitmask.net)  

#### Start::  
    $ sudo apt-get install openvpn git-core python-dev python-pyside \
python-setuptools python-virtualenv python-all-dev python-pip \
python-dev python-openssl git libgnutls-dev python-qt4 g++ libsqlite3-dev pyside-tools  

    $ git clone https://github.com/leapcode/bitmask_client
    $ virtualenv .
    $ source bin/activate
    $ pkg/postmkvenv.sh
    $ pip install -r pkg/requirements.pip
    $ sudo mkdir -p /etc/leap
    $ sudo cp pkg/linux/resolv-update /etc/leap
    $ ./setup.py develop
    $ make
    $ bin/bitmask --debug
