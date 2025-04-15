# **Correlação: Teoria e Aplicação**  

A correlação é uma medida estatística que expressa o grau de relação entre duas variáveis. Em termos simples, ela indica se as variáveis aumentam ou diminuem juntas e o quão forte essa relação é. É amplamente utilizada em estatística, ciência de dados, economia, e muitas outras áreas.

Neste conteúdo, vamos explorar a teoria da correlação e implementá-la em Python, utilizando gráficos para facilitar a visualização.

---

## **1. O que é Correlação?**  

A correlação mede a relação entre duas variáveis quantitativas. Seu valor varia entre **-1 e 1**, e pode ser interpretado da seguinte maneira:

- **Correlação positiva (+1)** → Quando uma variável aumenta, a outra também tende a aumentar.  
- **Correlação negativa (-1)** → Quando uma variável aumenta, a outra tende a diminuir.  
- **Correlação zero (0)** → Não há relação linear entre as variáveis.  

A fórmula da correlação de Pearson, a mais comum, é:

$$
r = \frac{\sum (X_i - \bar{X})(Y_i - \bar{Y})}{\sqrt{\sum (X_i - \bar{X})^2} \times \sqrt{\sum (Y_i - \bar{Y})^2}}
$$

Onde:
- $(X_i, Y_i)$ são os valores individuais das variáveis.
- $(\bar{X}, \bar{Y})$ são as médias das variáveis.
- O numerador calcula a covariância entre \(X\) e \(Y\).
- O denominador normaliza os valores pelos desvios padrão.

---

## **2. Tipos de Correlação**  

Existem diferentes tipos de correlação, dependendo da forma como a relação entre as variáveis é avaliada:

1. **Correlação de Pearson** → Mede a relação linear entre duas variáveis.
2. **Correlação de Spearman** → Mede a relação monotônica (não necessariamente linear).
3. **Correlação de Kendall** → Avalia a força da dependência entre as variáveis baseada em rankings.

---

## **3. Implementação em Python**  

Vamos agora implementar a correlação em Python com gráficos para visualização.

### **3.1. Importando Bibliotecas**  

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import pearsonr, spearmanr
```

---

### **3.2. Criando um Conjunto de Dados**  

Vamos gerar dados fictícios para ilustrar diferentes tipos de correlação:

```python
# Gerando dados artificiais
np.random.seed(42)
x = np.arange(1, 101)

# Correlação positiva forte
y1 = x + np.random.normal(0, 10, 100)

# Correlação negativa forte
y2 = 200 - x + np.random.normal(0, 10, 100)

# Sem correlação
y3 = np.random.normal(100, 30, 100)

# Criando DataFrame
df = pd.DataFrame({'X': x, 'Y1': y1, 'Y2': y2, 'Y3': y3})

df.head()
```

---

### **3.3. Calculando a Correlação de Pearson**  

```python
correlation_y1, _ = pearsonr(df['X'], df['Y1'])
correlation_y2, _ = pearsonr(df['X'], df['Y2'])
correlation_y3, _ = pearsonr(df['X'], df['Y3'])

print(f"Correlação entre X e Y1 (positiva): {correlation_y1:.2f}")
print(f"Correlação entre X e Y2 (negativa): {correlation_y2:.2f}")
print(f"Correlação entre X e Y3 (nenhuma relação): {correlation_y3:.2f}")
```

Saída esperada (valores podem variar ligeiramente devido à aleatoriedade):

```
Correlação entre X e Y1 (positiva): 0.97
Correlação entre X e Y2 (negativa): -0.97
Correlação entre X e Y3 (nenhuma relação): -0.05
```

---

### **3.4. Visualizando a Correlação com Gráficos**  

Vamos criar gráficos de dispersão para visualizar a relação entre as variáveis.

```python
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

# Correlação positiva
sns.scatterplot(x=df['X'], y=df['Y1'], ax=axes[0], color='blue')
axes[0].set_title(f'Correlação Positiva (r={correlation_y1:.2f})')

# Correlação negativa
sns.scatterplot(x=df['X'], y=df['Y2'], ax=axes[1], color='red')
axes[1].set_title(f'Correlação Negativa (r={correlation_y2:.2f})')

# Sem correlação
sns.scatterplot(x=df['X'], y=df['Y3'], ax=axes[2], color='green')
axes[2].set_title(f'Sem Correlação (r={correlation_y3:.2f})')

plt.show()
```

---

### **3.5. Matriz de Correlação e Heatmap**  

Para verificar a correlação entre múltiplas variáveis, podemos usar um **heatmap**:

```python
# Matriz de correlação
corr_matrix = df.corr()

# Criando o heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt=".2f", linewidths=0.5)
plt.title("Matriz de Correlação")
plt.show()
```

A matriz de correlação exibe a relação entre todas as variáveis do conjunto de dados, com valores entre -1 e 1.

---

## **4. Correlação de Spearman e Kendall**  

Caso os dados não sigam uma relação linear, podemos usar Spearman ou Kendall.

```python
spearman_corr, _ = spearmanr(df['X'], df['Y1'])
kendall_corr, _ = spearmanr(df['X'], df['Y1'])

print(f"Correlação de Spearman entre X e Y1: {spearman_corr:.2f}")
print(f"Correlação de Kendall entre X e Y1: {kendall_corr:.2f}")
```

Essas correlações são mais adequadas para relações monotônicas não lineares.

---

## **5. Cuidados ao Interpretar Correlação**  

- **Correlação não implica causalidade!**  
  - Apenas porque duas variáveis estão correlacionadas não significa que uma causa a outra.
- **Outliers podem afetar a correlação.**  
  - Dados atípicos podem distorcer a relação entre as variáveis.
- **A correlação mede apenas relações lineares.**  
  - Se a relação for não linear, a correlação de Pearson pode ser enganosa.

---

# **Caso de Uso Prático: Analisando o Impacto da Publicidade nas Vendas**  

## **Cenário**  
Uma empresa quer entender se seus gastos com publicidade estão realmente impulsionando as vendas. Para isso, coletou dados mensais dos últimos 3 anos sobre:  

- **Investimento em publicidade (\$)**
- **Número de vendas realizadas (unidades)**
- **Número de visitas ao site (tráfego)**
- **Taxa de conversão (%)**

Vamos analisar se há correlação entre esses fatores e quais insights podem ser extraídos.  

---

## **1. Simulando os Dados e Explorando a Correlação**  

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import pearsonr

# Gerando dados fictícios
np.random.seed(42)
meses = np.arange(1, 37)  # 3 anos de dados

# Variáveis simuladas
publicidade = np.random.randint(1000, 10000, size=36)  # Investimento em publicidade ($)
visitas_site = publicidade * np.random.uniform(0.08, 0.12, size=36) + np.random.normal(500, 200, 36)
taxa_conversao = np.random.uniform(0.02, 0.05, size=36)  # Percentual de visitantes que compram
vendas = visitas_site * taxa_conversao + np.random.normal(10, 5, 36)  # Número de vendas

# Criando DataFrame
df = pd.DataFrame({
    'Mês': meses,
    'Publicidade ($)': publicidade,
    'Visitas ao Site': visitas_site.astype(int),
    'Taxa de Conversão (%)': (taxa_conversao * 100).round(2),
    'Vendas': vendas.astype(int)
})

print(df.head())  # Exibir as primeiras linhas do dataset
```

---

## **2. Matriz de Correlação e Visualização**  

```python
# Matriz de correlação
corr_matrix = df.drop(columns=['Mês']).corr()

# Criando o heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt=".2f", linewidths=0.5)
plt.title("Matriz de Correlação entre Publicidade, Tráfego e Vendas")
plt.show()
```

🔍 **Insights esperados:**  
- O investimento em publicidade pode ter **forte correlação positiva** com o número de visitas ao site.  
- O tráfego pode estar correlacionado com as vendas, mas a força da correlação pode variar conforme a taxa de conversão.  
- A correlação entre publicidade e vendas pode ser menos direta devido à variação da taxa de conversão.  

---

# **Exercícios Avançados**

### **1. Exercício: Identificando um Ponto de Saturação no Investimento em Publicidade**  
A empresa suspeita que, a partir de um certo ponto, aumentar o investimento em publicidade não gera um aumento proporcional nas vendas.  

📌 **Desafio:**  
- Divida os dados em dois grupos:  
  - **Baixo investimento** (abaixo da mediana da publicidade).  
  - **Alto investimento** (acima da mediana da publicidade).  
- Calcule a correlação entre **publicidade e vendas** para cada grupo.  
- Compare os resultados e interprete se há um ponto de saturação.

```python
mediana_pub = df['Publicidade ($)'].median()

# Separando os grupos
baixo_inv = df[df['Publicidade ($)'] <= mediana_pub]
alto_inv = df[df['Publicidade ($)'] > mediana_pub]

# Correlação para cada grupo
corr_baixo, _ = pearsonr(baixo_inv['Publicidade ($)'], baixo_inv['Vendas'])
corr_alto, _ = pearsonr(alto_inv['Publicidade ($)'], alto_inv['Vendas'])

print(f"Correlação para baixo investimento: {corr_baixo:.2f}")
print(f"Correlação para alto investimento: {corr_alto:.2f}")
```

🔍 **Pergunta crítica:**  
- O aumento no investimento ainda está gerando impacto positivo ou há um **ponto de saturação** onde a correlação diminui?  

---

### **2. Exercício: Correlação vs Causalidade – Impacto da Taxa de Conversão**  
A taxa de conversão tem impacto nas vendas, mas será que um aumento na publicidade afeta diretamente essa taxa?  

📌 **Desafio:**  
- Analise a correlação entre **investimento em publicidade** e **taxa de conversão**.  
- Se houver baixa correlação, o que isso pode significar?  
- Se houver alta correlação, como a empresa poderia explorar essa relação?  

```python
correlation_conv, _ = pearsonr(df['Publicidade ($)'], df['Taxa de Conversão (%)'])
print(f"Correlação entre Publicidade e Taxa de Conversão: {correlation_conv:.2f}")
```

🔍 **Pergunta crítica:**  
- Se a correlação for fraca, a empresa deveria focar mais na **qualidade dos anúncios** em vez de apenas aumentar o orçamento?  
- Que estratégias poderiam ser testadas para aumentar a taxa de conversão?  

---

