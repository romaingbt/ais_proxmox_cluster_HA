# ais_proxmox_cluster_HA
Déploiement d'un cluster Proxmox VE à 3 nœuds avec stockage partagé NFS et Haute Disponibilité

# ⚡ Cluster Proxmox VE à Haute Disponibilité (HA) & Stockage NFS

## 📋 Présentation du projet
Ce projet réalisé dans le cadre de ma formation consiste à concevoir et déployer une infrastructure virtualisée haute disponibilité à l'aide de **Proxmox VE**. 

L'objectif est d'assurer la continuité de service d'une application critique (serveur web) même en cas de panne matérielle ou de perte d'un nœud du cluster.

## 🏗️ Architecture & Environnement technique
* **Virtualisation :** VMware Workstation (pour simuler l'infrastructure hôte).
* **Nœuds du Cluster :** 3 serveurs Proxmox VE (`pve-01`, `pve-02`, `pve-03`).
* **Stockage Partagé :** Serveur Debian sous `nfs-kernel-server`.
* **Machine Virtuelle test :** VM Debian hébergeant un serveur web Apache (VM ID 100).

## ⚙️ Étapes de mise en œuvre

1. **Préparation du réseau et résolution DNS :**
   * Édition du fichier `/etc/hosts` sur chaque nœud pour lier les adresses IP et les noms d'hôtes (`192.168.100.10` à `12`).
   * Validation de la connectivité croisée par tests de ping par nom d'hôte.

2. **Création du Cluster et Stockage Partagé :**
   * Initialisation du cluster principal sur `pve-01` et ajout des nœuds `pve-02` et `pve-03`.
   * Déploiement d'un stockage NFS centralisé sur Debian pour accueillir les images ISO et servir de datastore commun indispensable à la Haute Disponibilité.

3. **Mise en place de la Haute Disponibilité (HA) :**
   * Déploiement d'une VM Web sur le cluster.
   * Activation du service de Haute Disponibilité (HA / Quorum).
   * **Test de bascule :** Coupure volontaire du nœud principal (`pve-01`). Constat de la relance automatique et transparente de la VM web sur le nœud survivant (`pve-02`), validant le bon fonctionnement du cluster.

---
📁 *Infrastructure virtualisée et validée en environnement de laboratoire.*
