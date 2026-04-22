# Livrable - Installation et Configuration d’un Contrôleur UniFi

## Caractéristiques de la machine virtuelle
- **Nom de VM** : VM-R4-01
- **Système d'opération** : Ubuntu-24.04.3-live-server-amd64 
- **Adresse IP** : 192.168.80.10

- Pour faire l'installation de Unify sur Ubuntu la version 24.04, c'est-à-dire une version plus récente d'Ubuntu, nous avons utilisé un script. 
- La première commande pour mettre à jour les paquets et installé les dépendances: apt-get update; apt-get install ca-certificates curl -y
- La deuxième commande pour démarrer le scrip d'installation (nous avons suivis les étapes et répondu Yes lorsque nous avions l'option): 

```bash
curl -sO https://get.glennr.nl/unifi/install/unifi-os-server-4.3.6.sh && bash unifi-os-server-4.3.6.sh
```

![alt text](images/10.png)
