# Hospitalisation-DataWarehouse

## Présentation

Ce projet a été réalisé dans le cadre du module **Data Warehousing & Business Intelligence**.

Il consiste à concevoir et mettre en œuvre une plateforme décisionnelle permettant d'analyser les données d'hospitalisation du **Centre Hospitalier Universitaire Ibn Sina (CHU Ibn Sina)**.

La solution est basée sur une architecture **Medallion (Bronze / Silver / Gold)** et utilise les technologies Microsoft SQL Server.

---

## Objectifs du projet

* Concevoir un Data Warehouse dédié à l'analyse des hospitalisations.
* Développer les processus ETL avec SSIS.
* Construire un cube décisionnel avec SSAS.
* Réaliser des tableaux de bord interactifs avec Power BI.
* Fournir des indicateurs d'aide à la décision pour les responsables hospitaliers.

---

## Technologies utilisées

* SQL Server 2022
* SQL Server Integration Services (SSIS)
* SQL Server Analysis Services (SSAS)
* Power BI Desktop
* Git & GitHub

---

## Architecture de la solution

Le projet suit une architecture Medallion composée de :

* **Bronze** : stockage des données brutes.
* **Silver** : nettoyage, validation et transformation des données.
* **Gold** : Data Warehouse en schéma en étoile.
* **Data Marts** : données spécialisées pour les analyses métier.

---

## Fonctionnalités

* Extraction, transformation et chargement des données (ETL).
* Création d'un Data Warehouse en schéma en étoile.
* Construction d'un cube OLAP.
* Calcul de KPIs décisionnels.
* Création de tableaux de bord Power BI.

---

## Auteur

**Nabil Aberouz**

