# TP d’analyse de données — Jeu de données « Adult Census Income (UCI) »

> **Choix du dataset**  
> Nous utiliserons le jeu de données **Adult / Census Income** (UCI / OpenML), très connu et librement disponible. Il décrit des individus (employés/actifs) avec des variables socio-professionnelles et une variable cible indiquant si le **revenu annuel** dépasse 50 000 $ (`<=50K` / `>50K`).  Dataset et la description des données se trouve sur : [Lien vers le dataset](https://www.kaggle.com/datasets/uciml/adult-census-income)

> Lien vers la [documentation Python](https://docs.python.org/3/)
---

## 1) Nature des colonnes & fonctions Python utiles

**Tâche**  
Une fois le jeu de données collecté, la première tâche consiste à lister et décrire la nature de chaque colonne du jeu de données. Pour chaque colonne, vous préciserez :
- Le nom de la colonne ;
- Le type de donnée (quantitative, qualitative, discrète, continue, nominale, ordinale, etc.) en utilisant **la terminologie vue en cours** ;
- La signification de la colonne (ce qu’elle représente dans le contexte du jeu de données) ;
- Les valeurs possibles ;
- Les éventuelles valeurs manquantes.

**Outils Python utiles :**
Voici une liste de fonctions Python qui pourront vous aider à réaliser cette tâche. Pour plus de détails sur leur utilisation, reportez-vous au guide Python fourni en cours ou à la documentation officielle :
- `df.head()`
- `df.info()`
- `df.describe()`
- `df.dtypes`
- `df.isna().sum()`
- `df.nunique()`
- `df['colonne'].value_counts()`

N’hésitez pas à utiliser d’autres fonctions ou bibliothèques (comme `pandas`, `numpy`, etc.) si nécessaire.

## 2) Tendance centrale — Calcul & interprétation (à rédiger par vous)

**Tâche**
Calculez les indicateurs de tendance centrale pour les colonnes pertinentes du jeu de données. Pour chaque colonne quantitative analysée, vous fournirez :
- La moyenne arithmétique ;
- La médiane ;
- Le mode (le cas échéant) ;
- Une interprétation claire de la tendance centrale de la colonne, en utilisant la terminologie vue en cours

**Fonctions Python utiles :**
- `df.mean()`
- `df.median()`
- `df.mode()`
- `df.describe()`
- `df['colonne'].skew()`


## 3) Dispersion — Calcul & commentaire

**Tâche**  
Calculez **les indicateurs de dispersion** pour les colonnes quantitatives de votre jeu de données. Pour chaque colonne analysée, vous présenterez :
- L’étendue (différence entre la valeur maximale et minimale) ;
- La variance ;
- L’écart-type ;
- L’intervalle interquartile (Q1, Q3, et écart interquartile) ;
- **Une interprétation de la dispersion des données**, en utilisant la terminologie vue en cours ainsi que la justification votre interprétation en lien avec la nature de la colonne et le contexte du jeu de données.

**Fonctions Python utiles :**
- `df.max()` 
- `df.min()`
- `df.var()`
- `df.std()`
- `df.quantile([0.25, 0.75])`
- `df['colonne'].describe()`

## 4) « Ai-je le droit de… ? » — Validité d’un calcul selon le type de données

**Tâche**  
Prenez la colonne « workclass » (exemples de valeurs : Private, Self-emp-not-inc, Local-gov, …) du jeu de données Adult Census Income et envisagez d’y calculer la moyenne arithmétique.

**Question :**
Pour cette colonne et ce calcul statistique :

- **Est-il pertinent de calculer la moyenne arithmétique sur la colonne « workclass » ?**
Justifiez votre réponse en précisant le type de donnée (qualitative nominale) et la nature du calcul (mesure de tendance centrale réservée aux données quantitatives).
- **Pourquoi ce calcul n’est-il pas adapté ?**
Expliquez les raisons théoriques (échelle de mesure, absence de relation numérique entre les modalités) et proposez une alternative pertinente (par exemple : le mode ou une analyse de fréquence).

**Remarque :**
Appuyez votre réponse sur la terminologie statistique vue en cours.


## 5) Visualisations — Choix pertinents (rappel) & fonctions `matplotlib.pyplot`

> **Rappel pédagogique** : *Une représentation qui n’illustre aucun fait utile n’apporte rien en statistique.* Choisissez **le bon graphique** pour **le bon type de variable** et **formulez toujours un commentaire** : *quelle information exploitable en tire-t-on ?*


### 5.1 Rappel des correspondances variable → graphique

- **Quantitative (1 variable)** :  
  - **Histogramme** (forme, asymétrie, outliers)  
  - **Courbe de densité** (si ajoutée), **ECDF** (fonction de répartition empirique)  
  - **Boîte à moustaches** (dispersion, outliers)  
- **Quantitative vs qualitative (2 variables)** :  
  - **Boîtes à moustaches par groupe** (ex. `hours-per-week` par `salary`)  
  - **Barres des moyennes/IC** (avec prudence)  
- **Quantitative vs quantitative** :  
  - **Nuage de points** (relation, linéarité, hétéroscédasticité)  
  - **Hexbin** pour gros volumes  
- **Catégorielle (1 variable)** :  
  - **Diagramme en barres** (fréquences), **Pareto** (barres triées décroissantes + cumul)  
  - **(Camembert généralement déconseillé)**  
- **Catégorielle vs catégorielle** :  
  - **Carte de chaleur** d’un **tableau de contingence** (fréquences ou pourcentages)

### 5.2 Fonctions `matplotlib.pyplot` utiles (sans explications détaillées)

- Import de base : `import matplotlib.pyplot as plt`  
- Histogramme : `plt.hist(x, bins=...)`  
- Boîte à moustaches : `plt.boxplot(x, vert=True)` ; groupé : `plt.boxplot([x1,x2,...], labels=[...])`  
- Nuage de points : `plt.scatter(x, y, alpha=...)`  
- Hexbin : `plt.hexbin(x, y, gridsize=...) ; plt.colorbar()`  
- Barres : `plt.bar(categories, counts)` ; horizontales : `plt.barh(categories, counts)`  
- Courbe (ECDF manuelle) : trier `x`, puis `plt.plot(x_sorted, np.arange(1,len(x)+1)/len(x))`  
- Carte de chaleur simple : `plt.imshow(matrix, aspect='auto') ; plt.colorbar()`  
- Mise en forme : `plt.title`, `plt.xlabel`, `plt.ylabel`, `plt.xticks(rotation=...)`, `plt.legend`, `plt.tight_layout`  
- Sauvegarde : `plt.savefig('figure.png', dpi=300)`


## Format de rendu du TP1

**Date limite de rendu : Aujourd’hui avant 12h30.**

**1. Formats acceptés (au choix) :**
- **Fichier Jupyter Notebook (.ipynb) :*
    - Le fichier doit contenir **le code exécuté, les résultats affichés **(sorties des cellules), ainsi que l’analyse et l’interprétation détaillée de chaque résultat.
    - **Points bonus** pour les rendus sous ce format (clarté, reproductibilité, intégration code/analyse).
- **Document PDF :**
    - Le document doit inclure :
        - **Le code** (copié depuis votre environnement de travail, bien mis en forme).
        - **Les résultats** (tableaux, valeurs, graphiques).
        - **L’interprétation** et les commentaires pour chaque résultat (voir consignes ci-dessous).

**2. Consignes de rigueur et d’évaluation :**

- **Rigueur scientifique :**
    - Utilisez **systématiquement la terminologie vue en cours**.
    - **Tout écart de terminologie ou approximation sera pénalisé.**
- **Interprétation obligatoire :**
    - Pour **chaque résultat**, répondez aux questions suivantes :
        - Que signifie cette valeur dans le contexte du jeu de données 
        - Si vous deviez présenter ce résultat à un métier, comment l’expliqueriez-vous et quel impact pourrait-il avoir ?
- **Exemple d’interprétation attendue :**
> « La moyenne d’âge est de 38,6 ans. Cela signifie que la population étudiée est plutôt adulte, avec une expérience professionnelle significative. Pour le métier, cela peut indiquer une main-d’œuvre expérimentée, mais aussi un besoin de renouvellement ou de formation pour les plus jeunes. »

**3. Conseils pour maximiser votre note :**
- **Soyez précis et concis** : évitez les phrases vagues, allez à l’essentiel.
- **Reliez toujours les résultats au contexte métier** : montrez que vous comprenez l’impact des données.
- **Vérifiez l’orthographe et la mise en forme** : un rendu soigné facilite la lecture et la correction.


**Bon travail ! N’hésitez pas à relire vos interprétations pour vous assurer qu’elles répondent bien aux attentes.**


