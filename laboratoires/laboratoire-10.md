# Laboratoire 10 - Hyperviseur H2

## 1. Énonce

* **Créez un deuxième `hyperviseur H2`** _(Deux interfaces réseau seront configurées pour cet hyperviseur, la première en NAT la seconde en HOST ONLY)_
*   **Rattachez l'hyperviseur `H2` au Datacenter précédemment créé sur votre vCenter Server**

    `Memory : 4 Gb`

    `Processors : 2`

    `Hard Disk (SCSI) : 40 GB`

    `Hard Disk (SCSI) : 100 GB`

    `Network Adapter 1 : NAT (IP Static 192.168.XXX.140/24)`

    `Network Adapter 2 : Host Only (IP Static 10.10.10.140/16)`

    `Hostname : srv-esxi-02`

## 2. Installation ESXi

Suivre le tuto d'installation du premier ESXi

{% content-ref url="laboratoire-1.md" %}
[laboratoire-1.md](laboratoire-1.md)
{% endcontent-ref %}

Tout en remplacement l'ip de l'ESXi H1 évidemment.
