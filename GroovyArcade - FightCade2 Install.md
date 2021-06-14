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

## To Do
- Do these variables need to be changed to be inline with GroovyArcade?

```
fightcadeInstallFolder="/opt/$fightcadeUserFolderName"
fightcadeUserFolderPath="$HOME/.$fightcadeUserFolderName"
fightcadeRomsPath="$fightcadeUserFolderPath/ROMs"
oldVersionTxt="$fightcadeUserFolderPath/VERSION.txt"
newVersionTxt="$fightcadeInstallFolder/VERSION.txt"
oldVersion=0
```



- Check permissions as Fightcade2.sh needs to be run as root