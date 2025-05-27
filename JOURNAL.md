---
title: "RCRocket"
author: "DynamicWhiteHat"
description: "My first attempt at making the fastest RC car I can."
created_at: "2025-05-25"
---

# May 26th: Finished initial power sources!

Since I have some experience designing PCBs for other projects, this time I decided to run the project off an ESP32 SoC instead of using a devkit. This took some research, since I had no experience working with SoC's before. After watching some videos and looking at a few tutorials online, I designed a usb power circuit for the ESP32, one of the main parts of the whole design. THen I went on to designa  power circuit for the lipo input. i decided that using the lipo to power both the ESC's and the ESP32 was the best decision. When I was done, I ended up with this:

![image](https://github.com/user-attachments/assets/b7ac88c6-33cb-473b-931b-9b59a4b2e634)

Next, I worked on choosing the parts for the RC car. I decided to do a single 3700Kv motor paired with an ESC and a 35 kg servo. I also decided to include a fan for thrust at the back of the car. This required another ESC and thus another connection to the ESP32. I then put their connections in KiCad and ended up with this:

![image](https://github.com/user-attachments/assets/ca0f0995-a59e-4ff2-8f3f-03b9e4e2a828)

Finally, I started adding some sensors to the RC Car to send back as telemetry, such as an accelerometer and ToF sensors to detect imminent collisions. This is something I need to work on next time. I also adde some brake lights and headlights.

![image](https://github.com/user-attachments/assets/952d1c19-cd8a-48a4-9ac1-058a7a172cc9)



**Total time spent: 5h**
