# PL Tracker v8 — Deux modes d'affichage pour l'éditeur

## Le changement

L'éditeur a maintenant **deux vues** que tu peux basculer via un bouton en haut :

- **📱 Mode iPhone** : la vue mobile compacte, un onglet par semaine, exercices en 2 lignes, adaptée aux petits écrans tactiles
- **💻 Mode PC** : split-view large (programme à gauche, bibliothèque à droite), drag-drop souris, tout visible en même temps

Ton choix est **mémorisé** — l'app garde en mémoire ta préférence entre les sessions.

## Détection automatique

À la première ouverture (avant que tu aies choisi), l'app détecte la largeur d'écran :
- **≥ 900 px** (ordi, iPad landscape) → défaut **Mode PC**
- **< 900 px** (iPhone, iPad portrait) → défaut **Mode iPhone**

Tu peux toujours forcer l'autre mode via le toggle.

## Ce que tu peux faire en Mode PC (nouveautés vs mobile)

### Panneau programme (gauche, 60% de l'écran)
- Toutes les semaines listées (accordéon), pas d'onglets
- Chaque semaine pliable/dépliable
- Actions au niveau semaine : ✎ renommer · ⧉ dupliquer · × supprimer
- Actions au niveau jour : ✎ modifier · ⧉ dupliquer · × supprimer
- **Édition inline** sets/reps/weight sur chaque exercice (comme mobile mais plus compact)
- **Drag-drop souris** : réordonne les exercices dans un jour ou entre jours
- Boutons IMPORT / EXPORT / DÉFAUT en bas

### Panneau bibliothèque (droite, 40%)
- **Barre de recherche** en haut (filtre par nom en temps réel)
- **Filtre par groupe** (Squat, Bench, Deadlift, OHP, Jambes, Push, Dos, Épaules, Gainage, Autre)
- Liste alphabétique des exercices
- **Drag depuis la bibliothèque vers un jour** : glisse un exercice, il s'ajoute au jour où tu le déposes (l'endroit exact selon la position verticale du curseur)
- **Bouton "+ EXERCICE" en haut** : créer un nouvel exercice directement depuis le panneau
- **Bouton ✎ sur chaque exercice** : modifier nom, groupe, temps de repos par défaut. Le bouton Supprimer est dans la modale d'édition.

### Bibliothèque : gestion complète
Tu peux maintenant depuis le PC :
- Créer un nouvel exercice → bouton "+ EXERCICE" en haut du panneau
- Renommer un exercice → tap sur ✎
- Changer le groupe musculaire (impacte les stats de récup)
- Changer le temps de repos par défaut
- Supprimer un exercice → bouton "Supprimer" dans la modale

## En Mode iPhone (inchangé, juste le toggle en plus)

Toute l'interface mobile v7 reste, avec le toggle en haut. Rien n'a changé pour ce qui marchait déjà bien sur téléphone.

## Bonus

- **Escape** ferme les modales sur PC (raccourci clavier)
- La recherche dans la bibliothèque se met à jour en direct sans perdre le focus
- Le drag-drop utilise HTML5 natif, très fluide avec une souris

## À propos de `editor.html`

Le fichier `editor.html` séparé existe toujours (accessible sur `[ton-url]/editor.html`) pour ceux qui préfèrent l'utiliser en dehors de l'app principale. Mais maintenant tu peux tout faire depuis l'app principale — c'est devenu redondant. Tu peux le laisser ou le supprimer du repo GitHub, ça ne casse rien.

## Déploiement

Les 8 fichiers habituels à la racine, commit "v8 dual editor mode", cache SW passé à v8.

**Important sur PC** : après l'upload, force le rechargement (**Ctrl+Shift+R** sur Windows/Linux, **Cmd+Shift+R** sur Mac) sinon le navigateur peut garder l'ancienne version en cache.

**Sur iPhone** : ferme complètement l'app (swipe up), rouvre. Le sw v8 invalide l'ancien cache automatiquement.

## Cas d'usage type

**Session de planning sur canapé (PC/iPad)** :
1. Ouvre `[ton-url].vercel.app` sur ton PC
2. Auto-détection → Mode PC
3. Édite comme tu veux (drag-drop, création d'exos, duplication de semaines)

**Ajustement rapide en salle (iPhone)** :
1. Ouvre l'app installée sur iPhone
2. Auto-détection → Mode iPhone
3. Édite ce que tu as besoin (changer une charge, ajouter un exo)

**Astuce** : comme chaque appareil a sa propre copie locale, si tu édites sur PC puis veux voir sur iPhone (ou l'inverse), utilise Export sur un appareil → Import sur l'autre. Sinon reste sur un seul appareil pour éviter les divergences.
