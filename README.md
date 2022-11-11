# CS-230-Minecraft-Challenge
Project for CS-230 class

Introduction
For this project we plan to combine Minecraft gameplay with the Raspberry Pi. The Pi will host a lightweight minecraft server, fitted with a plugin that will check for certain requirements as part of a competition to see who can find diamonds first. The competition will be between 2 players: a player A and player B. The Raspberry Pi will have a poster board with neopixels connected to it that will light up when an achievement is unlocked or a new tool is acquired. For example, once a player gets the achievement “Getting Wood” or acquires a wooden tool the neopixels will flash and light up with a respective color of the respective player, along with a neopixel ring for that player lighting up one of its rings. Once one player gets diamonds, that player will win, and the lights will flash. All of this will be done by tracking a player’s data through code, specifically in a server side minecraft plugin. The reason why we chose this project is because our group enjoys playing Minecraft and would like to see an interesting twist to the game. This will give the player’s an incentive for hitting goals and giving something else to play for. We will also have the ability to incorporate many different pieces of hardware, including neopixels, the raspberry pi itself, and others, which will allow us to learn a lot about them.
Methodology 
    First we will need to set up a Raspberry Pi, and to start up a minecraft server, likely a forge server. Servers like this support mods and plugins. From here we will be able to attach a program that sends information to a python program running on the Pi that controls the neopixel board. Refer to Diagram One down below to see a basic layout of how this will work. On the board, it is planned that it will include a border of neopixels that will light up in different ways depending on how the challenge is going. There will be 2 concentric neopixel rings that will directly represent how many points a different player has. We will also try to include a stopwatch to show how long the competition has been going for. Please refer to Diagram Two to see how this board might be arranged. 
    Because of the amount of neopixels being used, a separate power supply will be needed to supply power to the Pi and the neopixels. This will be achieved through the use of a modified power supply that was fitted specifically for this type of project. We will also be bringing in a circuit board that powers the pi and facilitates power conversion to the neopixels. It also includes a number of buttons and a LCD screen, which we may use if we have time to spare.
    —
    Once we got some of the neopixels, we were able to do some testing with a Raspberry Pi 3 I had laying around. Powering them was slightly difficult without the proper converter, but with some jumpers, we were able to get a pixel to light up. Once we were able to get our hands on the converter board, we were able to easily plug in a strip of neopixels and they lit up without much work. Once we got the Pi4 8GB, we were able to start trying to set up a server. This took many hours of troubleshooting. We originally tried to use a SD card with an older version of Rasbian on it, and we attempted to upgrade it to the current version of Raspbian, Bullseye. It has some configs that we wanted to carry over, but unfortunately, it lost power during the upgrade and was not able to be recovered. We flushed a new SD card with the latest version of Rasbian, and began trying to install a server. First we installed the Java development kit, which is needed to run Forge, the minecraft server we decided on using. With some more troubleshooting, we were able to launch the server, but we ran into issues with dedicating ram to the server, as it turned out we were not running the 64 bit version of Rasbian, which was needed to run the 64 bit version of Java, which meant we could only use 2 Gigabytes of the available 8 Gigabytes of memory. This means we will have to reflash the OS, but with our new knowledge of the Linux command line and our prior experience setting up the server the first time, this will likely go much smoother.
    To facilitate a connection between the minecraft server and the program powering the neopixels, we are implementing a mod providing us with a web based API. This API features webhooks that will allow us to set actions in the server (i.e. achievements) as triggers (outputs) that will be read by the neopixel software. This will give us flexibility to create events not only based on achievements, but also users joining/leaving, using commands, or sending messages.
    
Diagram One


Diagram Two


Parts List
Neopixel Strands (Can supply if needed)
    Will use these as a border around the poster board. Will light up in different ways depending on how competition is going. 
Neopixel Concentric Rings (Will supply)
    Will directly display how many points player A and player B have. One layer will light up if the player has gotten stone, and another layer for iron, and so on, depending on challenges.
Foam Boards (14 x 11)
    Will be used to mount neopixels on. Holes can be poked through the board for wires to the neopixels.
Raspberry Pi 4 (Can supply if needed)
    Needed to control neopixels and other electronics. We have access to a Pi 4 4GB if needed.
Wifi USB (Can supply if needed)
    Will need a means of connecting Pi to the internet to allow for device connections.
A Device that Runs Minecraft (Our Owned Desktops, Laptops)
Our laptops should have no problem connecting to a minecraft server.
Power Bucket (Will be provided)
    Needed for powering large amounts of neopixels. Essentially is a bucket with a modified ATX power supply with a fan and an on/off switch. 
Website Resources

https://www.baeldung.com/java-working-with-python
    Details how one might connect a java file to a python file. This is one thing that we were unsure of how to accomplish.
https://pimylifeup.com/raspberry-pi-minecraft-server/
    Details how one person set up a minecraft server on a Raspberry Pi. Uses a spigot server, but still useful to see how things are downloaded on linux.
https://curtmorgan3.medium.com/hosting-a-modded-minecraft-1-16-4-server-on-a-raspberry-pi-45dec2fd14c6
    Details how another person set up a modded minecraft server on a Pi. Uses a forge server, just another approach to setting up a server.
