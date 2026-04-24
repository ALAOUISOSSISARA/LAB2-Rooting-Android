# LAB 2 — Rooting Android — Rapport Complet
**Date :** 24/04/2026
**Auteur :** hp
**Support :** AVD Pixel 5 — API 30 AOSP
**App :** SpaceMissionControl v1.0

---

# Étape 8 — AVB (Android Verified Boot 2.0)
AVB ajoute une vérification d'intégrité moderne sur chaque partition via des hashtrees.
La protection anti-rollback empêche de revenir à une ancienne version vulnérable du système.
Sur notre AVD : verifiedbootstate=orange = AVB contourné par le root.

---

# Étape 9 — Définition du Rooting
1. Root = privilèges super-utilisateur (uid=0), accès total au système
2. Cela modifie les protections système et invalide la chaîne de confiance
3. Utile en laboratoire pour observer les comportements système normalement cachés
4. Risqué : nécessite isolement + traçabilité + reset obligatoire en fin de séance

---

# Étape 10 — Intérêt Labo (non opérationnel)
En labo autorisé uniquement, un environnement privilégié peut aider à :
- Observer des artefacts système normalement inaccessibles
- Analyser les comportements runtime de l'application à bas niveau
- Tester la robustesse du stockage face à un attaquant privilégié

---

# Étape 11 — Matrice de Risques
| # | Risque | Impact |
|---|--------|--------|
| 1 | Intégrité non garantie | Conclusions biaisées sur la sécurité réelle |
| 2 | Surface d'attaque accrue | Exposition si appareil sort du labo |
| 3 | Données sensibles exposées | Violation potentielle de confidentialité |
| 4 | Instabilité système | Tests non reproductibles |
| 5 | Mélange comptes perso/test | Fuite d'informations personnelles |
| 6 | Mauvais nettoyage | Persistance de données sensibles |
| 7 | Réseau non isolé | Effets involontaires sur systèmes externes |
| 8 | Traçabilité insuffisante | Impossible de reproduire les tests |

---

# Étape 12 — Mesures Défensives
| # | Mesure |
|---|--------|
| 1 | Réseau isolé pour éviter toute communication non contrôlée |
| 2 | Données fictives uniquement |
| 3 | AVD dédié exclusivement aux tests |
| 4 | Wipe en fin de séance |
| 5 | Journal de configuration détaillé |
| 6 | Aucun compte personnel |
| 7 | Contrôle strict des APK installées |
| 8 | Horodatage + captures pour traçabilité complète |

---

# Étape 13 — OWASP MASVS
1. STORAGE-1 : Les données sensibles doivent être stockées avec chiffrement approprié
2. NETWORK-1 : Les communications doivent utiliser TLS avec vérification des certificats

---

# Étape 14 — OWASP MASTG
1. Vérifier /data/data/[package]/shared_prefs/ pour données sensibles en clair
2. Analyser adb logcat pour détecter des fuites d'informations pendant l'exécution

---

# Étape 15 — Commandes de Rooting (synthèse)
adb devices                              # Vérifier connexion
adb root                                 # Activer mode root
adb remount                              # Monter system en R/W
adb shell id                             # Vérifier uid=0
adb shell getprop ro.boot.veritymode     # État verity
adb shell getprop ro.boot.verifiedbootstate  # État verified boot

---

# Étape 16 — Fiche Environnement
- Date : 24/04/2026 15:50
- Auteur : hp
- Support : AVD Pixel 5 API 30 AOSP
- Version Android : 11.0 (R)
- App : SpaceMissionControl v1.0
- Scénarios : Load Satellite Feed / Orbital Calculation / Ping Control Tower
- Observations : uid=0 confirmé, verifiedbootstate=orange, remount succeeded
- Limites : su -c non fonctionnel sur AOSP émulateur
- Reset effectué : A faire en fin de séance

---

# Étape 19 — Livrables
- Definition rooting : 4 phrases (voir étape 9)
- Chaine de confiance : ROM > Bootloader > Kernel > System > Apps
- 8 risques + 8 mesures : voir étapes 11 et 12
- MASVS : 2 exigences (voir étape 13)
- MASTG : 2 tests (voir étape 14)
- Fiche environnement : voir étape 16
- Reset : a effectuer

---

# Étape 20 — Checklist Finale
DEBUT :
[x] Périmètre écrit
[x] AVD neuf (wipe-data)
[x] App test installée
[x] 3 scénarios notés
[x] Versions Android/app notées

FIN :
[ ] Données de test supprimées
[ ] Reset AVD effectué
[ ] Preuve du reset
[x] Rapport sauvegardé
[x] Aucun compte personnel utilisé
