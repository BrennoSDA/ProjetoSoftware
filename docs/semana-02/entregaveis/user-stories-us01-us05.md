# User Stories US-01 a US-05 (BDD/Gherkin)

**Semana:** [Semana 2 — Elicitação do Bloco A (Requisitos 01 a 05)](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 2") — *"Especificação BDD/Gherkin das User Stories US-01 a US-05"*
**Status:** Feito
**Responsável:** Brenno (AR1)

---

### US-01 — Conexão via Open Finance (RF01)
**Como** usuário do aplicativo **quero** conectar minhas contas bancárias via Open Finance **para que** o app monitore meus gastos automaticamente.

```gherkin
Funcionalidade: Conexão de contas via Open Finance

  Cenário: Conectar conta bancária com sucesso
    Dado que estou autenticado no aplicativo com 2FA
    E aceitei os termos de consentimento LGPD
    Quando autorizo o acesso via Open Finance ao meu banco
    Então o sistema deve armazenar um token de consentimento sem acessar minha senha bancária
    E o status da minha conexão deve mudar para "Ativo"
```

### US-02 — Categorização automática de transações (RF02)
```gherkin
Funcionalidade: Categorização automática de transações

  Cenário: Transação categorizada automaticamente
    Dado que uma nova transação foi sincronizada via Open Finance
    Quando o motor de classificação processa a transação
    Então ela deve ser categorizada automaticamente com precisão esperada acima de 92%
```

### US-03 — Metas financeiras (RF03)
```gherkin
Funcionalidade: Definição de metas financeiras

  Cenário: Criar meta de longo prazo
    Dado que estou na tela de gestão de metas
    Quando crio uma meta de longo prazo com valor alvo e prazo
    Então a meta deve ser exibida no painel com o progresso calculado a partir do saldo disponível
```

### US-04 — Notificação preventiva (RF04)
```gherkin
Funcionalidade: Notificação preventiva antidesperdício

  Cenário: Notificação enviada 1h antes do horário habitual (RN02)
    Dado que o sistema mapeou que costumo comprar delivery às sextas-feiras às 20h
    Quando chega sexta-feira às 19h
    Então devo receber uma notificação preventiva amigável sobre o gasto habitual
```

### US-05 — Registro manual em dinheiro (RF05)
```gherkin
Funcionalidade: Registro manual rápido de gastos

  Cenário: Registrar gasto em dinheiro em até 3 toques
    Dado que estou na tela inicial do aplicativo
    Quando toco no atalho de registro rápido, informo o valor e confirmo
    Então o gasto deve ser salvo utilizando no máximo 3 toques na tela
```
