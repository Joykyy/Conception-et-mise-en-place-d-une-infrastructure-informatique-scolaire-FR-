# livrable - Configuration initiale du commutateur


## Documentation du commutateur  

### 1. Informations générales  
- **Modèle et version du firmware** : Cisco Catalyst 9200, firmware 
- **Nom du commutateur (hostname)** : SW-D3740-01  
- **Adresse IP de gestion** : 192.168.20.2/24
- **Passerelle par défaut** : 192.168.20.1  
- **Serveurs DNS** : 8.8.8.8, 1.1.1.1, 192.168.85.2 
- **Mode d’administration** : accès via console, par SSH, MobaXterm  



### 2. Configuration des VLANs 
#### Liste des VLANs créés  
```
# Configurez uniquement les VLAN du siège social
# Noms et VLAN ID conformes à votre plan d'adressage.
VLAN 460 - INTERNET-ISP (206.167.46.0/24)
VLAN 20 - Admin (192.168.20.0/24)
VLAN 40 - WIFI-PROF (192.168.40.0/24)
VLAN 60 - IOT (192.168.60.0/24)
VLAN 70 - WIFI-VISITEUR (192.168.70.0/24)
VLAN 80 - DMZ (192.168.80.0/24)
VLAN 85 - SERVEURS-PRIVES (192.168.85.0/24)
VLAN 90 - WIFI-ETUDIANT (192.168.90.0/24)
```

#### Assignation des ports VLAN  
```
Assignation initiale des ports
Interface gi1/0/1 (SERVEUR) → VLAN 20
Interface gi1/0/2 (TOPOFRACK) → VLAN 460
Interface gi1/0/3 (PC) → VLAN 20
```

### 3. Configuration des Trunks  
#### Interfaces en mode Trunk et VLANs autorisés  
```
Interface Gig1/0/2 (Trunk (toR <-> SWITCH))
VLANs autorisés : 460
Interface Gig1/0/1 (Trunk (SERVEUR <-> SWITCH))
VLANs autorisés : 460, 20, 40,60,70,80,85,90
```



### 4. Sécurisation et gestion des accès  
#### Activation et sécurisation de l’accès SSH  
```
ip domain-name cboreale.local
username admin privilege 15 secret *4%BZV1VTv7q!@
crypto key generate rsa modulus 2048
ip ssh version 2
line vty 0 15
login local
transport input ssh
exec-timeout 10 0
exit
end
write memory
```

#### Configuration de la protection contre les boucles (STP)  
```
configure terminal

*STP rapide pour tous les VLANs 
spanning-tree mode rapid-pvst
spanning-tree vlan 1-4094 priority 4096
spanning-tree vlan 1-4094 root primary


*Ports d'accès 
interface range Gi1/0/3-48
 spanning-tree portfast
 spanning-tree bpduguard enable
 spanning-tree loopguard default
 storm-control broadcast level 5.00
 storm-control multicast level 5.00
 storm-control unicast level 5.00


* Uplink / Trunk vers le reste du réseau 
interface Gi1/0/2
 no spanning-tree portfast
 spanning-tree guard root
 spanning-tree loopguard default

interface Gi1/0/1
 no spanning-tree portfast

end
write memory


```



### 5. Sauvegarde et exportation de la configuration  
- **Emplacement du fichier de configuration** : _GitLab > Documentation > `startup-config.txt`_  

