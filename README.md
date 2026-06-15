# PL Tracker — Déploiement sur Vercel

Ton app powerlifting prête à déployer sur Vercel. Aucun code à écrire, juste à uploader le dossier.

---

## Étape 1 — Créer un compte Vercel (2 min)

1. Va sur **https://vercel.com/signup**
2. Clique sur **"Continue with Email"** (ou GitHub si tu en as un — plus rapide)
3. Valide l'email, choisis un nom d'utilisateur
4. Sur la page "Choose Plan" → **Hobby** (gratuit, suffit largement)

---

## Étape 2 — Déployer l'app (3 min)

Vercel ne propose pas d'upload manuel direct via leur interface principale, mais le déploiement via leur outil en ligne de commande est le plus simple. **Voici la méthode la plus rapide sans coder.**

### Option A — Via GitHub (recommandée, 5 min)

Cette méthode te donne aussi l'avantage que toute modif future est automatiquement déployée.

1. Crée un compte gratuit sur **https://github.com/signup** si tu n'en as pas
2. Sur GitHub, clique le **+** en haut à droite → **New repository**
3. Nom du repo : `pl-tracker` (ou ce que tu veux). Mets-le en **Public**. Clique **Create repository**
4. Sur la page du repo vide, clique **"uploading an existing file"** (lien bleu au milieu)
5. **Glisse-dépose** tous les fichiers du dossier `pl-tracker` (index.html, manifest.json, sw.js, et les 4 icônes PNG)
6. En bas, clique **Commit changes**
7. Va sur **https://vercel.com/new**
8. Clique **"Import"** à côté du repo `pl-tracker` (autorise GitHub si demandé)
9. Sur la page de config, laisse tout par défaut → clique **Deploy**
10. Attends ~30 sec → ton app est en ligne, Vercel te donne une URL type `pl-tracker-xyz.vercel.app`

### Option B — Via Vercel CLI (si tu te sens à l'aise avec le Terminal Mac)

1. Installe Node.js depuis **https://nodejs.org** (clique le bouton "LTS")
2. Ouvre Terminal (Spotlight → "Terminal")
3. Tape : `npm install -g vercel` puis Entrée
4. Tape : `cd ~/Downloads/pl-tracker` (ou le chemin où tu as mis le dossier)
5. Tape : `vercel` puis Entrée
6. Réponds aux questions : login (par email), accept all defaults
7. Une URL apparaît : c'est ton app en ligne

---

## Étape 3 — Installer sur l'écran d'accueil iPhone (30 sec)

1. Sur ton iPhone, ouvre **Safari** (pas Chrome, important pour iOS)
2. Va sur l'URL Vercel donnée à l'étape précédente (ex: `pl-tracker-xyz.vercel.app`)
3. Touche le bouton **Partager** (carré avec flèche vers le haut, en bas au milieu)
4. Fais défiler le menu vers le bas → **"Sur l'écran d'accueil"**
5. Confirme **Ajouter**
6. L'icône PL Tracker apparaît sur ton écran d'accueil

À l'ouverture, l'app se lance en plein écran, sans barre Safari. Comme une vraie app.

---

## Ce qui est inclus

- **Programme complet 8 semaines** avec toutes les charges qu'on a calculées
- **Cocher les séries** une par une avec timer de repos automatique
- **Modifier charge / reps / RPE** en temps réel, tout est sauvegardé
- **Statistiques** : PR du cycle, volume par séance, progression
- **Fonctionne hors ligne** une fois ouverte une première fois
- **Données stockées sur ton iPhone uniquement** (pas de cloud, pas de compte)

---

## Limitations à connaître

- **Données locales à ton iPhone** : si tu changes de téléphone ou réinstalles Safari, tu perds la progression. Pour partager entre appareils il faudrait ajouter un backend (compliqué, pas utile pour ton usage).
- **Pas d'auto-ajustement RPE** dans cette v1 : tu peux modifier manuellement les charges sur la séance en cours, mais l'app ne suggère pas les charges suivantes. Améliorable plus tard.
- **Pas de notifications push** : le timer de repos vibre l'iPhone quand il est terminé, mais pas de notification si l'app n'est pas ouverte. Reste donc dans l'app pendant tes séries.

---

## Pour mettre à jour l'app

Si on adapte le programme (charges, exercices...), tu remplaces le fichier `index.html` sur GitHub :
1. Va sur ton repo GitHub
2. Clique sur `index.html`
3. Petit crayon en haut à droite → modifier
4. Colle le nouveau contenu → **Commit**
5. Vercel redéploie automatiquement en ~30 sec
6. Sur ton iPhone, ferme l'app et rouvre-la pour avoir la nouvelle version

---

## Problème ? Aide ?

Reviens vers moi avec une capture d'écran ou la description du blocage. Les pièges courants :
- Safari iPhone qui propose pas "Sur l'écran d'accueil" → vérifier que tu es bien sur Safari, pas Chrome ou autre
- Vercel demande une "carte bancaire" → c'est pour le plan Pro, choisis **Hobby (free)**, pas de carte requise
- App qui ne charge pas → vérifier que les 7 fichiers sont bien à la racine du repo (pas dans un sous-dossier)
