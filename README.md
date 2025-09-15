# Système de Recommandation Hybride (MovieLens 100k)

## Contexte
Ce projet présente la construction d’un système de recommandation hybride en Python à partir du jeu de données MovieLens 100k.  
Il a été réalisé dans le cadre d’un projet de portfolio en Data Science.

L’objectif est de comparer différentes approches (contenu, collaboratif, hybride) et d’évaluer leurs performances avec des métriques standards.

---

## Contenu du notebook
Le notebook `SR.ipynb` contient les étapes suivantes :

1. **Chargement et préparation des données**
   - Import des fichiers `u.data` (notes) et `u.item` (films).
   - Nettoyage et reconstruction des genres des films.
   - Création de matrices utilisateur × film.

2. **Approche Content-Based**
   - Représentation des films via leurs genres.
   - Similarité cosinus entre films.
   - Fonction `recommend_similar(title)` pour recommander des films proches en genres.

3. **Collaborative Filtering**
   - Item-based k-NN (similarité cosinus entre films).
   - Implémentation avec shrinkage et normalisation.
   - Factorisation matricielle (SVD via Surprise).

4. **Système Hybride**
   - Combinaison pondérée :  
     \[
     score = \alpha \times \text{content} + (1-\alpha) \times \text{collaboratif}
     \]
   - Tests avec différents α (0 = collaboratif pur, 1 = contenu pur).

5. **Évaluation**
   - Split train/test par utilisateur.
   - Métriques utilisées : Precision@k, Recall@k, NDCG@k.
   - Analyse comparative : content vs CF vs hybride.

6. **Visualisations**
   - Courbes de performance en fonction de α.
   - Interprétation des résultats.

---

## Résultats principaux
- **Collaboratif (SVD / k-NN)** > **Hybride** > **Content-based seul**.  
- Les genres seuls sont trop limités → l’hybride n’améliore pas sans features plus riches.  
- Precision@10 ≈ 9–10 % avec CF, contre 2–3 % avec contenu pur.  

---

## Technologies utilisées
- **Python 3.12**  
- **Pandas / NumPy** (préparation données)  
- **Scikit-learn** (cosine similarity, métriques)  
- **Surprise** (SVD, collaborative filtering)  
- **Matplotlib** (visualisations)

---

## Dataset
- **MovieLens 100k** (1998, GroupLens Research).  
- 100 000 notes de 943 utilisateurs sur 1682 films.  
- Lien : [MovieLens 100k Dataset](https://grouplens.org/datasets/movielens/100k/)

---

## Améliorations possibles
- Enrichir les features contenu (TF-IDF sur synopsis, acteurs, réalisateurs, embeddings).  
- Implémenter une factorisation matricielle plus avancée (ALS, NMF).  
- Intégrer une interface web (Streamlit) pour tester les recommandations en direct.  

---

## ✍️ Auteur
Projet réalisé par **[Ton Nom]**, étudiant en Data Science / Data Engineering.  
