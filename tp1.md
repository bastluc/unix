# Compte rendu du TP1

## notes en vrac

numéros d'identifiant de processus : PID (processus identifiants)
identifiant de l'utilisateur : UID
id de root : 0

utilisateurs dans /etc/passwd
groupes dans /etc/group
mots de passe dans /etc/shadow

## 1.SSH

installer ssh : 
apt-get install ssh

autoriser les connexions distantes avec mot de passe : 
nano /etc/ssh/sshd_config
décommenter la ligne : "PermitRootLogin prohibit-password"
