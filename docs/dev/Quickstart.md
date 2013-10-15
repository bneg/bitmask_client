#### Quickstart build of dev environment
**Assumptions:** These instructions were made on a clean Ubuntu 12.04.3 system.  
**Goal:** With minimal effort or reading install the necessary packages to build and develop on bitmask_client  
**Outcome:** At the end of these instructions, you should be able to run the bitmask client GUI in debug mode and connect to a LEAP node (bitmask.net)  

#### Start:

    $ sudo apt-get install openvpn git-core python-dev python-pyside \
    python-setuptools python-virtualenv python-all-dev python-pip \
    python-dev python-openssl git libgnutls-dev python-qt4 g++ libsqlite3-dev \
    pyside-tools  

Clone the repo into your working directory

    $ git clone https://github.com/leapcode/bitmask_client

Create the virtualenv

    $ virtualenv .

Activate the virtualenv

    $ source bin/activate

Symlink to your gloabal PySide install

    $ pkg/postmkvenv.sh

Install python requirements

    $ pip install -r pkg/requirements.pip

Copy necessary files into system

    $ sudo mkdir -p /etc/leap
    $ sudo cp pkg/linux/resolv-update /etc/leap
    $ sudo cp pkg/linux/polkit/net.openvpn.gui.leap.policy /usr/share/polkit-1/actions/

Install the development environment

    $ ./setup.py develop
    
Compile the source

    $ make

Run bitmask_client in debug mode

    $ bin/bitmask --debug  

#### Finish
You should see the bitmask_client window prompting to connect to an existing node or add a new one.  If not, something went wrong, maybe ask on #leap-dev at irc.freenode.net
