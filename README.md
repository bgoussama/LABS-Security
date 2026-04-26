# Rapport d'analyse statique — LAB 6

**Date :** 26/04/2026  
**Analyste :** Oussama Bagy  
**APK :** UnCrackable-Level1.apk  
**Outil :** MobSF v4.0.6 — VM Mobexler  

<img width="643" height="539" alt="image" src="https://github.com/user-attachments/assets/0236e659-a6ac-4ce4-bf62-abc5bb93b87f" />




---

## Score global

**55/100 — Risque Moyen**

<img width="1511" height="489" alt="image" src="https://github.com/user-attachments/assets/96919006-cdf8-419d-836a-2f68fcceab37" />

---

## Vulnérabilités trouvées

| # | Problème | Sévérité |
|---|----------|----------|
| 1 | AES ECB mode faible | Élevée |
| 2 | minSdk=19 trop bas | Élevée |
| 3 | allowBackup=true | Moyenne |
| 4 | Logs sensibles | Info |

<img width="1542" height="484" alt="image" src="https://github.com/user-attachments/assets/8c72b915-7506-4ed3-baf1-0e83557da648" />




---

## Détail des vulnérabilités

**1. AES ECB Mode**  
L'application utilise AES en mode ECB.
Ce mode est faible car il produit le même
résultat pour les mêmes données.  
*Remédiation : utiliser AES GCM*

**2. minSdk trop bas**  
L'app fonctionne sur Android 4.4 (API 19).
Ces versions ne reçoivent plus de mises
à jour de sécurité de Google.  
*Remédiation : minSdk >= 29*

**3. allowBackup=true**  
Les données peuvent être sauvegardées
via ADB par n'importe qui ayant accès USB.  
*Remédiation : allowBackup=false*

**4. Logs sensibles**  
L'app écrit des informations dans les logs
Android visibles par d'autres applications.  
*Remédiation : désactiver en production*

---

## Points positifs

- 0 trackers publicitaires
- 0 permissions dangereuses
- Détection root implémentée

---

## Conclusion

L'application présente 2 vulnérabilités
élevées liées à la cryptographie et à la
configuration. Ces problèmes doivent être
corrigés avant toute mise en production.
