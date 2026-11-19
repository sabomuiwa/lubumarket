ÉTAPE 1.
1. Logo : affiche logo/icon.svg dans l'en-tête et l'écran de connexion, favicon logo/icon-192.png, apple-touch-icon logo/apple-touch-icon.png.
2. Espace gérant en tableau de bord plein écran, réservé au gérant, avec barre de navigation en bas : Tableau de bord, Produits, Commandes, Livraisons, Plus (Stocks, Clients, Paiements, Promotions, Finances, Paramètres).
3. Tableau de bord : ventes du jour/semaine/mois, commandes à traiter, livraisons du jour, marge estimée, articles en stock bas, accès « Ajouter un article ».
4. Produits : recherche, ajout en moins de 2 minutes (photo, nom, prix, catégorie, stock, publier), modifier, supprimer, dupliquer, masquer, bouton « Réservé ». Champs avancés repliables : caractéristiques (paires nom/valeur, champs proposés selon la catégorie), variantes (taille/couleur avec stock propre), 3 points forts, contenu du colis, garantie, prix USD, prix barré, champ vendeur (= LubuMarket).
5. Stocks : quantités modifiables, alerte stock bas (seuil réglable), épuisés.
6. Paramètres : numéro WhatsApp, taux USD/FC, % d'acompte, numéros M-Pesa/Airtel/Orange, points de retrait, quartiers avec 2 prix (coût coursier, prix facturé) et délai estimé, créneaux de livraison (heure début/fin, heure limite), Drops Campus (lieu, date, heures, livraison gratuite), texte « Comment commander ».
7. Collections Firestore : products, orders, settings, zones, slots, pickupPoints, promos, announcements, users. Règles : lecture pour tout utilisateur connecté, écriture réservée au gérant, chaque client ne lit et n'écrit que son profil.
ÉTAPE 1.
1. Logo : affiche logo/icon.svg dans l'en-tête et l'écran de connexion, favicon logo/icon-192.png, apple-touch-icon logo/apple-touch-icon.png.
2. Espace gérant en tableau de bord plein écran, réservé au gérant, avec barre de navigation en bas : Tableau de bord, Produits, Commandes, Livraisons, Plus (Stocks, Clients, Paiements, Promotions, Finances, Paramètres).
3. Tableau de bord : ventes du jour/semaine/mois, commandes à traiter, livraisons du jour, marge estimée, articles en stock bas, accès « Ajouter un article ».
4. Produits : recherche, ajout en moins de 2 minutes (photo, nom, prix, catégorie, stock, publier), modifier, supprimer, dupliquer, masquer, bouton « Réservé ». Champs avancés repliables : caractéristiques (paires nom/valeur, champs proposés selon la catégorie), variantes (taille/couleur avec stock propre), 3 points forts, contenu du colis, garantie, prix USD, prix barré, champ vendeur (= LubuMarket).
5. Stocks : quantités modifiables, alerte stock bas (seuil réglable), épuisés.
6. Paramètres : numéro WhatsApp, taux USD/FC, % d'acompte, numéros M-Pesa/Airtel/Orange, points de retrait, quartiers avec 2 prix (coût coursier, prix facturé) et délai estimé, créneaux de livraison (heure début/fin, heure limite), Drops Campus (lieu, date, heures, livraison gratuite), texte « Comment commander ».
7. Collections Firestore : products, orders, settings, zones, slots, pickupPoints, promos, announcements, users. Règles : lecture pour tout utilisateur connecté, écriture réservée au gérant, chaque client ne lit et n'écrit que son profil.
# LubuMarket

Catalogue de la boutique LubuMarket, hébergé sur GitHub Pages et connecté à Firebase.

## Espace gérant et stocks

L’espace gérant plein écran comprend les ventes et commandes, la gestion des produits, les livraisons, les clients, les paiements, les promotions, les finances et les paramètres. Les produits peuvent avoir des variantes taille/couleur, chacune avec son propre stock; le client choisit la variante avant de l’ajouter au panier, et sa réservation est suivie séparément dans Firestore. Les quantités et le seuil d’alerte se règlent depuis **Espace gérant → Stocks**.

## Panier et commandes

Le panier reste enregistré sur le téléphone. Le client peut choisir les quantités, retirer des articles ou utiliser **Commander direct** depuis une fiche produit. Le formulaire affiche séparément le total de retrait et le total de livraison, puis permet d’ajouter une livraison au quartier, un lien de position, un créneau, un cadeau, un code promo et l’acompte.

Chaque commande reçoit un numéro `LM-AAMMJJ-XXXX`, un code de livraison à quatre chiffres, des articles avec leurs prix copiés et un historique horodaté. Après création, l’application ouvre WhatsApp avec un récapitulatif complet. **Mes commandes** affiche les statuts, le code de livraison et le reçu.

## Annonces de la boutique

Dans **Espace gérant → Paramètres → Annonces d’accueil**, choisissez le type, renseignez le titre et le message, puis cochez ou décochez l’affichage sur l’accueil. Les annonces publiées sont visibles dans le bandeau d’accueil.

## Commandes et règles Firestore

1. Dans Firebase Console → **Firestore Database → Règles**, collez le contenu de [firestore.rules](./firestore.rules) et publiez-le. Le compte gérant doit être `djodjojsk6@gmail.com` et avoir une adresse Google vérifiée.
2. Connectez-vous à l’application avec ce compte. Dans **Espace gérant**, configurez les zones et frais de livraison, les créneaux, les numéros de paiement et le point relais. Les coûts coursier sont enregistrés séparément et ne sont lisibles que par le gérant.
3. Créez des articles depuis l’espace gérant. Les documents d’inventaire nécessaires aux réservations sont initialisés automatiquement; les stocks de variantes sont suivis séparément.

Le panier est conservé sur l’appareil. Les commandes et les réservations temporaires, les codes promo, les annonces et les informations de suivi sont stockés dans Firestore. Le paiement n’est pas automatisé : vérifiez chaque acompte auprès de l’opérateur avant d’appuyer sur **Payée**. Le code à 4 chiffres s’affiche ensuite dans **Mes commandes**; vérifiez-le à la remise avant d’appuyer sur **Livrée**.

**Limites du forfait Spark sans serveur :** les réservations expirées sont libérées à la prochaine activité d’un navigateur connecté; aucune tâche ne tourne si personne n’utilise le site. Les règles protègent l’accès aux données, le stock réservé, les créneaux et les compteurs promo, mais une application exécutée dans le navigateur ne peut pas garantir les totaux ou vérifier un paiement comme le ferait un serveur. Contrôlez les détails et le paiement avant d’exécuter une commande. Les images des articles sont stockées dans Firestore; de nombreuses photos ou de gros volumes peuvent atteindre les limites du forfait.

## Déploiement

GitHub Pages sert `index.html` depuis la racine de la branche `main`. Les services Firebase doivent être configurés pour le domaine `sabomuiwa.github.io`.
