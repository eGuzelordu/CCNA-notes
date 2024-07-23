# CCNA Part 4

## Intro to CLI

### Introduction to the Cisco IOS CLI

* Connecting via the consol port(this is needed when first configuring a device).

* this can either be done by using the mini usb or a RJ45

#### Serial Config for Putty

|Name|Value|
|---|---|
|Speed(baud)|9600|
|Data bits|8|
|Stop bits|1|
|Parity|none|
|Flow Control|none|

* Data bits is how many bits are sent before the stop bits are sent.

* Stop bits are the bits sent after the data bits have been sent.

* Parity is a way to correct or detect errors.

* Flow control controls the flow.

* When first gotten into the CLI it will autamatically be in user EXEC mode.

* User EXEC mode is very limited mostly for looking at things rather than changing things.

* There are two separate config files kept on the device at once.

* Running-config = the current activeconfig file on the device. As you enter commands in the CLI, you edit the active config.

* Startup-config = the config file that will be loaded upon restart of the device.

|Command|Purpose|
|---|---|
|`hostname`|- Changes the name of the device|
|`enable`|- Puts user in privilaged EXEC mode</p>- A # will appear after the device name </p>- Provides complete access to view the divices config, restart the device, etc.</p>- Cannot change the config, but can change the time in the device, save the config file, etc.|
|`?`|- View all the command that the user can use</p> can be used like a * from linus CLI as well.|
|`configure terminal`|- Puts User in Golobal Config Mode</p>- Makes it so that you can configure the router|
|`enable password *`|- Enables password when password is written after the command</p>- Passwords are case sensetive.|
|`exit`|- Takes you back to User EXEC Mode.|
|`show running-config`|- Shows the buld cofig.|
|`show startup-config`|- Shows the startup config.|
|`write` or `write memory`|- Saves the build config.|
|`copy running-config startup-config`|- Saves the running config into the startup config.|
|`service password-encryption`|- encrypts the password so when executed `show *-config` the password will be in type 7 encrytion.|
|`enable secret *`|- Gives better more secure encrytion when setting up password.(MD5 encryption)</p>- If both `enable secret *` and `enable password *` are used the CLI will only ask for the password it got from the `enable secret *` command.</p>- should be used instead of `enable password *` due to it being more secure to begin with.|
|`no *`|- Changes the config, in the future the command will not abide by that command disabled|



#### Directory:

* CLI = command-line interface
* GUI = Graphicak User Interface.
* Rollover Cable: it is like a cross-over cable 

