# RF Ambient Noise Detector

### **Overview**:
This system monitors high frequency RF power in environments. The core of the system is the AD8318 Logarithmic detector which is used 
to measure RF signals between 1 MHz and 8 GHz. This system converts the surrounding RF energy into a
DC voltage that is sampled and processed by the ESP32 for real time analysis or data logging.

<img width="556" height="406" alt="Screenshot 2026-05-13 143049" src="https://github.com/user-attachments/assets/21e139bf-fd32-4869-8f12-8892f6214e32" />
<img width="556" height="317" alt="image" src="https://github.com/user-attachments/assets/ff65e893-6c95-41bd-95e6-38a7ee05688d" />


### Key Features:
ESP32 WROOM 32U with antenna attachment to do the logic and then be able to data log via wifi.
AD8318 demodulating logarithmic amplifier to receive the input from the antenna and accurately convert the RF signal into a corresponding decibel 
scaled output voltage.
LM358 Dual Op Amp was used to take the small converted decibel scaled output and amplify it further to a signal between 1.5 - 5V to allow it to be 
read by the ESP32 input pins.
AMS1117-3.3 was used to drop down the 5V input voltage that the board took from the USB-C input, to 3.3V to supply enough power to the ESP32 without
damaging it.
USB C Input was used to supply 5V efficiently.
BWSMA Input was used to get the input from the antenna about the ambient frequencies. 

### PCB Layout Strategy
The SMA connector and the AD8318 had to be placed on the corner of the PCB to minimize interference from the ESP32. Additionally the trace between the SMA 
and AD8318 is short to minimize resistance and stray inductance. The LM358 is between the AD8318 and the ESP32 to act as a buffer and gain and the traces 
that carry the 1.5 to 5V signal are routed away from high speed signal traces to minimize crosstalk. The whole bottom layer was also set to ground to create
a low impedance return path for the RF signals.
