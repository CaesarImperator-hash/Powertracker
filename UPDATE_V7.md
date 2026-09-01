# PL Tracker v7 — Éditeur intégré au mobile

## Le changement

L'onglet **Éditeur** de l'app iPhone contient maintenant un vrai éditeur, plus juste un message qui te renvoie sur PC. Chaque modification est **sauvegardée instantanément** dans ton programme.

Le workflow "PC → export → notes iCloud → import" n'est plus nécessaire pour les ajustements courants. L'éditeur PC (`/editor.html`) reste dispo pour ceux qui préfèrent grand écran.

## Ce que fait le nouvel éditeur mobile

### Navigation
- **Onglets de semaines** en haut (S1, S2, S3, S4, +) — une seule semaine visible à la fois pour éviter la cramponnerie visuelle
- Le **+** ajoute une nouvelle semaine et bascule dessus automatiquement

### Actions au niveau semaine
- **✎ Renommer** : prompt pour changer le nom (ex. "Deload")
- **⧉ Dupliquer** : copie complète de la semaine, utile pour créer un nouveau bloc à partir d'une semaine existante puis ajuster
- **× Supprimer** : avec confirmation

### Actions au niveau jour
- **✎** ouvre une modale pour modifier libellé (Lundi...), nom (Squat...), date
- **⧉** duplique le jour dans la même semaine
- **×** supprime avec confirmation
- **+ AJOUTER UN JOUR** en bas de la semaine

### Actions au niveau exercice (le cœur)
Chaque exercice a **2 lignes** :

**Ligne 1** : marker ● (mouvement principal) ou ○ (accessoire), nom, boutons ✎ et ×

**Ligne 2** : **édition inline** des 3 champs les plus utilisés :
```
[3] × [8] @ [180] kg
```
Tap sur un champ → clavier numérique s'ouvre → tape → tape ailleurs (ou "Suivant") → **sauvegardé automatiquement**. Pas de bouton "Enregistrer" à cliquer.

- Le **✎** ouvre une modale allégée pour : **RPE / Repos / Note / Mouvement principal**. Ce sont les champs plus rares à modifier.
- Le rond ● / ○ tout à gauche est cliquable aussi (même modale, raccourci)
- Le **×** demande confirmation avant de retirer l'exercice

### Ajouter un exercice
Bouton **+ AJOUTER UN EXERCICE** en bas de chaque jour → ouvre la bibliothèque (~34 exercices par défaut, tap pour l'ajouter au jour).

## Options en bas de l'éditeur

- **GÉRER LA BIBLIOTHÈQUE** : ajouter/renommer/supprimer les exercices disponibles
- **IMPORTER UN PROGRAMME** : si tu veux récupérer un programme depuis PC ou une sauvegarde
- **EXPORTER (SAUVEGARDE)** : copie ton programme pour le sauvegarder ailleurs
- **RESTAURER LE PEAK BLOCK PAR DÉFAUT** : reset au programme d'origine
- **URL de l'éditeur PC** en petit tout en bas, tap pour copier

## Correctifs par la même occasion

- Le bouton "× Supprimer" demande maintenant confirmation (avant on pouvait supprimer par erreur)
- Ajout de la duplication de jour (n'existait qu'au niveau semaine sur PC avant)

## Sur PC (editor.html)

Rien ne change côté PC. L'éditeur bureau reste disponible pour ceux qui préfèrent grand écran + souris.

## Déploiement

Toujours pareil : 8 fichiers à la racine du repo GitHub, commit "v7", cache SW passé en v7.

Sur iPhone :
1. Ferme complètement l'app (swipe up)
2. Rouvre
3. Onglet **Éditeur** en bas
4. Édite ! Chaque modif est sauvée en direct.

## Note technique

L'édition inline utilise l'événement `change` (déclenché quand tu quittes le champ), donc pas de spam de sauvegarde à chaque frappe. Ta batterie te remercie.

Les données sont stockées dans `localStorage` sur ton appareil. Le PC et l'iPhone ont chacun leur propre copie — si tu édites sur les deux, utilise Import/Export pour synchroniser (ou n'édite qu'à un endroit).
