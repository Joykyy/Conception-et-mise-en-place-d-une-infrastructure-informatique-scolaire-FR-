# Livrable – Plan d’adressage réseau

## 1. Objectif du plan d’adressage

Ce document présente le plan d’adressage IP initial du réseau.  
Il définit les sous-réseaux nécessaires, les VLANs, les plages d’adresses IP, ainsi que les modes d’attribution (statique ou dynamique) pour les équipements et utilisateurs.


## 2. Convention de nommage VLANs

- `VLAN-460` : Fournisseur Internet 
- `VLAN-20` : Administration 
- `VLAN-40` : Réseau Wi-Fi (PROF)  
- `VLAN-60` : Objets connectés (imprimantes,tableaux interactifs)
- `VLAN-70` : Réseau Wi-Fi (VISITEUR)
- `VLAN-80` : DMZ
- `VLAN-85` : Serveurs privés
- `VLAN-90` : Réseau Wi-Fi (ÉTUDIANT)


## 3. Schéma global d’adressage

- **Plage IP privée utilisée :** `192.168.0.0/x`
- **Méthode de segmentation :** VLANs + sous-réseaux dédiés
- **Passerelle par défaut :** première adresse utilisable du sous-réseau


## 4. Tableau du plan d’adressage

## Plan d’adressage réseau

| VLAN-ID  | Nom du VLAN        | Plage d’adresses (CIDR) | Adresse IP de la passerelle | Rôle et utilisation | Mode d’attribution |
|---------|--------------------|-------------------------|-----------------------------|---------------------|--------------------|
| VLAN-460 | INTERNET-ISP       | 206.167.46.0/24         | 206.167.46.24                | Liaison entre le fournisseur Internet et le routeur | Statique |
| VLAN-20  | ADMIN              | 192.168.20.0/24         | 192.168.20.1                | Direction, secrétariat, personnel administratif | Dynamique (DHCP) |
| VLAN-40  | WIFI-PROF          | 192.168.40.0/24         | 192.168.40.1                | Accès Wi-Fi réservé aux enseignants | Dynamique (DHCP) |
| VLAN-60  | IOT                | 192.168.60.0/24         | 192.168.60.1                | Imprimantes et tableaux interactifs | Dynamique (DHCP) |
| VLAN-70  | WIFI-VISITEUR      | 192.168.70.0/24         | 192.168.70.1                | Accès Internet pour les visiteurs | Dynamique (DHCP) |
| VLAN-80  | DMZ                | 192.168.80.0/24         | 192.168.80.1                | Serveurs accessibles depuis Internet | Statique |
| VLAN-85  | SERVEURS-PRIVES    | 192.168.85.0/24         | 192.168.85.1                | Serveurs internes | Statique |
| VLAN-90  | WIFI-ETUDIANT      | 192.168.96.0/20         | 192.168.96.1                | Accès Wi-Fi pour les élèves | Dynamique (DHCP) |

## 5. Attribution des adresses IP

### 5.1 Adresses IP statiques

Les équipements critiques utilisent des adresses IP statiques afin d’assurer une disponibilité et une gestion optimale.

| Équipement | Nom | Adresse IP |
|-----------|-----|------------|
| x | x | 192.168.x.x |



### 5.2 Attribution dynamique (DHCP)

Les postes clients et périphériques non critiques utilisent une attribution dynamique via DHCP.

- **Plages DHCP par VLAN :**

| VLAN | Plage DHCP | Justification |
|------|------------|---------------|
| VLAN-20  | 192.168.20.50 – 192.168.20.200 | Réserve les premières IP pour les équipements critiques et imprimantes. |
| VLAN-40  | 192.168.40.50 – 192.168.40.200 | Suffisant pour tous les enseignants, avec marge pour ajout futur. |
| VLAN-60 | 192.168.60.50 – 192.168.60.200 | Périphériques non critiques (imprimantes, TNI), avec réservations si nécessaire. |
| VLAN-70  | 192.168.70.50 – 192.168.70.200 | Plage temporaire pour visiteurs pour limiter l’impact réseau. |
| VLAN-90  | 192.168.90.50 – 192.168.105.200 | Plage large (/20) pour supporter 3000 étudiants, en réservant les premières IP pour équipements fixes éventuels. |
