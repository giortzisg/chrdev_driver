# Charecter Device Driver
A device driver for acquiring data from a collection of microcontroller sensors, reading them over a usb protocol and redirecting them to a set of custom /dev devices for access in userspace.
> It must be noted at this point, that access to the usb port was not direct, but rather through TCP protocol by a "new line discipline".Most of this part of the custom made driver code along with data storage in kernel had already been written in the context of a course on Operating Systems. The code which was implemented by the authors stated below consists only of the interaction between the sensor devices and the userspace where the sensor values were saved.


## Important notice concerning Intellectual Property
 For every part of the code, the author and the rightful ownership of the code is stated on top of the file in comments.


## What more does this "lunix" Charecter Device Driver offer
* Ability to discern between different types of data packets based on info (temperature,battery,light)
* Accessing the data from different processes running at the same time
* Being able to assign different read/write/execute rights depending on user/sensor/measurement

## Tested on "Ubuntu 14.04.5 LTS" and qemu 3.0.0

## How to run 
* Make the makefile
* Insert the module (insmod ./lunix.ko)
* Create special files in userspace (./lunix_dev_nodes.sh)
* Attach interface layer (./lunix-attach /dev/ttyS0)
* Check if special files were indeed created (cat /proc/devices) and if sensor system is online (netcat cerberus.cslab.ece.ntua.gr 49152)
* Display the values! (eg: cat /dev/lunix0-temp or other user space program)


### Driver-File Operations
* open() : Assign kernel memory and init values for new sensor-type file
* read() : Use of sleep and semaphores to obtain data and transfer them from kernel to user space  
* release() : Release memory when all files are closed


###### There was no need to implement the "write" file operation, as our device driver operated in a one-way manner, only providing us with readable measurements from the sensors.
###### There was no need to implement "lseek" as data was serial and  data packets indivisible.

#### Summary of the rest Driver Functions
 * Init/Destroy: Mapping/Assigning devices to major/minor numbers when initialising kernel module
 * Update/Refresh: Used in read(). Check if update is needed, use of spinlocks to safely acquire new data. 


# Authors
Giannis Giortzis Software Engineering Student [@ECE NTUA](https://www.ece.ntua.gr/)

Dimitrios Lampros Software Engineering Student [@ECE NTUA](https://www.ece.ntua.gr/)
