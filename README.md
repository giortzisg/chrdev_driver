# Charecter Device Driver
A device driver for acquiring data from a collection of microcontroller sensors, reading them over a usb protocol and redirecting them to a set of custom /dev devices for access in userspace. The driver code was given as part of a course on Operating Systems. The code which was implemented by the authors stated below consists only of the interaction between the sensor devices and the userspace where the sensor values were saved.


## Important Notice concerning Intellectual Property
 For every part of the code, the author and the rightful ownership of the code is stated on top of the file in comments.


## What more does this "lunix" Charecter Device Driver offer
* Ability to discern between different types of data packets based on info (temperature,battery,light)
* Accessing the data from different procedures running at the same time
* Being able to assign different read/write/execute rights depending on user/sensor/measurement











# Authors
Giannis Giortzis Software Engineering Student [@ECE NTUA](https://www.ece.ntua.gr/)

Dimitrios Lampros Software Engineering Student [@ECE NTUA](https://www.ece.ntua.gr/)
