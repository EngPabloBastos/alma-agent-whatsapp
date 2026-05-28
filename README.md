# alma-agent-whatsapp

AI-powered WhatsApp customer service automation built with n8n, Google Gemini, Evolution API and Redis.

🇺🇸 English | 🇧🇷 Português

* [English Version](#english)
* [Versão em Português](#português)

---

# English

# Alma Agent — Intelligent WhatsApp Customer Service

> AI-powered WhatsApp automation agent developed for **Alma Tecnologia** — a PagBank sub-acquirer specialized in payment solutions.

---

## About the Project

**Alma Agent** is an automation workflow built with **n8n** that acts as an intelligent WhatsApp virtual assistant, answering customer and lead questions based on business rules and AI prompts — including smart delivery of pricing/rate tables according to customer profiles.

The agent identifies the type of incoming message (text or image) and routes the workflow accordingly, ensuring fast, personalized and consistent responses 24/7.

---

## Workflow Architecture

```txt
Webhook (WhatsApp)
    └── Edit Fields
        └── Global Config
            └── FromME (Evolution API)
                ├── Key Block → [blocks unwanted messages]
                └── Redis (cache/session)
                    └── If (context validation)
                        ├── [Do Nothing] → No Operation
                        └── [AI] → AI Agent (Google Gemini)
                                └── Switch (response type)
                                    ├── Send Text → Evolution API
                                    ├── Send Image D0 → Evolution API
                                    └── Send Image D1 → Evolution API
```

---

## Stack & Technologies

| Component              | Technology                 |
| ---------------------- | -------------------------- |
| Workflow Orchestration | n8n                        |
| Messaging Channel      | WhatsApp via Evolution API |
| AI Model               | Google Gemini              |
| Session Memory         | Redis + Simple Memory      |
| Routing Logic          | Switch Node                |
| Hosting                | Self-hosted (Local/VPS)    |

---

## Features

* Receives WhatsApp messages via Webhook
* Processes and answers customer questions automatically
* Sends personalized pricing/rate tables based on customer profile
* Handles different response types (text and images)
* Session management using Redis
* Blocks unwanted messages and contexts
* Image understanding support (in development)
* Audio transcription and interpretation (in development)

---

## How to Use

### Requirements

* n8n installed (self-hosted or cloud)
* Evolution API configured and connected to WhatsApp
* Google Cloud account with Gemini API access
* Redis instance available

### Importing the Workflow

1. Download the `Alma_Agent.json` file
2. Open n8n → **Workflows → Import from File**
3. Select the JSON file
4. Configure your credentials:

   * Evolution API
   * Google Gemini API Key
   * Redis
5. Configure the **Global Config** node
6. Customize the AI prompt with your business information
7. Activate the workflow ✅

---

## Repository Structure

```txt
alma-agent-whatsapp/
├── Alma_Agent.json
├── README.md
└── assets/
    └── workflow-preview.png
```

---

## About Alma Tecnologia

**Alma Tecnologia** is a PagBank-accredited sub-acquirer focused on payment solutions, card machines and financial services for businesses of all sizes.

---

## License

This project was developed for internal use at Alma Tecnologia. Feel free to use the architecture as inspiration for your own projects.

---

*Built with n8n + Google Gemini + Evolution API*

---

# Português

# Alma Agent — Atendimento Inteligente via WhatsApp

> Agente de IA para atendimento automatizado no WhatsApp, desenvolvido para a **Alma Tecnologia** — subadquirente da PagBank especializada em soluções de meios de pagamento.

---

## Sobre o Projeto

A **Alma Agent** é uma automação construída em **n8n** que atua como assistente virtual no WhatsApp, respondendo dúvidas de clientes e potenciais clientes com base em informações configuradas no prompt — incluindo envio inteligente de tabelas de taxas de acordo com o perfil do cliente.

O agente identifica o tipo de mensagem recebida (texto ou imagem) e roteia o fluxo de forma adequada, garantindo respostas rápidas, consistentes e personalizadas 24/7.

---

## Arquitetura do Fluxo

```txt
Webhook (WhatsApp)
    └── Edit Fields
        └── Config Global
            └── FromME (Evolution API)
                ├── Chave Block → [bloqueia mensagens indesejadas]
                └── Redis (cache/sessão)
                    └── If (verifica contexto)
                        ├── [Fazer Nada] → No Operation
                        └── [IA] → AI Agent (Google Gemini)
                                └── Switch (tipo de resposta)
                                    ├── Enviar Texto → Evolution API
                                    ├── Enviar Imagem D0 → Evolution API
                                    └── Enviar Imagem D1 → Evolution API
```

---

## Stack & Tecnologias

| Componente         | Tecnologia                 |
| ------------------ | -------------------------- |
| Orquestração       | n8n                        |
| Canal de mensagens | WhatsApp via Evolution API |
| Modelo de IA       | Google Gemini              |
| Memória de sessão  | Redis + Simple Memory      |
| Roteamento         | Switch Node                |
| Hospedagem         | Self-hosted (local/VPS)    |

---

## Funcionalidades

* Recebe mensagens via Webhook do WhatsApp
* Processa e responde perguntas automaticamente
* Envia tabelas de taxas personalizadas
* Diferencia respostas em texto e imagem
* Gerencia sessões via Redis
* Bloqueia mensagens/contextos indesejados
* Compreensão de imagens (em desenvolvimento)
* Transcrição e interpretação de áudios (em desenvolvimento)

---

## Como usar

### Pré-requisitos

* n8n instalado
* Evolution API configurada
* Conta Google Cloud com Gemini API
* Instância Redis

### Importar o workflow

1. Baixe o arquivo `Alma_Agent.json`
2. No n8n vá em **Workflows → Import from File**
3. Selecione o JSON
4. Configure as credenciais:

   * Evolution API
   * Gemini API
   * Redis
5. Configure o nó **Config Global**
6. Ajuste o prompt do agente
7. Ative o workflow ✅

---

## Estrutura do Repositório

```txt
alma-agent-whatsapp/
├── Alma_Agent.json
├── README.md
└── assets/
    └── workflow-preview.png
```

---

## Sobre a Alma Tecnologia

A **Alma Tecnologia** é uma subadquirente credenciada da PagBank, oferecendo soluções completas em meios de pagamento para empresas de diversos portes.

---

## Licença

Projeto desenvolvido para uso interno da Alma Tecnologia. Sinta-se livre para se inspirar na arquitetura para seus próprios projetos.

---

*Construído com n8n + Google Gemini + Evolution API*

