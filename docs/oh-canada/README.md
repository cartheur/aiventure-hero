## How to use this ROM

Since you have the memory expansion option and USB Interface it can be done just from BASIC.  Should just be able to make a short program that loops through addresses $2000-$3FFF using a PEEK command to read the byte at the address then print it out which will end up in the terminal window on your computer.  I've done that before then just use the values to re-create the binary image.  Sounds a bit convoluted but isn't too bad.

An even easier method you can do right from the robots keypad if you have the USB connected and the terminal package open.  Type 3 9 and then it will prompt for the first address 2 0 0 0 then it will prompt for the last address 3 F F F

The robot will send the binary image of that area in the common S1/S9 format.  That can be easily converted back to a binary image.