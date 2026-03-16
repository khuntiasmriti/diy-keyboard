# Keyboard using Blue Pill

---

The circuit attached uses a matrix keypad connected to the STM32F103C8T6. The keypad buttons are arranged in a grid and scanned by the microcontroller to determine which key is pressed. The detected key values are then transmitted through UART to a virtual terminal.

---

### Parts used
* SPST push button (x30)
* VSM Virtual Terminal

---

#### KeyPad Matrix Structure

The push buttons are organised in a matrix of rows and columns
* **Columns:** Vertical lines connected together.
* **Rows:** Horizontal lines connected together.
* Each button connects one row and one column and hence reduces number of required GPIO pins.


## Electrical Connections
### Row lines
Row wires are connected to the GPIO output.
Purposes:
* The MCU drives one row low ar a time
* The other rows remain HIGH.

### Columns lines
Columns wires are connected to the GPIO input.
Purposes:
* The internal pull-up resistors enabled
* By default=logic HIGH
  
---

### Signal Path

When the key is pressed, it electrically connects a row to a column line. 
MCU drives Row2 LOW -- (button pressed) -- Column3 input reads LOW

So the controller detects Row=2, Column=3 which is a unique identity to a specific letter.

---

### MCU Processing

The STM32 performs three tasks:
*  **Row Activation:** Sequentially drives each row pin.
*  **Column Reading:** Reads column GPIO input to detect key presses
*  **Key mapping:** Converts (rows, column) coordinates into a key value
 
---

### Power connections
STM operates at these levels to provide power for the microcontroller and GPIO logic levels.
* VDD = 3.3V
* VSS = GND

---

![Keyboard Schematic](https://github.com/khuntiasmriti/diy-keyboard/blob/main/keyboard%20%5B20260207%2C%2019-08-54%5D.pdsprj)
