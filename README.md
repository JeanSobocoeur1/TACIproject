# TACI Project – Alignement culturel et développement inclusif dans les PEID

## Description

Ce dépôt contient les données et le code Python associés à l'article :

**"Alignement culturel et développement inclusif dans les Petits États Insulaires : une analyse par méthodes mixtes"**
Auteur : Jean Sobocoeur CHRISPIN

L'article teste la théorie de l'alignement sur la culture inclusive (TACI) sur un panel de 10 Petits États Insulaires en Développement (PEID) sur la période 2006-2024, combinant méthodes économétriques et qualitatives.

## Structure du dépôt
TACIproject/
├── README.md
├── main.py
├── 66d55de0-9d33-4211-a02d-b0d0331a3ad1_Data.csv
├── P_Data_Extract_From_Worldwide_Governance_Indicators 216 countries.xlsx
├── common-good-justifications-score.csv
├── democratic-culture-index-eiu.csv
├── elite-consultations-score.csv
├── hdi-vs-augmented-hdi.csv
├── justified-political-positions-score.csv
├── participatory-democracy-index.csv
├── physical-integrity-rights-index-vdem.csv
├── political-participation-index-eiu.csv
├── political-polarization-score.csv
└── sids_outputs/
├── panel_sids.csv
├── westerlund_results.csv
├── westerlund_country_results.csv
├── causality_ecm_results.csv
└── threshold_analysis_complete.png

text

## Données

Les données proviennent des sources publiques suivantes :

| Source | Variables |
|--------|-----------|
| Banque mondiale (WDI) | PIB par tête (PPA) |
| Economist Intelligence Unit (EIU) | Culture démocratique, participation politique, polarisation |
| V-Dem | Engagement des élites, intégrité physique, consultation des élites |
| Worldwide Governance Indicators (WGI) | État de droit, efficacité gouvernementale, contrôle de la corruption |

Toutes les variables explicatives ont été standardisées sur le panel mondial (144 pays, 2006-2024) avant extraction du sous-échantillon PEID.

## Code

Les scripts Python réalisent les analyses suivantes :

1. **Chargement et nettoyage des données** – Construction du panel PEID
2. **Tests de stationnarité** – ADF, Levin-Lin-Chu, Im-Pesaran-Shin, Hadri, Fisher
3. **Tests de cointégration** – Méta-analyse de Fisher (1932) par pays
4. **Tests de causalité de Granger** – Hurlin & Venet (2001) avec bootstrap (999 réplications)
5. **Modèle à seuil** – Hansen (1999) pour la culture démocratique et l'engagement des élites
6. **Analyses qualitatives** – Process-tracing et contrefactuels (documentation séparée)

## Principaux résultats

| Résultat | Valeur |
|----------|--------|
| Seuil culture démocratique (c*) | -1,093 (p < 0,001) |
| Seuil engagement des élites (e*) | 0,397 (p < 0,01) |
| Cointégration (Fisher) | p < 0,001 |
| Causalité de Granger | Significative pour les 5 dimensions TACI |

**Position d'Haïti** : Au-dessus du seuil culturel mais en dessous du seuil d'engagement des élites.

## Reproduction

### Prérequis

```bash
pip install pandas numpy scipy statsmodels matplotlib openpyxl requests
Exécution
bash
python main.py
Environnement
Le code a été développé et testé sous Python 3.9+ dans Google Colab. L'exécution locale est également possible.

Résultats générés
Après exécution, le dossier sids_outputs/ contient :

Fichier	Description
panel_sids.csv	Panel final des 10 PEID
westerlund_results.csv	Statistiques Gt et Pt du test de Westerlund
westerlund_country_results.csv	Coefficients ECM par pays
causality_ecm_results.csv	Résultats des tests de causalité
threshold_analysis_complete.png	Graphique des seuils (Hansen)
Référence
Chrispin, J. S. (2026). Alignement culturel et développement inclusif dans les Petits États Insulaires : une analyse par méthodes mixtes.

Licence
Ce contenu est mis à disposition sous licence MIT.

Contact
Jean Sobocoeur CHRISPIN – jean-sobocoeur.chrispin@ius.education
