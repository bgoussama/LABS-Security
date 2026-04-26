# 🔐 MobSF Static Analysis — LAB 6

## 🎬 Demo
<!-- Glissez votre vidéo ici sur GitHub -->

## 📱 Application analysée
- **Nom** : UnCrackable Level 1
- **Package** : owasp.mstg.uncrackable1
- **Score sécurité** : 55/100 (Medium Risk)

## 🛠️ Outils utilisés
- MobSF v4.0.6
- VM Mobexler

## 🔍 Vulnérabilités trouvées
- AES ECB Mode faible (HIGH)
- minSdk=19 trop bas (HIGH)
- allowBackup=true (MEDIUM)
- Insecure Logging (INFO)

## ✅ Points positifs
- 0 trackers détectés
- 0 permissions abusives

## 🚀 Comment reproduire
1. Lancer Mobexler
2. Lancer MobSF via MobSFdocker.sh
3. Ouvrir http://127.0.0.1:8000
4. Uploader UnCrackable-Level1.apk
5. Analyser le rapport
