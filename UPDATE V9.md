# PL Tracker v9 — Refonte navigation + volume par muscle

## Changements majeurs

### 1. Onglet "Aujourd'hui" retiré

La navigation passe de 3 onglets à 3 onglets différents :
- **Programme** (par défaut au lancement)
- **Éditeur**
- **Muscles** (nouveau, remplace Aujourd'hui)

Pour démarrer une séance : va sur **Programme**, choisis la semaine, tap sur le jour.

### 2. Nouvel onglet Muscles

Affiche le volume par groupe musculaire (séries et reps) sur la semaine sélectionnée ou l'ensemble du programme.

**Mode de calcul** : un exercice qui sollicite plusieurs muscles compte pour chacun. Ex : 4 séries de squat compétition (associé à quads/glutes/hamstrings/core) = 4 séries pour quads + 4 pour glutes + 4 pour hamstrings + 4 pour core. C'est la convention standard "sets per muscle per week" en hypertrophie.

**Colonnes affichées** :
- **SÉRIES** : nombre de séries planifiées touchant ce muscle
- **REPS VIS.** : total sets × reps visées
- **REPS RÉEL** : total sets × reps réellement effectuées (n'apparaît que si tu as renseigné des reps réelles quelque part)

Les muscles avec 0 volume sont affichés en grisé.

### 3. Association exercice ↔ muscles

Chaque exercice de la bibliothèque a maintenant un champ **MUSCLES SOLLICITÉS** (0 à plusieurs muscles).

**Muscles disponibles** : Pectoraux, Dos, Épaules, Biceps, Triceps, Quadriceps, Ischios, Fessiers, Mollets, Abdos/lombaires, Avant-bras.

Les ~34 exercices par défaut sont **pré-remplis** avec des associations sensées (Squat → quads/glutes/hamstrings/core, Bench → chest/triceps/shoulders, etc.).

**Modification individuelle** : dans la bibliothèque (mobile via "GÉRER LA BIBLIOTHÈQUE", PC via ✎ sur un exercice), tu vois maintenant une liste de "chips" muscles cliquables (multi-sélection).

### 4. Attribution en masse

Bouton **MUSCLES** dans la barre de contrôle de la bibliothèque (PC), ou **ATTRIBUER MUSCLES EN MASSE** dans les options mobile.

**Deux façons de l'utiliser** :

**A. Depuis la bibliothèque (PC)** :
1. Coche des exercices via la case à gauche de chaque item dans le panneau bibliothèque
2. Une barre "N sélectionnés" apparaît en haut
3. Clique **ATTRIBUER MUSCLES**
4. Choisis un muscle → les exos sélectionnés sont pré-cochés
5. Valide

**B. Directement (mobile ou PC)** :
1. Ouvre le modal directement
2. Choisis un muscle dans le sélecteur du haut → les exercices qui sollicitent déjà ce muscle sont cochés
3. Coche/décoche des exercices comme tu veux
4. Valide : le muscle est **ajouté** aux exercices cochés et **retiré** des décochés. Les autres muscles de chaque exercice sont préservés.

Tu peux répéter l'opération pour chaque muscle.

### 5. RPE retiré partout

- Plus de champ RPE dans le modal d'édition d'exercice
- Plus d'affichage "RPE X" dans les lignes
- Plus de colonne RPE dans la vue Session
- Plus de RPE dans les données par défaut du peak block

Les anciennes données (progression avec RPE stockés) restent lisibles mais le RPE ne s'affiche plus.

### 6. Colonne "reps réelles"

Dans l'éditeur, chaque exercice a maintenant **deux inputs de reps** côte à côte :

```
[sets] × [reps visées] / [reps réelles] @ [poids] kg
    4  ×      3         /       3       @   180  kg
```

- **Reps visées** : en rouge (couleur accent) — ce que tu avais prévu
- **Reps réelles** : en vert (couleur success) — ce que tu as effectivement fait

Tape une valeur, appuie Tab/clique ailleurs → sauvegardé auto. Vide = pas encore fait.

C'est cette valeur qui alimente les "REPS RÉEL" de l'onglet Muscles.

## Ce qui ne change pas

- Palette Plate Iron (rouge crimson sur noir)
- Le tracker de session (avec chronomètre de repos) fonctionne toujours pour ceux qui l'utilisent
- Import / Export / Restore Default toujours dispos
- Toggle mobile/PC dans l'éditeur toujours là
- Drag-drop dans l'éditeur PC toujours là
- Duplication de semaines/jours toujours là

## Migration automatique des données

Au premier lancement de v9 après update :
- Ta bibliothèque existante est **migrée** : pour chaque exercice qui n'a pas de champ `muscles`, on essaie de retrouver l'exercice dans les défauts par ID et on copie ses muscles. Les exercices que tu as créés toi-même auront une liste vide (à remplir manuellement).
- Ton programme existant continue de fonctionner — le champ `reps` reste "reps visées". Le nouveau champ `repsActual` est vide au départ, tu le remplis quand tu veux.

## Déploiement

**7 fichiers** à la racine (le fichier `editor.html` séparé n'est plus nécessaire — l'éditeur PC est intégré) :
- `index.html`
- `sw.js`
- `manifest.json`
- `apple-touch-icon.png`
- `favicon-32.png`
- `icon-192.png`
- `icon-512.png`

Sur GitHub → glisser-remplacer les fichiers → commit "v9 muscles reps réelles" → Vercel redéploie.

**Cache SW passé à v9** — l'ancien cache sera invalidé automatiquement.

Sur iPhone : ferme complètement l'app + rouvre.
Sur PC : **Ctrl+Shift+R** (ou Cmd+Shift+R) pour forcer le rafraîchissement.

## Note

Le fichier `editor.html` séparé peut être supprimé du repo maintenant, il n'a plus d'utilité. L'éditeur complet est dans l'app principale.
