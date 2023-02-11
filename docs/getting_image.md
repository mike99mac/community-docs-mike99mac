# Welcome To OpenVoice OS Getting Started User Guide
This section assumes you want to install the Open Voice Operating System.  If you just want to install "OVOS core" on to an existing Linux OS, go [here](https://openvoiceos.github.io/community-docs/core/).

You can find a PDF of a "Getting Started Guide" [here](https://github.com/OpenVoiceOS/ovos_assets/raw/master/printables/device-getting-started-guide.pdf).

### Where to get OVOS?

OVOS is in early stages, we publish our Raspberry Pi images for download but expect new bugs and new fixes on every release, we are not yet stable!

These images are development images in alpha stage, bugs and incomplete features are guaranteed.

There are two images to choose from: *buildroot* aims to be a consumer ready firmware based OS where *Manjaro* is the Manjaro Linux OS with an entire software stack including the OVOS core. There is a comparison [here](https://openvoiceos.github.io/community-docs/comparison/).

Download Images:

- [buildroot](https://drive.google.com/drive/folders/113-zmx6ncoeLNsayseNxoaTlaAk1AfU2)
  - SSH Details: Username: mycroft | password: mycroft
- [manjaro](http://downloads.openvoiceos.com/images/)
  - SSH Details for Respeaker Image: Username: mycroft | password: 12345
  - SSH Details for Mark-2/DevKit Image: Username: ovos | password: ovos

Build images from scratch:

- [buildroot](https://openvoiceos.github.io/community-docs/buildroot/)
- [manjaro](https://openvoiceos.github.io/community-docs/manjaro/)

### Flashing your image

Flashing your image to your SD card or USB drive is not different than flashing any other image. For the non-technical users we advise to use the flashing utility from the Raspberry Pi Foundation which you can find [here](https://www.raspberrypi.com/software/). Here is a high-level description of the process:

 - Insert a micro SD card into a card reader. 32 GB or larger is recommended. 
 - Install Raspberry Pi Imager - from a command line, enter ``sudo apt-get install rpi-imager``.
 - Under "CHOOSE OS" select custom at the very bottom of the list and browse to the downloaded image file. It is not required to unzip / unpack the image as the Raspberry Pi imager software can do that for you on the fly.
 - Under "CHOOSE STORAGE" select your SD card or USB device.
 - Click "WRITE"
 - You will be asked "Are you sure?" and may be prompted for a password.

If you have a Raspberri Pi 4 we recommend to use a good USB 3.1 device. If you have a Raspberry Pi 3, use a proper SD card. (From fast to slow: USB 3.1 - SD dcard - USB2)
