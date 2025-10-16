# TP : Analyse bivariée du dataset *Adult Census Income*

## Objectifs pédagogiques

Ce TP a pour but de te faire pratiquer les **analyses bivariées** sur un jeu de données réel et riche : le dataset **Adult Census Income**.  
Tu vas explorer les **relations entre deux variables à la fois**, qu’elles soient quantitatives ou qualitatives.

À la fin du TP, tu sauras :
- Visualiser des relations entre variables
- Interpréter des corrélations et des régressions simples
- Utiliser des outils graphiques et statistiques pour explorer des liens entre deux variables


## 1. Relations entre deux variables quantitatives

Nous allons commencer par les variables numériques continues (ex : `age`, `hours-per-week`, `capital-gain`, `education-num`).

### 1.1 Visualisation par nuage de points `scatterplot`

1. Trace un nuage de points entre age et hours-per-week.
- Que peux-tu dire de la relation ?
- Observe-tu une tendance linéaire ?
- Y a-t-il des valeurs extrêmes / abérantes ?

2.Fais de même pour education-num et capital-gain.
- Interprète la dispersion.

### 1.2 Corrélation linéaire

1. Calcule la corrélation de Pearson entre age et hours-per-week.
- Quelle est la valeur ?
- Est-ce une corrélation forte, faible ou inexistante ?

2. Compare avec la corrélation entre education-num et hours-per-week.
- Lesquelles semblent le plus liées ?

3. Utilise la fonction suivante pour afficher une matrice de corrélation de toutes les variables numériques : 

```python
plt.figure(figsize=(10,8))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm", center=0)
plt.title("Matrice de corrélation")
plt.show()
```

#### Questions :
- Quelles sont les paires de variables les plus corrélées ?
- As-tu des corrélations négatives ? Que signifient-elles ici ?


## 2. Régression linéaire simple

### 2.1 Ajustement d’un modèle linéaire

Prenons par exemple hours-per-week en fonction de age.

```python
sns.lmplot(data=df, x="age", y="hours-per-week", line_kws={"color":"red"})
plt.show()
```

- Observe la droite de régression.
- Est-elle ascendante ou descendante ?
- Que peux-tu dire de la pente (positive/négative) ?
- L’ajustement semble-t-il pertinent visuellement ?

### 2.2 Régression sur une autre paire

Fais la même analyse pour :
- `education-num` vs `age`
- `education-num` vs `capital-gain`

#### Questions :

- Quelle relation semble la plus "forte" visuellement ?
- Que peut-on en conclure sur les revenus et le niveau d’éducation ?


## 3. Relations entre une variable quantitative et une variable qualitative

Nous allons maintenant examiner comment une variable quantitative varie selon les modalités d’une variable qualitative.

### 3.1 Boxplots et violinplots

1. Trace un boxplot de hours-per-week en fonction du genre (sex).

```python
sns.boxplot(data=df, x="sex", y="hours-per-week")
plt.show()
```

#### Questions :

- Que remarques-tu ?
- Quelle catégorie travaille en moyenne plus d’heures ?
- Les distributions sont-elles symétriques ou asymétriques ?
2. Fais un violinplot pour la même relation.
3. Reproduis l’analyse pour `education` vs `hours-per-week`
- Quelle tendance observes-tu entre le niveau d’étude et les heures de travail ?

### 3.2 Moyennes par groupe

1. Calcule la moyenne et l’écart-type de `hours-per-week` selon sex
2. Compare avec la variable income :
- Calcule la moyenne de age et education-num selon les catégories income (<=50K et >50K).
- Qu’observes-tu ?


**Question:** 
1. Donner votre observation sur comment analyses différentes formes de relations bivariées entre dfférents types de variables. 
2. Trouver s'il existe au moins une relation de causalité dans le jeu de données si oui, calculer également la corrélation. Comparez et interpreter la différence.
