B3 - Conteneurisation TP2
===================


Hey! I'm your first Markdown document in **StackEdit**[^stackedit]. Don't delete me, I'm very helpful! I can be recovered anyway in the **Utils** tab of the <i class="icon-cog"></i> **Settings** dialog.

----------


Part 1 : Gitlab
-------------

`Les pré-requis : `

OS : CentOS7 
photo uname -a

Host configuration : 
photo host test

	>1. Ajout d'un disque.

A refaire chez moi avec une VM.

	>2. Installer Docker.

Docker est bien installé.

photo systemctl status docker

J'ai changé la configuration `daemon docker daemon.json` dans lequel j'ai renseigné :

photo daemonjson

On peut maintenant observer que dans `/data/docker/` se trouve tout ce qui était présent dans `/var/lib/docker ( après un cp -r )`

photo ls -alF /data/docker

 	>3. Installer gitlab-ce.

Voici gitlab-ce bien installé.

photo gitlab_well_installed

Voici maintenant mon certificat et ma clé dans /etc/gitlab/ssl.

photo crt_key_bon_fichier

Ensuite après avoir reconfiguré gitlab on va devoir agir sur les iptables pour permettre des connexions au port 443 (https) sur le serveur en INPUT et en OUTPUT.

photo iptables

Ou alors en agissant sur le daemon firewalld lui-même controllant les iptables à l'aide de la commande simplifiée firewall-cmd. (si notre serveur possède une interface graphique on peut installer des applets permettant de tout conf en clic clic)

photo firewalld (80/443/Https/http)
photo firewall-state
photo nestat-anpl

Voici le résultat :

photo rendu screen gitlab perso

	>4. Docker Registry.
