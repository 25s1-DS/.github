Na engenharia, a probabilidade é amplamente usada para análise de riscos, confiabilidade de sistemas, controle de qualidade e otimização de processos. Aqui está um exemplo prático:  

### **Confiabilidade de um Componente Eletrônico**  
Em engenharia elétrica e eletrônica, a **probabilidade de falha** de um componente é um fator crítico para garantir a confiabilidade de sistemas.  

Suponha que um capacitor em um circuito tenha uma taxa de falha de **0,001 por hora de operação**. Se o equipamento deve funcionar por **1000 horas**, podemos calcular a probabilidade de que o capacitor **não falhe** nesse período usando a **distribuição exponencial**:  

$P(\text{nenhuma falha}) = e^{-\lambda t}$

Onde:  
- $\lambda = 0,001$ falhas por hora  
- $t = 1000$ horas  
- $e$ é a base do logaritmo natural ($\approx 2,718$)  

$$
P(\text{nenhuma falha}) = e^{- (0.001 \times 1000)} = e^{-1} \approx 0.367
$$

Ou seja, a probabilidade do capacitor **não falhar** após 1000 horas é aproximadamente **36,7%**. Isso indica um risco significativo de falha e pode levar o engenheiro a buscar componentes mais confiáveis ou implementar redundâncias no sistema.  

Esse tipo de análise é essencial para projetar sistemas críticos, como aeronaves, equipamentos médicos e usinas de energia, onde falhas podem ter consequências graves.