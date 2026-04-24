# LAB 2 : Rooting Android

**Cours :** Securite des applications mobiles
**Date :** 24/04/2026

---

## Objectif
Comprendre ce que le root change, quoi verifier, comment tracer, comment remettre a zero.

---

## Environnement
| Champ | Valeur |
|-------|--------|
| Device | AVD Pixel 5 |
| Android | 11.0 (R) |
| API | 30 |
| Image | AOSP (sans Google) |
| App testee | SpaceMissionControl v1.0 |

---

## Etapes realisees
| # | Etape | Statut |
|---|-------|--------|
| 1 | Rooter l'AVD | OK |
| 2 | Fiche perimetre | OK |
| 3 | AVD propre | OK |
| 4 | Installer l'app de test | OK |
| 5 | Definir 3 scenarios | OK |
| 6 | Android Security | OK |
| 7 | Verified Boot | OK |
| 8 | AVB | OK |
| 9 | Definition rooting | OK |
| 10 | Interet labo | OK |
| 11 | Matrice de risques | OK |
| 12 | Mesures defensives | OK |
| 13 | OWASP MASVS | OK |
| 14 | OWASP MASTG | OK |
| 15 | Commandes synthese | OK |
| 16 | Fiche environnement | OK |
| 17 | Reset AVD | OK |

---

## Resultats cles
\\\
adb root              -> restarting adbd as root
adb remount           -> remount succeeded
adb shell id          -> uid=0(root)
verifiedbootstate     -> orange
\\\

---

## Scenarios testes
| # | Scenario | Resultat |
|---|----------|----------|
| 1 | Load Satellite Feed | Mission Status: Receiving satellite feed - OK |
| 2 | Orbital Calculation | Data: 51599823 - OK |
| 3 | Ping Control Tower | UI is responsive - OK |

---

## Fichiers
- rapport_lab2.md    -> Rapport complet
- perimetre.md       -> Fiche perimetre
- scenarios.md       -> Scenarios de test
- security_notes.md  -> Notes Android Security + Verified Boot
- logcat_root_check.txt -> Logs systeme

---

## Screenshots
### Emulateur roote
![adb root](screenshots/adb_root.png)

### App installee
![app](screenshots/app_running.png)

### Verified Boot Orange
![verified boot](screenshots/verified_boot.png)

---

## Concepts cles appris
- Root = uid=0 = acces total au systeme
- verifiedbootstate=orange = chaine de confiance compromise
- overlayfs = partitions systeme modifiables
- AOSP = image sans Google = rootable
- AVB = Android Verified Boot 2.0

---

## Regles respectees
- App de test uniquement - OK
- Donnees fictives - OK
- AVD isole - OK
- Reset effectue - OK
