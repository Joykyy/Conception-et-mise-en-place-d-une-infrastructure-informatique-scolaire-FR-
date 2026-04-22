# Livrable: Définition d'une convention de nommage

## 1- Description de l'entreprise  
**Nom choisi** : Collège Boréale

**Description de votre entreprise** : Un collège secondaire. 
Le département informatique devra s'assurer de déployer une infrastructure réseau fonctionnelle et sécuritaire à tous les employés et étudiants du collège.

**Combien de succursales** : 1 

**Combien d'employés** : 200



## 2- Nom de domaine interne et internet  
- **Nom de domaine interne** : it.cboreale.space
- **Nom de domaine externe** :  cboreale.space
- **Fournisseur DNS** : NameCheap

## 3- Convention de nommage  

Élaborer une convention de nommage couvrant les éléments suivants :

- Serveurs physiques et virtuels
- Commutateurs et routeurs
- Points d’accès Wi-Fi
- Postes de travail
- Volumes de stockage 
- Utilisateurs
- Machines virtuelles dans le cloud 
- Étiquetage de vos fils CAT6 Rj45

Définir une structure de nommage claire et uniforme, incluant les éléments suivants :

- Préfixe ou suffixe distinctif pour identifier le rôle de l’équipement (ex. : SRV, VM, SW, RTR, etc.).
- Localisation si nécessaire (ex. : MTL pour Montréal, QC pour Québec).
- Numérotation cohérente pour différencier plusieurs instances d’un même type.
- Présenter votre convention sous forme de tableau, avec une colonne expliquant la logique derrière chaque type de nom.


**Remplissez le tableau suivant.**

| **Type d’équipement** | **Convention de nommage** | **Justificatif** |
|----------------------|------------------------|------------------------|
| Serveurs physiques  | SRV-EMPLACEMENT-NUMERO | Ajouter l'emplacement (numéro de local ou cloud), ainsi qu'un numéro d'identification vont faciliter l'administration. |
| Machines virtuelles | VM-ID_Role-INSTANCE | Identifier le rôle des VMs avec R (rôle) et un numéro va permettre d'identifier les rôles de manière confidentielle et assigner une instance permettera d'identifier de maniere unique des serveurs de mêmes types (exemple, leur backup) Par exemple, VM-A1-1 est la vm AD principale, VM-A1-2 est son backup. *Voir légende|
| Commutateurs        | SW-EMPLACEMENT-NUMERO | Numéroter les switchs avec l'emplacement (numéro de local)|
| Routeurs            | RTR-EMPLACEMENT-NUMERO | Numéroter les routeurs |
| Points d’accès WiFi | AP-EMPLACEMENT-NUMERO | Identifier l'emplacement du point d'accès pour identifier la zone desservie. |
| Noms d'utilisateurs administratif | PNOMX | Identification unique des employés qui leur donne accès aux ressources de l'école. On utilise la première lettre du prenom et les cinq premières lettres du nom. Si deux identifiants sont identiques, on ajoute un numéro à la fin, d'où le X à la fin.|
| Noms d'élèves | eMatricule | Permet aux élèves de recevoir un identifiant unique qui leur donne accès aux ressources de l'école. |
| Volumes de stockage  | VOL-EMPL_SRV-NUMERO | Identifier l'emplacement des volumes sur les différents serveurs  |
| Poste de travail  | PC-EMPL-NUM | Identifier l'emplacement dans l'établisement des différents postes. |
| Imprimantes  | IMP-DEPARTEMENT-NUMERO | Identifier le département des différentes imprimantes pour avoir une idée de l'emplacement et de qui y a accès. |
| Étiquetage des fils CAT6 Rj45  | Nom de l'équipement connecté | Identifier à quoi le câble est connecté |
---
---
* Légende
    Rôle et code associé: nous séparons les rôles par catégorie. 
    Catégories:
    - A = Annuaire
        - AD = 1
    - R = Réseau
        - DNS = 1
        - DHCP = 2
        - PfSense = 3 
        - UniFi = 4
    - D = données
        - Veeam= 1
    - S = Sécurité 
        - VPN = 1
        - Journalisation = 2
    - G = Gestion:
        - Serveur de sauvegarde = 1
        - Nagios = 2
        - Splunk = 3
        - Portail Étudiant = 4
        - Ansible = 5
    
    PS: pour chaque logiciel utilisé, l'ajouter à cette légende si pas déjà dedans.
    EMPLACEMENT: numéro de local
