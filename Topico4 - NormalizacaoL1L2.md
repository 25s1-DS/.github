# L1 e L2 

Na **análise exploratória de dados (EDA)**, o uso de **normalização L1 e L2** pode ser útil em diversos contextos, especialmente quando lidamos com algoritmos sensíveis à escala dos dados ou quando buscamos compreender a distribuição relativa de características em um conjunto de dados. A seguir, explico o que são essas normalizações e os **motivos** pelos quais você poderia usá-las durante a EDA:

---

### 🔧 O que são L1 e L2?

- **Normalização L1 (Manhattan norm):**
  - Transforma cada amostra (linha) de forma que a **soma dos valores absolutos** das suas características seja igual a 1.
  - Fórmula:  
    $$
    
    x_{i}^{\text{norm}} = \frac{x_i}{\sum_{j=1}^{n} |x_j|}
    
    $$

- **Normalização L2 (Euclidean norm):**
  - Transforma cada amostra de forma que a **soma dos quadrados** das suas características seja igual a 1 (ou seja, norma euclidiana = 1).
  - Fórmula:  
   $$
    x_{i}^{\text{norm}} = \frac{x_i}{\sqrt{\sum_{j=1}^{n} x_j^2}}
    $$

---

### 🎯 Motivos para usar L1 ou L2 na Análise Exploratória

1. **Comparabilidade entre amostras**  
   Em conjuntos de dados com diferentes escalas ou unidades (e.g., metros, segundos, graus Celsius), normalizar os dados permite compará-los mais facilmente.

2. **Redução do viés por magnitude**  
   Quando há colunas com valores numericamente maiores, elas podem dominar análises como PCA ou clustering. Normalizar evita esse viés.

3. **Melhora visualizações (como PCA, t-SNE, etc.)**  
   Transformações L1/L2 são úteis antes de técnicas de redução de dimensionalidade que se baseiam em distância.

4. **Análise de proporções (L1)**  
   A normalização L1 transforma os vetores de características em **proporções relativas**, o que pode ajudar a interpretar dados como perfis ou distribuições (ex: % de gasto por categoria).

5. **Preservação da direção (L2)**  
   A normalização L2 mantém a **direção do vetor** original, útil para modelos e análises que se baseiam em ângulos ou direções no espaço vetorial (como em vetores TF-IDF de texto).

6. **Preparação para algoritmos de machine learning**  
   Durante a EDA, é comum testar algoritmos simples (como KNN ou SVM), e muitos desses são sensíveis à escala — por isso, normalizações L1/L2 ajudam na comparação justa.

7. **Detecção de outliers mais eficiente**  
   Após normalizar, outliers podem se destacar mais claramente em gráficos ou análises de distância, pois as distâncias passam a refletir **diferenças relativas**, e não absolutas.

---

### 🧠 Quando escolher L1 vs L2?

| Situação | Prefira L1 | Prefira L2 |
|---------|------------|------------|
| Dados esparsos (muitos zeros) | ✅ Sim | ❌ Não recomendado |
| Proporções/importância relativa | ✅ Sim | ❌ Menos interpretável |
| Preservar direção do vetor | ❌ Não garante | ✅ Sim |
| Robustez a outliers | ✅ Maior | ❌ Menor |
| Aplicações de texto (TF-IDF, etc.) | ✅ Comum | ✅ Também comum |

---

