### 📌 **Correlação entre o Algoritmo e o Teorema de Bayes**  

O **Naïve Bayes** é uma aplicação direta do **Teorema de Bayes**, simplificada pela suposição de independência condicional das palavras no texto. Vamos analisar essa relação detalhadamente.  

---

## 📖 **Relembrando o Teorema de Bayes**  
$
P(A | B) = \frac{P(B | A) \cdot P(A)}{P(B)}
$
Onde:  
- \( P(A | B) \) → Probabilidade da classe \( A \) (spam ou não spam) dado o texto \( B \) (**probabilidade posterior**).  
- \( P(B | A) \) → Probabilidade do texto \( B \) aparecer dado que pertence à classe \( A \) (**verossimilhança**).  
- \( P(A) \) → Probabilidade a priori da classe (**probabilidade inicial antes dos dados**).  
- \( P(B) \) → Probabilidade total do texto (**pode ser ignorada, pois é constante para todas as classes**).  

Agora, vejamos **como esse teorema se aplica no código do classificador**.

---

## 🔗 **Passo 1: Como o Código Implementa o Teorema de Bayes?**  

No **treinamento (`train`)**, o código calcula:
- **\( P(A) \) (probabilidade a priori)**:  
  - Contamos quantos exemplos existem de cada classe.  
  - Exemplo: se 60% dos e-mails são spam, então **\( P(Spam) = 0.6 \)**.  

- **\( P(B | A) \) (probabilidade condicional das palavras dado a classe)**:  
  - Contamos quantas vezes cada palavra aparece dentro de cada classe.  
  - Aplicamos **suavização de Laplace** para evitar probabilidades zero.

No **teste (`predict`)**, aplicamos:
$
\log P(A | B) = \log P(A) + \sum \log P(Palavra_i | A)
$
Essa soma de logaritmos equivale à multiplicação da fórmula original do Teorema de Bayes.

---

## 🔎 **Passo 2: Analisando o Código com a Fórmula**  

Vamos examinar um trecho do código e associá-lo ao Teorema de Bayes.

### 🔹 **Cálculo da Probabilidade A Priori \( P(A) \)**
No código:
```python
class_prob = math.log(self.classes[class_label] / total_examples)
```
Isso corresponde a:
\[
P(A) = \frac{\text{número de exemplos da classe}}{\text{total de exemplos}}
\]

---

### 🔹 **Cálculo da Probabilidade Condicional \( P(B | A) \)**
No código:
```python
word_prob = (word_freq + 1) / (self.total_words[class_label] + len(self.word_counts[class_label]))  # Laplace smoothing
class_prob += math.log(word_prob)
```
Aqui estamos calculando:
$
P(Palavra | Classe) = \frac{\text{Frequência da palavra na classe} + 1}{\text{Total de palavras na classe} + \text{Número total de palavras únicas}}
$
A soma dos logaritmos evita **underflow** e faz a multiplicação das probabilidades.

---

## 🔥 **Passo 3: Exemplo Numérico**
Suponha que temos o seguinte treinamento:

| E-mail | Texto | Classe |
|--------|--------------------------|---------|
| 1 | "Ganhe dinheiro fácil" | Spam |
| 2 | "Dinheiro extra agora" | Spam |
| 3 | "Relatório financeiro atualizado" | Não Spam |
| 4 | "Reunião sobre investimentos" | Não Spam |

Agora, queremos classificar um novo e-mail:  
**"Dinheiro grátis agora"**  

### **Cálculo da Probabilidade A Priori \( P(A) \)**
- Temos 2 spams e 2 não spams → \( P(Spam) = 0.5 \), \( P(NãoSpam) = 0.5 \)

### **Cálculo da Probabilidade Condicional \( P(B | A) \)**  
Frequência das palavras no treinamento:

| Palavra | Spam (contagem) | Não Spam (contagem) |
|---------|---------------|------------------|
| dinheiro | 2 | 0 |
| grátis | 0 | 0 |
| agora | 1 | 0 |

Usando **Laplace smoothing** (\(+1\) para evitar zero):

$
P(Dinheiro | Spam) = \frac{2+1}{6+3} = \frac{3}{9} = 0.33
$

$
P(Agora | Spam) = \frac{1+1}{6+3} = \frac{2}{9} = 0.22
$

Para **não spam**:

$
P(Dinheiro | NãoSpam) = \frac{0+1}{5+3} = \frac{1}{8} = 0.125
$

$
P(Agora | NãoSpam) = \frac{0+1}{5+3} = 0.125
$

Agora, aplicamos o log:
$[
\log P(Spam | Texto) = \log 0.5 + \log 0.33 + \log 0.22
$

$
\log P(NãoSpam | Texto) = \log 0.5 + \log 0.125 + \log 0.125
$

O maior valor define a classe final.

---

## 🎯 **Conclusão**
- O **Naïve Bayes** segue diretamente o **Teorema de Bayes**.
- A implementação usa **contagem de palavras** para estimar \( P(B | A) \).
- Utiliza **logaritmos** para evitar multiplicação de números pequenos.
- **Suavização de Laplace** previne probabilidades zero.
- Pode ser aplicado para **filtragem de spam, classificação de sentimentos, e até diagnóstico médico**.

