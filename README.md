# Altium_5vain_to_5vpwm
Altium project files for a 5V analog to 5V pwm (4kHz) convertor using [LTC6992-1](https://www.analog.com/media/en/technical-documentation/data-sheets/LTC6992-1-6992-2-6992-3-6992-4.pdf).

![A rendered image of the circuit board](assets/img/PCB1.png)

LTC6992-1 linearly maps a 0.1-0.9V analog input to a 0-100% duto-cycle pwm signal. The output pwm frequency can be set between 3.81Hz and 1MHz by adusting the resistor values (R_SET, R1, and R2). To identify these values for your desired output frequency, you want to first decide N_dev, referring to the table [here](https://www.analog.com/media/en/technical-documentation/data-sheets/LTC6992-1-6992-2-6992-3-6992-4.pdf#page=16). Once you decide on N_dev, the table gives you the R1 and R2 values, and you can obtain the corresopnding R_SET value using Equation (1b) on [this page](https://www.analog.com/media/en/technical-documentation/data-sheets/LTC6992-1-6992-2-6992-3-6992-4.pdf#page=20).

This pcb scales a 5V analog signal to a 0.1-0.9V one using a resistor network. Then, the LTC6992-1 converts it into a 4kHz 5V pwm signal.
- INPUT: 0-5V analog; JST-XH terminal.
- VIN: 5V DC; barrel jack (DIN 2.1mm; DOUT 5.5mm)
- OUTPUT: 5V 4kHz pwm (AIN=0V -> OUT=0%; AIN=5V -> OUT=100%. Linearly mapped); JST-XH terminal.
- DigiKey component list: https://www.digikey.com/en/mylists/list/5BIYH8LDG3
