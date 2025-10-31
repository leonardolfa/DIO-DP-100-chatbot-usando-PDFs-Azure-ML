# Chat Interativo com IA sobre o DASS

Este projeto utiliza Azure Foundry, Azure ML Studio, Cognitive Search e OpenAI para criar um sistema de chat inteligente que responde com base em dois artigos científicos sobre o uso de aprendizado de máquina no questionário Depression, Anxiety and Stress Scales (DASS).

## Objetivo
Facilitar a análise de artigos científicos usando IA generativa e busca vetorial.

## Tecnologias Utilizadas
- Azure Foundry
- Azure ML Studio
- Azure Cognitive Search
- Azure OpenAI
- Azure Blob Storage

## Etapas Realizadas
1. Upload de dois PDFs no Foundry.
2. Configuração de prompt no Playground com GPT-4o.
3. Testes com perguntas sobre os artigos.
4. Validação das respostas geradas.

## Artigos Utilizados

Este projeto foi baseado nos seguintes artigos científicos sobre o uso de aprendizado de máquina no questionário DASS:

1. **Assessment of Anxiety, Depression and Stress using Machine Learning Models**  
   DOI: [10.1016/j.procs.2020.04.213](https://doi.org/10.1016/j.procs.2020.04.213)

2. **Machine Learning-Based Classification of Mental Health State Using the DASS-21 Profile**  
   DOI: [10.1109/BMEiCON64021.2024.10896316](https://doi.org/10.1109/BMEiCON64021.2024.10896316)

### Instrução para o modelo

Instruções e o contexto do modelo: *"Você é um especialista em aprendizado de máquina com experiência na aplicação de modelos preditivos e análises estatísticas baseadas no questionário Depression, Anxiety and Stress Scales (DASS). Seu objetivo é me ajudar a desenvolver e entender abordagens adequadas para o uso de dados do DASS em contextos de pesquisa, predição e avaliação psicológica."*

## Exemplos de Perguntas e Respostas

*Pergunta*: **O que é o DASS?**

*Resposta:*
O DASS, ou **Depression, Anxiety and Stress Scales**, é um questionário de autoavaliação amplamente utilizado para pré-triagem de sintomas de depressão, ansiedade e estresse. Ele foi originalmente desenvolvido em sua forma completa como DASS-42 por Lovibond et al. em 1995, sendo um instrumento padronizado baseado em uma escala Likert  ^1^  ^2^ .   
  
Existem versões reduzidas do DASS, como o **DASS-21** e o **DASS-12**, contendo 21 ou 12 questões, respectivamente. Essas versões mantêm alta precisão de avaliação em relação ao DASS-42, conforme demonstrado por análises fatoriais confirmatórias  ^1^  ^2^ . O DASS é utilizado em contextos clínicos e de pesquisa para avaliar o nível de gravidade dos estados emocionais, como depressão, ansiedade e estresse, permitindo classificá-los em cinco níveis de severidade: normal, leve, moderado, grave e extremamente grave  ^3^ .

---
*Pergunta*: **Como o aprendizado de máquina está sendo aplicado a esse questionário?**

*Resposta:*
O aprendizado de máquina está sendo aplicado ao questionário **DASS-21** para melhorar a triagem e classificação dos estados emocionais de depressão, ansiedade e estresse. A abordagem envolve o uso de modelos de classificação para prever a gravidade desses estados com base nas respostas fornecidas pelos participantes. Aqui estão os principais pontos sobre essa aplicação:  
  
1. **Construção de Modelos**: Foram avaliados seis modelos de aprendizado de máquina — incluindo deep learning, k-nearest neighbor (k-NN), support vector machine (SVM), random forest, Naïve Bayes e AdaBoost — para prever os níveis de severidade (normal, leve, moderado, grave e extremamente grave) dos estados emocionais com base no DASS-21  ^1^  ^2^ .  
  
2. **Desempenho dos Modelos**: O modelo de deep learning apresentou o melhor desempenho geral, com precisão superior a 90% para as categorias de depressão, ansiedade e estresse, e área sob a curva (AUC) acima de 99%  ^1^  ^3^ . Outros modelos, como o Naïve Bayes e o multilayer perceptron, também tiveram alta precisão em diferentes níveis de severidade  ^2^  ^4^ .  
  
3. **Benefícios Clínicos**: A aplicação de aprendizado de máquina ao DASS-21 permite automatizar e melhorar os processos de triagem de saúde mental, especialmente em configurações não clínicas ou diagnósticos iniciais. Isso pode ajudar profissionais de saúde a tomar decisões mais precisas e rápidas sobre o estado mental dos pacientes  ^3^ .  
  
4. **Desafios Identificados**: Apesar do sucesso, os modelos enfrentaram dificuldades em classificar corretamente os estados de severidade "grave" e "extremamente grave", principalmente devido ao desequilíbrio de classes nos dados. Soluções como aumento de dados, técnicas de reamostragem ou modelos híbridos foram sugeridas para melhorar a precisão nesses casos  ^3^ .  
  
5. **Ampliação do Modelo**: Para tornar os modelos mais robustos, pesquisas futuras poderiam integrar dados demográficos, variáveis psicossociais ou outros parâmetros clínicos, ampliando sua aplicabilidade em contextos clínicos e em diferentes populações  ^3^ .  
  
Essas aplicações demonstram o potencial do aprendizado de máquina para transformar ferramentas de avaliação psicológica como o DASS-21 em sistemas inteligentes e adaptáveis, promovendo melhores resultados em saúde mental.

---
Veja todas as perguntas em [`docs/arquitetura.md`](docs/arquitetura.md) na seção "Testes Realizados". 
Também há os arquivos com as perguntas e respostas em [perguntas/](perguntas/) ou [img/](img/).

## Experimento e Resultados

Durante os testes realizados com dois artigos científicos sobre o uso de aprendizado de máquina no questionário DASS, o sistema apresentou **bons resultados** na geração de respostas contextuais.

### Observações

- O sistema foi capaz de **referenciar corretamente os dois artigos** em diversas respostas, demonstrando que a busca vetorial e a IA generativa estavam funcionando de forma integrada.
- Em algumas perguntas a resposta gerada foi **completa e técnica**, mas **referenciou apenas um dos artigos** - [Machine Learning-Based Classification of Mental Health State Using the DASS-21 Profile](pdfs/Machine%20Learning-Based%20Classification%20of%20Mental%20Health%20State%20Using%20the%20DASS-21%20Profile.pdf), mesmo que o conteúdo da pergunta envolvesse aspectos abordados nos dois.
- Isso indica que, embora o sistema consiga recuperar trechos relevantes, ele pode priorizar um documento em detrimento de outro, dependendo da similaridade vetorial ou da estrutura dos textos.

### Conclusão

O experimento validou a eficácia da arquitetura RAG aplicada via Azure Foundry, mostrando que é possível construir um sistema de apoio à pesquisa científica com base em documentos específicos. Pequenas limitações na cobertura de múltiplas fontes podem ser ajustadas com refinamento de prompt ou ajustes na vetorização.

## Arquitetura

Veja em [`docs/arquitetura.md`](docs/arquitetura.md)