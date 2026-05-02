# 🤖 Prospecção Automatizada com n8n + IA

> *"Enquanto você dorme, o sistema prospecta."*

![n8n](https://img.shields.io/badge/n8n-Workflow-orange?style=for-the-badge)
![Groq](https://img.shields.io/badge/Groq-AI-purple?style=for-the-badge)
![WhatsApp](https://img.shields.io/badge/WhatsApp-Evolution_API-green?style=for-the-badge)
![Google Sheets](https://img.shields.io/badge/Google-Sheets-blue?style=for-the-badge)

---

## 🎯 O Problema

Você passa horas no Google Maps, copia nome por nome, abre o ChatGPT, personaliza a mensagem, abre o WhatsApp, manda uma por uma.

**Isso é tempo. Tempo é dinheiro. Dinheiro é liberdade.**

Esse projeto automatiza tudo isso da coleta de leads ao disparo no WhatsApp com mensagens geradas por IA, personalizadas por lead, rodando sozinho todo dia.

---

## ⚡ Como funciona

```
Google Maps → Planilha → n8n → IA gera mensagem → WhatsApp → Status atualizado
```

```
📍 Coleta leads do Google Maps
       ↓
📊 Importa para Google Sheets
       ↓
🔍 n8n lê e filtra leads com telefone
       ↓
🧠 IA analisa perfil (tem site? não tem?)
       ↓
✍️  Gera mensagem personalizada
       ↓
⏳ Aguarda 1 minuto (anti-ban)
       ↓
📱 Envia via WhatsApp
       ↓
✅ Atualiza status na planilha
```

---

## 🛠️ Stack Completa

| Ferramenta | Função | Custo |
|---|---|---|
| **n8n** | Orquestração do fluxo | Trial / Self-hosted |
| **Evolution API** | Envio via WhatsApp | Railway free tier |
| **Groq API** | Geração de mensagens com LLM | Gratuito |
| **Google Sheets** | Base de leads e controle | Gratuito |
| **Instant Data Scraper** | Coleta de leads no Maps | Gratuito |

**Custo total: R$ 0,00**

---

## 📁 Estrutura do Projeto

```
n8n-prospeccao-whatsapp/
├── workflow_prospeccao.json   # Workflow para importar no n8n
├── leads_exemplo.csv          # Modelo da planilha de leads
└── README.md
```

---

## 🚀 Como usar

### Passo 1 — Coletar leads
- Instale a extensão **Instant Data Scraper** no Chrome
- Pesquise no Google Maps: `"seu nicho + cidade"`
- Deixe rodar com rolagem infinita por 10-15 minutos
- Exporte como CSV e importe no Google Sheets

A planilha precisa ter estas colunas:
```
nome | telefone | tem_site | site | status
```

### Passo 2 — Configurar credenciais

No workflow, preencha com suas próprias chaves:

```
GROQ_API_KEY=       → console.groq.com
EVOLUTION_URL=      → sua URL da Evolution API
EVOLUTION_API_KEY=  → sua chave da Evolution API
SHEETS_ID=          → ID da sua planilha Google
```

> ⚠️ **Nunca suba suas chaves no GitHub.** Configure diretamente nos nodes do n8n.

### Passo 3 — Importar no n8n
- Clique nos 3 pontinhos → **Importar de arquivo**
- Selecione `workflow_prospeccao.json`
- Conecte sua conta Google nos nodes do Sheets
- Configure o agendamento (recomendo 10h da manhã)
- Clique em **Publicar**

---

## 🧠 Lógica de personalização

| Situação | Ângulo da mensagem |
|---|---|
| **Sem site** | "Não encontramos seu negócio no Google..." |
| **Com site** | "Seu site pode estar perdendo clientes..." |

---

## ⚠️ Boas práticas anti-ban

- Use um número dedicado para prospecção
- Comece com 20-30 mensagens por dia
- Mantenha o delay de 1 minuto entre envios
- Aumente gradualmente conforme o número aquece

---

## 🏆 Resultados

- **116 leads** coletados em 15 minutos
- **112 com telefone** prontos para disparo
- Mensagens personalizadas por IA para cada lead
- Disparo automático todo dia às 10h

---

## 👨‍💻 Autor

**João Roberto** — Desenvolvedor de sites, landing pages e automações com IA

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Conectar-blue?style=flat-square)](https://linkedin.com/in/joaorobertoo)
[![GitHub](https://img.shields.io/badge/GitHub-Seguir-black?style=flat-square)](https://github.com/joao-robertoo)

---

*Desenvolvido com auxílio do [Claude](https://claude.ai) — Anthropic*

> ⭐ Se esse projeto te ajudou, deixa uma estrela!
