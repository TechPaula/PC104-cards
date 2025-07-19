# PC104 Transputer card

This is a PC104plus board that provides a connection to an INMOS C011 and on to a transputer.
This is going to form the basis of a PC104 stack of transputers.

The PCI connector is not connected and is not needed, it is there so that should I get any PCI cards in the future I can use them on my system

![Alt text](Images/TransputerISALinkCard.jpg?raw=true "Interface and single TRAM PCB, TopSide of PCB")
![Alt text](Images/DualTRAM.png?raw=true "Dual TRAM PCB, TopSide of PCB")

## Updates
2025-07-19 - OMG, so much work... CPLD files updated and fixed a couple of errors. I can now write and read from 0x150 to 0x153 as expected. I can now also write to 0x160 & 0x161 as expected and get the behaviours expected. But when you read from 0x160 you got the wrong value and from then on when you read from 0x153 (output status) returns 0, so the output has not been sent/acknowledged by the TRAM.

### Some useful things I've discovered along the way;
* write a 1 to 0x160 Asserts reset, writing a 0 deasserts it.
* Write a 1 to 0x161 to asset Analyse, writing a - deasserts it
* Write a 0 to 0x152 to clear INPUT interrupt enable (unless you plan to use interrupts)
* Write a 0 to 0x152 to clear OUTPUT interrupt enable (unless you plan to use interrupts)
* READ from 0x152 to get the input status (if bit0 is 0 then there is no Data waiting)
* READ from 0x160 to get the error stats (if bit 0 is 0 then there is no error)
* Write to 0x151 to send data into the C011/TRAM.
* READ from 0x150 to receive data from the C011/TRAM


2025-07-11 - Spotted another mistake, I had the Databus reversed. I also added the CPLD files I've programmed and tested.

2025-07-09 - Spotted a major mistake with the CPLD, the board needs a redesign as it has the wrong pin out!

2025-07-06 - Fixed a few minor issues with both boards & added image of Dual TRAM board

2025-07-06 - Added TRAM model

2025-07-05 - Board routed but NOT yet built/tested, the code for the CPLD is not not written.


## License
There isn't one, if you want to build it or adapt it, go for it.
I offer no warranty, nor will I accept any responsiblity for damage to you or your equipment
