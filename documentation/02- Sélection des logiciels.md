# Livrable: Sélection des logiciels

## Tableau des besoins logiciels

Vos besoins logiciels dans un tableau ici...
| Catégorie | Nom du logiciel | Rôle dans l’infrastructure | Pourquoi ce choix ? |
|---------|----------------|---------------------------|--------------------|
| Gestion des accès et mots de passe | Bitwarden | Gestion des mots de passe | Permet la gestion sécuritaire et centralisée. |
| Plateforme de documentation | gitlab + markdown ia: chat+gemini, google sheets | Documentation technique pour l’équipe | Interface colllaboratif et facile de l'utilisation.  |
| Hyperviseur | VMware ESXi | Héberger et gérer nos machines virtuelles de manière sécurisé | Un des logiciels les plus populaire et qui a déjà fait ses preuves. |
| Systèmes d’exploitation desktop| Windows 11 |  systèmes d'exploitation qui sera déployé sur les Destops utilisateurs. | Compatible avec windows server et le plus utilisé en entreprise |
| Systèmes d’exploitation serveur | Windows Server 2022 & Debian 13 | Deux systèmes d'exploitation qui vont permettre d'installer des logiciels et des applications nécessaires à l'infrastructure  | Se sont deux systèmes puissant, avec beaucoup de support technique en ligne et qui offrent un large évantail de compatibilité avec d'autres logiciels. |
| Sauvegarde des données | Powershell & Bash (Cron) | Automatiser la sauvegarde sur les VM Linux et Windows | Se sont les deux principales logiciels d'automatisation des systèmes d'exploitations associés. |
| Supervision et monitoring | Nagios & Splunk | Surveillance des serveurs, services et journaux | Open source, bon pour la détection proactive des incidents et analyse des logs |
| Pare-feu et sécurité réseau | pfSense | Filtrage du trafic réseau et sécurisation des accès | Open source, performant, interface web et fonctionnalités avancées |
| Gestion et déploiement de configurations | Ansible | Ansible est un logiciel qui permet l'automatisation de certaine tâche, et du déploiment de certaines configuration sur plusieurs serveurs de manière simultanée. | C'est utile, car nous allons pouvoir installer plusieurs logiciels ou config sur différents serveurs en une fois, évitant ainsi des répétions inutiles. Par exemple, installer l'agent de monitoring nagios en une fois. |
| Virtualisation et conteneurisation | Docker | Permettre d'isoler certain service, sur une VM ou quelques VM, sans que la panne d'un d'entre eux n'impacte les autres. | Permettre d'économiser les ressources matériels grâce à l'isolations, augmenter la fiabilité, ainsi que la gestion des services.  |
