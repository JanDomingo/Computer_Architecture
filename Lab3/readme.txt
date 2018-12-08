Group members: Jan Domingo and Blaine Renner

Contributions of Jan Domingo: Documentation, Part 2: 8 bit Sequencer, Programmable User Code
Contributions of Blaine Renner: Lock Part 1: Sequence Recognizer, Gotcha Anti-Theft
Contributions shared: State diagram, state table, readme

Files:

8 bit sequencer.cct: The 8 bit sequencer uses a shift register to allow the user to input binary values. The shift register uses 1 D Latch and 7 Flip Flops. For each input, the bit is pushed down until the desired code is achieved. It is connected to the lock which to limit the user input up to 16 bits until it needs to be reseted. In this program the user should enter the right 4 bits that is displayed in the hex keyboard first and then enter the left 4 bits.

lock.cct: A counter that counts up to 16 and "locks" when that number is reached, preventing it from counting higher.  This is used in part 1 and part 2 to prevent the user from unlocking the device.  The clock pulse for this counter is the triggering of either button 0 or 1.

lab3 seq.cct: The sequence recognizer takes our pre-determined code (00100110) and checks to see if the sequence has been recognized, while the Lock is not preventing us from continuing.  It uses three D flip flops to remember the previous state and keep track of the entered values.

Lab3.cct: Contains our solutions to Part 1 and Part 2.  Part 1 has an anti theft gotcha machine with a built in factory lock code, ours beiing 00100110.  It unlocks if, given 16 tries, the correct sequence is entered.  The second Part allows a user to enter a custom code and save it.  Given 16 tries if this code is entered then the device unlocks.

Lab3Pt1.cct: The gotcha anti-theft machine with a predefined factory lock code, in this case 00100110.  Instructions to use are as follows: 
Step 1: Push button 0 or 1 to enter the code (00100110)
Step 2: If unsuccessful after 16 tries, the device will not accept anymore inputs.
             Flip the RESET from 1 to 0 then back to 1
Step 3: If code entered correctly, STATUS will display a 1*

Program3_Library.clf: The library file containing all of the parts we created for this lab assignment.  

Programmable User Code.cct: The programmable user code contains 8 D flip flops which contains the input from the hex keyboard. The output is then compared using OR gates to the user input from the 8 bit sequencer to determine if they match. These values then go into an 8 input XOR gate to determine if all the values match. If it matches, it will output a 1.