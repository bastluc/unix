# Compte rendu du TP1

## notes en vrac

numéros d'identifiant de processus : PID (processus identifiants)
identifiant de l'utilisateur : UID
id de root : 0

utilisateurs dans /etc/passwd
groupes dans /etc/group
mots de passe dans /etc/shadow

supprimer une partition:

- fdisk
- p
- d {numero de la partition}
- commenter la ligne de la partition dans /etc/fstab
démonter une partition avec umount


## 1.SSH

1 - installer ssh : 
apt-get install ssh

2 - autoriser les connexions distantes avec mot de passe : 
nano /etc/ssh/sshd_config
décommenter la ligne : "PermitRootLogin yes" et la ligne "PassworkAuthentification"
mettre la carte réseau de la machine en bridge

3. Résultat des commandes 

~~~
df -h

Filesystem      Size  Used Avail Use% Mounted on
udev            228M     0  228M   0% /dev
tmpfs            49M  1.7M   47M   4% /run
/dev/sda1       4.6G  1.6G  2.8G  36% /
tmpfs           242M     0  242M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           242M     0  242M   0% /sys/fs/cgroup
/dev/sda3       453M  5.3M  420M   2% /var/log
/dev/sda2       1.9G  5.7M  1.7G   1% /tmp
tmpfs            49M     0   49M   0% /run/user/0
~~~

~~~
fdisk -l

Disk /dev/sda: 10 GiB, 10737418240 bytes, 20971520 sectors
Disk model: VBOX HARDDISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C3A0FFFE-64B2-47C4-BA61-7A6C66FBDA39

Device        Start      End Sectors  Size Type
/dev/sda1      2048  9764863 9762816  4.7G Linux filesystem
/dev/sda2   9764864 13670399 3905536  1.9G Linux filesystem
/dev/sda3  19994624 20969471  974848  476M Linux filesystem
~~~

~~~
dpkg -l | wc -l

561
~~~




