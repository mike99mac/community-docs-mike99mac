# OVOS-core

[OpenVoiceOS](https://openvoiceos.com/) is an open source platform for smart speakers and other voice-centric devices.

OVOS-core is a backwards-compatible descendant of [Mycroft-core](https://github.com/MycroftAI/mycroft-core), the central component of Mycroft. It contains extensions and features not present upstream. 

All Mycroft Skills and Plugins should work normally with OVOS-core. 

OVOS-core is fully modular. Furthermore, common components have been repackaged as plugins. That means it isn't just a great assistant on its own, but also a pretty small library!

## Get the code
Start by cloning the OVOS-core code in your home directory.
```
$ cd
$ git clone https://github.com/OpenVoiceOS/ovos-core
...
```
## Create a virtual environment
It is recommended that you install OVOS-core in a Python virtual environment. To do so, perform the following steps.
- Create a virtual environment named venv and symlink .venv to it.
```
$ python3 -m venv ~/ovos-core/venv
...
$ ln -s venv .venv

```
- Activate the virtual environment.
```
$ source ~/ovos-core/venv/bin/activate
```
## Install co-requisite software
- Install packages with ``apt-get``. This steps can take a few minutes.
```
(venv) $ sudo apt-get install -y build-essential python3-dev swig libssl-dev libfann-dev libpulse-dev libasound2-dev mpg123 portaudio19-dev python3-pyaudio liblapack-dev libopenblas-dev
```
- Download the source code of SuiteSparse, untar it, and export the environment variable ``CVXOPT_SUITESPARSE_SRC_DIR``. It will be needed to install adapt.
```
(venv) $ wget https://people.engr.tamu.edu/davis/SuiteSparse/SuiteSparse-5.4.0.tar.gz
(venv) $ tar xvf SuiteSparse-5.4.0.tar.gz
(venv) $ export CVXOPT_SUITESPARSE_SRC_DIR=~/ovos-core/SuiteSparse
```
- Install the following packages with pip. This can take up to ten minutes.
```
(venv) $ pip install silero adapt wheel tornado
...
```
## Install OVOS core
OVOS-core is very modular, depending on where you are running OVOS-core you may want to run only a subset of the services.

By default OVOS-core only installs the minimum components common to all services, for the purposes of this document we will assume you want a full install.

if you want to fine-tune the components please replace `[all]` in commands below with the subset of desired extras, eg `[skills,bus]`

OVOS-core can be installed from pypi or from source.
### Install from pypi
You can install either beta or stable code.  Choose one.
- To install beta code, run the following command. 
```
(venv) $ pip install --pre ovos-core[all]
...
```
- To install stable code, run the following command.
```
(venv) $ pip install ovos-core[bus,skills,audio,skills-essential]
...
```
If the install fails you may need to install some system dependencies, how to do this will depend on your distro.

### Install from source
```
(venv) $ pip install git+https://github.com/OpenVoiceOS/ovos-core
```
## Running ovos-core
**Note**: MycroftAI's `dev_setup.sh` does not exist in OVOS-core.
### Developer launcher script

`start-mycroft.sh` is available to perform common tasks.

Assuming you installed ovos-core in your home directory, run:
```
(venv) $ cd ~/ovos-core
(venv) $ ./start-mycroft.sh debug
```

The "debug" argument will start the background services (microphone listener, skill, messagebus, and audio subsystems) as
well as bringing up a text-based Command Line Interface (CLI) you can use to interact with Mycroft and see the contents
of the various logs. Alternatively you can run `./start-mycroft.sh all` to begin the services without the command line
interface. Later you can bring up the CLI using `./start-mycroft.sh cli`.

The background services can be stopped as a group with:

- `./stop-mycroft.sh`

### Automatically on boot

We recommend you create system services to manage ovos instead of depending on the launcher script above

A good explanation can be found here https://github.com/j1nx/mycroft-systemd

A reference implementation can be found in [ovos-buildroot](https://github.com/OpenVoiceOS/ovos-buildroot/tree/develop/buildroot-external/rootfs-overlay/usr/lib/systemd/user)
