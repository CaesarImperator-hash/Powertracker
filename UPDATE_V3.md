# PL Tracker — Mise à jour v3 (refonte complète)

Cette mise à jour est **majeure**. Elle remplace tous les fichiers existants.

---

## Ce qui change

**Couleurs — palette « Plate Iron »**
- Fond noir profond, accent crimson red (#D4382F), texte os blanc
- Icône régénérée dans la nouvelle palette
- Indicateurs verts/oranges conservés pour le statut de récup

**Animations**
- Transitions entre onglets : fade 200 ms
- Démarrage de séance : slide depuis le bas 300 ms
- Retour à l'accueil : slide depuis le haut 250 ms
- Toggle d'une série : pulse + scale 280 ms sur la case ✓
- Boutons : compression légère au touch
- Feedback haptique : vibration courte sur ✓, longue à la fin du timer de repos

**Page d'accueil enrichie**
- Date du jour
- **Compte à rebours peak** : « J−X · TEST DEADLIFT · 10 juil. » (calcul auto vers le prochain test)
- **Statut récup** : jours écoulés depuis ta dernière séance de SQ / BP / DL / OHP, code couleur (rouge < 24 h, orange 24-48 h, vert 48 h+)
- **Poids de corps** : saisie rapide, conservé par date
- **État du jour** : 😴 🙂 💪 🔥 — tap pour enregistrer, retap pour effacer
- **Séance du jour** avec preview complet
- **Dernière séance résumée** : nom + top set
- **Progression cycle** en bas

**Programme : peak block 4 semaines**
- Le programme 8 semaines précédent est remplacé par le peak block 22 juin → 15 juillet
- Toutes les modifs qu'on a faites sont intégrées : leg press (pas de Bulgarian), OHP en samedi, plus de pause squat, plus de board press, oiseau au lieu de face pull, tirage vertical prise serrée, etc.
- **Séances de test** spéciales (DL ven 10, Squat lun 13, Bench mer 15) avec échauffement progressif détaillé et essais étiquetés (cible / cible principale / stretch PR)

**Stats refondues**
- Résumé : séances faites · % complétion · tonnage cycle (en tonnes)
- **e1RM estimé** par mouvement principal (SQ / BP / DL / OHP) avec dernière valeur + delta vs début
- Graphique multi-courbes e1RM par séance, code couleur par mouvement
- Tonnage par semaine (graphique en barres)
- Distribution des RPE (histogramme — utile pour détecter sur/sous-stimulation)
- Régularité par semaine (barres de progression)
- Poids de corps si suivi (courbe)
- État moyen par semaine si suivi
- Bouton « Réinitialiser » en bas

**Fonctionnalités supprimées**
- Pas Apple Santé (jamais utilisé)
- Programme 8 semaines initial

---

## Déployer la mise à jour

Tu as deux options.

### Option A — Remplacer un par un sur GitHub (manuel mais simple)

1. Va sur ton repo : `github.com/[ton-pseudo]/pl-tracker`
2. Pour chaque fichier modifié, clique dessus → crayon ✏️ → remplace le contenu → Commit changes :
   - `index.html`
   - `sw.js`
   - `manifest.json`
   - `icon-192.png` (upload directement via "Upload files")
   - `icon-512.png` (idem)
   - `apple-touch-icon.png` (idem)
   - `favicon-32.png` (idem)

### Option B — Tout remplacer d'un coup (recommandé)

1. Va sur ton repo GitHub
2. Pour chaque ancien fichier qui est encore là, supprime-le (clique le fichier → corbeille en haut à droite → Commit)
3. Sur la page principale du repo : **Add file → Upload files**
4. Glisse-dépose les **7 fichiers** du nouveau dossier `pl-tracker` (sauf le README/UPDATE)
5. **Commit changes**

Vercel redéploie automatiquement en ~30 sec.

### Forcer la mise à jour sur ton iPhone

Le cache du service worker change de v2 à v3, donc l'ancien sera invalidé automatiquement. Mais pour aller vite :

1. **Ferme complètement l'app** : swipe up depuis le bas + écarte la fenêtre
2. Attends 10 sec
3. Rouvre depuis l'écran d'accueil

Si tu vois encore l'ancienne version, supprime l'icône de l'écran d'accueil, ouvre l'URL Vercel dans Safari, refais "Sur l'écran d'accueil".

---

## Important : tes données existantes

**Tes séances déjà cochées seront conservées** (même clé localStorage `pl-progress`). Mais comme le programme change, certaines clés de séance ne correspondront plus aux nouvelles dates/structures. La barre de progression peut afficher des incohérences.

Si tu veux repartir propre pour le peak block, utilise le bouton « Réinitialiser » en bas de l'onglet Stats — ça efface toute la progression localement.

Les anciennes données « pas » Apple Santé sont ignorées par la nouvelle version mais restent en mémoire du téléphone. Pas grave.

---

## Bugs ou retours

Teste l'app pendant un jour ou deux et reviens-moi avec les ajustements à faire. Quelques points sur lesquels j'aimerais bien tes retours :
- La densité d'infos sur la home page : trop / juste / pas assez ?
- Les animations : trop lentes, trop rapides, bien ?
- L'écran de test (échauffement + essais) : lisible ? Tu vois bien la différence entre warmup et tentative ?
- Les stats : ce qui manque, ce qui sert pas ?
