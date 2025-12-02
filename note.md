# 1. Estimateur de moyenne (niveau de vie, revenu médian…)

**Estimateur :**
\[
\hat{\mu}_n = \frac{1}{n}\sum_{i=1}^n X_i
\]
où \(X_i\) = niveau de vie médian ou revenu disponible médian d’un IRIS.

### Propriétés

| Propriété               | Résultat                                        | Justification                                |
|------------------------|--------------------------------------------------|-----------------------------------------------|
| Non-biaisé             | oui                                              | \(E[\hat{\mu}] = \mu\)                        |
| Variance               | \(\mathrm{Var}(\hat{\mu}) = \sigma^2/n\)         | décroît en \(1/n\)                            |
| Consistant             | oui                                              | loi forte des grands nombres (LLN)            |
| Normalité asymptotique | oui                                              | théorème central limite (CLT)                 |
| MVUE                   | oui si normalité                                 | optimum pour loi normale                      |
| BLUE                   | non en général, oui en régression linéaire       | théorème de Gauss–Markov                      |

### Tests possibles
- Test bilatéral \(H_0 : \mu = \mu_0\).  
- Comparaison de moyennes (t-test, Welch).


# 2. Estimateur de variance

**Estimateur :**
\[
S^2 = \frac{1}{n-1}\sum_{i=1}^n (X_i - \bar{X})^2
\]

### Propriétés

| Propriété | Résultat |
|-----------|----------|
| Non-biaisé | oui (avec \(n-1\)) |
| Consistant | oui |
| Normalité asymptotique | variance liée à une loi \(\chi^2\) |
| Asymptotiquement normal | oui (Delta-method) |
| MVUE | oui sous normalité |

### Analyses
- Intervalle de confiance via \(\chi^2\).  
- Bootstrap des variances.


# 3. Estimateurs de proportions (taux de pauvreté, part des ménages…)

**Estimateur :**
\[
\hat{p} = \frac{1}{n}\sum_{i=1}^n Y_i
\]

### Propriétés

| Propriété | Résultat | Justification |
|-----------|----------|---------------|
| Non-biaisé | oui | \(E[\hat{p}] = p\) |
| Variance | \(p(1-p)/n\) | variance binomiale |
| Consistant | oui | LLN |
| Normalité asymptotique | oui | CLT (si \(np(1-p) > 10\)) |

### Tests possibles
- Test \(H_0 : p = p_0\).  
- Comparaison de proportions.  
- IC de Wilson, Wald ou Agresti-Coull.


# 4. Estimateur de différence de moyennes

\[
\hat{\mu}_1 - \hat{\mu}_2
\]

### Propriétés
- Non-biaisé.  
- Variance : \(\sigma_1^2/n_1 + \sigma_2^2/n_2\).  
- Normalité asymptotique (CLT).  
- Bootstrap recommandé.


# 5. Estimateur de covariance et corrélation

**Covariance :**
\[
\widehat{\sigma}_{XY} = \frac{1}{n-1}\sum (X_i - \bar{X})(Y_i - \bar{Y})
\]

**Corrélation :**
\[
\hat{\rho} = \frac{\widehat{\sigma}_{XY}}{\widehat{\sigma}_X \widehat{\sigma}_Y}
\]

### Propriétés
- Covariance non biaisée.  
- Estimateurs consistants.  
- Asymptotiquement normaux (Delta-method).  
- Corrélation asymptotiquement normale pour grands n.

### Tests
- Test de corrélation (Student).  
- Bootstrap pour IC.


# 6. Estimateurs issus d’une régression linéaire

Modèle :
\[
Y_i = \beta_0 + \beta_1 X_{1i} + \beta_2 X_{2i} + \cdots + \varepsilon_i
\]

**Estimateur OLS :**
\[
\hat{\beta} = (X'X)^{-1}X'Y
\]

### Propriétés (Gauss–Markov)

| Propriété | Résultat | Conditions |
|-----------|----------|------------|
| Non-biaisé | oui | \(E[\varepsilon|X]=0\) |
| BLUE | oui | homoscédasticité, erreurs non corrélées |
| Consistant | oui | \(X'X/n \to Q\) inversible |
| Normalité asymptotique | oui | CLT : \(\hat{\beta} \sim N(\beta, \sigma^2 (X'X)^{-1})\) |

### Tests possibles
- Tests t sur les coefficients.  
- Test F global.  
- IC asymptotiques.  
- Bootstrap des coefficients.


# 7. Estimateur de quantiles (médiane, quartiles)

**Estimateur :**
\[
\hat{q}_\tau = \text{quantile empirique}
\]

### Propriétés
- Consistant (Glivenko–Cantelli).  
- Asymptotiquement normal :
\[
\sqrt{n}(\hat{q}_\tau - q_\tau)
  \rightarrow \mathcal{N}\left(0,\frac{\tau(1-\tau)}{f(q_\tau)^2}\right)
\]

- Delta-method pour transformations.


# 8. Estimateurs par bootstrap

Bootstrap possible pour :
- moyenne,  
- variance,  
- proportion,  
- différence de moyennes,  
- corrélation,  
- régression,  
- quantiles.

### Propriétés
- Consistance sous IID et moments finis.  
- IC souvent plus stables que ceux basés uniquement sur le CLT.


# 9. Estimateurs de ratios

\[
\hat{R} = \frac{\hat{A}}{\hat{B}}
\]

### Propriétés
- Faible biais si \(\hat{B}\) est grand.  
- Normalité asymptotique via Delta-method :
\[
\sqrt{n}(\hat{R} - R) \to N(0, \nabla g \Sigma \nabla g')
\]


# 10. Résumé des estimateurs utilisables

| Type d’estimateur | Variables IRIS | Propriétés | Théorèmes utilisés |
|-------------------|----------------|------------|--------------------|
| Moyenne | niveau de vie, revenu | non-biaisé, normalité asympt. | LLN, CLT |
| Variance | mêmes | non-biaisé, \(\chi^2\) approx | \(\chi^2\), Delta-method |
| Proportion | taux de pauvreté | normalité asympt. | CLT |
| Différence de moyennes | groupes d’IRIS | non-biaisé, asympt. normal | CLT |
| Corrélation/covariance | revenu ↔ pauvreté | asympt. normal | Delta-method |
| Régression OLS | revenu ~ X | BLUE (si homosc.), normalité asympt. | Gauss–Markov, CLT |
| Quantiles | médiane, Q1, Q3 | consistant, asympt. normal | Glivenko–Cantelli |
| Ratios | revenu local/national | asympt. normal | Delta-method |
| Bootstrap | tous | approximation empirique | Consistance bootstrap |
