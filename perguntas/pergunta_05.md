Quais algoritmos de aprendizado de máquina e quais métricas de avaliação foram usados? 

Diversos algoritmos de aprendizado de máquina foram utilizados para desenvolver modelos preditivos com base nos dados do **DASS-21**, e as métricas de avaliação foram aplicadas para medir o desempenho desses modelos. Aqui estão os detalhes:  
  
### **Algoritmos Utilizados**  
1. **Deep Learning**:  
   - Um modelo de rede neural profunda baseado no algoritmo multilayer perceptron (MLP) foi construído, utilizando funções ReLU e o otimizador Adam para ajuste de pesos. Estrutura: (21, 50, 50, 50, 3), onde 21 representa os atributos (questões do DASS-21) e 3 são as classes-alvo (depressão, ansiedade e estresse)  ^1^ .  
  
2. **K-Nearest Neighbor (k-NN)**:  
   - Número de vizinhos estimados: 20.  
   - Método de distância: Euclidiana  ^1^ .  
  
3. **Support Vector Machine (SVM)**:  
   - Kernel: RBF.  
   - Parâmetros: custo da penalidade $ C = 1.0 $, epsilon $ \epsilon = 0.1 $ e $ \gamma = 0.047 $  ^1^ .  
  
4. **Random Forest (RF)**:  
   - Número de árvores: 10  ^1^ .  
  
5. **Naïve Bayes**:  
   - Utilizado como um modelo probabilístico para classificação  ^1^ .  
  
6. **AdaBoost**:  
   - Número de estimadores: 50.  
   - Taxa de aprendizado: 1.0.  
   - Método de boosting: SAMME com função de perda de regressão linear  ^1^ .  
  
### **Métricas de Avaliação**  
As métricas aplicadas para avaliar o desempenho dos modelos incluem:  
1. **Precisão (Accuracy)**: Mede a proporção de classificações corretas em relação ao total de previsões  ^1^ .  
2. **Área sob a curva ROC (AUC)**: Avalia a capacidade do modelo de distinguir entre classes  ^1^  ^2^ .  
3. **F1-Score**: Combina precisão e recall para medir o equilíbrio entre falsos positivos e falsos negativos  ^1^ .  
4. **Precisão (Precision)**: Mede a proporção de verdadeiros positivos entre as previsões positivas  ^1^ .  
5. **Recall**: Mede a proporção de verdadeiros positivos entre os casos realmente positivos  ^1^ .  
6. **Coeficiente Kappa**: Avalia a concordância entre as previsões do modelo e os valores reais, ajustando pelo acaso  ^2^ .  
  
### **Desempenho dos Modelos**  
- O modelo de deep learning apresentou **precisão acima de 90%** e **AUC acima de 99%** para as categorias de depressão, ansiedade e estresse, sendo o mais eficaz em geral  ^1^  ^2^ .  
- Outros modelos, como Naïve Bayes e Random Forest, também apresentaram bons resultados, com precisão variando entre 83% e 85% dependendo do estado emocional  ^1^  ^2^ .  
  
Esses algoritmos e métricas foram cruciais para identificar o modelo mais eficiente, permitindo sua aplicação em contextos clínicos e de pesquisa.
