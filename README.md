# Rapport d'analyse statique — UnCrackable Level 1

**Date :** 26/04/2026
**Analyste :** Oussama Bagy
**APK :** UnCrackable-Level1.apk
**SHA256 :** 1da8bf57d266109f9a07c01bf7111a975ce01f190b9d914bcd3ae3dbef96f21
**Outil :** MobSF v4.0.6 dans VM Mobexler

<img width="1568" height="446" alt="image" src="https://github.com/user-attachments/assets/c594adf5-fb50-46e2-8f01-0ae406632a55" />

<img width="1568" height="386" alt="image" src="https://github.com/user-attachments/assets/77c1dca3-025b-4797-8c5b-7362a45d4e8b" />


---

## Résumé exécutif

L'analyse statique révèle un niveau de risque MOYEN (55/100).
Les principales vulnérabilités concernent :
- AES ECB mode faible (cryptographie insuffisante)
- minSdk=19 trop bas (Android vulnérable)
- allowBackup=true (vol de données possible)

---

## Vulnérabilités identifiées

### Constat #1 : AES ECB Mode faible
**Sévérité :** Élevée 🔴
**MASVS :** MSTG-CRYPTO-2
**CWE :** CWE-327
**Description :** AES ECB produit le même
chiffré pour les mêmes blocs
**Localisation :** sg/vantagepoint/a/a.java
**Impact :** Patterns visibles dans les données
**Remédiation :** Utiliser AES GCM ou CBC

### Constat #2 : minSdk trop bas
**Sévérité :** Élevée 🔴
**MASVS :** MSTG-ARCH-1
**Description :** minSdk=19 (Android 4.4)
versions non supportées par Google
**Localisation :** AndroidManifest.xml
**Impact :** Exploitation de failles non corrigées
**Remédiation :** Mettre minSdk >= 29

### Constat #3 : allowBackup=true
**Sévérité :** Moyenne 🟡
**MASVS :** MSTG-STORAGE-8
**Description :** Sauvegarde ADB activée
**Localisation :** AndroidManifest.xml
**Impact :** Vol de données via adb backup
**Remédiation :** Mettre allowBackup=false

### Constat #4 : Insecure Logging
**Sévérité :** Info 🔵
**MASVS :** MSTG-STORAGE-3
**CWE :** CWE-532
**Description :** Informations dans les logs
**Localisation :** sg/vantagepoint/uncrackable1/a.java
**Impact :** Fuite d'informations sensibles
**Remédiation :** Désactiver logs en production

---

## Points positifs

- Trackers : 0/433 ✅
- Permissions abusives : 0/24 ✅
- Root detection implémentée ✅

---

## Recommandations prioritaires

1. Remplacer AES ECB par AES GCM
2. Augmenter minSdk à 29 minimum
3. Désactiver allowBackup en production
4. Supprimer les logs sensibles

---

## Annexes

### Permissions demandées
- Aucune permission dangereuse

### Composants exportés
- MainActivity (via intent-filter)

### Score MobSF
- Security Score : 55/100
- Risk Rating : Medium Risk
- Grade : B
