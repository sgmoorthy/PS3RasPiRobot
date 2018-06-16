# PS3 Joystick Controlled Raspberry Pi Robot
Controlling Raspberry Pi powered robot using PS3 controller and plot drawing using Turtle and Python code.

# Step 1 : Getting your Hardware ready
Have used Google Voice Hat for motor control, you can use any other motor DC motor HAT (eg Adafruit DC Motor HAT )

if in case you are using Google AIY voice HAT ensure you isolated power jumper from raspberry pi power, Read AIY manual

Also you need 2DW robotic base, GoPiGo based, i have build some additions to manage the Pan Tilt which i am planning to use it for this project upgrade.

Follow the PIN diagram specified in the AIY manual. I have used GPIO 04 and GPIO 17 to drive the DC motors , powered by battery power pack

# Step 2 : Setting up PS3 controller
Before connecting PS3 controller to Rapberry pi ensure you powered off PS3 station as the bluetooth auto conflict with connectivity.

Once you booted Raspberry Pi connect the PS3 controller via USB cable and run following command

```sh
jstest /dev/input/js0
```
this command should list all the buttons and values configurations from PS3. if you have the already a joystick driver in place
>, if in case you want to calibrate use command --> 

```sh
jscal -c /dev/input/js0
```

to install the joystick driver and pygame , Refer sixpair instructions for more

```sh
sudo apt-get -y install libusb-dev joystick python-pygame
cd ~
wget http://www.pabr.org/sixlinux/sixpair.c
gcc -o sixpair sixpair.c -lusb
```
  
# Step 4 : Pair PS3 Bluetooth
as said, ensure you disconnect PS3 console before you press PS3 button in PS3 controller and run following commands to pair

```sh
sudo ~/sixpair
```
Result Screen
Current Bluetooth master: b8:27:eb:cb:33:9c
Setting master bd_addr to b8:27:eb:cb:33:9c 
```sh
sudo bluetoothctl
```
>Result screen

>[NEW] Controller B8:27:EB:CB:33:9C raspberrypi [default]

>[NEW] Device CC:B1:1A:DA:B5:F1 [TV] Samsung 5 Series (32)

>[NEW] Device E0:AE:5E:A8:A0:89 PLAYSTATION(R)3 Controller

```sh
[bluetooth]# discoverable on
```
>Changing discoverable on succeeded

>[CHG] Controller B8:27:EB:CB:33:9C Discoverable: yes

```sh
[bluetooth]# agent on
```
>Agent registered 

>Type trust command on the identified device code on [bluetooth]#

```sh
trust E0:AE:5E:A8:A0:89
```
>Result 
>[CHG] Device E0:AE:5E:A8:A0:89 Trusted: yes
>Changing E0:AE:5E:A8:A0:89 trust succeeded
>[CHG] Device E0:AE:5E:A8:A0:89 Connected: yes
>[PLAYSTATION(R)3 Controller]#  

# Step 3 : Getting Code ready

I have re-used the code from JoyBorg, and have removed the pygame screen and replaced with turtle screen for interactive drawing experience. the idea was to draw turtle drawing in the screen in which Robot would replicate in parallel.
```sh
git clone 
```
