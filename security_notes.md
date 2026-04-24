# Étape 6 — Android Security (résumé)

1. Sandboxing : chaque app est isolée dans son propre processus Linux
2. Permissions : l'app doit demander l'accès aux ressources sensibles
3. Verified Boot : vérifie l'intégrité du système au démarrage
4. SELinux : contrôle les actions autorisées pour chaque processus
5. Chiffrement : les données utilisateur sont chiffrées par défaut
6. Isolation : les apps ne peuvent pas accéder aux données des autres apps

# Étape 7 — Verified Boot

- Objectif : Garantir que le système qui démarre est celui prévu par le fabricant
- Chain of trust : chaque composant vérifie le suivant avant de lui faire confiance.
  Du bootloader au kernel jusqu'aux partitions système.
- Pourquoi critique : si le boot est compromis, toutes les protections suivantes tombent

## Vérification sur notre AVD :
ro.boot.verifiedbootstate = 
orange = système modifié, Verified Boot contourné par le root
ro.boot.verifiedbootstate = orange
orange = système modifié, Verified Boot contourné par le root
