# Compte-rendu du TP2

# 1. SSH
## 1.1 Connexion en Root par SSH
Cette étape a déjà été effectuée au TP précédent.

## 1.2 Génération de clefs SSH
Sur la machine windows executer la commande suivante :

~~~
ssh-keygen
~~~

La passphrase est utilisée pour encrypter la clé, sinon n'importe qui peut utiliser les clefs sans avoir de clef privée.

## 1.3  Authentification par clef / Connection serveur

Création du dossier ".ssh" : 
~~~
mkdir .ssh
~~~
Le dossier existe déjà dans mon cas.

Création du fichier "authorized_keys":
~~~
nano authorized_keys
~~~
Je copie ensuite ma clé publique dans le fichier.

Enfin je donne les droits minimaux pour le fichier : 
~~~
chmod 600 authorize_keys
~~~

## 1.4  Authentification par clef :  sous Windows

Nous pouvons maintenant nous connecter sans avoir besoin de rentrer le mot de passe sur le serveur.

## 1.5 Sécurisez !

pour n'autoriser que les connections avec une clé :
~~~
nano /etc/ssh/ssh_config
~~~
remplacer la ligne :
~~~
#PasswordAuthentication yes
~~~
par : 
~~~
PasswordAuthentication no
~~~

Une attaque par brute-force ssh est une attaque où l'on va essayer toutes les combinaisons de mot de passe possibles jusqu'à trouver le mot de passe qui fonctionne pour se connecter au serveur.

Il existe plusieurs techniques pour contrer cette attaque :

- Limiter le nombre de tentatives de connexions possibles : le serveur bloque la connexion si trop d'essais de mot de passe ont été effectés. Inconvénient : il est possible d'être bloqué assez rapidement

- Autoriser la connexion qu'avec une clé publique connue par le serveur. Cette méthode limite la connexion, une personne qui n'auras pas sa clé publique sur le serveur, même si celle-ci à les codes d'accès au serveur

- Il est également possible d'autoriser que certaines adresses IP à se connecter. Cela bride fortement les possibilités de connexions. Cela veut dire qu'il faut obligatoirement avoir sont IP autorisée sur le serveur pour pouvoir y accéder or nous pouvons changer d'IP à chaque changement de réseau.

# 2. Processus

## 2.1 Étude des processus UNIX

### 2.1.1 Liste des processus

Pour afficher tous les processus tournant sur la machine dans le format demandé : 
~~~
ps -uax
~~~

- L'information TIME correspond au temps d'utilisation du CPU pour un processus en particulier.

- Le processus ayant utilisé le plus longtemps le CPU de ma machine est le processus de PDI 13 lancé avec la commande [kworker/0:1-events]

- Le premier processus lancé après le boot de la machine est [/sbin/init]

- Ma machine a démarré à 14:20, une autre commande pour trouver le temps depuis lequel le serveur tourne est : 

~~~
uptime
~~~

Pour compter approximativement le nombre de processus créés depuis le démarrage de la machine : 

~~~
ps -uax | wc -l
~~~

### 2.1.2 

- Commande permettant d'afficher le PPID d'un processus
~~~
ps -ef
~~~
- Afficher la liste ordonnéee des processus ancêtres :

~~~
ps -ef --sort=ppid
~~~

## 2.1.3 pstree

~~~
apt-get install psmisc
~~~
pstree affiche un arbre des processus (plus compréhensible)

## 2.1.4 top

- la touche M permet d'afficher un résumé à l'aide de top trié par occupation mémoire

- Le plus gros processus lancé sur la machine est "systemd"

- passer l'affichage en couleur : z, mettre en avant la colonne de tri : <>, 

- htop a des paramètres plus lisibles, il est plus rapide à utiliser que top mais moins configurable

# 3. Arrêt d'un processus

lancer les deux processus: 
~~~
sh date.sh
sh date-toto.sh
~~~

pour tuer les processus :

~~~
fg 
(CTRL-C)

fg
(CTRL_C)
~~~


# 4. les tubes







