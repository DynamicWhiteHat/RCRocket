---
title: "RCRocket"
author: "DynamicWhiteHat"
description: "My first attempt at making the fastest RC car I can."
created_at: "2025-05-25"
---

# May 26th: Finished initial power sources!

Since I have some experience designing PCBs for other projects, this time I decided to run the project off an ESP32 SoC instead of using a devkit. This took some research, since I had no experience working with SoC's before. After watching some videos and looking at a few tutorials online, I designed a usb power circuit for the ESP32, one of the main parts of the whole design. Then I went on to design a  power circuit for the lipo input. i decided that using the lipo to power both the ESC's and the ESP32 was the best decision. When I was done, I ended up with this:

![image](https://github.com/user-attachments/assets/b7ac88c6-33cb-473b-931b-9b59a4b2e634)

Next, I worked on choosing the parts for the RC car. I decided to do a single 3700Kv motor paired with an ESC and a 35 kg servo. I also decided to include a fan for thrust at the back of the car. This required another ESC and thus another connection to the ESP32. I then put their connections in KiCad and ended up with this:

![image](https://github.com/user-attachments/assets/ca0f0995-a59e-4ff2-8f3f-03b9e4e2a828)

Finally, I started adding some sensors to the RC Car to send back as telemetry, such as an accelerometer and ToF sensors to detect imminent collisions. This is something I need to work on next time. I also added some brake lights and headlights.

![image](https://github.com/user-attachments/assets/952d1c19-cd8a-48a4-9ac1-058a7a172cc9)



**Total time spent: 5h**

# May 27th: Finalized Power Circuits And Added More Sensors + Outputs!

Today, I worked on fixing the wiring for the MPU6050 and the lights. I decided to have 4 sets of lights with 3 neopixels in each set, allowing me to have split front headlights and split brake lights. Instead of splitting my PCB, I decided to have the lights separate and instead run their wires into the PCB. I also added 2 ToF sensors for collision detection. I decided to use a breakout for those. It took me a while to figure out how to wire the SDA and SCL lines to the MCU since they need pull up resistors, but I figured it out. I also added a fan for a speed boost at the back. I am currently working on adding a hall effect sensor to measure RPM. I also added a way to read the voltage from the Lipo battery. This is my current schematic:

![image](https://github.com/user-attachments/assets/79942c84-4247-486b-ac65-228c61d8f2ff)

I also took some time to pick out parts:

[Motor + ESC](https://www.amazon.com/HOBBYWING-Quicrun-10BL120-G2-QR10BL120-3660-3700KV/dp/B0C6BFFB96/ref=sr_1_6?crid=2GLWWCIJMF4GU&dib=eyJ2IjoiMSJ9.8ChSsRu2ggkRm0N2UcTo3s8XwfptuIsvx65iR2LIg5muf1JSHy0vtnELQ86QYJDx4WvZkFlYVlaacq9JVPW1ZXzwFG8T8RaeWX1uCPlYRiWeQq1TPSqla9zxhL6Utijh5d6hDXNKbLFf98KYOxJczOK0VRLIexn-y3KcpFkdGguTlDYXxnw7zrMy07UkYJ1imNJcrV1WjWylSnJbef-T2wXEEmOjtgRL-gOiuf6kmiBYvSw632WhL49FXDPe-U6_Th__7bfePq5tj9XiuF7KoXXXmoyOLh0wdQNsZ3HlEzY.TO152DIn2zMVWwIf-LqpNBpko4Rbb8-dUP9FB0hpb6s&dib_tag=se&keywords=brushless%2Bmotor%2Band%2Besc&qid=1748285295&sprefix=brushless%2Bmotor%2Band%2Besc%2Caps%2C161&sr=8-6&th=1)
[2x Servo](https://www.amazon.com/Steering-Servo-Motor-35KG-Torque/dp/B0B2C7TWS4/ref=sr_1_6?crid=1JGGEWAFQIU25&dib=eyJ2IjoiMSJ9.Wcp0wpi1uHDtGjZ9jSbSMW0zlOvAxMyX5LCtp292MXB2YEq95CXNk1d4PXKn4MVtJhTNGXcHi5yCQOsce_f7iI3XelUwu7FN_PgyybvjtmrzmRzUkZttM-5zMRwZjL10reeXmDFUkycjjYIoDwfhWuOUy2onRg8GY3cPu36n_0sxBl01rI_uPG7aVGy58ZozuztYmsVwEvUSzBFb6C05DE-MCLpMZ8kOh4a-q_RxXTHRXH66uMQ-YK6Hb0KvVJLHZ9FlM2tFXUlJ5tFdterWhJqYvhIisn_KuRf-Fp6o86o.dZxRxpe9E02O71EiMDcPAlZDGqR1Nq1a2OXbFS53RyI&dib_tag=se&keywords=35kg%2Bservo&qid=1748289042&sprefix=35kg%2Caps%2C103&sr=8-6&th=1)
[Lipo Splitter to power the Motor ESC, Fan ESC, and the MCU](https://www.amazon.com/GINTOOYUN-Splitter-Extension-Connector-Generator/dp/B0C4SMWZ6F/ref=sr_1_3?crid=3E46LSLUPNB43&dib=eyJ2IjoiMSJ9.c-TZI--fYD7--_q041QT7pdT8H6bq2bqwQmz4c1U-OEAuUXSW-hEOgmk4XFEn5rj8QtKziRvR-F1srrlG2GmoQijqaidJYxjNA1GULtWuwKOb26kiCpbC1d5GgNm4dROBKAiTfItOpl9jQIr8nDLiaCvrXpm-75j7z2jgVv4ZRL9rDwUps6MGiv128BO3l-XCQ7mQ-4C0leE9BAvza9yoM-s2buhvNyESSAh3tYdAYzOvWekcFRE8nEyPH1E79G3E6JAO4Q7BIjdg-5hzNNyjLmUE9a1DxW-ilNvD6ue_e4.6qM2mgL8NQ6nikEz1LPs5r1boX6XAOb_L66nd8ihitk&dib_tag=se&keywords=xt60+splitter+3+way&qid=1748296254&sprefix=xt60+splitter+3%2Caps%2C139&sr=8-3)
[EDF Fan](https://www.amazon.com/Powerfun-Ducted-Blades-Brushless-Airplane/dp/B07C3ZLPWG?th=1)

I still have to add the telemetry and work on finishing the hall effect sensor. I currently am having a hard time trying to get the 5v from the hall effect sensor down to 3.3v since I'm new to voltage divider. I might end up using an IC for this.


**Total time spent: 2h**

# May 28th: Finished Schematic

Today I finished the schematic for the car itself so I could get started on the PCB design. I added an NRF24L01 for telemetry. I also found out after speaking to @koeg on Slack that I did the pull up resistors wrong. They should be fixed now and look like this:

![image](https://github.com/user-attachments/assets/1b71f3c9-7340-4230-b5ce-8f25f831b95b)

I also finished the hall effect sensor, once again with help from @koeg. It took me a while to figure out how to properly wire it since it was a 5v device. I pulled the sensor up to 5v and then pulled the data pin back down to 3.3v to ensure compatibility with the ESP32, which runs at 3.3v. This is what it looks like now:

![image](https://github.com/user-attachments/assets/1347c057-66b9-40bd-b020-04721c166222)

Then I selected the footprints to use for the PCB, which is what took me the most time. This took a while since I have never used capacitors or resistors before and I didn't know what footprints they would use, since they all have different sizes based on their capacitance/resistance. I ended up watching a YouTube tutorial to figure it out. I also took a look at the economic PCBA option for JLCPCB and found that they only assemble SMD components, so I made sure to use SMD capacitors and resistors. The only thing left before moving on to designing my PCB is finishing up some footprints for custom parts. Once I finish this and my PCB, I can get started on the controller, which should use much of the same power logic. 

This is my final schematic:

![image](https://github.com/user-attachments/assets/61e19a63-01ce-4190-9372-661012fe6446)


**Total time spent: 3h**

