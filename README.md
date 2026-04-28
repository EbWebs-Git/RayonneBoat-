# RAYONNE! — Logiciel de jauges
### Les 2 Loire — 1-2-3 Mai 2026
**by EbWebs** — [ebwebs.org](https://ebwebs.org) — Ethan MORGADO — contact@ebwebs.org

---

## Installation

1. Extraire le ZIP dans un dossier
2. Mettre la police **Gagalin-Regular.otf** dans `assets/fonts/`
3. Double-cliquer sur **LANCER.bat**
4. La première fois : npm installe Electron automatiquement (2-3 min, connexion internet requise)

> **Node.js requis** — télécharger sur [nodejs.org](https://nodejs.org) si pas encore installé

---

## Les deux fenêtres

### Fenêtre OBS — projection publique
Ce que le public voit, à capturer dans OBS via "Capture de fenêtre".

| Zone | Description |
|------|-------------|
| **Jauge Construction** (haut) | Image personnalisable, révélation gauche → droite |
| **Jauge Son** (gauche) | Image personnalisable, révélation bas → haut |
| **Fond** | Vidéo en plein écran, change automatiquement selon le % |
| **Titre** | RAYONNE! 1-2-3 MAI 2026 en bas |
| **Heure** | Optionnelle, bas à droite (toggle depuis le contrôle) |
| **Message push** | Texte temporaire en haut, déclenché depuis le contrôle |

### Fenêtre Contrôle — tableau de bord
Cachée du public. Permet de tout piloter en direct.

---

## Sections du panneau de contrôle

### Etat en direct
- Pourcentage affiché au public (0–100%)
- Points internes (0–10 000)
- VU-mètre sonore en temps réel
- Bouton **Pause** — fige l'accumulation audio sans couper le VU-mètre
- Bouton **Remise à zéro**

### Valeur immédiate
- Saisir directement un nombre de points (0–10 000)
- Slider pourcentage rapide

### Bonus
- **Multiplicateur** : x5 par défaut, paramétrable
- **Durée** : en secondes
- **Bonus VISIBLE** : déclenche les animations (notes flottantes) sur OBS
- **Bonus DISCRET** : multiplie le score sans animation visible

### Message sur OBS
- Taper un texte → il s'affiche en grand sur OBS pendant X secondes
- Bouton Effacer pour le retirer immédiatement

### Audio
- Sélection de la source audio (micro, table de mixage, etc.)
- Réglage de sensibilité (1–100)

> **Fonctionnement** : le logiciel accumule les dB moyens pendant 5 secondes, puis les ajoute au score. Exemple : 120 dB moyen → +120 points toutes les 5 secondes.

### Images des jauges
- Importer une image PNG/JPG pour la jauge Construction
- Importer une image PNG/JPG pour la jauge Son
- L'image se révèle progressivement selon le niveau

### Options affichage OBS
| Option | Effet |
|--------|-------|
| Afficher le pourcentage | Montre/cache le % sur la jauge construction |
| Afficher l'heure | Heure en direct en bas à droite de l'écran OBS |
| Animation finale auto à 100% | Déclenche automatiquement les confettis à 100% |

### Animation finale
- Déclencher manuellement les confettis + plein écran
- Bouton Arrêter pour couper

### Vidéos de fond
6 plages paramétrables :

| Plage | Vidéo jouée |
|-------|-------------|
| 0% → 20% | Début de construction |
| 20% → 40% | En cours |
| 40% → 60% | Milieu |
| 60% → 80% | Avancé |
| 80% → 100% | Presque fini |
| > 100% (finale) | Célébration |

Cliquer **Parcourir** pour associer un fichier vidéo (MP4, WebM, MOV...) à chaque plage.

---

## Utilisation dans OBS

1. Lancer le logiciel via LANCER.bat
2. Dans OBS : **Ajouter une source → Capture de fenêtre**
3. Sélectionner **"RAYONNE! — Projection OBS"**
4. Redimensionner en 16:9 dans la scène
5. La fenêtre contrôle reste sur ton écran, invisible dans OBS

---

## Structure des fichiers

```
rayonne/
├── main.js              — Logique principale Electron
├── obs.html             — Fenêtre projection OBS
├── control.html         — Panneau de contrôle
├── package.json         — Dépendances npm
├── LANCER.bat           — Script de démarrage Windows
├── README.md            — Ce fichier
└── assets/
    ├── fonts/
    │   └── Gagalin-Regular.otf   — Police à placer ici
    └── videos/                   — Dossier optionnel pour les vidéos
```

---

## Résolution de problèmes

**Le logiciel ne s'ouvre pas**
- Vérifier que Node.js est installé : ouvrir un terminal, taper `node -v`
- Supprimer le dossier `node_modules` et relancer LANCER.bat

**Les images des jauges ne s'affichent pas**
- Les sélectionner manuellement via le bouton "Changer" dans la section Images des jauges
- Formats acceptés : PNG, JPG, JPEG, GIF, WEBP, BMP

**Pas de source audio dans la liste**
- Autoriser l'accès au microphone si Windows le demande
- Changer de source et revenir si le VU-mètre ne réagit pas

**La police Gagalin n'est pas chargée**
- Placer `Gagalin-Regular.otf` dans `assets/fonts/`
- Relancer le logiciel

---

© EbWebs 2026 — ebwebs.org — contact@ebwebs.org
