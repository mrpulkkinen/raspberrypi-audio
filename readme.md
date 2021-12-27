Raspberry PI Zero to Airplay with HDMI Output

sudo apt-get install autoconf libtool libdaemon-dev libasound2-dev libpopt-dev libconfig-dev
sudo apt-get install avahi-daemon libavahi-client-dev
sudo apt-get install libssl-dev
sudo apt-get install git


cd ~
git clone https://github.com/mikebrady/shairport-sync.git

cd shairport-sync
autoreconf -i -f
./configure --with-alsa --with-avahi --with-ssl=openssl --with-systemd --with-metadata

make
sudo make install

sudo systemctl enable shairport-sync

sudo service shairport-sync start

Adjust Audio
sudo nano /usr/local/etc/shairport-sync.conf

In the file find 

//      volume_range_db = 60 ;

Un comment and replace with 

        volume_range_db = 80;
        
        



