# TP : Lien entre variables et tests statistiques – *Adult Census Income*

## Objectifs pédagogiques

Dans ce TP, tu vas approfondir l’analyse statistique du dataset **Adult Census Income**.  
Nous allons explorer plusieurs approches pour **mesurer la force et la nature des liens** entre variables :

- Mesure du **V de Cramer** (force de l’association entre variables qualitatives)  
- Analyse **Qualitative vs Quantitative** avec **boxplots** et **tests statistiques**  
- Réalisation et **interprétation de tests statistiques de comparaison**

**Question**
- Donne deux exemples de relations qualitative vs quantitative pertinentes à étudier.

## 1. Mesure de Cramer’s V – Force du lien entre deux variables qualitatives

Le V de Cramer mesure l’intensité de l’association entre deux variables qualitatives.

### 1.1 Application à plusieurs couples de variables
- `sex` vs `income`
- `education` vs `income`
- `marital-status` vs `income`
- `occupation` vs `income`

**Questions :**
- Quelle paire présente le lien le plus fort ?
- Comment interpréter un V proche de 0 ? Et proche de 1 ?
- Quelle conclusion tires-tu sur les relations sociales et économiques observées ici ?

## 2. Comparaison Qualitative vs Quantitative

Nous allons maintenant comparer une variable quantitative entre groupes définis par une variable qualitative.

### 2.1 Exemple : `hours-per-week` selon `sex`

**Questions :**
- Quelle tendance générale observes-tu ?
- Les médianes sont-elles proches ?
- La dispersion est-elle similaire entre les groupes ?

### 2.2 Autre exemple : `age` selon le revenu (`income`)

**Questions :**
- Quelle catégorie semble regrouper les personnes les plus âgées ?
- Observe-tu des valeurs extrêmes ?
- Quelles hypothèses pourrais-tu formuler à partir de ce graphique ?

### 2.3 Moyennes par groupe

Calcule les moyennes et écarts-types entre `age` et revenu (`income`)

**Questions :**
- Quelle différence de moyenne d’âge existe entre les deux groupes de revenu ?
- Est-elle importante ?

## 3. Tests statistiques de comparaison

Nous allons tester si les différences observées dans les boxplots sont statistiquement significatives.

## 3.1 Test t de Student (deux groupes)

Exemple : comparaison de `hours-per-week` entre `hommes` et `femmes`.

**Questions :**
- Quelle est la valeur de la p-value ?
- En considérant un seuil α = 0.05, que conclure ?
- Le résultat est-il cohérent avec la visualisation précédente ?

### 3.2 Test ANOVA (plus de deux groupes)

Exemple : comparer `hours-per-week` selon le `niveau d’éducation`.

**Questions :**
- Quelle hypothèse teste-t-on ici ?
- Que signifie une p-value inférieure à 0.05 ?
- Le niveau d’étude influence-t-il significativement le temps de travail ?

## 4. Visualisation complémentaire

### 4.1 Boxplot multiple : `hours-per-week` par `education`

**Questions :**
- Quelles catégories semblent les plus extrêmes ?
- Observe-tu une tendance claire selon le niveau d’étude ?
- Les résultats confirment-ils le test ANOVA précédent ?


## 5. Réflexion personnelle – 10 questions de synthèse

>Consigne importante :
>Rédige tes réponses avec tes propres mots, en expliquant le raisonnement derrière chaque conclusion. L’utilisation d’outils d’IA générative est strictement interdite pour cette partie.

**Questions de réflexion**
- Que mesure exactement le V de Cramer, et pourquoi est-il utile avant un test d’indépendance?
- Quelle différence fondamentale existe entre un test du χ² et un test t de Student?
- Que signifie une p-value inférieure à 0.05 dans un test statistique ?
- Pourquoi ne peut-on pas utiliser la corrélation de Pearson pour deux variables qualitatives?
- Comment interpréter visuellement un boxplot ? Quels indicateurs statistiques y sont représentés?
- Quelle est la différence entre une différence significative et une différence importante?
- Comment peut-on savoir si les résultats d’un test statistique sont fiables?
- Quelle variable du dataset Adult semble la plus liée au revenu (income)? Justifie.
- Quelle est la limite d’interprétation d’un test ANOVA lorsqu’il est significatif?
- Pourquoi est-il essentiel de croiser l’analyse graphique et les tests statistiques avant de tirer des conclusions?