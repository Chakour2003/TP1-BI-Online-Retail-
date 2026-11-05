# TP1 - Business Intelligence : Cadrage BI et découverte des sources

## Description

Ce projet correspond au premier travail pratique du module **Analyse de Données Multidimensionnelles et Business Intelligence**.

L'objectif est de réaliser le cadrage d'un projet BI à partir du jeu de données **UCI Online Retail**, en passant d'un besoin métier à des questions décisionnelles exploitables.

Le travail consiste à explorer les données avec **Python** et **Pandas**, sans effectuer de nettoyage avancé ni construire un Data Warehouse. Ce TP prépare les étapes suivantes du projet BI.

---

## Objectifs

- Comprendre le besoin métier
- Identifier les questions décisionnelles
- Explorer la structure des données
- Inventorier les sources disponibles
- Identifier les limites de la source
- Relier les colonnes au processus métier

---

## Dataset

Le projet utilise le dataset :

**UCI Online Retail**

Colonnes principales :

- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

---

## Technologies utilisées

- Python
- Pandas
- Jupyter Notebook
- Matplotlib

---

## Analyse réalisée

Le notebook contient notamment :

- Chargement des données
- Exploration de la structure
- Analyse des types de données
- Détection des valeurs manquantes
- Analyse descriptive
- Vérification des colonnes disponibles
- Identification des limites de la source
- Proposition de questions décisionnelles

---

## Résultats

Cette première étape permet de :

- comprendre le processus métier de vente ;
- identifier les informations réellement disponibles ;
- préparer le cadrage du futur Data Warehouse ;
- servir de base aux prochains TP du module.

### 📈 Analyse du Chiffre d'Affaires Mensuel (Online Retail)

Le graphique ci-dessous illustre l'évolution mensuelle du chiffre d'affaires (Revenue) sur la période allant de **décembre 2010 à décembre 2011**.
<img width="1123" height="619" alt="image" src="https://github.com/user-attachments/assets/960c4b27-6d4a-49d4-99d5-d14b7cd51fb0" />

#### 🔍 Points clés de l'analyse :
* **Stabilisation initiale (Déc 2010 – Aoû 2011) :** Le chiffre d'affaires oscille entre 520 000 et 800 000 unités monétaires, avec un creux enregistré en février et avril 2011 (environ 530 000 à 540 000).
* **Forte croissance automnale (Sep 2011 – Nov 2011) :** Une nette accélération des ventes est observée à partir de septembre 2011, atteignant un pic historique en **novembre 2011 avec plus de 1,5 million**. Cette hausse s'explique principalement par la saisonnalité des achats de fin d'année (période pré-navide / Q4).
* **Chute en décembre 2011 :** La baisse constatée en décembre 2011 est liée à un jeu de données tronqué en milieu de mois (collecte incomplète des données sur tout le mois).


### 🏆 Top 10 des Produits Générateurs de Chiffre d'Affaires

Ce graphique à barres horizontales présente les 10 articles ayant généré le chiffre d'affaires le plus élevé dans le jeu de données.
<img width="1164" height="574" alt="image" src="https://github.com/user-attachments/assets/2147ada3-dc86-47fc-a74f-9a324abc5895" />

#### 🔍 Constats principaux :
* **Services vs Produits physiques :** L'élément en tête est `DOTCOM POSTAGE`, correspondant aux frais d'envoi et de livraison professionnels, ce qui indique un impact financier majeur de la logistique sur le revenu global.
* **Best-sellers commerciaux :** Parmi les articles physiques, `REGENCY CAKESTAND 3 TIER` et `PAPER CRAFT , LITTLE BIRDIE` occupent les premières positions en termes de revenus générés.
* **Articles de décoration et accessoires :** On retrouve des produits phares de la boutique tels que `WHITE HANGING HEART T-LIGHT HOLDER`, `PARTY BUNTING` et `JUMBO BAG RED RETROSPOT`.

#### 🛠️ Méthodologie d'agrégation :
```python
top_produits = (
    df_copy.groupby('Description')['Revenue'].sum()
    .sort_values(ascending=False)
    .head(10)
)

#### 🛠️ Méthodologie & Nettoyage des données :
* Exclusion des transactions avec des quantités ou prix unitaires négatifs/nuls ($Quantity > 0$ et $UnitPrice > 0$).
* Filtrage des commandes annulées (identifiables par le préfixe `'C'` dans la colonne `InvoiceNo`).
---


## Auteur

Mohammed Chakour
Étudiant en première année de Master, filière Intelligence Artificielle et Applications.
ENSAB
