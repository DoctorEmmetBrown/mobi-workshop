# Site MoBI 2027 — mise en ligne

Site statique d'une page, prêt pour GitHub Pages (gratuit, HTTPS inclus).

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | La landing page |
| `img/` | Les six photos du CAES (crédits affichés sur la page) |
| `favicon.svg`, `apple-touch-icon.png` | Icônes d'onglet et d'écran d'accueil |
| `og-image.png` | Image d'aperçu quand le lien est partagé (mail, Slack, LinkedIn) |
| `CNAME` | Le nom de domaine du site (`mobi-workshop.org`) |
| `.nojekyll` | Demande à GitHub de servir les fichiers tels quels |
| `robots.txt` | Autorise l'indexation par les moteurs de recherche |

## Si tu choisis un autre nom de domaine

Remplace `mobi-workshop.org` à trois endroits :
1. dans `CNAME` (une seule ligne, sans `https://`) ;
2. dans `index.html`, balise `<link rel="canonical" …>` ;
3. dans `index.html`, balises `og:url` et `og:image`.

## Étape 1 — Publier sur GitHub Pages

1. Sur github.com, crée un dépôt public, par exemple `mobi-workshop`.
2. Bouton **Add file › Upload files** : glisse tout le contenu de ce dossier (y compris `img/`, `CNAME` et `.nojekyll`). Valide avec **Commit changes**.
   Sur Mac, `.nojekyll` est un fichier caché : appuie sur Cmd+Maj+. dans le Finder pour l'afficher avant de le glisser.
3. **Settings › Pages** : Source = *Deploy from a branch*, branche `main`, dossier `/ (root)`, puis **Save**.
4. Après une minute, le site est visible à `https://<ton-compte>.github.io/mobi-workshop/`.

## Étape 2 — Acheter le domaine

Chez OVHcloud, Gandi ou Cloudflare. Pas besoin de prendre d'hébergement ni d'adresse mail.

## Étape 3 — Relier le domaine (zone DNS chez le registrar)

Supprime les enregistrements A / AAAA proposés par défaut sur le domaine nu, puis ajoute :

| Type | Nom | Valeur |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | `<ton-compte>.github.io.` |

Ensuite, dans **Settings › Pages** du dépôt :
1. vérifie que *Custom domain* affiche `mobi-workshop.org` (il est lu depuis le fichier `CNAME`) ;
2. attends que le contrôle DNS passe au vert (de quelques minutes à quelques heures) ;
3. coche **Enforce HTTPS**.

Conseil : dans **Settings › Pages**, GitHub propose aussi de *vérifier* le domaine pour ton compte. Fais-le, cela empêche quelqu'un d'autre de l'utiliser sur GitHub.

## Mettre à jour le site

Modifie `index.html` (ou dépose une nouvelle version au même nom) dans le dépôt. Le site se met à jour en une minute environ.

## Avant de rendre l'adresse publique

- Accord du CAES pour l'usage de leurs photos (crédits déjà indiqués sous la galerie).
- Adresse de contact : dans `index.html`, cherche `CONTACT_EMAIL = ""` et mets l'adresse entre les guillemets pour afficher la ligne « Questions? Write to ».
