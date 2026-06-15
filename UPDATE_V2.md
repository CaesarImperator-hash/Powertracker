# PL Tracker — Mise à jour v2

Cette mise à jour ajoute :
- **Preview complet de la séance du jour** : tous les exercices visibles avec charges, principaux mis en valeur
- **Détection du jour de la semaine** : "Séance du jour" si on est lundi/mercredi/vendredi/samedi, "Jour de repos · Prochaine séance" sinon
- **Compteur de pas** depuis Apple Santé via Raccourci iOS
- **Date du jour** affichée en haut

---

## Déployer la mise à jour (3 min)

Tu dois remplacer **deux fichiers** sur ton repo GitHub : `index.html` et `sw.js`.

### Méthode rapide (un fichier à la fois)

1. Va sur ton repo GitHub : `github.com/[ton-pseudo]/pl-tracker`
2. Clique sur `index.html`
3. Touche le crayon ✏️ en haut à droite ("Edit this file")
4. **Sélectionne tout** (Cmd+A) → supprime → **colle** le nouveau contenu du `index.html` v2
5. Descends en bas → **Commit changes**
6. Refais la même chose pour `sw.js` (juste une ligne change : `v1` → `v2`)
7. Vercel redéploie automatiquement en ~30 sec

### Après déploiement, forcer la mise à jour sur ton iPhone

Le changement de version du cache (`v2` dans `sw.js`) va invalider l'ancienne version stockée. Mais pour être sûr :

1. Sur ton iPhone, **ferme complètement** l'app PL Tracker (swipe up depuis le bas, écarte la fenêtre vers le haut)
2. Attends 10 secondes
3. Rouvre l'app depuis l'écran d'accueil

Si tu vois toujours l'ancienne version :
1. Supprime l'icône (touche maintenue → "Supprimer le favori")
2. Ouvre l'URL Vercel dans Safari
3. Re-fais "Sur l'écran d'accueil"

---

## Créer le Raccourci iOS pour les pas (5 min, une seule fois)

L'app reçoit le nombre de pas via une URL avec un paramètre `?steps=12345`. Le raccourci va lire les pas dans Apple Santé et ouvrir l'app avec cette URL.

### Étape par étape

1. **Ouvre l'app "Raccourcis"** sur ton iPhone (préinstallée par Apple, icône bleue avec 2 cercles entrelacés)

2. **Onglet "Raccourcis"** en bas, puis **"+"** en haut à droite pour créer un nouveau raccourci

3. Touche le titre en haut ("Nouveau raccourci") et renomme-le exactement : **`PLTrackerSteps`** (sans espaces, sensible à la casse — c'est ce nom que l'app appelle)

4. **Ajoute la première action** : touche "Ajouter une action" → cherche `Échantillons de santé`
   - Sélectionne **"Rechercher des échantillons de Santé"**
   - Catégorie : **Activité** → **Nombre de pas**
   - Filtres : touche **"Date de début"** → **"est"** → **"Aujourd'hui"** (ajuste l'opérateur si besoin)
   - Limite : aucune (toutes les valeurs de la journée)

5. **Ajoute la deuxième action** : cherche `Calculer la statistique`
   - Sélectionne **"Calculer la statistique des échantillons de santé"**
   - Méthode : **Somme**
   - Sur : les échantillons de l'étape précédente (sera prérempli "Échantillons de santé")

6. **Ajoute la troisième action** : cherche `URL`
   - Sélectionne **"URL"**
   - Dans le champ, tape : `https://TON-URL-VERCEL.vercel.app/?steps=`
   - Puis touche le champ et choisis **"Statistique des échantillons"** (variable de l'étape précédente) pour qu'elle se colle à la fin
   - Le résultat doit ressembler à : `https://pl-tracker-xyz.vercel.app/?steps=[Statistique]`

7. **Ajoute la quatrième action** : cherche `Ouvrir URL`
   - Sélectionne **"Ouvrir l'URL"**
   - Elle utilisera automatiquement l'URL de l'étape précédente

8. **Touche "Terminer"** en haut à droite

### Tester le raccourci

1. Dans la liste des raccourcis, touche **PLTrackerSteps** une fois — il s'exécute
2. La première fois, iOS te demande l'autorisation d'accéder à Santé → **Autoriser**
3. Le raccourci ouvre Safari, qui ouvre l'app, qui affiche les pas

### Utiliser le raccourci depuis l'app

Une fois l'app ouverte sur la page d'accueil :
- Touche le bouton **"↻ Santé"** dans le widget des pas
- L'app appelle le raccourci, qui lit Santé, qui rouvre l'app avec les pas à jour

Si le bouton "↻ Santé" ne marche pas (rare), tu peux toujours :
- Lancer manuellement le raccourci depuis l'app Raccourcis
- Ou toucher "Manuel" dans l'app et saisir le chiffre à la main

---

## Bonus : exécuter le raccourci en un geste

Une fois le raccourci créé, tu peux :

**Ajouter un widget Raccourci sur ton écran d'accueil**
1. Touche maintenue sur l'écran d'accueil → "+" en haut à gauche → cherche "Raccourcis"
2. Choisis la taille petite → "Ajouter le widget"
3. Touche le widget pour le configurer → choisis `PLTrackerSteps`
4. Maintenant un tap sur le widget = pas mis à jour

**Ou utiliser Back Tap** (taper 2-3 fois au dos de l'iPhone)
1. Réglages → Accessibilité → Toucher → Toucher l'arrière
2. Choisis "Toucher 2 fois" ou "Toucher 3 fois" → sélectionne ton raccourci

---

## Si ça ne marche pas

**"Le raccourci n'existe pas"** quand on touche "↻ Santé"
→ Vérifie que le raccourci s'appelle **exactement** `PLTrackerSteps` (majuscule P, T, S, sans espace, sans tiret)

**Le raccourci s'exécute mais l'app n'affiche pas les pas**
→ Vérifie l'URL dans l'étape "URL" du raccourci, elle doit pointer vers ton URL Vercel exacte

**Les pas s'affichent à zéro**
→ Vérifie dans Santé que tu as bien des données de pas (l'iPhone doit les enregistrer automatiquement, sauf si l'option "Suivre les mouvements" est désactivée dans Réglages → Confidentialité → Mouvements et forme)

**Le widget des pas reste à "—"**
→ Touche "Manuel" pour saisir une valeur de test. Si ça marche → le souci vient du raccourci. Si ça ne marche pas → l'app n'a pas bien chargé la mise à jour, force le rafraîchissement (voir plus haut).
