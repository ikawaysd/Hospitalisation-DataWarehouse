=====================================================================
PROJET : Plateforme Décisionnelle Hospitalisation — CHU Ibn Sina
Note pour l'ouverture du projet (SQL Server / SSIS / SSAS)
=====================================================================

Ce zip ne contient pas de sauvegarde de base de données (.bak) : 
 ainsi que les projets Visual
Studio (SSIS et SSAS) et le rapport / la présentation.

---------------------------------------------------------------------
ETAPE 1 — Recréer la base de données (obligatoire avant tout le reste)
---------------------------------------------------------------------
le fichier .bak
---------------------------------------------------------------------
ETAPE 2 — Ouvrir le projet SSIS
---------------------------------------------------------------------

Dossier /SSIS. Ouvrir le fichier .sln avec Visual Studio 2022
 "SQL Server Integration Services Projects" nécessaire).

A l'ouverture, le gestionnaire de connexion du projet pointe vers mon
serveur local. Il faut le reconfigurer sur votre propre instance :

  - Dans l'Explorateur de solutions > Connection Managers >
    double-clic sur la connexion existante.
  - Server name : remplacer par le nom de VOTRE instance SQL Server
    (celui utilisé pour vous connecter dans SSMS).
  - Database : HospitalDWH (déjà recréée à l'étape 1).
  - Authentification Windows.

Vous pouvez ensuite exécuter le package (F5) pour rejouer tout le
pipeline ETL (Bronze -> Silver -> Gold) tel que documenté dans le
rapport, section "ETL avec SSIS".

---------------------------------------------------------------------
ETAPE 3 — Ouvrir le projet SSAS
---------------------------------------------------------------------

Dossier /SSAS. Ouvrir le fichier .sln avec Visual Studio 2022
(extension "SQL Server Analysis Services Projects" nécessaire, et
un moteur SSAS en mode Multidimensionnel installé sur votre machine).

Deux éléments à reconfigurer avant de déployer :

  1. Source de données : ouvrir HospitalDWH.ds > modifier la chaîne
     de connexion pour pointer vers votre instance SQL Server et la
     base HospitalDWH. Impersonation Information : choisir
     "Use the credentials of the current user".

  2. Propriétés de déploiement : clic droit sur le projet >
     Propriétés > onglet Déploiement > champ "Server" : remplacer
     par le nom de VOTRE instance SSAS (visible dans les Services
     Windows sous "SQL Server Analysis Services (NOM_INSTANCE)").

Ensuite : clic droit sur le projet > Deploy, puis clic droit sur la
base > Process (Traitement complet).

---------------------------------------------------------------------
ETAPE 4 — Power BI
---------------------------------------------------------------------

Ouvrir le fichier .pbix. Si la connexion Live ne se met pas à jour
automatiquement : Transformer les données > Paramètres de la source
de données > modifier la connexion Analysis Services (serveur / base
/ cube) pour pointer vers votre instance SSAS.

---------------------------------------------------------------------
NOTE
---------------------------------------------------------------------

Les données utilisées sont entièrement synthétiques (générées pour ce
projet), les données réelles du CHU étant confidentielles. Le rapport
détaille les difficultés techniques réellement rencontrées et
résolues durant la construction (section "Difficultés Rencontrées et
Solutions").
