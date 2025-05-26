# Openvas
Audit de vulnérabilité sur openvas


# Projet : Analyse de Vulnérabilités avec OpenVAS et Kali Linux

## 1. Configuration du Réseau dans VirtualBox

Assurez-vous que les deux machines virtuelles (Kali Linux et OpenVAS) soient dans le même réseau.

### Étapes :

- Ouvrir les paramètres de chaque VM (dans VirtualBox)
- Aller dans l’onglet **Réseau**
- Sélectionner : `Réseau interne`
- Nom du réseau : `BUREAUTIQUE`

---

## 2. Configuration IP statique sur OpenVAS (Greenbone OS)

### Étapes dans l’interface Greenbone :

1. Aller dans : `Network > Interfaces > eth0`
2. Activer `IPv4`
3. Choisir `Static IP`
4. Saisir l’adresse IP :

```text
192.168.56.10/24

---

### 5. Saisir le DNS :

```text
8.8.8.8

---

## 6. Enregistrer et appliquer les paramètres

Après avoir saisi l’adresse IP statique et le DNS, cliquez sur `Save` pour enregistrer la configuration réseau sur la VM OpenVAS.

---

## 3. Vérification de la connectivité

Depuis la VM Kali, ouvrez un terminal et testez la connexion vers la VM OpenVAS :

```bash
ping 192.168.56.10


## 4. Configuration IP statique sur la VM Kali Linux

Attribuez une IP compatible avec celle d’OpenVAS :

```bash
sudo ip addr add 192.168.56.20/24 dev eth0
sudo ip link set eth0 up


## 5. Accès à l’interface web d’OpenVAS

Ouvrez Firefox depuis la VM Kali et accédez à :

```text
https://192.168.56.10

Ignorez le message d’avertissement SSL et connectez-vous avec les identifiants suivants :

Identifiant : ....
Mot de passe : ....

----

## 6. Lancement d’un Scan
Aller dans l’onglet Scans > Tasks

Cliquer sur Wizard pour créer un scan rapide

Remplir les champs :

Nom du scan : scan_vulnérabilités

Cible : 192.168.56.1/24

Scan Config : Full and fast

Start time : Démarrer immédiatement

Cliquer sur Create

----

## 7. Export d’un Rapport
Aller dans l’onglet Scans > Reports

Cliquer sur le rapport voulu

Sélectionner le format :

PDF

Cliquer sur OK pour générer et télécharger le rapport

---

##  8. Résultat attendu

Détection des machines actives sur le réseau

Identification des vulnérabilités (critique, haute, moyenne, faible)

Rapport exportable et réutilisable pour présentation ou archivage





