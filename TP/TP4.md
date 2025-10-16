# TP : Tableaux de contingence et tests d’indépendance – *Adult Census Income*

## Objectifs pédagogiques

Ce TP te permettra de maîtriser l’analyse des **relations entre variables qualitatives** à travers :
- la construction et l’interprétation de **tableaux de contingence**,
- le calcul de **fréquences conditionnelles**,
- la **visualisation** des relations catégorielles,
- la réalisation et l’interprétation de **tests d’indépendance du χ²**.

### 1. Types de variables

**Questions :**

1. Distingue dans le dataset :
        - les variables quantitatives (mesurées sur une échelle numérique)
        - les variables qualitatives (catégorielles)
2. Donne quelques exemples de variables qualitatives pertinentes pour ce TP. (Indice : sex, education, occupation, marital-status, income, workclass…)


### 2. Tableaux de contingence simples

#### 2.1 Création d’un tableau croisé

Commençons par deux variables simples : `sex` et `income`.

**Questions :**
- Que représente chaque cellule du tableau ?
- Quelle est la modalité la plus fréquente ?
- Quelles proportions observes-tu globalement ?

#### 2.2 Tableau normalisé par lignes ou par colonnes

On peut normaliser le tableau pour obtenir des proportions :

```python
pd.crosstab(df["sex"], df["income"], normalize="index")
```

**Questions :**
- Que signifie ici `normalize="index"` ?
- Interprète la proportion obtenue pour chaque sexe.
- Refais le tableau avec `normalize="columns"`. Quelle différence d’interprétation ?

#### 2.3 Fréquences conditionnelles

Les fréquences conditionnelles permettent d’analyser une variable conditionnellement à une autre.

Exemple :
Quelle est la probabilité qu’une personne ait un revenu >50K sachant qu’elle est un homme ?

**Questions :**

1. Quelle cellule du tableau correspond à cette probabilité ?
2. Quelle interprétation concrète peux-tu en donner ?
3. Calcule maintenant la probabilité d’un revenu >50K sachant que la personne est une femme. Compare.

## 3. Tableaux de contingence à plusieurs modalités

### 3.1 Étude de `education` et `income`

**Questions :**
- Quelle variable semble influencer la probabilité d’avoir un revenu élevé ?
- Observe-tu une tendance claire selon le niveau d’éducation ?
- Refais le tableau avec normalize="index" pour mieux comparer les proportions entre niveaux d’études.

### 3.2 Visualisation graphique de `education` et `income`

(Choissisez une forme de graphique adapté au contexte)

**Questions :**

- Quelle forme générale le graphique suggère-t-il ?
- Les catégories supérieures semblent-elles avantagées ?
- Quels biais possibles peuvent influencer cette interprétation ?

### 3.3 Étude de `marital-status` et `income`

1. Crée le tableau croisé.
2. Calcule les fréquences conditionnelles par statut marital.
3. Trace le graphique correspondant.

**Questions :**
- Les personnes mariées ont-elles plus souvent un revenu élevé ?
- Quelles différences remarques-tu selon le statut marital ?

## 4. Tableaux de contingence à trois variables

### 4.1 Utiliser pd.crosstab avec trois dimensions

Tu peux ajouter une troisième variable avec `columns=[...]` et `values=None`.

Exemple : `sex`, `education`, `income`.

**Questions :**
- Quelle est la structure de ce tableau ?
- Interprète les résultats pour quelques cas (ex : femmes avec Master ou Doctorate).
- Que permet ce type de tableau par rapport à un tableau à deux dimensions ?

## 5. Test du χ² d’indépendance

Le test du χ² d’indépendance permet de vérifier si deux variables qualitatives sont statistiquement indépendantes.

### 5.1 Principe

**Hypothèse nulle H₀** : les deux variables sont indépendantes.
**Hypothèse alternative H₁** : les deux variables ne sont pas indépendantes (elles sont liées).

### 5.2 Application pratique

Exemple : `sex` et `income`

**Questions :**
- Quelle est la valeur de la p-value ?
- Quelle règle utilises-tu pour rejeter ou non H₀ (au seuil de 5%) ?
- Quelle conclusion tires-tu : indépendance ou dépendance entre sex et income ?

### Autres tests d’indépendance

Réalise le test du χ² pour les couples suivants :
- `education` et `income`
- `marital-status` et `income`
- `occupation` et `income`

**Questions :**
- Les résultats sont-ils tous significatifs ?
- Quelles paires de variables semblent les plus dépendantes ?
- Que peut-on interpréter sociologiquement de ces résultats ?

## Visualisation des relations qualitatives

### 6.1 Diagrammes empilés et proportions

Pour une visualisation claire des proportions conditionnelles : 

```python
cross = pd.crosstab(df["education"], df["income"], normalize="index")
cross.plot(kind="bar", stacked=True)
plt.title("Proportion de revenu par niveau d'éducation")
plt.ylabel("Fréquence conditionnelle")
plt.show()
```

**Questions :**
- Quelle tendance observes-tu ?
- Ce graphique te semble-t-il cohérent avec les résultats du test du χ² ?

### 6.2 Heatmap (carte de chaleur)

Pour mieux visualiser les valeurs d’un tableau de contingence : 

```python!
sns.heatmap(pd.crosstab(df["occupation"], df["income"], normalize="index"),
            annot=True, cmap="YlGnBu")
plt.title("Proportion de revenu par profession")
plt.show()
```

**Questions :**
- Quelles professions ont les plus fortes proportions de revenus élevés ?
- Comment interpréter les cases les plus foncées ?