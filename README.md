# IC Tester

Small update: 
1) replace "pulling outputs to ground" to avoid possible overloading the output pin of DUT replaced by pull down resistors
2) Update schematic and code for arduino nano, and including pull down resisters via D12
3) Ínclude option to test high Z
4) corrected 4503 test and include Disable (High Z function) , included 7406 open collector test.
5) rewired to "easy connection to solder board"

// DuT pin:                   1  2  3  4  5  6  7  8   9  10  11  12  13  14  15  16
//                           -------------------------------------------------------
const int chipPins16 [16] = { 9, 8, 7, 6, 5, 4, 3, 2, 10, 11, A5, A4, A3, A2, A1, A0};
additional D12 connected via sixteen 230kohm resistors to each ZIF pin
ZIF pin - Arduino pin
1         D12  Via 230 kohm resistor
2         D12 Via 230 kohm resistor
3         D12 Via 230 kohm resistor
4 thu 15  D12 Via 230 kohm resistor     
16        D12 Via 230 kohm resistor


A simple chip tester for retro 4, 6, 8, 10, 12, 14 or 16-pin chips, designed around an Arduino Uno, some resistors, a ZIF socket, and a couple of breadboards.

Full description at <http://www.gammon.com.au/forum/?id=14898>

To use the code unmodified, wire up as follows:

 ZIF pin |Arduino pin | Notes
--------:|-----------:|---------------------
1        | 9         | Via 330 ohm resistor
2        |  8        | Via 330 ohm resistor
3        |  7        | Via 330 ohm resistor
4        |  6        | Via 330 ohm resistor
5        |  5        | Via 330 ohm resistor
6        |  4        | Via 330 ohm resistor
7        |  3        | Via 330 ohm resistor
8        |  2        | Via 330 ohm resistor
9        |  10       | Via 330 ohm resistor
10       |  11       | Via 330 ohm resistor
11       |  A5        | Via 330 ohm resistor
12       |  A4        | Via 330 ohm resistor
13       |  A3        | Via 330 ohm resistor
14       |  A2        | Via 330 ohm resistor
15       |  A1        | Via 330 ohm resistor
16       |  A0        | Via 330 ohm resistor
7        |  2         | via jumper/switch to gnd 
8        |  13        | via jumper/switch to gnd
16       |  +5V       | via jumper/switch to +5V (optional - see text of article)

Compile and upload sketch (tested on an Arduino Uno). Open the Serial Monitor, set baud rate to 115200, line ending: newline.

Follow prompts in the serial monitor. Specifically:

* L : lists all known chips
* S4, S6, S8 ... S16 : scan for chips with that many pins
* \<chip number\> : search for that chip
* T : test a chip previously found by searching

Not all tests have been verified by the author. Many are not exhaustive, but should be adequate to identify a chip, or to see
if its basic logic functions and output drivers are working.

Only connect pin 16 on the ZIF chip to +5V if your target chip expects power (Vcc) on that pin.

Chips are inserted at the **top** of the ZIF holder. That is, pin 1 is always in the same place.


![Screenshot_20221011-193156_Gallery](https://user-images.githubusercontent.com/13838239/195161154-13c7af3a-4692-4290-9b5a-1ecf650860ba.jpg)
![Screenshot_20221011-193221_Gallery](https://user-images.githubusercontent.com/13838239/195161167-d3034f23-1b33-4ca0-a698-40c3ee57e8e5.jpg)
