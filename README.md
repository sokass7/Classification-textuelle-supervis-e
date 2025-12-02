# Classification supervisée de textes et données médicales  
Projet réalisé dans le cadre du Master 1 Langue & Informatique à Sorbonne Université. L'objectif est de comparer plusieurs modèles de classification supervisée sur un corpus textuel.
**Auteures : Soukaïna Bouhaid & Amina-M’bariqui Ahamada**

---

## 🎯 Objectifs
Ce projet vise à comparer plusieurs algorithmes de **classification supervisée** sur deux jeux de données différents :

1. **Student Health** (données médicales et physiologiques)
2. **Short Text Humor Detection** (textes courts annotés selon leur caractère humoristique)

L’objectif est :
- de tester plusieurs classifieurs,
- d’évaluer leurs performances,
- d’optimiser les résultats (temps d’exécution et accuracy),
- d’identifier les modèles les plus adaptés à chaque problématique.

---

## 📂 Jeux de données

### 1) **Student Health Dataset**
Source : Kaggle  
Variables : données physiologiques, données catégorielles (mood, sleep, etc.)  
Variable cible : **Stress_Level_Biosensor** (discrétisée en *faible / moyen / élevé*)

Points clés :
- encodage OneHotEncoder pour variables catégorielles  
- transformation de la variable cible avec 'pandas.cut'  
- dataset déséquilibré → attention aux métriques  

---

### 2) **Short Text Humor Detection**
Source : Kaggle  
200 000 textes courts annotés (humor = True/False)

Points clés :
- vectorisation CountVectorizer puis TfidfVectorizer  
- réduction du temps d’exécution du modèle SVM  
- tests sur n-grammes, stopwords, max_features  

---

## 🧠 Algorithmes testés
Les modèles suivants ont été comparés :

- Perceptron  
- Logistic Regression  
- Random Forest  
- Support Vector Machine (SVM)

---

## ⚙️ Méthodologie générale
1. Analyse exploratoire  
2. Nettoyage & prétraitement  
3. Vectorisation (OneHotEncoder, CountVectorizer, TF-IDF)  
4. Séparation train/test (70% / 30%)  
5. Entraînement & comparaison des classifieurs  
6. Analyse des erreurs  
7. Optimisation (sélection de features, changement de vectoriseur)

---

## 🏆 Principaux résultats

### **Student Health**
- SVM est le meilleur classifieur (accuracy ≈ 0.60)
- Modèles linéaires très rapides mais moins efficaces
- Importance forte des variables :
  - Health_Risk_Level_Low
  - Health_Risk_Level_High

### **Humor Detection**
- Sans prétraitement : accuracy ≈ 0.91 mais SVM très lent  
- Avec CountVectorizer : temps réduit, accuracy 0.93  
- Avec TF-IDF : execution ~316 sec, accuracy ≈ 0.82

Conclusion :
- TF-IDF réduit fortement le temps
- CountVectorizer + SVM = meilleur compromis performance / vitesse
