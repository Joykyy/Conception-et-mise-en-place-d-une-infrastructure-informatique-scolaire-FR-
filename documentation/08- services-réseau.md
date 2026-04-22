# Livrable - Installation des serveurs et des services réseau  

 

### Informations générales des serveurs dans le plan d'adressage  
- Liste des serveurs installés et leur rôle  
- Adresses IP et VLAN attribués  

 Windows Server 2022 sert de Active directory et de DNS interne
 
 Une machine Linux Debian 11 dans la DMZ (vlan 80) pour héberger la page web du portail étudiant du collège.
 

### Configuration Active Directory  
- Structure des OU (Unités Organisationnelles)  
- Comptes utilisateurs créés et leurs rôles  
- Groupes et stratégies appliquées  

 Nom domaine privé: it.cboreale.space
 NetBios: CBIT

- Unités organisationnelles créées:
 - Etudiants (tous les étudiants font partie de cette OU), Enseignants, Tech, Ordinateurs, Administration

- Compte Enseignant
- Compte Élèves:
  Jonh Doe

 Pour ajouter un étudiant, utiliser le script etudiant_nommage.ps1 pour attribuer automatiquement un matricule unique

- Compte technicien
Groupe Tech_Admin_domaine (administrateur du domaine dans l'OU TECH):
Jeanne Lavoie
Joseph Hoang
Ashtonn Kabore

- Compte administrateur (ex Directeur, Secrétaire)


### Configuration DNS  
- cboreale.space = 206.167.46.1
  Les enregistrements des machines linux sont ajoutées manuellement. Par exemple, VM-G4-01 <-> 192.168.80.3


### Configuration DHCP sur le PFsense

| VLAN | Plage DHCP | 
|------|------------|
| VLAN-20  | 192.168.20.100 – 192.168.20.200 
| VLAN-40  | 192.168.40.100 – 192.168.40.200 
| VLAN-60 | 192.168.60.100 – 192.168.60.200  
| VLAN-70  | 192.168.70.100 – 192.168.70.200 
| VLAN-90  | 192.168.90.100 – 192.168.105.200 

### Configuration du serveur web  
- Logiciel utilisé: Apache
- Chemin du fichier HTML hébergé: /var/www/html/index.html 
- Nom de domaine configuré et résolution DNS: https://cboreale.space  
- Certificat SSL/TLS installé et statut HTTPS: Certbot-
```bash
#Installation WEBSERVEUR
sudo apt update
sudo apt install apache2
#Allow le Port HTTPS
sudo ufw allow 443
sudo ufw restart
#Installation de la génératrice de clé SSL/TLS
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache -d cboreale.space -d www.cboreale.space
```
