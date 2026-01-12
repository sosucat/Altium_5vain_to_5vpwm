# Altium_3v3ain_to_5vpwm
Altium project files for a 3.3V analog to 5V pwm (4kHz) convertor using [LTC6992-1](https://www.analog.com/media/en/technical-documentation/data-sheets/LTC6992-1-6992-2-6992-3-6992-4.pdf).
This enables 3.3V ILDA DACs (e.g., [Helios DAC](https://bitlasers.com/helios-laser-dac/)) to control PWM-based industry lasers.
For 5V-based ILDA DACs, you want to look for commercially-available 5V analog-pwm converters.

![A rendered image of the circuit board](assets/img/PCB2.png)

### LTC6992-1
LTC6992-1 linearly maps a 0.1-0.9V analog input to a 0-100% duto-cycle pwm signal. The output pwm frequency can be set between 3.81Hz and 1MHz by adusting the resistor values (R_SET, R1, and R2). To identify these values for your desired output frequency, you want to first decide N_dev, referring to the table [here](https://www.analog.com/media/en/technical-documentation/data-sheets/LTC6992-1-6992-2-6992-3-6992-4.pdf#page=16). Once you decide on N_dev, the table gives you the R1 and R2 values, and you can obtain the corresopnding R_SET value using Equation (1b) on [this page](https://www.analog.com/media/en/technical-documentation/data-sheets/LTC6992-1-6992-2-6992-3-6992-4.pdf#page=20).

### PCB Overview & Usage
This pcb scales a 3.3V analog signal to a 0.1-0.9V one using a resistor network. Then, the LTC6992-1 converts it into a 4kHz 5V pwm signal.
- INPUT: 0-3.3V analog; JST-XH terminal.
- VIN: 12-24V DC; Terminal block. The LDO regulates it to 5V (VDD). Current spike protection with a series resistor and a zener diode.
- OUTPUT: 5V 4kHz pwm (AIN=0V -> OUT=0%; AIN=5V -> OUT=100%. Linearly mapped); JST-XH terminal.
- Calibration: The analog--duty-cycle gain is adjustable with the potentiometer to compensate the voltage drop over the analog wires.
  - Connect the power supply and analog signal lines.
  - Send the maximum analog signal (i.e., 3.3V).
  - Twist the potentiometer so that the measured voltage at Pin 1 (MOD) of LTC6992-1 is about 0.9V.
  - Set the analog input to the lowest (i.e., 0.0V) and check the Pin 1 voltage is below 0.1V. No need to twist the pot this time. This will ensure the 0% duty cycle for the lowest analog voltage.
- DigiKey component list
  - https://www.digikey.com/en/mylists/list/5BIYH8LDG3
  - https://www.digikey.com/en/mylists/list/SE503POLSQ (additional components for the 3.3V version)
