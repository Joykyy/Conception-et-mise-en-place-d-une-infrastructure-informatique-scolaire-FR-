# Livrable - Configuration des points d'accès

## Liste des équipements utilisés
- Deux points d'accès physique. (AP-D3740-0[1-2])
- Deux câbles reliant la SW-D3740-01 au point d'accès: 
    - port 23 -> AP-D3740-01, port 24 -> AP-D3740-02

## Configuration Vlans sur la switch



```bash
conf t

interface range gigabitEthernet 1/0/23 - 24
switchport mode access
switchport access vlan 85
switchport trunk allowed vlan 40,70,90,85
spanning-tree portfast
end
write memory
```
## Configuration metric
```bash
route change 0.0.0.0 mask 0.0.0.0 192.168.20.1 metric 15
```
## Configuration Network
1. Settings -> Network -> Create New Virtual Network
2. Mettre un nom et VLAN ID pour les VLANs de la topologie.
## Configuration des SSID
1. Settings -> WiFi -> Create New
2. Mettre un nom par exemple: __420-6r1-cboreale-PUBLIC__, __420-6r1-cboreale-PROF__ ou __420-6r1-cboreale-EMPLOYES__
3. Dans l'onglet Network, mettre le bon vlan
4. Pour le réseau publique, on clique sur Advanced (Manual) et le protocole de sécurité, on met __open__

Pour chque point d'accès, nous avons attribué les config suivantes:

Pour 2.4 GHz:
```
AP-D3740-01 : Channel Width : 20, Channel 1, Transmit Power Medium

AP-D3740-02 : Channel Width : 20, Channel 6, Transmit Power Medium
```

Pour 5 GHz:
```
AP-D3740-01 : Channel Width : 40, Channel 36, Transmit Power High

AP-D3740-02 : Channel Width : 40, Channel 40, Transmit Power High
```