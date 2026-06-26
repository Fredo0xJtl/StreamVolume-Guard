# AGENTS.md

Guide de travail pour StreamVolume Guard. Ce fichier sert aux contributeurs humains et aux assistants IA qui travaillent sur le projet.

## Objectif Du Projet

StreamVolume Guard aide les streamers à garder un volume navigateur plus stable pendant un live, sans tracker, sans collecte de données et avec un traitement audio local.

La priorité est de livrer une extension simple, fiable et compréhensible avant d'ajouter des optimisations ou des capacités avancées.

## Principes Non Négociables

- Open source, code lisible et sans obfuscation.
- Aucune télémétrie automatique.
- Aucune collecte d'audio, d'historique ou de données personnelles.
- Permissions Manifest V3 minimales.
- Réglages stockés localement par défaut.
- Expérience pensée d'abord pour les streamers.
- MVP fonctionnel avant complexité technique.

## Méthode De Travail

Avant une modification importante :

1. Comprendre le besoin utilisateur.
2. Identifier les options possibles.
3. Cartographier l'impact produit, technique et maintenance.
4. Chercher les risques avant de coder.
5. Recommander l'option la plus simple qui résout vraiment le problème.
6. Implémenter seulement après validation explicite.

Exception : si une demande commence par `!`, traiter la demande directement et garder le changement minimal.

## Priorités Produit

Ordre de décision recommandé :

1. Protéger le streamer contre les pics audio.
2. Garder le son agréable, sans pompage audible.
3. Rendre l'état de l'extension clair en live.
4. Garder la configuration simple pour un testeur.
5. Préserver la confiance : local, open source, zéro tracker.
6. Préparer les futures fonctions sans alourdir la V1.

## Règles Techniques

- Suivre l'architecture existante : `audio/`, `storage/`, `popup/`, `options/`, `license/`.
- Ne pas traiter deux fois le même média.
- Garder la logique audio séparée de l'interface.
- Préserver la possibilité d'ajouter `chrome.tabCapture` plus tard.
- Ne pas ajouter de dépendance ou de build tool sans raison forte.
- Préférer des modules petits, testables et nommés clairement.
- Mettre à jour la documentation quand le comportement utilisateur change.
- Mettre à jour `CHANGELOG.md` dès qu'un changement public ajoute, modifie, corrige ou clarifie quelque chose pour les utilisateurs ou testeurs.

## Avant Une Pull Request Ou Une Release

Vérifier au minimum :

```powershell
node tests/unit.test.js
node tests/build-targets.test.js
node tests/dist-packages.test.js
node tests/branding.test.js
node tests/browser-smoke.js
node --check background.js
node --check content.js
node --check popup/popup.js
node --check options/options.js
```

Pour une release, suivre la checklist interne mainteneur avant de publier une version ou de partager un build à des testeurs.
Utiliser des messages de commit en français pour garder l'historique public lisible.
