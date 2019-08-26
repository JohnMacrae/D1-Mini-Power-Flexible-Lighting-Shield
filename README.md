# D1-Mini-Power-Flexible-Lighting-Shield

## Here are the specs of the final shield:

- 6-24V voltage regulator at up to 3A
- 3 pwm channels (up to 2.5A) for controlling RGB led strings
- 1 channel with WS2812B ‘driver’
- 1 other breakout pin
- Voltage divider on board for battery monitoring and switching
- Stackable! You can use more than one lighting board per D1 Mini
- Serial pins unused should you need to wire to an array of other microcontrollers.
- Configurable.  Only populate the areas you need on the board for the required functionality

## Testing confirms the following:

- Power supply good to 2.5A continuous at 30C
- Drives a string of 120 WS2812B at 80% brightness
- PWM channels (current sink) good for 2.5A per channel
- McLighting, Tasmota compatible
- PWM and WS2812B drivers work separately or concurrently

[![Watch the video](https://img.youtube.com/vi/jdQjJ58oq-U/maxresdefault.jpg)](https://youtu.be/jdQjJ58oq-U)

## Getting Started

- The board is configurable. You only need to populate the areas required to meet your needs. 

- If you don't need to monitor a voltage, omit R12 and R13
- If you don't need to PWM RGB led strings you can omit Q1-3 and R5-10
- If you don't need to drive the WS2812B, then you can omit LED1 and D1
- If you don't want to drive output D1 then omit R13
	
## Input pins

- Connect the power supply (6-24V) to the connections marked +12v and GND
- The ADC input is connected to the +12v pin for monitoring if required. The suggested values are R11, 20k and R12, 5K. This will allow an input of up to 16V to be measured.  

## Output Pins
	
- +5v and GND is supplied at JP4 - you can use it to supply any peripherals you like, including lighting. It also supplies the 5V pin of the D1 Mini.
- PWM0 is an output, via R13 from D1 (GPIO 5 (D1))
- WS is the WS2812B driver pin, via LED1. This is the pin you'll add to the Adafruit Neopixel or Mclighting code.
- L0, L1 and L2 are designed to control RGB LED strings. (If you decide to use it for other purposes such as driving a small motor, at least a flyback diode will be required). You can either hook up one RGB string (up to 2.5-3A worth) using all 3 channels or one monochrome strip to each channel.
 
## Firmware

- For WS2812B, I have used [Mclighting](https://github.com/toblum/McLighting/tree/master/Arduino/McLighting). - It only needs one pin declared (LED_PIN 4 (D2))
- For PWM, I usually write my own code or sometimes use [Tasmota](https://github.com/arendst/Sonoff-Tasmota). 
		
		L0 - 14 (D5)
		L1 - 12 (D6)
		L2 - 13 (D7)

## Notes

- WS2812B strings will benefit from a large capacitor across the power terminals (not mandatory but is said to improve their lifespan)
- You can demand a lot of power from the power supply and potentially overload it. It will tell you its not happy by getting hot :)  Best to limit the amount of power you can draw in your firmware.


## Boards and Components
- I may have boards and or components available from time to time. Please contact me with a comment on [Here](https://kk4oyj.wordpress.com/2019/08/15/esp8266-d1-mini-lighting-shield/)
