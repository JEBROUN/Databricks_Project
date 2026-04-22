# Azure Databricks Streaming Pipeline : Auto Loader & Key Vault
Ce projet démontre la mise en place d'un pipeline d'ingestion de données en streaming (architecture Medallion - Couche Bronze) utilisant Databricks Auto Loader et sécurisé par Azure Key Vault.

#  Architecture du Projet
- Le pipeline suit les meilleures pratiques de l'ingénierie de données moderne sur Azure :

- Source : Fichiers CSV déposés dans un conteneur Azure Data Lake Storage (ADLS Gen2).

- Ingestion : Utilisation de Databricks Auto Loader (cloudFiles) pour une détection incrémentale et efficace des nouveaux fichiers.

- Sécurité : Authentification via un Secret Scope lié à Azure Key Vault (Zero Clear-Text Credentials).

- Destination : Stockage au format Delta Lake (Table Bronze) avec gestion des Checkpoints pour garantir la tolérance aux pannes.

#  Stack Technique
- Cloud : Microsoft Azure

- Plateforme : Azure Databricks

- Langage : PySpark

- Stockage : ADLS Gen2 & Delta Lake

- Sécurité : Azure Key Vault & RBAC (Role-Based Access Control)

- Orchestration : Structured Streaming & Checkpointing

#  Configuration de la Sécurité (Point Fort)
Une attention particulière a été portée à la cybersécurité :

- Création d'un Azure Key Vault pour stocker les clés d'accès au stockage.

- Configuration d'un Secret Scope dans Databricks.

- Attribution du rôle Key Vault Secrets User à l'identité système AzureDatabricks pour permettre une lecture sécurisée sans exposer les clés dans le code.


# Fonctionnalités Clés
Auto Loader : Gestion automatique de l'évolution du schéma et détection des fichiers sans lister tout le répertoire (optimisation des coûts/performances).

Auditability : Ajout systématique d'une colonne ingested_at pour la traçabilité des données.

Résilience : Utilisation de Checkpoints permettant de reprendre le flux exactement là où il s'est arrêté en cas d'interruption.

# Comment l'utiliser ?
- Configurer les Widgets Databricks avec vos paramètres Azure (Storage Account, Container, Scope Name).

- Déposer vos fichiers CSV dans le dossier /input/ de votre conteneur.

- Lancer le notebook. Le dashboard de streaming affichera les pics d'ingestion en temps réel.

spark_streaming.png