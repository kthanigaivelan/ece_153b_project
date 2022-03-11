# ECE 153B - Energy Efficient Lighting

### Overview/Goal/Purpose:
We would like to create a energy efficient lighting system, that will only draw as much power as is absolutely needed. To do this, we will implement a light sensor, which will monitor the ambient light of the space and make adjustments in the LED brightness to maintain a standard level of overall brightness in the space. A secondary goal to further conserve energy is to implement motion or infrared based triggering, so the light only turns on once there is someone in the vicinity, and turns off once they leave.

### Peripherals
- LED/smart lamp or dimmer switch: LIFX white e26 smart bulb
- light sensor: adafruit bh1750
- optional motion/infrared sensor: onyehn infrared pir motion sensor detector

### Serial Interfaces
- I2C (Light sensor)
- UART (To python script used to control light bulb)

### Software Structure
If implementing motion detector: From an idle state, system is "woken up" by an interrupt triggered by the pulse from motion sensor.

If manual wake: Simply powering on the circuit will let the system enter a monitoring state.

The system, when awake, will take continuous readings from the light sensor, and use the comparison of this lux value to determine how much the bulb should be adjusted. This is sent via UART to a Python script (do we need a bluetooth module here?), which then uses the LIFX API to control the brightness of the bulb, adjustable by percentage.

### Weekly Updates
**02/25:**
We bought the LIFX Smart Lamp and worked on interfacing with the LIFXLAN library to control the lamp with Python. We also worked on setting up the BH1750 sensor using I2C protocols, by pseudocoding all the functions (init, reset, mode set, read data, etc) and understanding the commands taken by the sensor. We referenced Lab 4's I2C setup to do this. We will also be ordering the motion sensor.

**03/04:**
We were successful in implementing the function necessary to set up the BH1750 sensor. It now reads the correct lux values, which we tested by using different levels of light from a phone flashlight. We used a serial connection to output this in Termite. We attempted to do the same using the Bluetooth module, but ran into problems with the use of pins for UART communication. We will look into this next week. We have ordered the motion sensor, and will be working on implementing PyBluez and LifxLAN libraries in Python in order to communicate with the lamp.

![Image](week2update.png)

**03/11**
We realized there was a conflict in our I2C pins and UART pins, so we reassigned the pins for our brightness sensor. We thought that our bluetooth module was broken, but after attending office hours we were able to have the module transmit the ambience data. We also worked on the Python interfacing with the Bluetooth, and are working on transmitting this to the smart bulb.

## Using Github pages (reference)

You can use the [editor on GitHub](https://github.com/kthanigaivelan/ece_153b_project/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# does this work?
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kthanigaivelan/ece_153b_project/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
