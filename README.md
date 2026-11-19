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

## Commandes et règles Firestore

1. Dans Firebase Console → **Firestore Database → Règles**, collez le contenu de [firestore.rules](./firestore.rules) et publiez-le. Le compte gérant doit être `djodjojsk6@gmail.com` et avoir une adresse Google vérifiée.
2. Connectez-vous à l’application avec ce compte. Dans **Espace gérant**, configurez les zones et frais de livraison, les créneaux, les numéros de paiement et le point relais. Les coûts coursier sont enregistrés séparément et ne sont lisibles que par le gérant.
3. Créez des articles depuis l’espace gérant. L’application initialise aussi les documents d’inventaire nécessaires aux réservations.

Le panier est conservé sur l’appareil. Les commandes et les réservations temporaires, les codes promo, les annonces et les informations de suivi sont stockés dans Firestore. Le paiement n’est pas automatisé : vérifiez chaque acompte auprès de l’opérateur avant d’appuyer sur **Payée**. Le code à 4 chiffres s’affiche ensuite dans **Mes commandes**; vérifiez-le à la remise avant d’appuyer sur **Livrée**.

**Limites du forfait Spark sans serveur :** les réservations expirées sont libérées à la prochaine activité d’un navigateur connecté; aucune tâche ne tourne si personne n’utilise le site. Les règles protègent l’accès aux données, le stock réservé, les créneaux et les compteurs promo, mais une application exécutée dans le navigateur ne peut pas garantir les totaux ou vérifier un paiement comme le ferait un serveur. Contrôlez les détails et le paiement avant d’exécuter une commande. Les images des articles sont stockées dans Firestore; de nombreuses photos ou de gros volumes peuvent atteindre les limites du forfait.

## Déploiement

GitHub Pages sert `index.html` depuis la racine de la branche `main`. Les services Firebase doivent être configurés pour le domaine `sabomuiwa.github.io`.
