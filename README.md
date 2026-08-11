# Séance

Application web (fichier statique, sans backend) pour générer des séances de sport à la maison,
avec chrono intégré. Tout est stocké en local sur l'appareil (`localStorage`) — rien n'est envoyé
à un serveur.

## Utiliser sur iPhone

1. Une fois le site publié via GitHub Pages (voir ci-dessous), ouvre l'URL dans Safari.
2. Bouton **Partager** → **Sur l'écran d'accueil**. L'icône et le nom de l'app sont configurés
   via `manifest.json` / `apple-touch-icon.png`.
3. Lancée depuis l'écran d'accueil, l'app s'ouvre en plein écran (mode standalone) et fonctionne
   hors-ligne grâce au service worker (`sw.js`).

## Activer GitHub Pages (une fois, manuellement)

Ce dépôt ne contient pas de workflow de déploiement : GitHub Pages peut servir `index.html`
directement depuis une branche, sans étape de build.

1. Sur GitHub → **Settings** → **Pages**.
2. **Source** : *Deploy from a branch*.
3. **Branch** : `main` (une fois cette PR fusionnée) → dossier `/ (root)`.
4. Enregistre. L'URL sera de la forme `https://<utilisateur>.github.io/<repo>/`.

## Mises à jour

Le service worker sert la page en réseau d'abord (network-first) : tant que le téléphone a du
réseau, la dernière version poussée sur GitHub Pages est utilisée automatiquement et mise en
cache pour les usages hors-ligne suivants.

## Fichiers

- `index.html` — l'application (UI, logique de génération de séance, chrono, historique).
- `manifest.json` — métadonnées PWA (nom, icônes, couleurs, mode standalone).
- `sw.js` — service worker (cache offline + mise à jour automatique).
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` — icônes de l'app.
