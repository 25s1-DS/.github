# Principais algoritmos de **Machine Learning** e suas **complexidades computacionais** em relação ao número de amostras \( n \) e número de características \( d \).  

## **1. Algoritmos de Aprendizado Supervisionado**  

### **Regressão Linear**  
- **Complexidade de Treinamento**: \( O(nd^2) \) ou \( O(d^3) \) se for necessário calcular a inversa da matriz  
- **Complexidade de Predição**: \( O(d) \)  
- **Descrição**: Ajusta uma linha (ou hiperplano) para minimizar o erro quadrático médio.  

### **Regressão Logística**  
- **Complexidade de Treinamento**: \( O(nd) \) a \( O(nd^2) \) (dependendo do método de otimização)  
- **Complexidade de Predição**: \( O(d) \)  
- **Descrição**: Modelo estatístico para prever probabilidades, usado principalmente em classificação binária.  

### **k-Nearest Neighbors (k-NN)**  
- **Complexidade de Treinamento**: \( O(1) \) (apenas armazena os dados)  
- **Complexidade de Predição**: \( O(nd) \)  
- **Descrição**: Para prever um novo ponto, busca os k vizinhos mais próximos e faz uma votação.  

### **Árvores de Decisão (Decision Trees)**  
- **Complexidade de Treinamento**: \( O(nd \log n) \)  
- **Complexidade de Predição**: \( O(\log n) \)  
- **Descrição**: Cria uma estrutura de árvore onde cada nó divide os dados com base em uma característica.  

### **Random Forest (Floresta Aleatória)**  
- **Complexidade de Treinamento**: \( O(m \cdot n d \log n) \) (onde \( m \) é o número de árvores)  
- **Complexidade de Predição**: \( O(m \log n) \)  
- **Descrição**: Conjunto de árvores de decisão, onde cada uma é treinada em subconjuntos aleatórios dos dados.  

### **Suport Vector Machine (SVM)**  
- **Complexidade de Treinamento**:  
  - Linear Kernel: \( O(nd) \)  
  - Kernel Gaussiano/RBF: \( O(n^2 d) \) a \( O(n^3) \)  
- **Complexidade de Predição**:  
  - Linear Kernel: \( O(d) \)  
  - Kernel Gaussiano: \( O(n d) \)  
- **Descrição**: Encontra um hiperplano ótimo para separar as classes.  

### **Redes Neurais (MLP, CNN, RNN)**  
- **Complexidade de Treinamento**: \( O(n d L) \) (onde \( L \) é o número de camadas e neurônios por camada)  
- **Complexidade de Predição**: \( O(d L) \)  
- **Descrição**: Modelos inspirados no cérebro humano, usados para classificação, regressão e visão computacional.  

---

## **2. Algoritmos de Aprendizado Não Supervisionado**  

### **K-Means**  
- **Complexidade de Treinamento**: \( O(nkd) \) (onde \( k \) é o número de clusters)  
- **Complexidade de Predição**: \( O(kd) \)  
- **Descrição**: Agrupa dados minimizando a variância dentro de cada cluster.  

### **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**  
- **Complexidade de Treinamento**: \( O(n \log n) \) a \( O(n^2) \) (depende da implementação e do número de pontos vizinhos)  
- **Complexidade de Predição**: \( O(1) \)  
- **Descrição**: Identifica clusters baseando-se na densidade dos pontos.  

### **Hierarchical Clustering (Aglomerativo ou Divisivo)**  
- **Complexidade de Treinamento**: \( O(n^2 \log n) \)  
- **Complexidade de Predição**: \( O(n) \)  
- **Descrição**: Forma uma hierarquia de clusters através de fusões ou divisões sucessivas.  

---

## **3. Algoritmos de Redução de Dimensionalidade**  

### **PCA (Principal Component Analysis)**  
- **Complexidade de Treinamento**: \( O(n d^2) \) (se \( d \) for menor que \( n \)) ou \( O(d^3) \) (se \( d \) for grande)  
- **Complexidade de Predição**: \( O(d^2) \)  
- **Descrição**: Reduz a dimensionalidade projetando os dados em direções de maior variância.  

### **t-SNE (t-Distributed Stochastic Neighbor Embedding)**  
- **Complexidade de Treinamento**: \( O(n^2) \)  
- **Complexidade de Predição**: \( O(n) \)  
- **Descrição**: Usa técnicas probabilísticas para mapear dados de alta dimensão em um espaço de menor dimensão para visualização.  

