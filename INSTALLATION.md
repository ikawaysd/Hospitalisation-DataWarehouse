# Installation — Hospitalisation Data Warehouse

## Présentation

Ce document décrit les étapes nécessaires pour installer et exécuter la plateforme décisionnelle **Hospitalisation Data Warehouse — CHU Ibn Sina**.

Le projet utilise :

* Microsoft SQL Server ;
* SQL Server Integration Services (SSIS) ;
* SQL Server Analysis Services (SSAS) ;
* Visual Studio 2022 ;
* Power BI Desktop.

> **Important :** le dépôt ne contient pas de sauvegarde de base de données `.bak`. La base `HospitalDWH` doit donc être créée à partir du script SQL fourni dans `sql-scripts/`.

Les données utilisées dans le projet sont **entièrement synthétiques**, les données réelles du CHU étant confidentielles.

---

## Étape 1 — Créer la base de données

Avant d'exécuter les projets SSIS et SSAS, il faut créer la base de données `HospitalDWH`.

### 1. Ouvrir SQL Server Management Studio

Ouvrir **SQL Server Management Studio (SSMS)** et se connecter à son instance SQL Server locale.

### 2. Exécuter le script SQL

Le script principal est disponible dans :

```text
sql-scripts/HospitalDWHSCRIPT.sql
```

Ouvrir ce fichier dans SSMS et l'exécuter.

Le script permet de créer la structure nécessaire à la base **HospitalDWH**.

Après l'exécution, vérifier que la base apparaît dans l'Explorateur d'objets :

```text
Databases
└── HospitalDWH
```

---

## Étape 2 — Ouvrir le projet SSIS

Les fichiers du projet SSIS sont disponibles dans :

```text
ssis-packages/
```

Ouvrir le projet avec **Visual Studio 2022**.

L'extension **SQL Server Integration Services Projects** est nécessaire.

### Configuration de la connexion

Le gestionnaire de connexion doit être adapté à l'instance SQL Server utilisée localement.

Dans Visual Studio :

1. Ouvrir le projet SSIS.
2. Accéder aux **Connection Managers**.
3. Ouvrir la connexion utilisée par le projet.
4. Modifier le **Server name** avec le nom de votre instance SQL Server.
5. Sélectionner la base :

```text
HospitalDWH
```

6. Utiliser l'authentification correspondant à votre configuration SQL Server.

Après configuration, le package SSIS peut être exécuté afin de rejouer le processus ETL :

```text
Bronze → Silver → Gold
```

---

## Étape 3 — Ouvrir le projet SSAS

Les fichiers de la solution SSAS sont disponibles dans :

```text
ssas-cube/
```

Le projet utilise le fichier :

```text
SSAS_Hospit_v3.dwproj
```

Ouvrir la solution avec **Visual Studio 2022**.

L'extension **SQL Server Analysis Services Projects** est nécessaire.

### Configuration de la source de données

Avant le déploiement :

1. Ouvrir la source de données du projet.
2. Modifier la chaîne de connexion.
3. Pointer vers l'instance SQL Server utilisée localement.
4. Sélectionner la base :

```text
HospitalDWH
```

5. Configurer l'impersonation selon l'environnement local.

### Configuration du déploiement

Dans les propriétés du projet SSAS :

1. Ouvrir les propriétés du projet.
2. Accéder à l'onglet **Deployment**.
3. Modifier le champ **Server**.
4. Indiquer le nom de l'instance SSAS utilisée.

Après configuration :

```text
Deploy
   ↓
Process
   ↓
Full Processing
```

Le cube peut ensuite être utilisé pour l'analyse décisionnelle.

---

## Étape 4 — Ouvrir le rapport Power BI

Le fichier Power BI est disponible dans :

```text
powerbi/
```

Ouvrir le fichier `.pbix` avec **Power BI Desktop**.

Le rapport utilise une connexion au modèle décisionnel SSAS.

Si la connexion ne fonctionne pas automatiquement sur une autre machine :

1. Ouvrir les paramètres de la source de données.
2. Modifier le serveur Analysis Services.
3. Indiquer l'instance SSAS locale.
4. Vérifier la base et le cube utilisés.
5. Actualiser les données.

---

## Étape 5 — Vérification

Après l'installation, vérifier les éléments suivants :

### SQL Server

```text
HospitalDWH
```

La base doit être accessible et contenir les tables nécessaires au Data Warehouse.

### SSIS

Le package doit pouvoir exécuter le pipeline :

```text
Bronze → Silver → Gold
```

### SSAS

Le projet doit être déployé et traité correctement.

### Power BI

Le rapport doit pouvoir se connecter au modèle décisionnel et afficher les tableaux de bord.

---

## Structure des livrables

```text
Hospitalisation-DataWarehouse/
│
├── sql-scripts/
│   └── HospitalDWHSCRIPT.sql
│
├── ssis-packages/
│   └── Packages SSIS
│
├── ssas-cube/
│   └── Solution SSAS
│
├── powerbi/
│   └── Rapport Power BI
│
├── diagrams/
│   └── Schémas du projet
│
├── docs/
│   └── Documentation technique
│
├── INSTALLATION.md
└── README.md
```

---

## Données

Les données utilisées dans ce projet sont **synthétiques** et ont été générées dans le cadre du projet.

Aucune donnée réelle et confidentielle du **CHU Ibn Sina** n'est distribuée dans ce dépôt.

---

## Remarque

Les paramètres de connexion SQL Server et SSAS peuvent varier selon l'environnement de la machine utilisée.

Il est donc nécessaire d'adapter les noms des serveurs et les connexions avant l'exécution des packages SSIS, le déploiement du cube SSAS et l'ouverture du rapport Power BI.
