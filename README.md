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
https://github.com/[TON_PSEUDO_GITHUB]/BoutiqueDiayma2025-TD

## 6. Deux bugs trouvés (exploration)
1. **Panier non persistant** → Après ajout d’un produit, F5 → panier vide (session non activée)
2. **Prix total toujours 0 dans le panier** → bug dans Cart.cs (ligne GetTotalValue pas implémentée correctement)

## 7. Points d’arrêt placés et testés
- CartSummaryViewComponent.cs → ligne 12  
- ProductController.cs → ligne 15  
- OrderController.cs → ligne 17  
- CartController.cs → ligne 15  
- Startup.cs → ligne 20  

Tous déclenchés en navigation normale.


## 8. Trace détaillée au démarrage (F11 pas à pas détaillé)
Namespaces / classes / méthodes traversées avant affichage produits :

1. `Program.cs` → `Main()` → `CreateHostBuilder().Build().Run()`
2. `Startup.cs` → `ConfigureServices()` → enregistrement DbContext + Repository
3. `Startup.cs` → `Configure()` → UseRouting + UseEndpoints
4. `ProductController.Index()` → appelé par défaut
5. `ProductController` ligne 15 → `_repo.Products.ToList()`
6. EF Core génère SQL → SELECT * FROM Products
7. Retour View() → Views/Product/Index.cshtml
8. Layout appelle → `CartSummaryViewComponent.Invoke()` ligne 12
9. Affichage final du panier (vide car bug)

→ 12 étapes parcourues en mode "Pas à pas détaillé" (F11)

## 9. Exécutable Windows publié (single file)
Commande exécutée :
```bash
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true /p:PublishTrimmed=true