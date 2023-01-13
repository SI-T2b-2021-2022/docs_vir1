# Laboratoire 12 - vMotion

## 1. Énoncé

Il existe plusieurs types de migrations :

* La migration à froid (VM éteinte ou dans un état suspendu).
* Les migrations à chaud ou migration avec vMotion. Le vMotion est une fonctionnalité introduite par le vCenter, permettant de déplacer l’emprunte mémoire d’un hyperviseur à l’autre.

Il existe plusieurs types de migration à chaud.

* La migration à chaud d’un hyperviseur à l’autre est appelée vMotion.
* La migration à chaud des fichiers de machines virtuelles d’un datastore à l’autre est appelée storage vMotion.

Ces deux types de migration sont communément appelés simplement vMotion.

_Avant d'effectuer ce laboratoire, assurez-vous que toutes les VM sont allumées_

* **Effectuez un `storage vMotion` des machines virtuelles existantes vers le DataStore `DS_SAN` partagé**

## **2**. Migrer une machine

On fait clique droit sur la machine et on sélectionne "**Migrer"**

![](<../.gitbook/assets/image (47).png>)

Ensuite on sélectionne "**Modifier la ressource de calcul et le stockage**"

![](<../.gitbook/assets/image (72).png>)

On sélectionne ensuite notre node H2

![](<../.gitbook/assets/image (20).png>)

On sélectionne le Stockage partagé donc "**DS\_SAN**"

![](<../.gitbook/assets/image (48).png>)

On garde le réseau des VM

![](<../.gitbook/assets/image (36).png>)

On sélectionne une priorité élevée pour que ce soit plus rapide

![](<../.gitbook/assets/image (50).png>)

Et on finit par le résumé

![](<../.gitbook/assets/image (46).png>)

## 3. Vérification

Et voila notre vm est sur H2

![](<../.gitbook/assets/image (29).png>)
