## Inspiration
I've worked at Behaviour Interactive (http://bhvr.com/) for a while now and the idea behind this project was simply that Fred and I like to make fun stuff which we bring to the company Christmas party.

Last year, we built a 3D printed belt buckle with green and red LEDs that displayed the company's logo. Those LEDs were lit using a push button. This year we wanted to make it a bit bigger and since last year's Christmas party was all about being in line ups (to get food, to get drinks, to give/get your coat), we decided to make a device to entertain our friends/co-workers.

Since we were two working on this project, we decided to build two such devices.

This project started with just Fred and I, but it ended with Antonio Maiorano and Rémi Veilleux helping out as extra programmers. Those two guys did amazing work on the software side to integrate bEtris (a Tetris clone), a NES emulator with Super Mario Bros., a movie player and more.

## What It Is, What It Does
The device is an RGB LED display with a resolution of 64x32 that is controlled by a Raspberry Pi 2. This Raspberry Pi has up to 4 USB controllers plugged into it to control the gaming console.  For simple gameplay, we used four cheap NES controller knockoffs.

The applications we built pretty much make the system into a mini game console. We wrote a few games:
- Snake
- Tron
- bEtris
- NES emulator running Super Mario Bros
- Movie Player

Tron and bEtris support networking over UDP.  To accomplish this, we use Wi-Fi dongles plugged directly into the Raspberry Pi.

## How We Built It
Hardware-wise, the device is relatively simple.  A lithium-polymer battery feeds into a big buck converter, which lowers the 3-cell voltage of the battery from around 11-12V to the 5V that are required for both the Raspberry Pi and the LED matrix.

On the Pi, there is an Adafruit HAT designed expressly for controlling the RGB LED matrix.  The buck converter's output is fed directly to both the Pi and the HAT, and the HAT redistributes power to the LED matrix via fat conductors.  The HAT is also connected to the LED matrix via an IDC ribbon cable, which sends across the high-frequency control signals required to drive the individual LEDs at good framerates.

Other than that, on the evening of the Christmas party, the four USB ports of the Raspberry Pi were taken up by the USB controllers.  Under different circumstances, we might choose instead to plug two controllers and a wireless network adapter to bridge the two devices together for network play.    

## Challenges We Ran Into
We worked on this project at home when we had the time; we had a fixed deadline, the Christmas party. We started early but we had a very slow pace (3-5 hours per week). By mid-November we realized that our current pace would not allow us to accomplish everything we had set out to do, so we had to cut planned features. We also increased our production pace significantly to be able to ship this on time.

One issue we had with power delivery. In order to be mobile within the bar where the party was to be held, we decided to power the device via Li-Po batteries we normally used for our RC planes.  In order to do this, we needed a beefy DC-DC buck converter which could deliver up to the 5 amps required by the Pi and the display.  We already had one such converter on hand and ordered a second one from China; as luck would have it, it took so long to ship that the second converter came in two weeks after the deadline. Thus, we were only able to finish one of the devices on time for the party.

Due to the time constraints, we faced the all-too-familiar challenge of having many features in development at the same time:

- Networking
- OpenGL shader rendering
- NES emulator
- Electronics assembly
- Packaging (i.e. case construction)
- Tron
- bEtris
- Movie player and movie production
- Interactive movies (for dancing) - we never finished this unfortunately
- Controller interfacing

On top of that we were building on multiple operating systems - Windows, Linux and OS X - which increased the maintenance burden to keep things compiling on all targets.  With everything we had to do, we had to cut networking, shaders and interactive movies. We barely had time to optimize the NES emulator to have it working fast enough to play smoothly.

We had, and still have, an intermittent crash on boot in the LED display driver which caused us a lot of pain and debugging. The night of the party the crash was happening 100% of the time, so we had to go debug and come a bit later (thanks to Fred!).

The NES controllers were from two different eBay vendors, and it turned out there were three different hardware makes.  One of the makes was of much higher quality than the others, so using the one controller of that make gave the player a slight but undeniable advantage over the others.  Additionally, all three makes behaved differently as far as the software was concerned, so we implemented a routine that would observe incoming input until it could automagically determine which controller was connected to which port by analyzing reported button press patterns.  

3D printers are nice - when they work. I have a Ultimaker 2 and I'm having a lot of issues printing large models.  For example, the printer underextrudes, the model won't come off the plate, the feeder stops feeding, the nozzle cloggs, name it... In the end, we had to fashion a case out of hardboard scraps, a few nuts and bolts, and a few pieces of nylon tubing for the party.

## Accomplishments of Which we are Proud
We shipped in time! At one point we were not sure we were going to make it, but we did and it worked all night long.

We were expecting to entertain for 15 minutes or so, and for people to be bored of the device afterwards. It was actually quite surprising how popular it was. There were people playing all the time, the entire evening - it was a hit! Tron was simple and competitive, it was the most played game, a great candidate for such an event.

We are also proud of the level of productivity we managed to maintain with a group of four programmers continuously making sweeping changes to the code.  Antonio Maiorano and Rémi Veilleux greatly contributed to the software part, adding the NES emulator, bEtris, a movie player and many smaller features.  It was a great bonding experience to deploy our individual programming prowess on such a small playground without stepping on each other's toes too much.

## What we Learned
A lot of what we learned stems from the challenges we faced which are outlined above.  Generally speaking, however, we learned a lot about:

- driving the hardware RGB LED matrix display and how such displays are built
- the Raspberry Pi 2 and different versions of its OS - we have the software running on both Jessie and Wheezy Raspbian builds
- subverting SDL rendering to gain access to the main render target data to drive the LED matrix.  This drove us into strange, dark corners of SDL and we had to resort to platform-specific solutions to get the pipeline working similarly on both Windows and Linux.

## What's Next for bEXmas
We would like to finish the second hardware device now that we have the required buck converter on hand.  That will finally allow us to validate network play using final devices instead of breadboarded prototypes. We would also like to add new multiplayer competitive games, such as Pong.  We would also like to revisit the packaging and print proper cases with the Ultimaker.