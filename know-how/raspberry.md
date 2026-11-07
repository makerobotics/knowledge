General
#######
Write image with Ubuntu: imagewriter
sudo apt-get install git-core

debian
######

login:pi
pwd:raspberry

/etc/inittab:
#1:2345:respawn:/sbin/getty 115200 tty1
1:2345:respawn:/bin/login -f pi tty1 </dev/tty1 >/dev/tty1 2>&1

/etc/profile:
startx # At the scroll to the bottom and add it

#scp
scp file.txt you@192.168.1.1:/home/you/directory 

#ssh
sudo mv /boot/boot_enable_ssh.rc /boot/boot.rc

ssh pi@192.168.2.103 -X geany

ssh-keygen -f "/home/letzner/.ssh/known_hosts" -R 192.168.2.103

#enable sound immediatly
sudo modprobe snd-bcm2835

or at each boot:
sudo echo 'snd-bcm2835' >> /etc/modules

#enable video:
sudo usermod -aG video pi

#TV problem
###/boot/config.txt###
overscan_top=50
overscan_bottom=50
overscan_left=50
overscan_right=50
# Set stdv mode to PAL (as used in Europe)
sdtv_mode=2
sdtv_aspect=1  

Webradio
########
sudo nano /var/lib/mpd/playlists/radiosender.m3u
sudo ./daemon-example.py start
mpc load radiosender
mpc play 1

XBMC
#####
username: root
password: openelec

fuse
####
http://thedigitallifestyle.com/w/index.php/2012/05/15/tip-getting-fuse-zx-spectrum-emulator-running-on-a-raspberry-pi/

cd /boot
cp start.elf start.elf.backup #(Restore afterwards)
cp arm224_start.elf start.elf

cd libspectrum-1.0.0
./configure
make
sudo make install

add /usr/local/lib to your /etc/ld.so.conf file
sudo /sbin/ldconfig

cd ../fuse-1.0.0.1a
./configure --with-sdl
make
sudo make install

for some reason it doesn’t search the right location for libspectrum so 
“export LD_LIBRARY_PATH=/usr/local/lib”.  
I’m sure there should be an option on the configure to fix this

snes
####
sudo apt-get install zlib1g-dev
git clone https://github.com/ToadKing/pocketsnes-libretro.git
make

git clone https://github.com/ToadKing/RetroArch-Rpi.git
sudo apt-get install pkg-config
sudo apt-get install libsdl1.2-dev
./configure --disable-libpng
make

./RetroArch-Rpi/retroarch -L ./pocketsnes-libretro/libretro.so /home/pi/Super\ Mario\ World.smc

console
#######
joy2key -X -dev /dev/input/js0 -buttons o x k z space

GPIO
####

http://hobbyelektronik.org/w/index.php/Raspberry_Pi_IO



What I would do is make all the gpio files accessible to a group called gpio. Then add your user(s) to that group. This is what gpio-admin does I think (I haven't played with gpio yet) but you can do it manually.

As root
CODE: SELECT ALL
groupadd gpio
useradd -G gpio pi
cd /sys/devices/virtual/gpio
chgrp -R gpio *

The last two commands might need to be executed every time you start your Pi. You could instead of that add some initialise scripts to automatically chgrp the gpio files at boot time.
As this seems to be quite a common question, and to do it properly with a group is pretty easy I would recommend that the standard distribution is updated to have a gpio group and that the group ownership of the virtual devices are set accordingly on boot.