OpenVAS — Audit de vulnérabilité avec Kali Linux
Projet : Analyse de Vulnérabilités avec OpenVAS et Kali Linux

Sommaire
Configuration du Réseau dans VirtualBox
Configuration IP statique sur OpenVAS
Vérification de la connectivité
Configuration IP statique sur Kali Linux
Accès à l’interface web d’OpenVAS
Lancement d’un Scan
Export d’un Rapport
Résultat attendu


1. Configuration du Réseau dans VirtualBox
Assurez-vous que les deux machines virtuelles (Kali Linux et OpenVAS) soient sur le même réseau interne.

Étapes :

Ouvrir les paramètres de chaque VM
Onglet Réseau
Sélectionner : Réseau interne
Nom du réseau : BUREAUTIQUE

Image ici (paramétrage VirtualBox)


2. Configuration IP statique sur OpenVAS
Étapes dans l’interface Greenbone :

Aller dans : Network > Interfaces > eth0
Activer IPv4
Choisir Static IP
Saisir l’adresse IP :

192.168.56.10/24

Saisir le DNS :

8.8.8.8

Cliquer sur Save pour enregistrer la configuration.

Image ici (paramétrage réseau dans Greenbone)


3. Vérification de la connectivité
Depuis la VM Kali, ouvrez un terminal et testez la connexion vers OpenVAS :

ping 192.168.56.10


4. Configuration IP statique sur Kali Linux
Attribuez une IP compatible :

sudo ip addr add 192.168.56.20/24 dev eth0

sudo ip link set eth0 up

Image ici (commande dans terminal Kali)


5. Accès à l’interface web d’OpenVAS
Ouvrez Firefox depuis la VM Kali et accédez à :

https://192.168.56.10

Ignorez le message SSL, puis connectez-vous :

Identifiant : admin

Mot de passe : toor

Image ici (interface web OpenVAS)


6. Lancement d’un Scan
Aller dans l’onglet Scans > Tasks
Cliquer sur Wizard
Remplir les champs :
Nom : scan_vulnérabilités
Cible : 192.168.56.1/24
Scan Config : Full and fast
Start time : Démarrer immédiatement
Cliquer sur Create

Image ici (création d’un scan)


7. Export d’un Rapport
Aller dans l’onglet Scans > Reports
Cliquer sur le rapport voulu
Choisir le format :

PDF

Cliquer sur OK pour le générer et le télécharger.

Image ici (export du rapport)


8. Résultat attendu
Détection des machines actives
Identification des vulnérabilités :
Critiques
Hautes
Moyennes
Faibles
Génération d’un rapport professionnel


Auteur





