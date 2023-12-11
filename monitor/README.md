## Sources for the monitor program

Files that are located in this directory contain the source code for the Hero-1 robot. I have found them scattered across the Internet, circa 2001 and before.

### What is here

* Hero-1 Memory Dump
    This program creates a formatted memory dump of the specified range of HERO-1 memory addresses on a terminal connected to the robot's serial port. It requires that the robot have HERO-1 BASIC, memory expansion with at least 8K ram, and the serial port.
* Symbolic Macro Assembler
    SMAL Hero is a symbolic macro assembly language for the Heathkit Hero-1 robot. The assembler accepts the standard mnemonics for the Motorola 6800 instruction set, as well as a set of special extended mnemonics for the Hero-1 Robot Control Language interpreter. In addition to providing the basic assembly functions the SMAL Hero assembler provides a powerful macro facility and a linkage editor facility supporting separate assembly, subprogram libraries, and shared common blocks. Assembler and linker output may be either absolute or relocatable, and the object language is encoded in an easily interpreted textual form.
* Hero-1 C Compiler
    A C cross compiler for the Hero-1 with source.

### How to use the upgrades

For a replacemenet ROM version that is provided, use a 68764 (8K Eprom in 24 pin package). As an alternative, one can implement a conversion to allow the use of a 2764 (8K Eprom in 28 pin package).

1 tie high (+5) 2 tie to socket #21 28 tie to socket #24 27 tie high (+5) 24 Pin 28 Pin Notes -------------------------- Vcc 24 26 N/C OK to pass through A8 23 25 A8 OK to pass through A9 22 24 A9 OK to pass through A12 21 23 A11 Socket to prom#2, pin to socket #18 E 20 22 OE OK to pass through A10 19 21 A10 OK to pass through A11 18 20 CE Socket to prom#23, pin to ground
![Table](/monitor/table.png)

![RomUpgrade](/monitor/RomUpgrage.png)

#### For reference

This [site](https://hero.dsavage.net/robots/Hero1/index.html) has some details but the site is extremely old. Precambrian Internet era.