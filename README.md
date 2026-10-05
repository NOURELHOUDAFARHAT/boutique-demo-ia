# Boutique e-commerce avec assistant de vente IA

Démonstration technique : une boutique d'équipement de football en page unique,
avec un assistant de vente capable de chercher dans le catalogue, de suivre une
commande et d'ajouter lui-même au panier.

**Démo en ligne :** https://NOURELHOUDAFARHAT.github.io/boutique-demo-ia/

## Ce que ça fait

- Catalogue filtrable de 9 références, variantes, tailles et état du stock
- Interface responsive avec cartes flottantes, interactions au survol et palettes
  de couleurs persistantes
- Fiches produits, panier persistant par visiteur, tunnel jusqu'au récapitulatif
- Assistant conversationnel avec **appel d'outils** : le modèle décide quand
  appeler `rechercher_produits`, `suivre_commande` ou `ajouter_au_panier`,
  et l'ajout au panier modifie réellement l'état de l'application
- Données structurées JSON-LD `Product` pour le référencement, avec URL d'image

## Pile technique

Aucune. Une seule page HTML, sans framework ni dépendance hormis les polices
Google. Les fiches produits utilisent des photos d'illustration distantes
chargées depuis Unsplash, avec un fallback SVG si une image est indisponible.

## Les deux versions

| | Catalogue, panier, outils | Rédaction des réponses |
| --- | --- | --- |
| GitHub Pages | réels | pré-écrite |
| Version Claude Artifact | réels | modèle de langage |

L'assistant s'appuie sur la capacité `sample` du runtime des artefacts Claude.
Hors de cet environnement, `window.claude` n'existe pas : la page le détecte,
bascule en mode hors ligne et le dit explicitement à l'utilisateur. Les outils,
eux, continuent de s'exécuter pour de vrai dans les deux cas.

Pour brancher un vrai modèle sur la version GitHub Pages, il faudrait un
back-end qui détienne la clé d'API — une clé exposée côté navigateur serait
immédiatement exploitable par n'importe qui.

## Paiement

Le tunnel va jusqu'au récapitulatif. Les boutons Stripe, PayPal et Apple Pay
sont volontairement désactivés et **la page ne demande aucune donnée bancaire**.
Dans une boutique réelle, ce bouton ouvrirait une session Stripe Checkout créée
côté serveur, jamais un formulaire de carte hébergé par la page.

## Données

Boutique fictive. Les produits et les prix sont ceux d'articles réellement
commercialisés, relevés sur Decathlon.fr en octobre 2026 et utilisés comme jeu
de données. Aucune image de marque n'est reproduite : toutes les illustrations
sont dessinées en SVG.

---

Nourelhouda Farhat — [portfolio](https://nourelhouda-farhat.netlify.app)
