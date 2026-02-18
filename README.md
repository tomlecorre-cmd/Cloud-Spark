# 🛒 Analyse Big Data & Segmentation Client (PySpark)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Spark](https://img.shields.io/badge/Apache_Spark-PySpark-orange?style=flat&logo=apachespark)
![Machine Learning](https://img.shields.io/badge/ML-Clustering%20%26%20Classification-green)

## 🏫 Contexte Académique
Ce projet a été réalisé dans le cadre du **DU Data Analytics** à l'**Université Paris 1 Panthéon-Sorbonne** (Cours de Cloud Computing).

L'objectif est de démontrer la capacité à traiter un grand volume de données transactionnelles (Big Data) pour en extraire de la valeur décisionnelle en utilisant un environnement distribué.

---

## 🔍 Que fait ce projet ? (Vue d'ensemble)

Ce projet simule le travail d'un Data Scientist dans une entreprise de e-commerce. Nous partons d'un fichier brut contenant 500 000 transactions pour répondre à deux questions business majeures :
1.  **Qui sont nos clients ?** (Segmentation pour adapter le marketing).
2.  **Qui va dépenser beaucoup d'argent ?** (Prédiction pour cibler les futurs VIP).

Le projet suit un pipeline de données complet en 3 étapes :

### 1️⃣ Data Engineering (Nettoyage & ETL)
Les données réelles sont souvent "sales". Avant d'analyser, nous avons dû :
* Supprimer les transactions orphelines (sans identifiant client).
* Filtrer les annulations de commandes (quantités négatives) qui faussent le Chiffre d'Affaires.
* Convertir les formats de dates et de prix pour qu'ils soient lisibles par Spark.
* **Résultat :** Nous passons de 541 000 lignes brutes à **397 000 données fiables**.

### 2️⃣ Segmentation Client (Clustering RFM)
Pour comprendre les comportements, nous avons utilisé la méthode marketing **RFM**. Chaque client est noté sur :
* **R**écence : Date de son dernier achat.
* **F**réquence : Combien de fois a-t-il acheté ?
* **M**ontant : Combien a-t-il dépensé au total ?

En appliquant l'algorithme **Bisecting KMeans**, nous avons découvert 3 groupes de clients :
* 🔴 **Les Inactifs :** N'ont pas acheté depuis longtemps (Risque de départ).
* 🔵 **Les Réguliers :** Achètent de temps en temps, panier moyen.
* 🟢 **Les VIP :** Achètent très souvent et dépensent beaucoup (Cœur de cible).

### 3️⃣ Prédiction (Machine Learning Supervisé)
Nous avons entraîné une Intelligence Artificielle (Régression Logistique) pour qu'elle apprenne à reconnaître automatiquement un client à fort potentiel.
* Le modèle prédit avec **98% de précision** si un client sera un "Gros Dépensier" (> 500€).

---

## 🛠 Technologies Utilisées
* **Langage :** Python
* **Big Data Framework :** Apache Spark (via l'API **PySpark**)
* **Machine Learning (Spark MLlib) :**
    * `VectorAssembler` & `StandardScaler` (Préparation des features)
    * `BisectingKMeans` (Clustering Non-Supervisé)
    * `LogisticRegression` (Classification Supervisée)
* **Environnement :** Google Colab / Jupyter Notebook

## 📂 Structure du Repository
```text
├── Projet_Cloud.ipynb      # Le Notebook complet (Code commenté étape par étape)
├── cloudspark.pdf          # PPT du projet
└── README.md               # Documentation du projet
