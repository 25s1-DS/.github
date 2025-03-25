# Estatística Básica e Distribuições Estatísticas

## 1. Introdução
A estatística é um ramo da matemática que lida com a coleta, análise, interpretação e apresentação de dados. 
Ela é amplamente utilizada em ciência de dados para inferir padrões e tomar decisões baseadas em evidências. 
Desde tempos antigos, a estatística tem sido usada para contagens populacionais, planejamento econômico e previsões. Com o avanço da tecnologia, tornou-se essencial para a análise de grandes volumes de dados.

## 2. Medidas de Tendência Central
As medidas de tendência central são utilizadas para determinar um valor representativo para um conjunto de dados. Elas ajudam a entender o comportamento central dos dados, sendo amplamente usadas em pesquisas e análises econômicas, sociais e científicas.

### 2.1. Média
A **média aritmética** é obtida somando todos os valores do conjunto e dividindo pelo número total de observações:
$\bar{x} = \frac{\sum_{i=1}^{n} x_i}{n}$

**Exemplo:**
Se temos as notas de um aluno em 5 provas: 7, 8, 6, 9 e 10, a média será:
$\bar{x} = \frac{7+8+6+9+10}{5} = 8$

A média é usada, por exemplo, para calcular o desempenho acadêmico de estudantes ou para estimar salários em uma região.

### 2.2. Mediana
A **mediana** é o valor central de um conjunto de dados ordenado. Se houver um número par de elementos, a mediana é a média dos dois valores centrais.

**Exemplo:**
Para o conjunto de dados [3, 7, 8, 12, 15], a mediana é **8**, pois é o valor do meio. Para [2, 5, 9, 11, 14, 18], a mediana é **(9+11)/2 = 10**.

A mediana é usada para representar melhor dados com valores extremos, como renda, onde alguns valores muito altos poderiam distorcer a análise.

### 2.3. Moda
A **moda** é o valor que aparece com maior frequência no conjunto de dados.

**Exemplo:**
Se temos as idades de 10 crianças: [5, 6, 6, 7, 8, 9, 9, 9, 10, 12], a moda é **9**, pois aparece mais vezes.

A moda é útil para análises de mercado, como determinar o tamanho de calçado mais vendido.

## 3. Medidas de Dispersão
As medidas de dispersão quantificam a variabilidade dos dados, ajudando a entender o quão espalhados os valores estão.

### 3.1. Variância
A **variância** mede o quão distante os valores estão da média:
$\sigma^2 = \frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n}$

**Exemplo:**
Se temos [4, 8, 6, 5, 3, 7, 9, 6], calculamos a variância para medir a dispersão dos valores.

A variância é usada em finanças para medir o risco de investimentos.

### 3.2. Desvio Padrão
O **desvio padrão** é a raiz quadrada da variância e fornece uma medida de dispersão na mesma unidade dos dados:
$\sigma = \sqrt{\sigma^2}$

Ele é usado para determinar a volatilidade de ações no mercado financeiro ou a precisão de máquinas em processos industriais.

### 3.3. Amplitude
A **amplitude** é a diferença entre o maior e o menor valor do conjunto de dados:
$\text{Amplitude} = x_{\text{max}} - x_{\text{min}}$

**Exemplo:**
Se as temperaturas em uma cidade variam entre 10°C e 35°C, a amplitude é **35 - 10 = 25°C**.

A amplitude é usada para entender variações climáticas ou oscilações de preço em mercados financeiros.

## 4. Distribuições Estatísticas
Distribuições estatísticas descrevem como os dados se distribuem e são essenciais para modelagem estatística. Elas surgiram para ajudar a prever fenômenos naturais e sociais, como crescimento populacional, flutuações econômicas e resultados de experiências.

### 4.1. [Distribuição Normal](./Topico3%20-%20Normal.md)
A **distribuição normal** tem formato de sino e aparece naturalmente em várias situações, como altura da população ou notas escolares.

**Exemplo:**
Se as alturas seguem uma distribuição normal com $\mu = 170$ cm e $\sigma = 10$ cm, podemos calcular quantas pessoas têm altura entre 160 e 180 cm.

### 4.2. Distribuição Binomial
A **distribuição binomial** modela situações de sucesso ou fracasso, como lançar uma moeda.

**Exemplo:**
Se lançamos uma moeda 10 vezes, qual a probabilidade de obtermos exatamente 5 caras?

### 4.3. Distribuição de Poisson
A **distribuição de Poisson** é usada para modelar eventos raros, como a chegada de clientes a um caixa eletrônico.

**Exemplo:**
Se em média 3 pessoas chegam por minuto ao caixa, podemos calcular a probabilidade de exatamente 5 chegarem em um minuto.

### 4.4. Distribuição Exponencial
A **distribuição exponencial** modela o tempo entre eventos sucessivos, como falhas em sistemas.

**Exemplo:**
Se o tempo entre falhas de um computador segue uma distribuição exponencial com $\lambda = 0.5$, podemos prever o tempo até a próxima falha.



## 5. Lista de Exercícios

1. Calcule a média, mediana e moda do conjunto de dados: [2, 3, 3, 5, 7, 10, 10, 10, 12].
2. Encontre a variância e o desvio padrão dos dados: [4, 8, 6, 5, 3, 7, 9, 6].
3. Determine a amplitude do conjunto [15, 22, 8, 29, 12].
4. Uma amostra segue distribuição normal com $\mu = 50$ e $\sigma = 5$. Qual a probabilidade de um valor estar entre 45 e 55?
5. Qual é a probabilidade de obter exatamente 3 sucessos em 5 tentativas com probabilidade de sucesso de 0.6 em cada tentativa?
6. Modele a chegada de clientes em um banco usando uma distribuição de Poisson com $\lambda = 4$ clientes por minuto.
7. Determine o tempo esperado até o próximo evento em uma distribuição exponencial com $\lambda = 2$.
8. Simule um conjunto de 100 amostras de uma distribuição normal com $\mu = 10$ e $\sigma = 2$.
9. Calcule a probabilidade de um evento raro ocorrer pelo menos uma vez em 10 minutos, se ocorre a uma taxa de 0.1 por minuto.
10. Interprete o desvio padrão na distribuição dos salários de uma empresa.
11. Explique como a distribuição binomial pode modelar o lançamento de uma moeda.
12. Qual a diferença entre distribuição normal e binomial?
13. Em que situações a distribuição de Poisson é apropriada?
14. Como a distribuição exponencial se relaciona com a distribuição de Poisson?
15. Qual o efeito do aumento da variância em uma distribuição normal?
16. Como a mediana pode ser mais representativa do que a média?
17. Explique o significado de um valor-p na estatística.
18. Como interpretar um histograma de distribuição normal?
19. Calcule a probabilidade de obter ao menos um sucesso em 4 tentativas com $p = 0.2$.
20. Qual é a função cumulativa da distribuição exponencial?





