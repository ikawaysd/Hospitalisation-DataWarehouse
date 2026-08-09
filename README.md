# Hospitalisation Data Warehouse

## Présentation

Ce projet a été réalisé dans le cadre du module **Data Warehousing & Business Intelligence**.

Il consiste à concevoir et mettre en œuvre une plateforme décisionnelle permettant d'analyser les données d'hospitalisation du **Centre Hospitalier Universitaire Ibn Sina (CHU Ibn Sina)**.

La solution repose sur une architecture **Medallion (Bronze / Silver / Gold)** et utilise les technologies Microsoft pour l'intégration, le stockage, la modélisation décisionnelle et la visualisation.

---

## Objectifs du projet

Les principaux objectifs sont :

* Concevoir un **Data Warehouse** dédié à l'analyse des hospitalisations.
* Mettre en place une architecture **Medallion** composée des couches Bronze, Silver et Gold.
* Développer les processus **ETL avec SSIS**.
* Construire un **cube décisionnel avec SSAS**.
* Réaliser des **tableaux de bord interactifs avec Power BI**.
* Fournir des indicateurs permettant de faciliter l'analyse et la prise de décision.

---

## Architecture de la solution

L'architecture du projet est organisée selon le modèle Medallion :

```text
Sources de données
       │
       ▼
   ┌─────────┐
   │ BRONZE  │
   │ Données │
   │ brutes  │
   └────┬────┘
        │ SSIS
        ▼
   ┌─────────┐
   │ SILVER  │
   │ Nettoyage│
   │ et       │
   │transformation│
   └────┬────┘
        │ SSIS
        ▼
   ┌─────────┐
   │  GOLD   │
   │   Data  │
   │Warehouse│
   └────┬────┘
        │
        ├──────────────► Data Marts
        │
        ▼
      SSAS
    Cube OLAP
        │
        ▼
    Power BI
   Dashboards
```

### Bronze

La couche **Bronze** assure le stockage des données extraites des sources, dans leur état initial.

### Silver

La couche **Silver** permet le nettoyage, la validation et la transformation des données avant leur intégration dans le Data Warehouse.

### Gold

La couche **Gold** constitue la couche décisionnelle. Elle contient le **Data Warehouse**, organisé selon une modélisation dimensionnelle.

### Data Marts

Des **Data Marts** permettent de préparer les données selon les besoins d'analyse métier.

---

## Processus ETL

Les processus ETL sont développés avec **SQL Server Integration Services (SSIS)**.

Le processus général est :

```text
Extraction
    ↓
Bronze
    ↓
Nettoyage / Transformation
    ↓
Silver
    ↓
Chargement
    ↓
Gold / Data Marts
```

Les packages SSIS sont disponibles dans le dossier :

```text
ssis-packages/
```

---

## Cube décisionnel

La modélisation multidimensionnelle est réalisée avec **SQL Server Analysis Services (SSAS)**.

Le cube permet notamment de travailler avec :

* des mesures décisionnelles ;
* des dimensions d'analyse ;
* des hiérarchies ;
* des indicateurs KPI.

Les fichiers de la solution SSAS sont disponibles dans :

```text
ssas-cube/
```

---

## Tableaux de bord

Les tableaux de bord sont réalisés avec **Power BI Desktop**.

Ils permettent de présenter les résultats sous forme de visualisations interactives et de faciliter l'analyse des données d'hospitalisation.

Le fichier Power BI est disponible dans :

```text
powerbi/
```

---

## Technologies utilisées

* **Microsoft SQL Server**
* **SQL Server Integration Services (SSIS)**
* **SQL Server Analysis Services (SSAS)**
* **Power BI Desktop**
* **Git**
* **GitHub**

---

## Structure du dépôt

```text
Hospitalisation-DataWarehouse/
│
├── sql-scripts/
│   └── Scripts SQL
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

## Prérequis

Pour reproduire le projet, les principaux composants nécessaires sont :

* Microsoft SQL Server ;
* SQL Server Integration Services (SSIS) ;
* SQL Server Analysis Services (SSAS) ;
* Visual Studio avec les extensions nécessaires pour SSIS et SSAS ;
* Power BI Desktop ;
* Git.

---

## Installation et exécution

Les scripts SQL nécessaires sont disponibles dans :

```text
sql-scripts/
```

Les packages d'intégration sont disponibles dans :

```text
ssis-packages/
```

La solution SSAS est disponible dans :

```text
ssas-cube/
```

Le rapport Power BI est disponible dans :

```text
powerbi/
```

Les instructions détaillées d'installation et de configuration sont disponibles dans :

```text
INSTALLATION.md
```

---

## Livrables

Le dépôt contient les principaux livrables du projet :

* Scripts SQL ;
* Packages SSIS ;
* Solution SSAS ;
* Rapport Power BI ;
* Schémas d'architecture et de modélisation ;
* Documentation technique ;
* Instructions d'installation.

---

## Auteur

**Nabil Aberouz**
