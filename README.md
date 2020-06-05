# KdG examentool Linux
De examentool geeft een foutmelding bij het opstarten in Ubuntu focal. 


## Installeer libgconf-2-4 voor Ubuntu focal (20.04)
https://www.ubuntuupdates.org/package/core/focal/universe/base/libgconf-2-4


## Installeer Mono 3.6
sudo apt-get remove mono-complete
sudo apt-get install build-essential gettext
wget http://download.mono-project.com/sources/mono/mono-3.6.0.tar.bz2
tar xvjf mono-3.6.0.tar.bz2
cd mono-3.6.0
./configure
make
make install
cd ..
rm mono-3.6.0.tar.bz2
rm -R mono-3.6.0


## Installeer pango-1.42.4 indien je volgende foutmelding krijgt "Harfbuzz version too old error message"
curl -JOL http://ftp.acc.umu.se/pub/GNOME/sources/pango/1.42/pango-1.42.4.tar.xz
tar xf pango-1.42.4.tar.xz
cd pango-1.42.4
printf "all:\n\ttrue\n\ninstall:\n\ttrue\n\n" > tests/Makefile.in
./configure --prefix=/usr
make && make DESTDIR="/home/user/oldlib/pango" install


## Start de examentool
LD_LIBRARY_PATH=/home/user/oldlib/pango/usr/lib /home/user/downloads/LNX-v4-alpha-P2.2017-18/kdg-xtl
