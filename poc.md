# POC

## Proof Of Concept

### **Etat des machines au début du POC**

* Hyperviseur H1 - `ON`
* Hyperviseur H2 - `ON`
* OpenFiler SAN - `ON`
* VM Debian - `ON` _(Fichiers sur DATASTORE SAN / Processus sur H2)_
* VM Windows 10 - `ON` _(Fichiers sur le second DATASTORE de H1 / Processus sur H1)_

### Grille d'évaluation

| PT Max | Fait ?      | Tâche à exécuter                                                                          |
| ------ | ----------- | ----------------------------------------------------------------------------------------- |
| 1      | ✅           | Hyperviseur H1 → Installation ESXi (NAT/HostOnly)                                         |
| 1      | ✅           | Hyperviseur H1 → eth0 (NAT) - Admin 192.168.xxx.130 STATIC                                |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | Hyperviseur H1 → Connexion SSH depuis machine local W10                                   |
| 1      | ✅           | Hyperviseur H1 → ISO Debian dans un datastore sur H1                                      |
| 1      | ✅           | Hyperviseur H1 → Ajout d’un second DATASTORE                                              |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | Hyperviseur H2 → Installation ESXi (NAT/HostOnly)                                         |
| 1      | ✅           | Hyperviseur H2 → eth0 (NAT) - Admin 192.168.xxx.140 STATIC                                |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | Hyperviseur H1 → VM vCenter Server Appliance                                              |
| 1      | ✅           | vCenter Server Appliance → 192.168.xxx.150 STATIC                                         |
| 1      | ✅           | vCenter Server Appliance → Web Client depuis la machine W10 locale                        |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | OpenFiler SAN → Installation ESXi (NAT/HostOnly)                                          |
| 1      | ✅           | OpenFiler SAN → eth0 (NAT) - Admin 192.168.xxx.160 STATIC                                 |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | OpenFiler SAN → eth1 (HostOnly) - 10.10.10.160 STATIC                                     |
| 1      | ✅           | H1 iSCSI→ eth1 (HostOnly) - 10.10.10.130 STATIC                                           |
| 1      | ✅           | H2 iSCSI→ eth1 (HostOnly) - 10.10.10.140 STATIC                                           |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | DATASTORE SAN → LUN accessible par H1 et H2                                               |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | VM Debian → Sur DATASTORE SAN                                                             |
| 1      | ✅           | VM Debian → Open VMware Tools                                                             |
| =      | =========== | ===========================================                                               |
| 1      | ✅           | Hyperviseur H1 → VM Windows 10 sur second DATASTORE                                       |
| 1      | ✅           | VM Windows 10 → VMware Tools                                                              |
| 2      | ✅           | VM Windows 10 → Mise en pause - Alarme par mail nom.prenom@cpnv.ch                        |
| =      | =========== | ===========================================                                               |
| 6      | ✅           | Hyperviseur H2 Power OFF - Automatiquement la VM Debian est redémarrée sur Hyperviseur H1 |
| 6      | ✅           | Hyperviseur H2 Power ON - Automatiquement la VM Debian retourne sur Hyperviseur H2        |
| 2      | ✅           | Backup VM Debian - Suppression VM Debian - Restauration VM Debian                         |
| ===    | =========== | ===========================================                                               |

{% hint style="info" %}
Total : **36 points**
{% endhint %}
