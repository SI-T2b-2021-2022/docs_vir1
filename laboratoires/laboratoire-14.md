# Laboratoire 14 - Alarmes

## 1. Énoncé

Les alarmes VMware sont très utiles pour vous avertir d’un dysfonctionnement ou d’un événement qui se produit sur vos hyperviseurs ou vos machines virtuelles. Dans ce laboratoire nous allons donc créer une alarme qui nous prévient quand une machine virtuelle est mise en pause.

* **Créez une `alarme` pour être averti par `mail` lorsque une machine du datacenter est mise en `pause`.**

## 2. Configurer l'envoie de mail

Pour configurer l'envoi d'un mail en cas d'alerte, allez sous **IP vCenter -> Configurer -> Paramètres avancés -> Modifier les paramètres**

![](../.gitbook/assets/Tlo8rtiMah.gif)

On se rend à la page **80**

![](<../.gitbook/assets/image (31).png>)

Puis on modifie

* **mail.smtp.password**
* **mail.smtp.port**
* **mail.smtp.username**

Et changer y les informations concernant votre email

![](<../.gitbook/assets/image (53).png>)

## 3. Définir des alarmes

Cliquer sur la machine dont vous souhaitez mettre une alarme -> **Configurer -> Définitions des alarmes** -> **Ajouter**

![](../.gitbook/assets/3JqUZ95J0B.gif)

Ajoutez y un **nom**, **une description**, ainsi que **le type de la cible**

![](../.gitbook/assets/0EyByvj2df.gif)

Dans cette partie, remplissez les informations comme l'image ci-dessous.

![](<../.gitbook/assets/image (2).png>)

On laisse par défaut les valeurs

![](<../.gitbook/assets/image (14).png>)

Et on créer l'alarme

![](<../.gitbook/assets/image (58).png>)

## 4. Vérification

![](<../.gitbook/assets/image (28).png>)
