---
description: vCenter Server Appliance
---

# Laboratoire 9 - vCenter Appliance

## 1. Énoncé

vCenter est un outil de gestion ayant pour fonction la gestion de plusieurs hyperviseurs et des éléments liés. Ces objets (machines virtuelles, hyperviseurs, répertoires, etc.) sont des objets de l’inventaire vCenter. La configuration et les statistiques des objets de l’inventaire sont consignés dans une base de données qu’utilise vCenter.

Considérons les actions les plus courantes effectuées sur un environnement de virtualisation à savoir :

* Créer une machine virtuelle
* Installer le système d’exploitation invité
* Supprimer une machine virtuelle
* Configurer l’accès au stockage
* Configurer le réseau virtuel

Est-il possible de se passer de vCenter ? Bien sûr, mais ces opérations sont les plus basiques. vCenter permet d’effectuer ces actions sur plusieurs hyperviseurs. Le fait de les avoir dans le même inventaire est un premier pas vers l’uniformisation des configurations.

On parle d’import et non d’installation pour une appliance virtuelle car de manière assez basique, on télécharge le fichier voulu chez l’éditeur (pour vCenter c’est évidemment VMware), on se connecte à un hyperviseur pour y transférer les fichiers. Ensuite, on doit répondre à certaines questions, enregistrer des paramètres. Tout ceci est prévu dans le script de déploiement de l’appliance. Ce script est généralement contenu dans le fichier ovf, les autres fichiers présents étant les disques virtuels.

Dans la version vSphere 6, l’import se fait absolument à partir d’un système Microsoft Windows. Dans le cadre de l’import du VCSA en version 6.5, il est possible d’utiliser Windows, Linux ou Mac OS.

* **Importez VMware vCenter Server Appliance VCA sur l’hyperviseur `H1`.**
* **Connectez à `vCenter` via la base SSO afin de configurer les accès au vCenter.**
* **Créez un Datacenter (centre de données) et placez l'hyperviseur `H1` à l’intérieur de ce Datacenter**

## 2. synchronisation heure NTP

### 1. Ajouter server vmware

Pour commencer il nous faut synchroniser notre serveur ESXi avec un serveur NTP. Pour ce faire nous devons nous connecter en SSH à la machine H1. (Comme vu dans[ laboratoire 3](laboratoire-3.md#2-activaton-ssh))

Une fois connecté en SSH il faut édité le fichier "**/etc/ntp.conf**"

![](../.gitbook/assets/IJFGKbOtJC.gif)

Pour y ajouter la ligne : "**server time.vmware.com**". Enregistrez et fermez l'éditeur de texte.

### 2. Activation du service sur ESXi

Maintenant, retournons sur la page d'administration de ESXi. Ensuite nous devons allez dans **Manage > Services** et il nous faut démarer le service ntpd.

![](../.gitbook/assets/shgxiLnygu.gif)

## 3. Installation vCenter

### 1. Stage 1

Bien, maintenant il nous faut exécuter le fichier intaller.exe

![](../.gitbook/assets/installer\_LeB4zpNHRn.png)

On continue simplement en faisant "**Next**"

![](../.gitbook/assets/installer\_vd9aiRtlTA.png)

Ensuite on accepte les termes

![](../.gitbook/assets/installer\_d85SQg6ae5.png)

Maintenant il nous faut entrer les données de connexion de notre hôte ESXi.

> ESXi host or vCenter Server name : **10.10.34.2**\
> \*\*\*\*User name : **root**\
> \*\*\*\*Password : (Le mot de passe définit à l'installation.)

{% hint style="info" %}
Il faudra également accepter la mise en garde pour le SSL (Voir screen2)
{% endhint %}

![](../.gitbook/assets/installer\_kTShLcsVK5.png)

![](../.gitbook/assets/installer\_EjeAs4a1km.png)

Ensuite il nous faut donner un nom ainsi qu'un nouveau mot de passe au vCenter.

> VM Name : **vCenter-H1**\
> Set root password : **Pa\$$w0rd**

![](../.gitbook/assets/installer\_H0vHGpDyfE.png)

Maintenant on choisit la taille de notre vCenter. Ce sera une petite infra, donc : **Tiny**

![](../.gitbook/assets/installer\_6jhdU42sBa.png)

Ensuite on choisit le datastore que nous voulons utiliser. Donc notre **DS\_02**.

{% hint style="warning" %}
Ne pas oublier de cocher "**Enable Thin Disk Mode**" sinon l'installation ne pourra se faire.
{% endhint %}

![](../.gitbook/assets/installer\_2B36dqgqQh.png)

Ensuite on configure le réseau du vCenter

![](../.gitbook/assets/installer\_OjL8CgUnI6.png)

Petit résumé de la configuration

![](../.gitbook/assets/installer\_jLzjphauyV.png)

Et maintenant on attend

![](../.gitbook/assets/installer\_lnZ714Zx8c.png)

Voilà !

![](../.gitbook/assets/installer\_IO7UwY0Mv5.png)

### 2. Stage 2

Maintenant que c'est installé il faut le configuré.

![](../.gitbook/assets/installer\_umhJbS4dDG.png)

Maintenant on laisse les paramètres pas défauts.

![](../.gitbook/assets/installer\_EPBy3rsAWe.png)

Ensuite on créer la configuration SSO

![](../.gitbook/assets/installer\_HPHPRGLGOC.png)

Ensuite on décoche la case car nous ne voulons pas envoyer de données à VmWare

![](../.gitbook/assets/installer\_epioYhhCV0.png)

Et voilà, petit résumé de la configuration

![](../.gitbook/assets/installer\_hR6f8Mlimh.png)

{% hint style="warning" %}
Attention, une fois le processus lancé il ne pourra être arreté.
{% endhint %}

![](../.gitbook/assets/installer\_9bwd4okGlL.png)

Puis on attend

![](../.gitbook/assets/installer\_AqN4rDQe27.png)

Voilà

![](../.gitbook/assets/installer\_4FbDUsFiOK.png)

## 4. Vérification

On essaye de se connecter au vsphere

![](../.gitbook/assets/opera\_n5vLSLNJyj.png)

## 5. Création d'un datacenter

### 1. Création du datacenter

On commence pas créer un nouveau Datacenter

![](../.gitbook/assets/00O2J0wXqq.gif)

### 2. Ajout d'hôte ESXi dans le datacenter

On commence en faisant clique droit sur "**Ajouter un hôte**"

![](<../.gitbook/assets/image (22).png>)

Ensuite on entre l'addresse IP de l'ESXi

![](<../.gitbook/assets/image (70).png>)

On rentre le compte root de l'ESXi

![](<../.gitbook/assets/image (72).png>)

On accepte que le certificat n'est pas verifié

![](<../.gitbook/assets/image (14).png>)

On reçoit un petit résumé de l'hôte ESXi

![](<../.gitbook/assets/image (69).png>)

On laisse la licence d'éval

![](<../.gitbook/assets/image (67).png>)

On laisse le mode de verrouillage sur "**Désactivé**"

![](<../.gitbook/assets/image (46).png>)

On a qu'un seul DC donc rien à changé ici

![](<../.gitbook/assets/image (40).png>)

Puis on finit

![](<../.gitbook/assets/image (45).png>)

Voilà notre hôte

![](<../.gitbook/assets/image (54).png>)

{% hint style="info" %}
Refaire la même manipulation pour **H2**
{% endhint %}
