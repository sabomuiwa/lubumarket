# LubuMarket

Catalogue de la boutique LubuMarket, hébergé sur GitHub Pages et connecté à Firebase.

## Activer les descriptions IA

La génération de descriptions utilise Gemini via Firebase AI Logic. Aucune clé Gemini n’est stockée dans le dépôt.

1. Dans la [console Firebase](https://console.firebase.google.com/project/lubumarket-29a24/ailogic), ouvrez **AI Logic**, lancez **Get started** et sélectionnez **Gemini Developer API**.
2. Dans **App Check**, enregistrez l’application Web avec **reCAPTCHA Enterprise** et le domaine `sabomuiwa.github.io`. Activez l’application puis appliquez l’enforcement App Check à Firebase AI Logic.
3. Renseignez la **clé de site publique** reCAPTCHA Enterprise dans la balise `firebase-app-check-site-key` de [index.html](./index.html). Ne renseignez jamais la clé secrète reCAPTCHA dans le dépôt.
4. Après le déploiement GitHub Pages, connectez-vous avec le compte gérant, ouvrez **Espace gérant**, puis **Générer une description avec Gemini**.

La description générée est un brouillon à vérifier avant publication. Les quotas et éventuels frais dépendent de la configuration Firebase/Google du projet.

## Annonces de la boutique

Dans **Espace gérant → Annonce du jour**, choisissez le type, renseignez le titre et le message, puis cochez ou décochez l’affichage sur l’accueil. Les annonces publiées sont visibles dans le bandeau d’accueil.

## Déploiement

GitHub Pages sert `index.html` depuis la racine de la branche `main`. Les services Firebase doivent être configurés pour le domaine `sabomuiwa.github.io`.
