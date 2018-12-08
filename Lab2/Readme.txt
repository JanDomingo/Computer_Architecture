Group members: Jan Domingo and Blaine Renner

Contributions of Jan Domingo: ECC Generator, 13 bit Data Transmission Part, Main Memory (4 to 12 line decoder)
Contributions of Blaine Renner: Main Memory (ECC Corrector, Hex Display Output)
Contributions shared: Main Memory (5 Parity Bit Detector), Documentation, Testing

Files:

ECCGenerator.cct: The circuit file for the ECC generator. 
Description of this part's function and usage: 
The ECC generator accepts two 4 bit inputs resulting in an 8 bit input.  Using odd bit parity we create an extra four parity bits based off the 8 data inputs.  After this, we create a 5th parity bit to measure the overall odd parity.  We insert the parity bits into the corresponding slots amidst the data bits in the structure of Hamming Code.

DataTransmissions.cct: The circuit file for our Data Transmission.
Description of this part's function and usage:
The 13 bit Data Transmission accepts the original 8 data bits and 5 parity bits and offers us the chance to modify those individual errors to simulate real world error occurences.  The data transmission will replace the old values at those bits with the new, toggled error bit(s) and then port out the 13 bits to be taken by Main Memory.

MainMemory.cct: the part file for our Main Memory.
Description of this part's function and usage:
The main memory accepts a 13 bit input from the data transmission.  It creates a second, fifth parity bit with the possibly altered input received from data transmission and compares this new, last parity bit with the old last parity bit to see if there's a change.  It also calculates four values: C8,C4,C2,C1 which show if the parity of any section has changed.  If it has, then C is not 0.  If C is not 0 and the last parity bits are different, then there is a single error which is corrected by our ECC corrector and the hex display outputs "C".  If c is not 0 and the last parity bits are the same, then there is a double error that cannot be corrected and "E" is displayed.  If C is 0 and the last parity bit is also the same, then there is no error and "0" is displayed.  If C is 0 and the last parity bit is different, then there is an error in the last parity bit and "E" is displayed.  This part also outputs the 8 bit data after it is modified, if needed, via two hex displays.  We use a 4 to 12 line decoder to detect which bit needs to be changed.

Lab#2.cct: our circuit schematic for the lab, containing our individual parts
Description of this file's function and usage:
Shows our parts connected together and allows for the toggling of bits in the data transmission part.  Also connects the ported out values of our Main Memory to the corresponding hex displays.







