# 🤖 Telegram Bot – Verificação de Assinatura

Bot desenvolvido em **Python** utilizando a biblioteca **TeleBot (pyTelegramBotAPI)** para automatizar a verificação de pagamentos e assinaturas, coletar dados do usuário e fornecer acesso a grupos exclusivos no Telegram.

O bot interage de forma conversacional, validando **nome**, **telefone** e **e-mail**, além de integrar com APIs externas e um banco de dados.

---

## 🚀 Funcionalidades

- Atendimento automatizado via Telegram
- Coleta e validação de dados do usuário (nome, telefone e e-mail)
- Verificação automática de status de assinatura
- Envio de link de grupo para assinantes ativos
- Comandos administrativos (exclusão de usuários)
- Integração com banco de dados
- Integração com API externa de pagamentos
- Agendamentos automáticos com `schedule`

---

## 🧩 Tecnologias Utilizadas

- Python 3
- TeleBot (pyTelegramBotAPI)
- Regex para validação de dados
- Schedule (tarefas agendadas)
- API externa (pagamentos / membros)
- Banco de dados relacional

---

## ⚙️ Variáveis de Ambiente

Antes de iniciar o bot, configure as seguintes variáveis de ambiente:

```env
TOKEN=SEU_TOKEN_DO_BOT_TELEGRAM
Owner_id=ID_DO_ADMINISTRADOR
```

---

## 🗂️ Estrutura do Projeto

```bash
.
├── main.py
├── functions/
│   ├── api_requests.py
│   └── db_requests.py
└── requirements.txt
```

---

## 🔄 Fluxo de Funcionamento

1. Usuário inicia o bot com `/start`
2. Bot solicita os dados necessários
3. Dados são validados via regex
4. Bot consulta a API de pagamentos
5. Verifica o status da assinatura
6. Usuário recebe:
   - Acesso ao grupo (assinatura ativa)
   - Mensagem de erro (assinatura inválida)
7. Dados são armazenados no banco

---

## 📌 Comandos Disponíveis

### 👤 Usuário

- `/start` – Inicia o atendimento
- `/grupo` – Solicita link de acesso ao grupo
- `/eu` – Exibe os dados cadastrados
- `/alterar_dados` – Altera nome, telefone ou e-mail
- `/Nome` – Alterar nome
- `/Telefone` – Alterar telefone
- `/Email` – Alterar e-mail
- `/help` – Lista de comandos
- `/suporte` – Informações de contato
- `/get_id` – Retorna o ID do usuário

---

### 🛠️ Administrador

- `/del` – Remove um usuário do banco de dados

---

## ⏱️ Tarefas Agendadas

O bot executa automaticamente, todos os dias às **12:00**, a verificação de membros:

```python
schedule.every().day.at("12:00").do(api_requests.ver_membros, bot)
```

---

## 🧪 Validações

- **E-mail:** Regex padrão
- **Telefone:** Validação com DDD
- **Confirmação:** O usuário precisa confirmar os dados digitando palavras como:
  - `sim`, `correto`, `certo`, `s`

---

## ⚠️ Observações Importantes

- O bot funciona apenas em **conversas privadas**
- Alterações na API externa podem exigir ajustes
- O bot utiliza estados globais (flags), recomendado uso com cuidado
- Ideal para automações de **produtos digitais, cursos ou assinaturas**

---
