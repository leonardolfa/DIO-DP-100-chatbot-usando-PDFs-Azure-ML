## 🧱 Arquitetura do Projeto

Este projeto utiliza uma arquitetura baseada em **RAG (Retrieval-Augmented Generation)**, combinando IA generativa com busca vetorial para responder perguntas sobre documentos PDF.

### Componentes Utilizados

| Componente              | Função                                                                 |
|-------------------------|------------------------------------------------------------------------|
| **Azure Foundry**       | Orquestra os serviços de IA e permite configurar o chat com GPT-4o.    |
| **Azure OpenAI**        | Gera respostas contextuais com base nos PDFs carregados.               |
| **Azure Blob Storage**  | Armazena os arquivos PDF utilizados como fonte de conhecimento.        |
| **Azure Cognitive Search** | Indexa os PDFs e realiza busca vetorial para recuperar trechos relevantes. |
| **Azure ML Studio**     | (Opcional) Pode ser usado para treinar modelos personalizados.         |

---

### Fluxo de Funcionamento

1. **Upload dos PDFs**: Os arquivos são enviados para o Azure Blob Storage.
2. **Processamento dos documentos**: O Foundry extrai o texto dos PDFs e divide em trechos (chunks).
3. **Vetorização**: Cada trecho é transformado em um vetor de embeddings usando modelos da OpenAI.
4. **Indexação**: Os vetores são armazenados no Azure Cognitive Search.
5. **Interação via Chat**:
   - O usuário faz uma pergunta no chat.
   - A pergunta é convertida em vetor.
   - O sistema busca os trechos mais relevantes nos PDFs.
   - Esses trechos são enviados como contexto para o modelo GPT-4o.
   - O modelo gera uma resposta fundamentada nos documentos.

---

### Testes Realizados

- Foram adicionados dois artigos científicos sobre o uso de ML no DASS-21.
- O chat foi testado com as perguntas:
  - [“O que é o DASS?”](../perguntas/pergunta_01)
  - [“Como o aprendizado de máquina está sendo aplicado a esse questionário?”](../perguntas/pergunta_02)
  - [“Como é feito o pré-processamento dos dados?”](../perguntas/pergunta_03)
  - ["Os modelos treinados podem ter aplicações clínicas?"](../perguntas/pergunta_04)
  - ["Quais algoritmos de aprendizado de máquina e quais métricas de avaliação foram usados? "](../perguntas/pergunta_05)
  - ["Quais foram os principais achados dos estudos? Há limitações apontadas nos estudos sobre o uso do DASS com ML?"](../perguntas/pergunta_06)
  - ["Os dois estudos concordam sobre a eficácia do DASS com ML?"](../perguntas/pergunta_07)

---

### Benefícios da Arquitetura

- Permite respostas precisas com base em documentos específicos.
- Reduz dependência de conhecimento genérico dos modelos.
- Facilita análise de artigos científicos para fins acadêmicos.