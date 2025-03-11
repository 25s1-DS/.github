# Apresentação sobre Teoria das Probabilidades

## Objetivo
Fornecer uma introdução à Teoria das Probabilidades, abordando conceitos fundamentais, distribuições de probabilidade e aplicações práticas.

---
## 1. Introdução (30 minutos)

### O que é probabilidade?


Probabilidade é um ramo da matemática que estuda a chance de um determinado evento acontecer. Ela é usada para medir a incerteza e pode ser expressa como um número entre 0 e 1, onde:  

- **0** significa que o evento é impossível de acontecer.  
- **1** significa que o evento é certo de acontecer.  

Por exemplo, ao lançar um dado de seis faces, a probabilidade de sair um número "4" é **1/6** (ou aproximadamente 16,67%).  

A probabilidade é aplicada em diversas áreas, como estatística, inteligência artificial, finanças, engenharia e até mesmo no dia a dia, como na previsão do tempo ou em jogos de azar.

### Origem histórica [(Pascal e Fermat)](Fermat_and_Pascal.md)

### Aplicações em diferentes áreas (ciência, engenharia, economia, IA, etc.)



**Exemplo prático:**
Lance de uma moeda: Qual a probabilidade de sair cara?

---
## 2. Conceitos Fundamentais (45 minutos)
- [Espaço amostral e eventos](./Topico2%20-%20EspacoAmostral_Eventos.md)
- [Definições de probabilidade (clássica, frequentista e bayesiana)](./Topico2%20-%20DefinicaoProbabilidade.md)
- [Probabilidade condicional e independência de eventos](./Topico2%20-%20ProbabilidadeAmostral.md)

**Exemplo prático:**
Jogar dois dados: Qual a probabilidade da soma ser 7?

```python

'''
Este script simula o lançamento de dois dados 100.000 vezes e estima a probabilidade de obter a soma 7. A saída mostrará a probabilidade calculada, que deve estar próxima de 1/6 (~0.1667), o valor teórico.
'''

import random
import matplotlib.pyplot as plt

def jogar_dados():
    """Simula o lançamento de dois dados e retorna a soma."""
    dado1 = random.randint(1, 6)
    dado2 = random.randint(1, 6)
    return dado1 + dado2

def calcular_probabilidade(n=100000):
    """Calcula a probabilidade da soma dos dados ser 7 após N lançamentos."""
    contagem_7 = sum(1 for _ in range(n) if jogar_dados() == 7)
    return contagem_7 / n

def gerar_grafico(n=100000):
    """Gera um gráfico de distribuição das somas dos dados."""
    resultados = [jogar_dados() for _ in range(n)]
    plt.hist(resultados, bins=range(2, 14), edgecolor='black', alpha=0.7, density=True)
    plt.xticks(range(2, 13))
    plt.xlabel('Soma dos dados')
    plt.ylabel('Frequência relativa')
    plt.title(f'Distribuição das somas dos dados ({n} lançamentos)')
    plt.grid(axis='y', linestyle='--', alpha=0.7)
    plt.show()

if __name__ == "__main__":
    n_simulacoes = 100000
    probabilidade = calcular_probabilidade(n_simulacoes)
    print(f"Probabilidade estimada de obter soma 7: {probabilidade:.4f}")
    gerar_grafico(n_simulacoes)

```
---
# Tarefa
### **Exercício 1: Dado viciado (mais chances de sair 6)**  
Modifique o código para que um dos dados seja viciado, tendo o número 6 com o dobro da probabilidade dos outros valores. Como isso afeta a distribuição da soma?  

### **Exercício 2: Dado viciado (menos chances de sair 1)**  
Agora, ajuste o código para que um dos dados tenha menor probabilidade de sair 1 (por exemplo, 1 só aparece 5% das vezes, enquanto os outros números são distribuídos igualmente). Como isso muda a distribuição?  

### **Exercício 3: Aumentando o número de dados**  
Altere o código para lançar três dados em vez de dois. Depois, gere o gráfico da nova distribuição da soma. Como isso muda a curva dos valores obtidos?

### **Exercício 4: Alterar a função calcular_probabilidade()**
Ao invés de somente calcular para o 7, faça-a receber o valor que quer testar a probabilidade como um novo parâmetro

```python

#de bandeja pra vocês
pesos = [1, 1, 1, 1, 1, 2]  # O número 6 tem o dobro de peso
return np.random.choice([1, 2, 3, 4, 5, 6], p=np.array(pesos) / sum(pesos))

```

---
## 3. Teorema de Bayes (20 minutos)
- Definição formal
- Importância na inferência estatística

**Exemplo prático:**
Teste de Covid-19: Como calcular a probabilidade de uma pessoa estar doente dado que o teste deu positivo?

---
## 4. Variáveis Aleatórias e Distribuições (30 minutos)
- Variáveis aleatórias discretas e contínuas
- Distribuições mais comuns:
  - Binomial
  - Poisson
  - Normal
  - Exponencial

**Exemplo prático:**
Qual a probabilidade de que um aluno acerte 7 de 10 questões de uma prova de múltipla escolha ao chutar?

---
## 5. Lei dos Grandes Números e Teorema do Limite Central (20 minutos)
- Explicação intuitiva
- Implicações em estatística

**Exemplo prático:**
Simulação de lançamentos de moeda: conforme o número de lançamentos aumenta, a frequência relativa se aproxima de 50%.

---
## 6. Aplicabilidades da Probabilidade (10 minutos)
- Jogos de azar
- Machine Learning
- Seguro e risco financeiro
- Redes neurais probabilísticas

---
## 7. Exercícios (Lista com 20 problemas)

1. Qual a probabilidade de tirar um ás de um baralho de 52 cartas?
2. Se lançarmos um dado honesto, qual a probabilidade de obter um número par?
3. Uma urna tem 3 bolas vermelhas e 5 bolas pretas. Qual a probabilidade de retirar uma bola vermelha?
4. Qual a probabilidade de jogar duas moedas e ambas caírem com cara para cima?
5. No lançamento de dois dados, qual a probabilidade da soma ser 8?
6. Qual a probabilidade de tirar uma carta de espadas de um baralho?
7. Qual a probabilidade de tirar um número primo ao jogar um dado de 6 faces?
8. Um baralho tem 52 cartas. Qual a probabilidade de tirar uma carta vermelha?
9. Um aluno tem 70% de chance de passar em uma prova. Se ele faz duas provas, qual a probabilidade de passar em ambas?
10. Em uma lanchonete, 60% dos clientes pedem refrigerante. Qual a probabilidade de dois clientes seguidos pedirem refrigerante?
11. Qual a probabilidade de tirar uma bola azul de uma urna contendo 4 bolas vermelhas e 2 bolas azuis?
12. Um teste de Covid-19 tem 90% de precisão. Se a prevalência da doença é de 1%, qual a probabilidade de um teste positivo realmente indicar a doença? (Usar o Teorema de Bayes)
13. Qual a probabilidade de um casal com dois filhos ter pelo menos uma menina?
14. Em uma pesquisa, 80% dos entrevistados preferem produto A ao produto B. Qual a probabilidade de três entrevistados aleatórios preferirem A?
15. Se lançarmos uma moeda 5 vezes, qual a probabilidade de obter 3 caras?
16. Um jogador tem 30% de chance de marcar um gol por chute. Qual a probabilidade de ele acertar pelo menos um gol em 3 chutes?
17. Se um carro tem 5% de probabilidade de falhar a cada viagem, qual a probabilidade de completar 10 viagens sem falha?
18. Qual a probabilidade de um cliente escolher aleatoriamente um produto da prateleira se há 4 produtos diferentes em igual quantidade?
19. Se uma lâmpada tem uma vida útil que segue uma distribuição exponencial com média de 1000 horas, qual a probabilidade de durar mais de 1200 horas?
20. Qual a probabilidade de, em um grupo de 23 pessoas, pelo menos duas terem aniversário no mesmo dia?

---
## Conclusão e Discussão (10 minutos)
- Recapitulação dos principais conceitos
- Importância da probabilidade no dia a dia
- Discussão sobre aplicações específicas

**Dúvidas e encerramento.**

