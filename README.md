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

### By replacing your already installed libsigrok

#### Local build and install

`TODO`

#### Debian and derived pre-built package

`TODO`

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

### 0.4.0
 * Bad state, should be cleaned up and aligned on the 0.3.3 version
 * Do not use these early development version

### Master
 * Discution were started on the early 0.4.0 version, must be rebased on the 0.3.0 architecture and integrated in the official libsigrok source repository

## Contact & Help

Feel free to report Issues and submit Pull Requests.

