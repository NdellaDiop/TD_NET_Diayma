# Boutique Diayma
**Étudiante :** Ndeye Ndella DIOP
**Date :** 25 novembre 2025

## 1. Code récupéré et exécuté
git clone https://github.com/devehod/BoutiqueDiayma2025.git puis je me suis placée dans le dossier BoutiqueDiayma2025 toujours dans le dossier je fais un code . qui me permet d’ouvrir VS code dans le dossier racine du projet .


## 2. Projets de la solution
Un seul projet dans la solution :
- **Diayma** → ASP.NET Core MVC (.csproj)

## 3. Version SDK .NET utilisée
Le projet utilise le framework .NET Core 2.0 et ASP.NET Core 2.0.6.

## 4. SDK installé
Pour exécuter le projet correctement, l'installation du SDK .NET Core 2.1 est nécessaire (compatibilité pour la version 2.0). Je tenais à préciser que je suis sous ubuntu.
Commande d'installation : sudo apt update , sudo apt install dotnet-sdk-2.1

## 5. Dépôt GitHub personnel
https://github.com/NdellaDiop/TD_NET_Diayma

## 6. Deux bugs trouvés (exploration)
1. Langue espagnol non prise en compte
2. Problème de Stock après Commande

## 7. Points d’arrêt placés et testés
- CartSummaryViewComponent.cs → ligne 12
- ProductController.cs → ligne 15
- OrderController.cs → ligne 17
- CartController.cs → ligne 15
- Startup.cs → ligne 20

Tous déclenchés en navigation normale.


## 8. Quels sont les namespaces, classes et méthodes visités avant l’affichage des produits sur l’écran d’accueil de votre navigateur ? Choisissez le mode approprié selon le contexte, "Pas à pas détaillé", "Pas à pas principal" ou "Pas à pas sortant". Namespaces / classes / méthodes traversées avant affichage produits :

Le mode de débogage le plus approprié est le "Pas à pas détaillé" (Step Into ou F11), car il permet d'entrer dans l'implémentation de chaque méthode (comme le chargement des données ou l'initialisation des composants) pour observer le flux complet du code.

Voici la séquence des appels exécutés par le framework MVC avant que la page d'accueil de la boutique ne soit affichée :

Séquence d'appels visités

    Phase d'Initialisation (Démarrage)

        Namespace/Classe/Méthode : P2FixAnAppDotNetCode.Startup.ConfigureServices()

        Rôle : Le framework configure les services nécessaires, notamment l'injection de dépendances pour les contrôleurs et les composants (ICart, IProductRepository, etc.).

    Phase d'Exécution de la Route

        Namespace/Classe/Méthode : P2FixAnAppDotNetCode.Controllers.ProductController.Index()

        Rôle : Le système de routage reconnaît la racine (/) et exécute l'action par défaut, qui est la méthode Index() du ProductController.

    Phase de Chargement des Données

        Namespace/Classe/Méthode : P2FixAnAppDotNetCode.Models.ProductRepository.GetAllProducts()

        Rôle : La méthode du contrôleur appelle la couche de données (le Repository) pour récupérer la liste des produits à afficher sur l'écran.

    Phase d'Affichage du Composant de Vue

        Namespace/Classe/Méthode : P2FixAnAppDotNetCode.Components.CartSummaryViewComponent.Invoke()

        Rôle : Avant de rendre la vue principale, le composant de vue (appelé par un tag dans le code HTML de la page) est exécuté pour générer le résumé du panier.

    Phase de Rendu de la Vue

        Namespace/Classe/Méthode : P2FixAnAppDotNetCode.Controllers.ProductController.View(products)

        Rôle : La méthode Index retourne le résultat, passant le modèle de données à la vue (fichier .cshtml) pour que le HTML soit généré et envoyé au navigateur.

9. Affichage final du panier (vide car bug)

→ 12 étapes parcourues en mode "Pas à pas détaillé" (F11)

## 9. Exécutable Windows publié (single file)
Commande exécutée :
/home/ndella/dotnet/dotnet publish Diayma.csproj --self-contained -r win-x64 -c Release --output ../DeployWindows

## 10. LIEN DRIVE
https://drive.google.com/file/d/1QEhkINMbF80dGLAS4CYRg85wmtAtN6Kz/view?usp=sharing

