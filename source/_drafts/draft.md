Fix openssh retropi
googling brought me to this article [1], there are 2 suggested CLI commands but the command below fixed my issue:

$> sudo rm /etc/ssh/ssh_host_* && sudo dpkg-reconfigure openssh-server
sudo apt-get purge openssh-client openssh-server openssh-sftp-server ssh
sudo apt-get install openssh-client openssh-server openssh-sftp-server ssh


ADD ports
"/home/pi/.emulationstation/gamelists/ports/gamelist.xml"
?xml version="1.0"?>
<gameList>
        <game>
                <path>./Cave\ Story.sh</path>
                <name>Cave Story</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>
        <game>
                <path>./Doom.sh</path>
                <name>Doom</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>
        <game>
                <path>./Duke\ Nukem\ 3D.sh</path>
                <name>Duke Nuekem 3D</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>
        <game>
                <path>./Quake\ III\ Arena.sh</path>
                <name>Quake III Arena</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>        
        <game>
                <path>./Quake.sh</path>
                <name>Quake</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>
        <game>
                <path>./Super\ Mario\ War.sh</path>
                <name>Super Mario War</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>
        <game>
                <path>./hello.sh</path>
                <name>Hello</name>
                <playcount>2</playcount>
                <lastplayed>20171130T183547</lastplayed>
        </game>
</gameList>
                                                                                                                                                             
Create ports folder in rooms



Instal nds 
lr-desmume
DraStic


Autostart, no scrap

/opt/retropie/configs/all/autostart.sh"

emulationstation --gamelist-only #auto


Add roms or other in /etc/fstab

192.168.1.129:/volume1/rpi/ulstrastardx         /home/pi/RetroPie/ulstrastardx  nfs rw,nolock 0 0

Config folder:

Fire up the config.ini (Windows: Program folder I think, Linux: ~/.ultrastardx/config.ini) and edit the [Directories] part. Example:

[Directories]
SongDir1=/home/user/Musik/Karaoke/
SongDir2=/home/user/Dokumente/Dropbox/Karaoke/


parted to mount img

Mount .img iso.

It is necesary install parted
`apt-get install parted`

Use it:

```bash
parted file.img

(parted) unit B
(parted) print
.....
Number  Start          End            Size           Type     File system  Flags
 1      1048576B       1573912575B    1572864000B    primary  ntfs         boot
 2      1573912576B    156774694911B  155200782336B  primary  ntfs
 3      156774694912B  171454758911B  14680064000B   primary  ntfs
 4      171454758912B  180044693503B  8589934592B    primary

(parted )q 
```

And mount the partitons you want:
`sudo mount -o loop,ro,offset=1048576 /path/to/image/file/sda5.img /mnt/partition
`



https://askubuntu.com/questions/236263/browse-img-without-mounting
