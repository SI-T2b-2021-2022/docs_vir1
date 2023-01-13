---
description: Machine virtuelle DEBIAN
---

# Laboratoire 5 - Machine Virtuelle Debian

## 1. Énoncé

Une machine est un ensemble de fichiers exécutés par l’hyperviseur. Les processus qui en résultent sont appelés « worlds » au niveau de l’hyperviseur. Les fichiers sont stockés sur les datastores accessibles par les hyperviseurs ESXi.

Pour une machine virtuelle que l’on appellera VM, le répertoire VM sera créé, dans lequel les fichiers suivants seront créés (immédiatement ou pendant la « vie » de la VM) :

* `VM.vmx` : le fichier de configuration qui contient entre autres la configuration matérielle de la VM. C’est un fichier texte où sont inscrits la quantité de mémoire vive, les types de cartes réseau utilisées, le nombre et la configuration des disques, ainsi que d’autres informations comme le nombre et le type de ports série et parallèles, le nombre de processeurs, etc.
* `VM.vmxf` : fichier de configuration étendue. À l’origine prévu pour inclure les informations de VM quand elles font partie d’une « team » (sorte de vApp mais dans VMware Workstation). Le fichier est créé automatiquement pour les VM hébergées sur un serveur ESXi pour assurer la compatibilité avec Workstation.
* `VM.vswp` : le fichier d’échange. Il est créé automatiquement au démarrage de la VM mais n’est utilisé qu’en cas de contention mémoire sur le serveur hôte. Sa taille est égale à la quantité de mémoire vive allouée moins la réservation mémoire configurée.
* `VM.nvram` : le fichier représentant le BIOS de la VM. Il est automatiquement recréé au démarrage de la VM s’il a été effacé.
* Les fichiers de journalisation de l’activité portent l’extension `.log`. Plusieurs (anciens) fichiers log sont présents dans le répertoire de la VM. Le fichier courant est toujours nommé vmware.log. À chaque démarrage de la VM, un nouveau fichier log est créé.
* Le fichier `vmsn` est un fichier créé avec la machine virtuelle, comme descripteur de snapshots.
* Les fichiers `.vmdk` : chaque disque virtuel de la VM est constitué de deux fichiers. L’un est toujours le descripteur, portant par exemple le nom VM.vmdk. Pour les autres fichiers, il s’agit de données : VM-flat.vmdk pour le fichier de disque virtuel, VM-delta.vmdk pour les snapshots et VM-rdm.vmdk si on configure un rdm (raw device mapping ou accès direct au stockage) en lieu et place d’un disque virtuel. Le fichier -rdm.vmdk remplace le -flat.vmdk le cas échéant.
* Les fichiers `VM-####-delta.vmdk`sont les fichiers qui stockent les modifications du disque virtuel si on a fait des snapshots il peut y avoir plusieurs fichiers de ce type pour une seule machine virtuelle.

Comme sur VMware Workstation, nous pouvons créer des machines virtuelles directement sur notre hyperviseur ESXi. La création d’une machine virtuelle dans votre hyperviseur passe auparavant par l’upload de fichiers .iso la banque de données.

* **Transférez l’ISO Debian sur la datastore local de l’`hyperviseur H1`**
* **Effectuez la création d'une machine virtuelle `DEBIAN` directement sur l'`hyperviseur H1`.** (No desktop, RAM 512 megabytes, HDD 2 gigabytes)

## 2. VM Debian

![](../.gitbook/assets/opera\_feppMmRN6d.jpg)

![](../.gitbook/assets/opera\_g7u1GRgsuz.jpg)

![](../.gitbook/assets/opera\_1p1XlfhxxH.jpg)

![](../.gitbook/assets/opera\_YV3m9jD9WS.jpg)

![](../.gitbook/assets/opera\_QDSbc7cJCY.jpg)

![](../.gitbook/assets/opera\_CavrcxIhfW.jpg)

![](../.gitbook/assets/opera\_hGmxN32peV.jpg)

![](../.gitbook/assets/opera\_3ttN71GUNI.jpg)

![](../.gitbook/assets/opera\_Hodm0nNk7Y.jpg)

![](../.gitbook/assets/opera\_R3r8sPXiWQ.jpg)

![](../.gitbook/assets/opera\_EW6wiaBKaC.jpg)

![](../.gitbook/assets/opera\_IGUokWSJrW.jpg)
