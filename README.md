# FSgenslave
![Client Photo](https://github.com/bonnette/FSgenslave/blob/main/photo/IMG_3475s.jpg)
<br>
This Project is a variation of my FSgenweather project. The FS in "FSgenslave" stands for Full Screen. The "gen" in the name stands for "general" in that instead of 
grabbing data from a "SwitchDoc" weather station at the house. The weather data is derived from an api provided by openweathermap.com as well as QJsondocument to extract 
json data from the website.
The "slave" in "FSgenslave" indicates that the projects solves a problem.</br>
The Problem: "openweathermap.com" allows a limited number of queries each day. I was able to run one weather client using openweathermap.com but found that I hit the limits 
allowed by openweathermap.com if I tried to run two or more units.</br>
The fix for this problem was to have one master in the house that asked openweathermap.com for the weather (the master) and then have a slave ask the master for the weather
information instead of going to openweathermap.com for it. This allowed me to use 99% of FSgenweather code on FSgenslave. 
The Operating system is Buster version of Raspbian. The case shown is a new version of the case and the pi inside is an older version of a pizero with an Edimax network dongle
soldered to the bottom of it.
<br>
The case in the photo is from my Thingiverse repository and can be found here :
<br>
https://www.thingiverse.com/thing:4566312
</br></br>
Code and Pi modifications:</br>
- FSgenweather was modified to save weather info in a file in the "/home/pi" folder. "wthr.dat" see the sample on this repository.
- All code from FSgenweather was copied to FSgenslave.
- The code on FSgenslave was modified to eliminate the connection to openweathermap.com
- The code was further modified to read from the "wthr.dat" file to get its weather data.
- A script file was created on the slave pi "getwthr.sh".
- This script "getwthr.sh" copies the wthr.dat file from the master to the slave.
- The script "getwthr.sh" runs every 3 minutes using CRONTAB.
- No passwords were needed to complete the "wthr.dat" copy because keys were exchanged. 
- see: https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md
</br>
The operation goes like this:</br></br>
- Every 3 minutes the master gets weather data from openweathermap.com.</br>
- Every 3 minutes the slave copies the weather data (wthr.dat) from the master to the slave.</br>
- Every 3 minutes the master and the slave display the weather data on their respective TFT's</br>
</br>
To auto start the application in X-Windows after the X11 server has started edit:</br>
/etc/xdg/lxsession/LXDE-pi/autostart </br></br>
@lxpanel --profile LXDE-pi</br>
@pcmanfm --desktop --profile LXDE-pi</br>
@xscreensaver -no-splash</br>
@xset s off</br>
@xset -dpms</br>
@xset s noblank</br>
@/home/pi/fsweather  <-------- Add this to the end of the file. </br>
(Assuming that fsweather is the application you want to start)</br>

</br>
