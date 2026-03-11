# Livrable - Installation de l'hyperviseur


## Documentation de l’Installation d’un Hyperviseur  



### 1. Informations générales  
- **Nom de l’hyperviseur** : VMware ESXi  
- **Version et build installés** : 8.0.0   
- **Serveur hôte** : Dell PowerEdge R260  

---

### 2. Paramètres d’installation  
- **Médium utilisé** : ISO sur clé USB
- **Mode de déploiement** : Installation sur disque local
- **Taille du stockage alloué pour les VM** : 1.69 To
- **Mode de partitionnement** : GPT
- **Configuration du mot de passe administrateur/root** : 4jRXhcDiDPka?B

---

### 3. Configuration réseau initiale  
- **Adresse IP de gestion** : 192.168.20.3 
- **Passerelle par défaut** : 192.168.20.1 
- **Serveurs DNS** : 8.8.8.8, 1.1.1.1  
- **Mode d’attribution** : Statique
- **Nom d’hôte** : cboreale.local

---

### 4. Configuration matérielle de l’hyperviseur  
- **Processeur** : 8 CPUs x Intel(R) Xeon(R) E E-2468 
- **Mémoire vive (RAM)** : 31.83 GB 
- **Stockage total** : 1.69 TB  
- **Cartes réseau et configuration** : vmnic0, auto negotiate 1000 mbps, full duplex switch

---

### 5. Paramétrage post-installation  
- **Activation des accès distants** : Console Web   
- **Configuration des datastores** : Stockage Local

