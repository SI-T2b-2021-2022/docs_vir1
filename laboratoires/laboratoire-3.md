---
description: Command-Line Management
---

# Laboratoire 3 - Management ligne de commande

## 1. Énoncé

Sur les serveurs ESX, il était possible de se connecter sur le service console pour lancer des commandes sur l’hyperviseur. L’accès SSH n’a jamais été activé par défaut, tandis que la ligne de commande en local était possible sans autre opération que de se connecter au serveur. Dans les deux cas, l’activation peut se faire sur l’interface DCUI (Direct Console User Interface) du serveur ESXi. VMware conseille de n’utiliser le mode ESXi Shell qu’en cas d’urgence.

[Command-Line Management](https://pubs.vmware.com/vsphere-6-0/index.jsp?topic=%2Fcom.vmware.vcli.migration.doc%2Fcos\_upgrade\_technote.1.1.html)

* **Connectez-vous à la console de service (COS) de l'hyperviseur `H1` via SSH**
* **Exécutez la commande `esxtop`**

ESXTOP est le principal outil de suivi des performances en temps réel pour vSphere. Par défaut, vous visualisez l’utilisation des ressources CPU dès que vous lancez la command esxtop. Avec esxtop, vous pouvez aussi enregistrer les statistiques dans un fichier CSV pour qu’elle soit analysées plus tard. Pour cela vous devez exécuter esxtop en mode batch la commande suivante :

`esxtop -b -d 10 -n 90 >> /vmfs/volumes/DS/non-de-votre-fichier.csv`

* b = mode batch
* d = délai en secondes (10 secondes)
* n = nombre d’échantillons (90 échantillons)
  * **Récupérez votre fichier et visualisez les statistiques via l’outil** [**visualesxtop**](https://labs.vmware.com/flings/visualesxtop)

Attention : si aucun Datastore (banque de données) n'est disponible, rajoutez un disque dur à votre hyperviseur et créez ensuite une nouvelle banque de données à partir de ce disque que vous nommerez DS.

## 2. Laboratoire 2

### 1. Création Datastore

![](../.gitbook/assets/opera\_gTamDldZfc.jpg)

![](../.gitbook/assets/opera\_ZUyEloMRrV.jpg)

![](../.gitbook/assets/opera\_KoHGNxsiWh.jpg)

![](../.gitbook/assets/opera\_IGclrJx4fz.jpg)

![](../.gitbook/assets/opera\_NkQy3B52Vk.jpg)

### 2. Activaton SSH

![](../.gitbook/assets/opera\_3tKIwXGxYI.jpg)

### 3. Commande en SSH

![](../.gitbook/assets/putty\_QKG3ymZrEv.jpg)

![](../.gitbook/assets/putty\_cmHhfuKYFc.jpg)

![](../.gitbook/assets/putty\_VzT5YFtOdi.jpg)

![](../.gitbook/assets/putty\_yllWGBnoF3.jpg)

![](../.gitbook/assets/putty\_c6e6ctpNnr.jpg)
