# UltiBIOS
This is a BIOS for Raspberry Pi OS Development, using Ultibo as its core.

Beings that it is linked into Ultibo it will be GPL, unfortunately.

# Discription:

This sets up a call system that can be used to do all the basic IO stuff, including USB related I/O on the Raspberry Pi.

For now this is a call to a fixed address that is passed to your kernel in R11.   If I can get the ultibo author to implement a more reasonable SWI handler then it will be changed to a call to SWI #0x01 through SWI 0x0FFF with the parameters in R0 through R7.   For now the the call number is in R8.

# Function List:
Do to the above note, for now replace the SWI #n calls with LDR R8,#n followed by MOV R14,R15 then MOV R15,R11.   Yes that is replacing one instruction with three, though it is the way that Ultibo requires things for now.

The supported functions are to be:
SWI 0x01 : Keyboard.
SWI 0x02 : Mouse.
SWI 0x03 : Block Device.
SWI 0x04 : Sound.
SWI 0x05 : GPIO.
SWI 0x06 : Video.
SWI 0x0F : USB Stuff.
