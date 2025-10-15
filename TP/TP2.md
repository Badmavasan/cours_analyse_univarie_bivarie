# TP2 — Analyse de distributions, asymétrie, aplatissement et normalité
**Jeu de données : Adult Census Income** (colonnes usuelles : age, fnlwgt, education-num, capital-gain, capital-loss, hours-per-week, sex, race, education, marital-status, occupation, relationship, native-country, income, …)

## Objectifs
1. **Calculer** et **interpréter** l’**asymétrie** (skewness) et l’**aplatissement** (kurtosis).
2. **Vérifier la normalité** de variables sélectionnées (tests + QQ-plot).
3. **Implémenter vous-même** l’un des **tests de normalité** (Shapiro–Wilk *ou* Anderson–Darling) et interpréter les résultats.

### 1. Calculez γ1 et κ pour les variables numériques (au moins 3). Comparez :

- Quelle variable a l’asymétrie la plus forte ? dans quel sens ?
- Quelle variable a le kurtosis le plus élevé ? que raconte cela sur les valeurs extrêmes ?

### 2. QQ-plot (diagnostic visuel)

- Réalisez un QQ-plot normal pour 2–3 variables numériques.
- Commentez les écarts aux extrémités (queues) et la linéarité au centre.

### 3. Implémentez vous-même un test de normalité (au choix)

**Consigne importante** : n’utilisez pas la fonction toute faite du test choisi.
Vous devez coder le test **Shapiro–Wilk** ou **Anderson–Darling** à la main (formule + seuil/critère).
Vous pouvez en revanche comparer votre résultat à celui d’une librairie pour validation après.

### 4. Reliez asymétrie/kurtosis à la décision de normalité.

### 5. Effectuer un nettoyage des données en utilisant IQR et Z-Score