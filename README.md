##About
[FreeRTOS](http://www.freertos.org/) ported to [ARM Versatile Platform Baseboard](http://infocenter.arm.com/help/topic/com.arm.doc.dui0225d/DUI0225D_versatile_application_baseboard_arm926ej_s_ug.pdf), 
based on the ARM926EJ-S CPU.

The current version is based on FreeRTOS 7.5.2. The port will be regularly 
updated with newer versions of FreeRTOS when they are released. 

The port is still at an early development stage and includes only very basic 
demo tasks. More complex tasks will be included in the future.


##Prerequisites
* _Sourcery CodeBench Lite Edition for ARM EABI_ toolchain (now owned by Mentor Graphics), 
based on GCC. See comments in _setenv.sh_ for more details about download and installation.
* _GNU Make_
* _Qemu_ (version 1.3 or newer, older versions do not emulate the interrupt controller properly!)

##Build
A convenience Bash script _setenv.sh_ is provided to set paths to toolchain's commands 
and libraries. You may edit it and adjust the paths according to your setup. To set up 
the necessary paths, simply type:

`. ./setenv.sh`

If you wish to run the image anywhere else except in Qemu, you will probably have to 
edit the linker script _qemu.ld_ and adjust the startup address properly.

To build the image with the test application, just run _make_ or _make rebuild_. 
If the build process is successful, the image file _image.bin_ will be ready to boot.

#Run
To run the target image in Qemu, enter the following command:

`qemu-system-arm -M versatilepb -nographic -m 128 -kernel image.bin`

A convenience Bash script _start\_qemu.sh_ is provided. If necessary, you may 
edit it and adjust paths to Qemu and/or target image.

When the test application completes, it ends running in an infinite loop. 
The instance of Qemu must be "killed" manually. A convenience Bash script 
_stop\_qemu.sh_ (it must be run in another shell) is provided to automate 
the process. Note that it may not work properly if several instances of 
_qemu-system-arm_ are running.

For more details, see extensive comments in both scripts.

##License
All files from the FreeRTOS source distribution, including derived files (with a 
few exceptions, this includes all files in FreeRTOS/ and its subdirectories), are 
licensed under the [modified GPL license](http://www.freertos.org/license.txt).
All other files are licenced under the
[Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0).

For more details see each file's heading as all GPL licenced files 
are clearly marked.