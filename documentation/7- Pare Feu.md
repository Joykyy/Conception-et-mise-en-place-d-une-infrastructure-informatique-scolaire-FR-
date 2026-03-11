
# Livrable - Installation et configuration du Routeur pare-feu Virtuel  

## Objectif  
L’objectif de ce livrable est d’installer et configurer une **machine virtuelle jouant le rôle de routeur** pour l’entreprise, en utilisant un logiciel tel que **pfSense**. Cette machine doit gérer le **routage entre plusieurs VLANs** et appliquer des **règles de filtrage du trafic** pour assurer la sécurité et la segmentation du réseau.  


## Consignes  

### 1. Installation et paramétrage initial  
- Déployer une **machine virtuelle dédiée au routage** (ex: pfSense, OPNSense, VyOS, Forti VM) sur l’hyperviseur choisi.  
- Configurer les **paramètres de base** :  
  - Nom de la machine  VM-R3-01
  - Accès distant sécurisé HTTPS

### 2. Configuration des interfaces réseau  
- Chaque VLAN doit être associé à une **interface spécifique** du routeur virtuel.  
- Au minimum, les VLANs suivants doivent être définis :  
  - WAN (accès à Internet)  
  - Admin (réseau de gestion)  
  - Wi-Fi (réseau sans fil des utilisateurs)  
  - DMZ (réseau des serveurs accessibles depuis l’extérieur, si applicable)  

### 3. Règles de trafic et filtrage  
- Définir des **politiques de routage** entre les VLANs.  

<mark>Les règles de pare-feu peuvent attendre la fin du projet</mark>
ATTENTION: Vous ne devez configurer aucune règle autorisant l'accès TCP80/443 sur l'interface WAN de PFSENSE.
<!--
- Configurer les **règles de pare-feu** selon les besoins de l’entreprise :  
  - Autoriser ou bloquer certains flux entre les VLANs.  
  - Contrôler l’accès à Internet pour les utilisateurs.  
  - Limiter les connexions aux services critiques (ex : SSH uniquement pour l’Admin VLAN).  
-->

### 4. Documentation des paramètres du routeur
Produisez un fichier Markdown nommé `livrable12-pare-feu.md` qui contient cette section. Déposez ce fichier dans le dossier **documentation** dans GitLab.

- **Informations générales du routeur**  
  - Nom de la machine  : `votre-hostname.fqdn`
  - Système installé : pfSense CE 2.7.2

- **Configuration des interfaces**  

| Interface | VLAN-ID | Réseau associé | Adresse IP | Passerelle |
|------------|----------|----------------|------------|------------|
| WAN | VLAN-460 | 206.167.46.0/24 | 206.167.46.24 | 206.167.46.1 |
| ADMIN | VLAN-20 | 192.168.20.0/24 | 192.168.20.1 | — |
| WIFI-PROF | VLAN-40 | 192.168.40.0/24 | 192.168.40.1 | — |
| IOT | VLAN-60 | 192.168.60.0/24 | 192.168.60.1 | — |
| WIFI-VISITEUR | VLAN-70 | 192.168.70.0/24 | 192.168.70.1 | — |
| DMZ | VLAN-80 | 192.168.80.0/24 | 192.168.80.1 | — |
| SERVEURS-PRIVES | VLAN-85 | 192.168.85.0/24 | 192.168.85.1 | — |
| WIFI-ETUDIANT | VLAN-90 | 192.168.96.0/20 | 192.168.96.1 | — |


- **Configuration des services**  
  - DNS interne, DHCP, ... 

  ```
  Service DHCP activé sur les VLANs suivantes:

  VLAN-20 (ADMIN)
  VLAN-40 (WIFI-PROF)
  VLAN-60 (IOT)
  VLAN-70 (WIFI-VISITEUR)
  VLAN-90 (VLAN-90)
  ```

  - Accès distant 

  ```
  Avec le WEB 
  ```

- **Sauvegarde de la configuration**  
  ```
  Sauvegarde du mot de passe _admin_ dans BitWarden.
  Exporter la configuration au format XML et l’ajouter au dépôt GitLab dans *Documentation*
  ```

