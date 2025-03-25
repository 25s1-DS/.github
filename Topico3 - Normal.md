# Estatística Aplicada

## 1. Distribuição Normal de Probabilidade
A distribuição normal é uma distribuição de probabilidade contínua que segue um padrão simétrico em torno da sua média. Ela é descrita pela fórmula:

$$
 f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}
$$

Onde:
- $\mu$ é a média,
- $\sigma$ é o desvio padrão,
- $x$ é a variável aleatória.

A distribuição normal é fundamental para a inferência estatística, pois muitas variáveis naturais seguem esse comportamento, como altura, peso e notas de exames padronizados.

Exemplo:
Se a altura média de uma população é 170 cm com desvio padrão de 10 cm, qual a probabilidade de uma pessoa ter entre 160 cm e 180 cm?

Usando a tabela z-score:
$$
Z = \frac{X - \mu}{\sigma}
$$
Para  $X = 160$ e $X = 180$:
- $Z_{160} = \frac{160 - 170}{10} = -1.0$ 
- $Z_{180} = \frac{180 - 170}{10} = 1.0$ 
Consultando a tabela normal, obtemos uma probabilidade de aproximadamente 68,27%.

---

## 2. Variância e Desvio Padrão

A variância mede a dispersão dos dados em relação à média:

$$
\sigma^2 = \frac{\sum (x_i - \mu)^2}{n}
$$

O desvio padrão é a raiz quadrada da variância:

$$
\sigma = \sqrt{\sigma^2}
$$

Exemplo:
Dado o conjunto de dados ${2, 4, 6, 8, 10}$, a média $\mu$ é:

$$
\mu = \frac{2+4+6+8+10}{5} = 6
$$

A variância:

$$
\sigma^2 = \frac{(2-6)^2 + (4-6)^2 + (6-6)^2 + (8-6)^2 + (10-6)^2}{5} = 8
$$

E o desvio padrão:

$$
\sigma = \sqrt{8} \approx 2.83
$$

---

## 3. Correlação e Covariância

A covariância mede a relação entre duas variáveis:

$$
Cov(X, Y) = \frac{\sum (X_i - \bar{X})(Y_i - \bar{Y})}{n-1}
$$

A correlação de Pearson é a padronização da covariância:

$$
 r = \frac{Cov(X,Y)}{\sigma_X \sigma_Y}
$$

Exemplo:
Se temos os pares de dados $(1,2), (2,3), (3,5), (4,7)$, podemos calcular a covariância e correlação para entender a relação entre as variáveis.

---

## 4. p-value

O valor-p (“p-value”) é uma medida de evidência contra a hipótese nula $H_0$. Um valor pequeno indica forte evidência contra $H_0$.

Se $p < 0.05$, geralmente rejeitamos $H_0$.

Exemplo:
Um teste de médias entre dois grupos produz um valor-p de 0.03. Como $0.03 < 0.05$, rejeitamos a hipótese nula e concluímos que há diferença estatisticamente significativa entre os grupos.

---

## Exercícios

1. Calcule a probabilidade de um evento ocorrer em uma distribuição normal com $\mu = 50$e $\sigma = 5$ no intervalo de 45 a 55.
2. Dado o conjunto ${10, 20, 30, 40, 50}$, calcule a variância e o desvio padrão.
3. Se duas variáveis possuem uma covariância positiva, o que isso significa?
4. Dado o conjunto de pares $(1,3), (2,5), (3,7), (4,9)$, calcule a covariância.
5. Explique o conceito de correlação negativa.
6. Se um estudo retorna um p-value de 0.08, devemos rejeitar $H_0$ ao nível de 5%? Justifique.
7. Qual a diferença entre correlação e causalidade?
8. Para um conjunto de dados com distribuição normal, qual a probabilidade de um valor estar dentro de um desvio padrão da média?
9. Explique por que o desvio padrão é mais intuitivo que a variância.
10. Calcule o coeficiente de correlação para os dados $(2,3), (4,6), (6,9), (8,12)$.

- [+ Exercícios ..... ](./colabs/estatistica_basica.ipynb)
