# Python library for the Pololu Dual G2 High-Power Motor Drivers for Raspberry Pi

Version: 1.0.0<br>
Release Date: 2017-11-16<br>
[![Build Status](https://travis-ci.org/pololu/dual-g2-high-power-motor-driver-rpi.svg?branch=master)](https://travis-ci.org/pololu/dual-g2-high-power-motor-driver-rpi)<br>
[www.pololu.com](https://www.pololu.com/)

## Summary

This library runs on the [Raspberry Pi](https://www.pololu.com/product/2759)
(Model B+ or newer) and provides functions for controlling both channels of the
[Pololu Dual G2 High-Power Motor Drivers for Raspberry Pi](https://www.pololu.com/category/219/pololu-dual-g2-high-power-motor-drivers-for-raspberry-pi).
This library supports both Python 2 and Python 3.

Programs that use this library will need to be run as the root user so they can
access the GPIO pins.

## Getting Started

### Installation

This library depends on [WiringPi](http://wiringpi.com/) and
[WiringPi-Python](https://github.com/WiringPi/WiringPi-Python).
The instructions below explain how to install these prerequisites.

These instructions assume you are using Raspbian, Debian, or some other
distribution that provides the `apt-get` command for managing packages.
If you do not have `apt-get`, you will need to use a different method to install
the required packages.

These instructions also assume you will use Python 2.  If you want to use
Python 3, you will need to:
* replace `python` with `python3` in the names of the `apt-get` packages below
* use the `python3` command instead of `python` for running Python scripts
* use the `pip3` command instead of `pip` to install pip packages

First, to download and install WiringPi-Python, run:

```
sudo apt-get install python-dev python-pip
sudo pip install wiringpi
```

Finally, to download and install the dual_g2_hpmd_rpi library, run:

```
git clone https://github.com/pololu/dual-g2-high-power-motor-driver-rpi
cd dual-g2-high-power-motor-driver-rpi
sudo python setup.py install
```

### Running the example program

This library comes with an example program that drives each motor in both
directions.  To run the example, navigate to the
dual-g2-high-power-motor-driver-rpi directory and run:

```
sudo python example.py
```

## Library reference

This library uses ultrasonic 20&nbsp;kHz PWM to drive the motors.

Motor speeds in this library are represented as numbers between **-480** and
**480** (inclusive).  A speed of 0 corresponds to braking.  Positive speeds
correspond to current flowing from M1A/M2A to M1B/M2B, while negative speeds
correspond to current flowing in the other direction.

The library can be imported into a Python program with the following line:

```
from dual_g2_hpmd_rpi import motors, MAX_SPEED
```

After importing the library, you can use the commands below to enable the motors
and set motor speeds:

* `motors.enable()`: Enable both motor 1 and motor 2.
* `motors.motor1.enable()`: Enable motor 1.
* `motors.motor2.enable()`: Enable motor 2.
* `motors.disable()`: Disable both motor 1 and motor 2.
* `motors.motor1.disable()`: Disable motor 1.
* `motors.motor2.disable()`: Disable motor 2.
* `motors.setSpeeds(m1_speed, m2_speed)`: Set speed and direction for both motor 1 and motor 2.
* `motors.motor1.setSpeed(speed)`: Set speed and direction for motor 1.
* `motors.motor2.setSpeed(speed)`: Set speed and direction for motor 2.

For convenience, a constant called `MAX_SPEED` (which is equal to 480) is
available on all the objects provided by this library.  You can access it
directly by just writing `MAX_SPEED` if you imported it as shown above, or it
can be accessed in the following ways:

* `motors.MAX_SPEED`
* `motors.motor1.MAX_SPEED`
* `motors.motor2.MAX_SPEED`

If you are controlling multiple motor drivers, you might prefer to import the
library using `import dual_g2_hpmd_rpi`, which requires the commands listed
above to be prefixed with `dual_g2_hpmd_rpi.`.

## Version history

* 1.0.0 (2017-11-16): Original release.