# Definições de Probabilidade

A probabilidade é uma área da matemática que estuda a incerteza e os processos aleatórios. Existem três principais definições de probabilidade: **clássica**, **frequentista** e **bayesiana**. Cada uma delas possui abordagens distintas para interpretar e calcular probabilidades.

## 1. Probabilidade Clássica (Laplaceana)

A definição **clássica** de probabilidade foi introduzida por Pierre-Simon Laplace no século XVIII e se baseia na ideia de equiprobabilidade.

### Definição

Se um experimento aleatório possui um número finito de resultados igualmente prováveis, a probabilidade de um evento $A$ é dada por:

```math
P(A) = \frac{\text{Número de casos favoráveis a } A}{\text{Número total de casos possíveis}}
```

### Exemplo

No lançamento de um dado justo de seis faces, a probabilidade de obter um número par é:

```math
P(A) = \frac{3}{6} = 0.5
```

### Limitações

- Só funciona quando todos os eventos são igualmente prováveis.
- Não se aplica bem a eventos contínuos ou quando há desconhecimento sobre a distribuição dos eventos.

---

## 2. Probabilidade Frequentista

A definição **frequentista** se baseia na frequência relativa de um evento ocorrer ao longo de um grande número de experimentos repetidos.

### Definição

A probabilidade de um evento $A$ é definida como o limite da frequência relativa de $A$ conforme o número de repetições $n$ do experimento tende ao infinito:

```math
P(A) = \lim_{n \to \infty} \frac{N_A}{n}
```

onde $N_A$ é o número de vezes que o evento $A$ ocorre.

### Exemplo

Se lançarmos uma moeda justa 1.000 vezes e observarmos "cara" 510 vezes, a probabilidade estimada seria:

```math
P(\text{cara}) \approx \frac{510}{1000} = 0.51
```

### Limitações

- Exige um grande número de repetições para convergir para um valor confiável.
- Não pode ser aplicada a eventos únicos (como prever a probabilidade de um terremoto catastrófico em uma cidade específica).

---

## 3. Probabilidade Bayesiana

A definição **bayesiana** de probabilidade incorpora conhecimento prévio e atualizações à medida que novas informações se tornam disponíveis. Ela se baseia no **Teorema de Bayes**:

```math
P(A|B) = \frac{P(B|A) P(A)}{P(B)}
```

onde:

- $P(A|B)$ é a probabilidade de $A$ dado que $B$ ocorreu.
- $P(B|A)$ é a probabilidade de $B$ dado que $A$ ocorreu.
- $P(A)$ é a probabilidade prévia de $A$ (antes da nova evidência).
- $P(B)$ é a probabilidade de $B$.

### Exemplo

Suponha que 1% da população tenha uma certa doença. Um teste diagnóstico tem:

- 90% de chance de detectar corretamente a doença quando a pessoa está doente (sensibilidade).
- 95% de chance de identificar corretamente que a pessoa não tem a doença (especificidade).

Se uma pessoa testa positivo, qual a probabilidade de ela realmente estar doente?

Aplicando o Teorema de Bayes:

```math
P(\text{doente | positivo}) = \frac{P(\text{positivo | doente}) P(\text{doente})}{P(\text{positivo})}
```

O resultado pode surpreender: a probabilidade real de estar doente, mesmo com um teste positivo, pode ser bem menor do que 90%, pois depende da frequência da doença na população.

### Vantagens e Limitações

✅ Permite incorporar conhecimento prévio e atualizar as estimativas com novos dados.
✅ Se aplica bem a eventos raros e situações com poucas observações.
❌ Depende da escolha da probabilidade **a priori**, que pode ser subjetiva.

---

## Conclusão

Cada definição de probabilidade tem aplicações e limitações específicas:

- A **probabilidade clássica** é útil quando todos os eventos são igualmente prováveis.
- A **probabilidade frequentista** é eficaz em experimentos repetitivos de grande escala.
- A **probabilidade bayesiana** é poderosa para incorporar conhecimento prévio e ajustar estimativas com novas informações.

A escolha da abordagem depende do contexto do problema e da disponibilidade de dados. Na prática, a abordagem bayesiana tem ganhado popularidade devido à sua flexibilidade em lidar com incertezas e aprendizado progressivo.

