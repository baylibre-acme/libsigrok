# libsigrok with IIO

## Summary

IIO is a generic transport protocol, tools and libraries used to transport
Industrial Input/Output measurements.

In order to use the Sigrok facility to record and visualize IIO devices data,
a Generic IIO driver was added to the libsigrok source code.

This git repository is a fork of the official sigrok source code with the following goals :
 * Add Generic IIO support to actual distributed version for libsigrok, 0.3.0
 * Upstream a clean IIO support the the future libsigrok releases

## How to use

To specify your IIO device, you may either :
- only specify the generic-iio driver if the IIO devices are on the local machine
- specify the the IP or Hostname after the generic-iio as :
```
sigrok-cli -d generic-iio:conn=baylibre-acme.local
```
- specify an XML file as :
```
sigrok-cli -d generic-iio:conn=my-context-file.xml
```

For PulseView, you cannot specify a conn variable, so you can use some Environement variables as :
```
IIOD_REMOTE=baylibre-acme.local pulseview
```

### Ubuntu

#### Ubuntu Xenial 16.04

Replace the distribution libsigrok by adding the following PPA :
```
sudo add-apt-repository ppa:sigrok-iio/ppa
```

Then update and install the new libsigrok package :
```
sudo apt update
sudo apt install sigrok-cli
```
This should trigger installation of a libsigrok-iio package.

Running sigrok-cli should show the generic-iio package :
```
sigrok-cli -V
...
Supported hardware drivers:
...
  generic-iio          Generic IIO wrapper
...
```

#### Ubuntu Trusty 14.04

The installation depends on the official sigrok PPA archive, then the sigrok-iio PPA :
```
sudo add-apt-repository ppa:daniel-elstner/sigrok
sudo add-apt-repository ppa:sigrok-iio/ppa
```

Then update and install the new libsigrok package :
```
sudo apt update
sudo apt install sigrok-cli
```

Running sigrok-cli should show the generic-iio package :
```
sigrok-cli -V
...
Supported hardware drivers:
...
  generic-iio          Generic IIO wrapper
...
```

#### Local build and install

This method depends on the following libraries you should compile and install before :
- libiio version 0.6.0 : https://github.com/analogdevicesinc/libiio/archive/v0.6.tar.gz
- libserialport version 0.1.0 : http://sigrok.org/download/source/libserialport/libserialport-0.1.1.tar.gz

And system provided libraries : pkg-config libglib2.0-dev libusb-1.0-0-dev libzip-dev

And optionally : libftdi-dev

Download and extract the release tarball, then :
```
$ ./configure
$ make
$ sudo make install
```

Make sure the configure script shows :
```
  - generic-iio..................... yes
```
You may miss the libiio library, install the following package :
 * libiio-dev

In order to use the distribution's sigrok-cli or pulseview, you may use LD_LIBRARY_PATH to use the previously built shared library, like :
```
$ LD_LIBRARY_PATH=/usr/local/bin sigrok-cli -V
```
or 
```
$ LD_LIBRARY_PATH=/usr/local/bin pulseview
```

### By building a full sigrok install

Please look at the http://www.sigrok.org/wiki/Building and replace the tarballs
or git checkout by the one provided here.

See :
 * https://github.com/baylibre-acme/libsigrok/branches
 * https://github.com/baylibre-acme/libsigrok/releases

## Support status

### 0.3.0
 * Almost supported, each device exported as channel group
 * Need testing over more IIO devices

Releases :
 * [libsigrok-0.3.0-iio0](https://github.com/baylibre-acme/libsigrok/releases/tag/libsigrok-0.3.0-iio0)

### 0.4.0
 * Bad state, should be cleaned up and aligned on the 0.3.3 version
 * Do not use these early development version

### Master
 * Discution were started on the early 0.4.0 version, must be rebased on the 0.3.0 architecture and integrated in the official libsigrok source repository

## Contact & Help

Feel free to report Issues and submit Pull Requests.

