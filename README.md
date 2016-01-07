## Inspiration
I've been working at Behaviour Interactive (http://bhvr.com/) for a while now and the ideal behind this project was simply that Fred and I like to make fun stuff which we bring to the company Christmas party.

Last year, we build a 3D printed buckle belt with green and red LEDs that were showing off the company's logo. Those led were lit using a push button. This year we wanted to make it a bit bigger and since last year's Christmas party was all about being in line ups (to get food, to get drinks, to give/get your coat), we decided to make a device to entertain our friends/co-workers.

Since we are two that built this project from the bottom, we've built two such devices.

This project started with Fred and I, but ended with extra programmers : Antonio Maiorano and Remi Veilleux. Those two guys did amazing work on the software side to integrate Betris, a NES emulator with Super Mario Bros, movie player and more.

## What it does
The device is an RGB LED display with a resolution of 64x32 that is controlled by an RPI2. This raspberry by has up to 4 nintendo USB controllers plugged into it to control the gaming console.

The applications we've built is pretty much a mini game console. We have built few games which can be played with the controllers. Those games are:
- Snake
- Tron
- Betris
- NES emulator running Super Mario Bros
- Movie Player

All games which allows it support networking over UDP: Tron, Betris.

## How we built it
To be filled

## Challenges we ran into
We did this project at home when we had time and we had a dead line, the Christmas party. We started early but we had a very slow pace (3-5 hours per week). By mid November we realized that we had to remove feature from the final version, we wouldn't have time to deliver everything for the party. We also increased our pace significantly to be able to ship this on time.

On issues we had was with having the device plugged into the battery. We ordered parts from China, but it took so long to ship that one of the part came in after the dead line. We could only bring one of the two devices at the party.

We had many feature rolling at the same time:
- Networking
- Open GL shader rendering
- NES emulator
- Hardware
- Packaging
- Tron
- Betris
- Movies
- Interactive movies (for dancing)
- Controllers

On top of that we were building on multiple OS, Windows, Linux and iOS which led us to extra work to have it build on all platforms. With all those feature, issues with various platforms, we had to cut networking, shaders and interactive movies. We barely had time to optimize the NES emulator to have it working fast enough to play smoothly.

We had, and still have, a crash on boot in the LED display driver which caused us a lot of pain and debugging. The night of the party the crash was happening 100% of the time, we had to go debug and come a bit later (thanks to Fred!).

We ordered NES controllers from two different web site. One web site was providing controller WAY better than the other which led to a in-game advantage when you had the right controller.

3D printers are nice, well some time at least. I have a Ultimaker 2 and I'm having a lot of issue printing large models, either underextrusion, the model unstick from the plate, the feeder stop feeding, nozzle clogging, name it... We had to do a home made case which wasn't the 3d printed model for the party.

## Accomplishments that we're proud of
We shipped in time! At some point we were not sure we were gonna make it, but we did and it worked all night long.

We were expecting to entertain for 15 minutes or so at which point people would be bored of the device. It was actually quite surprising how it was popular. There were people playing all the time, it was a hit! Tron was simple and competitive, it was the most played game, a good candidate for such an event.

At some point we realized that we couldn't ship all we wanted so we talked about our project to some friends. Antonio Maiorano and Remi Veilleux were interested and joined us in the project. They greatly contributed on the software part, adding the NES emulator, Betris, a movie player and many low end features.

## What we learned
We learned a lot about the hardware display, RPI2 and SDL rendering, NES controller configuration, etc.

## What's next for bEXmas
Have the second device up and running with the part that just came in.
Add new competitive games, such as Pong.
Complete the packaging of the device. Have 3D printed cases.