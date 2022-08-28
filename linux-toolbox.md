## Bash History
View current history:
```bash
history
```
Commands are written to the HISTFILE environment variable, which is usually .bash_history. We can echo it to see the location:
```bash
echo $HISTFILE
```
We can use `unset` to remove the variable:
```bash
unset HISTFILE
```
We can also make sure the command history isn't stored by sending it to /dev/null:
```bash
HISTFILE=/dev/null
```
We can set the number of commands to be stored during the current session using the HISTSIZE variable:
```bash
HISTSIZE=0
```
The `set` or `shopt` commmands can be used to change shell options:
```bash
set +o history      # disable history
set -o history      # enable history
shopt -ou history   # disable history
shopt -os history   # enable history
```
The history can be cleared using `-c`:
```bash
history -c
```
To make sure the changes are written to disk, we can use `-w`:
```bash
history -w
```
That will only clear the history for the current session. To absolutely make sure the history is cleared when exiting a session, the following command comes in handy:
```bash
cat /dev/null > ~/.bash_history && history -c && exit
```

## Check Whether Reboot is Required
```bash
cat /var/run/reboot-required
```
If the file exists, then a reboot is required.

## Check Whether Computer has HDD or SSD
```bash
lsblk -o name,rota
```

## Boot Repair
```bash
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install boot-repair
boot-repair
```

## Change Boot Menu to Save Last Option
```bash
sudo nano /etc/default/grub
```
Change: `GRUB_DEFAULT=saved` <br />
Add: `GRUB_SAVEDEFAULT=true`
```bash
sudo update-grub
```

## Working with .tar.gz files
To compress:
gzip compression (faster and more common):
```bash
tar -czvf name-of-archive.tar.gz /path/to/directories-or-files
```
bzip2 compression (slower but more compression):
```bash
tar -cjvf name-of-archive.tar.bz2 /path/to/directories-or-files
```
To exclude files:
```bash
tar -czvf archive.tar.gz /home/ubuntu --exclude=*.mp4
```
To extract:
```bash
tar -xzvf name-of-archive.tar.gz
```
Or:
```bash
tar -xzvf name-of-archive.tar.gz -C /directory/to/extract/to
```

## SSH
SSH:
```bash
ssh user@host [-p port]
```
SFTP:
```bash
sftp [-R 128 -B 65536] user@host [-P port]
```

## Split
### Split file:
Split into xaa, xab, xac, …:
```bash
split -b 1G filename
```
Split into out.aa, out.ab, out.ac, …:
```bash
split -b 1G filename out.
```
### To recombine file:
```bash
cat out.?? > filename
```
