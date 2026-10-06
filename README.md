# Graphe CV–Job : modélisation bipartite, enrichissement sémantique par LLM et classification hybride

Projet M2 IASD – Graph Mining (Université Paris-Dauphine Tunis)
Auteurs : Gaies Nader, Harzallah Mohamed — encadrante : Mme Amel Tarifa

## Contenu
| Dossier | Fichier | Rôle |
|---|---|---|
| `notebooks/` | `graph_mining_cv_job.ipynb` | Version nettoyée (seed fixé, cellules dupliquées retirées) — **à utiliser** |
| `notebooks/` | `projet_GraphMining_original.ipynb` | Notebook d'origine, avec ses sorties |
| `docs/` | `rapport_graph_mining.pdf` | Rapport |
| `docs/` | `presentation.pdf` | Support de soutenance |

## Pipeline
1. Génération synthétique de 20 CV et 10 offres (domaines Data, Web, DevOps, Marketing) → graphe biparti NetworkX
2. Graphe interne de compétences par CV (densité)
3. Communautés Louvain, degrés, densité
4. Prédiction de liens : similarité sémantique Sentence-BERT (`all-MiniLM-L6-v2`, seuil 0.75) + Adamic-Adar sur la projection
5. Classification du niveau (junior / intermédiaire / senior) : embeddings + features de graphe → RandomForest
6. Profils polyvalents via la centralité d'intermédiation (betweenness)

## Lancer
```bash
pip install -r requirements.txt
jupyter notebook notebooks/graph_mining_cv_job.ipynb
```
Le premier lancement télécharge le modèle `all-MiniLM-L6-v2` depuis Hugging Face (connexion Internet requise).
