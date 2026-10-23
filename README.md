# REP Muscu — ton appli de suivi Basic-Fit

Une PWA (Progressive Web App) **100 % statique, gratuite et sans compte**, pensée pour iPhone.

## Mettre en ligne sur GitHub Pages (simple)

1. Crée un dépôt GitHub, par exemple `rep-muscu` (public pour l'hébergement gratuit).
2. Envoie **tous les fichiers** de ce dossier à la racine du dépôt (`index.html`, `styles.css`, `app.js`, `sw.js`, `manifest.webmanifest`, et le dossier `icons/`). Tu peux passer par **Add file → Upload files** sur GitHub.
3. Dans le dépôt, ouvre **Settings → Pages**. Sous *Build and deployment*, choisis **Deploy from a branch**, branche **main** et dossier **/(root)**, puis **Save**.
4. Ouvre l'adresse affichée dans Pages, normalement sous la forme `https://TON-PSEUDO.github.io/rep-muscu/`.
5. **Sur iPhone, ouvre cette adresse dans Safari** → bouton **Partager** → **Sur l’écran d’accueil** → **Ajouter**. L'application apparaît comme une icône et s'ouvre sans les barres de Safari.

> Il faut que l'application ait été ouverte en ligne au moins une fois pour enregistrer ses fichiers en cache et pouvoir l'utiliser sans connexion. Certaines restrictions iOS peuvent empêcher l'installation ou le cache sur des anciens systèmes.

## Ce que l'application fait

- Programme sur un calendrier récurrent du lundi au vendredi, repos le week-end.
- Séances **Push / Pull / Legs A / Upper / Legs B**, avec 3 × 8 reps par exercice (sauf gainage 3 × 30 s).
- Enregistrement **individuel de chaque série** (charge, répétitions, validation) avec historique automatique des derniers kilos utilisés.
- **Minuteur de repos** avec démarrage automatique facultatif, pause, reprise et +/− 15 secondes.
- Tableau de bord de progression avec suivi des records par exercice.
- **Photos facultatives** avec comparaison avant/après. Les images sont redimensionnées avant stockage local.
- Export et import d'une **sauvegarde JSON** contenant le journal **et les photos**.
- Icône iPhone, manifeste PWA, service worker pour le fonctionnement hors ligne après installation.

## Vie privée et stockage : important

Aucune donnée n'est envoyée à GitHub : **GitHub Pages héberge uniquement le code**. Toutes les charges et séances restent dans le stockage local du navigateur (`localStorage`) ; les photos restent dans `IndexedDB`. Il n'existe **aucune synchronisation entre appareils**. Safari peut supprimer les données lors d'un nettoyage du navigateur, et une désinstallation peut aussi effacer les données locales.

**Fais des exports réguliers** depuis Réglages. Conserve les JSON en lieu sûr (Fichiers, iCloud Drive privé, etc.) ; **ne publie jamais une sauvegarde dans le dépôt GitHub**, car elle peut contenir des photos personnelles.

## Modifier le programme

La liste des exercices est définie au début de `app.js`, dans la constante `PLAN`. Tu peux adapter les exercices, les durées de repos ou les conseils, puis renvoyer `app.js` sur GitHub. Si tu modifies les fichiers de l'application, incrémente `CACHE` dans `sw.js` pour forcer un cache neuf hors ligne.

## Sécurité sportive

Ce programme est un support de suivi, pas une prescription médicale. À 17 ans et débutant, privilégie la technique et les charges légères, garde des répétitions en réserve, respecte les jours de récupération et demande conseil à un coach de salle. Les 5 journées sont une **organisation possible**, pas une obligation en cas de fatigue ou de douleur.

## Exécution locale

Double-cliquer `index.html` donne un aperçu, mais la PWA et certaines fonctions de stockage fonctionnent mieux via HTTPS ou un serveur local. Exemple avec Python :

```bash
python -m http.server 8000
```

Ouvre ensuite `http://localhost:8000/` sur l'ordinateur. GitHub Pages sert directement les fichiers via HTTPS.

Licence : usage personnel libre.
