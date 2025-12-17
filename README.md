# Medical AI Assistant — Fine-tuned LLM with RAG & Agents  
Tech Challenge 3 — FIAP

Este repositório apresenta o desenvolvimento de um assistente virtual médico especializado, treinado com dados internos hospitalares, projetado para apoiar a tomada de decisão clínica com foco em privacidade, segurança e explicabilidade.

O projeto foi desenvolvido como requisito do Tech Challenge 3 da FIAP, explorando Inteligência Artificial Generativa, fine-tuning de LLMs, RAG (Retrieval-Augmented Generation) e arquiteturas agênticas.

---

## Objetivo

Desenvolver um assistente médico capaz de:

- Responder dúvidas clínicas de forma contextualizada e baseada em protocolos
- Consultar dados de prontuário eletrônico via ferramentas (API)
- Operar com dados sensíveis de forma segura
- Garantir rastreabilidade, explicabilidade e validação humana

---

## Arquitetura da Solução

### Modelo de Linguagem

- Modelo base: unsloth/gemma-3-4b-it-unsloth-bnb-4bit
- Fine-tuning:
  - Framework Unsloth
  - Quantização 4-bit (bitsandbytes)
  - Técnica QLoRA
- Ambiente: Google Colab (GPU T4 — 16GB)
- Consumo aproximado de VRAM: ~5GB

A abordagem permite execução eficiente, alto grau de especialização clínica e preservação da privacidade dos dados.

---

### Dataset

- Dataset de instruções médicas curadas
- Formato Alpaca (Instruction / Input / Response)
- Foco em respostas diretas, seguras e baseadas em evidências

---

## RAG — Retrieval-Augmented Generation

- Vector Store com protocolos médicos (ex.: AVC, Sepse, IAM)
- Busca semântica por embeddings
- Recuperação do protocolo clínico exato antes da geração da resposta
- Respostas citam explicitamente a fonte do protocolo

Exemplo:
"Conforme Protocolo 600 — AVC Isquêmico..."

---

## Sistema Agêntico (LangChain / LangGraph)

O assistente opera como um agente orquestrador capaz de:

1. Identificar a intenção da pergunta
2. Decidir entre:
   - Consulta à API Mock de Prontuário Eletrônico
   - Recuperação de protocolos via RAG
3. Consolidar informações clínicas
4. Gerar resposta segura, contextualizada e auditável

---

## Segurança, Validação e Governança

### Human-in-the-loop

- O sistema não realiza prescrição médica
- Todas as respostas incluem disclaimer obrigatório
- O conteúdo gerado é exclusivamente apoio à decisão clínica
- Validação final deve ser realizada por médico com CRM ativo

### Logging e Auditoria

- Logs estruturados armazenados em `medical_audit.log`
- Registro de:
  - Pergunta do usuário
  - Ferramentas acionadas
  - Documentos recuperados
  - Resposta final

### Explicabilidade

- Respostas indicam explicitamente a fonte da informação
- Permite verificação imediata por profissionais de saúde

---

## Organização do Projeto

### Vídeo Demonstrativo

https://www.youtube.com/watch?v=Oth00h4RcEA

### Repositório Principal

https://github.com/viniciusmmartins/PosFiap-AI-TechChallange-Fase3

### Notebooks

Treinamento Gemma (Fine-tuning):  
https://colab.research.google.com/drive/1Z02pa0usH0pG8KW-j2Z3uTyl857fORvw

Pipeline RAG:  
https://colab.research.google.com/drive/1iJxiqAwLOwVhVSPh0lRJ3GiRBpvlEysU

Agente LangChain / LangGraph:  
https://colab.research.google.com/drive/1GnsEOovhovirMb6L2SeZE5Lq5SOHSrvo

---

## Modelo no Hugging Face

https://huggingface.co/gerson-analista/gemma-3-4b-lora_model

---

## Equipe

- Bruno Amorim — RM365279
- Gabriel Rizzo — RM366033
- Mauricio Magnani — RM365929
- Vinicius Martins — RM365278
- Gerson Luiz — RM366284

---

## Considerações Finais

Este projeto demonstra a viabilidade técnica do uso de modelos de linguagem especializados combinados com RAG e arquiteturas agênticas em ambientes hospitalares críticos, respeitando princípios de segurança, governança, privacidade e explicabilidade.
