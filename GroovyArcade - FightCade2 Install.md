# GroovyArcade FightCade2 Install

https://aur.archlinux.org/packages/fightcade2/

Enable Multilib

```
sudo hostnamectl set-hostname "AstroCity"
sudo vi /etc/pacman.conf
```

uncomment out

```
[multilib-testing]
Include = /etc/pacman.d/mirrorlist

[multilib]
Include = /etc/pacman.d/mirrorlist
```

Update the repos

```
sudo pacman -Sy
```

Install base-devel so you can build the FightCade package from AUR

```
sudo pacman -S base-devel
# Select options: 1 2 3 4 5 6 10 17 19 20 21

sudo pacman -S git wget unzip rsync
```

Download the AUR FightCade2 package
```
mkdir $HOME/shared/tmp/
cd $HOME/shared/tmp/
git clone https://aur.archlinux.org/fightcade2.git
cd fightcade2
makepkg -Acs
sudo pacman -U fightcade2-2.1.3-1-any.pkg.tar.zst
```

Install required packages missed

```
sudo pacman -S multilib/lib32-libxss multilib/lib32-libcurl-gnutls community/libcurl-gnutls extra/libzip community/wine-mono libgnutls
```

I had some errors with the Flycast Emulator for missing some dependencies. To help out with this I will install yay

```
sudo git clone https://aur.archlinux.org/yay.git
sudo chown -R arcade:arcade yay
cd yay
makepkg -si
yay --version
yay -S aur/libcurl3-gnutls
```

restart Wine

```
sudo systemctl restart systemd-binfmt
```

start Fightcade2

```
sudo /opt/fightcade2/Fightcade2.sh
```

I'm still troubleshooting a segfault issue when loading Flycast ROMs.

# Flatpack - Fightcade

Install Fightcade via Flatpack

https://flathub.org/apps/details/com.fightcade.Fightcade

GroovyArcade uses an LXDE desktop. This is written in GTK2/3

```
sudo hostnamectl set-hostname "AstroCity"
sudo pacman -Sy
sudo pacman -S git wget unzip rsync flatpak

sudo pacman -Sy
sudo pacman -S flatpak
# Option 1 (GTK)
```

Install fightcade app

```
flatpak install flathub com.fightcade.Fightcade
```

Download json for needed roms

```
mkdir /home/arcade/shared/fc2-json
cd /home/arcade/shared/fc2-json
wget https://newchallenger.net/fc2/fc2roms.zip
unzip fc2roms.zip
rm fc2roms.zip
cp * /home/arcade/.var/app/com.fightcade.Fightcade/data
```



**To run this Flatpak app, enter:**

`flatpak run com.fightcade.Fightcade`



JSON Files

```
/home/arcade/.var/app/com.fightcade.Fightcade/data
~/.var/app/com.fightcade.Fightcade/data
```



## To Do
### Fightcade Flatpack

```

```

### FightCade Manual
- - Do these variables need to be changed to be inline with GroovyArcade?

```
fightcadeInstallFolder="/opt/$fightcadeUserFolderName"
fightcadeUserFolderPath="$HOME/.$fightcadeUserFolderName"
fightcadeRomsPath="$fightcadeUserFolderPath/ROMs"
oldVersionTxt="$fightcadeUserFolderPath/VERSION.txt"
newVersionTxt="$fightcadeInstallFolder/VERSION.txt"
oldVersion=0
```



- Check permissions as Fightcade2.sh needs to be run as root

# Commands to remember

### Add a repository

To add a remote flatpak repository do:

```
$ flatpak remote-add name location
```

where *name* is the name for the new remote, and *location* is the path or URL for the repository.

For example to add the official [Flathub repository](https://flathub.org/):

```
$ flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

### Delete a repository

To delete a remote flatpak repository do:

```
$ flatpak remote-delete name
```

where *name* is the name of the remote repository to be deleted.

### List repositories

To list all the added repositories do:

```
$ flatpak remotes
```



# Resources

- https://www.addictivetips.com/ubuntu-linux-tips/multiplayer-arcade-games-linux/
- https://lofi.netlify.app/post/fc2-json-pack-auto-download-roms-from-fightcade-2/