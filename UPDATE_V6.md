# PL Tracker v6 — Corrections + édition inline

## Bugs corrigés

### 1. Boutons ✎ / ⧉ / × sur les semaines et modales inopérants

Bug de propagation d'event : j'avais mis `onclick="event.stopPropagation()"` sur des éléments parents, ce qui empêchait les clics sur les boutons enfants d'atteindre le gestionnaire d'événements global. Résultat : les boutons ne réagissaient à rien.

Corrigé sur :
- Les actions dans les entêtes de semaine (rename ✎, duplicate ⧉, delete ×)
- **Toutes** les modales (le bouton "Enregistrer" ne faisait rien avant, idem "Importer")

**Conséquence pour toi** : ajouter/renommer/supprimer/dupliquer une semaine fonctionne, et les modales aussi.

### 2. "Impossible d'enregistrer les nouvelles semaines"

C'était le même bug déguisé : tu ajoutais bien la semaine (le "+ SEMAINE" fonctionnait), mais tu ne pouvais pas la renommer ni la modifier — donc l'impression qu'elle n'était pas enregistrée.

## Nouveautés

### Édition inline sur la ligne de l'exercice

Sur PC, chaque ligne d'exercice a maintenant **3 champs directement modifiables** : séries × reps @ charge kg. Modifie la valeur, appuie Tab ou clique ailleurs, c'est sauvegardé automatiquement.

Le bouton ✎ (crayon) à droite ouvre une modale allégée pour **le reste** : RPE, temps de repos, note technique, case "mouvement principal".

Astuce : clique sur le rond ● / ○ tout à gauche pour ouvrir la modale aussi (c'est un raccourci).

### Suppression de l'onglet Stats sur mobile

Retiré comme demandé. Les données restent tracées en arrière-plan (poids de corps, état, séances complétées) au cas où tu voudrais réactiver plus tard.

## Déploiement

Même procédure : glisse les **8 fichiers** à la racine du repo GitHub, commit "v6". Cache SW passé en v6.

Sur iPhone : ferme + rouvre l'app.
Sur PC : recharge la page editor.html (Ctrl+Shift+R pour forcer le rafraîchissement si nécessaire).

## Ce que ça donne côté PC après update

Une ligne d'exercice ressemble maintenant à :
```
⋮⋮  ●  Squat compétition    [4] × [3]  @ [180] kg  RPE 8 · 240s   ✎  ×
```

Où `[4]`, `[3]`, `[180]` sont éditables inline. Le `✎` ouvre la modale pour RPE / repos / note / marquer principal.
