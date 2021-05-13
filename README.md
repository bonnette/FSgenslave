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

