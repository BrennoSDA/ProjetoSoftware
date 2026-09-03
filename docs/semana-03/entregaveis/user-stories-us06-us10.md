# User Stories US-06 a US-10 (BDD/Gherkin)

**Semana:** [Semana 3 — Elicitação do Bloco B (Requisitos 06 a 10)](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 3") — *"Especificação BDD/Gherkin das User Stories US-06 a US-10"*
**Status:** Feito
**Responsável:** Joel (AR2)

---

### US-06 — Simulador de impacto de gasto (RF06)
```gherkin
Funcionalidade: Simulador de impacto de gastos nas metas

  Cenário: Simular impacto de gasto supérfluo em uma meta
    Dado que tenho uma meta "Viagem de Fim de Ano" com um prazo definido
    Quando simulo um gasto de R$ 600 fora do orçamento
    Então o sistema deve exibir o novo prazo estimado para alcançar a meta

  Cenário: Bloquear sugestão de aporte abaixo da reserva mínima (RN03)
    Dado que meu saldo atual é inferior a 1 mês do meu custo de vida básico
    Quando simulo ou consulto uma sugestão de aporte em uma meta de longo prazo
    Então o sistema não deve sugerir investimentos ou aportes
    E deve exibir um aviso explicando a trava de reserva mínima
```

### US-07 — Quiz de perfil comportamental (RF07)
```gherkin
Funcionalidade: Quiz de perfil comportamental de gastos

  Cenário: Concluir quiz e obter perfil
    Dado que respondi todas as perguntas do quiz comportamental
    Quando envio minhas respostas
    Então o sistema deve calcular e exibir meu perfil de gastador
```

### US-08 — Trilhas gamificadas (RF08)
```gherkin
Funcionalidade: Trilhas gamificadas de educação financeira

  Cenário: Receber trilha recomendada após identificar erro de consumo
    Dado que meu perfil comportamental identificou um padrão de compras por impulso
    Quando acesso o hub de trilhas
    Então devo ver uma trilha gamificada recomendada relacionada a esse padrão
```

### US-09 — Score comportamental semanal (RF09)
```gherkin
Funcionalidade: Score de saúde financeira comportamental semanal

  Cenário: Calcular score semanal
    Dado que todas as minhas transações da semana estão classificadas
    Quando o sistema processa o fechamento semanal
    Então uma pontuação de saúde financeira comportamental deve ser calculada e exibida no dashboard

  Cenário: Score não calculado com transações pendentes (RN04)
    Dado que existem transações no limbo "A Classificar" na semana
    Quando o sistema tenta calcular o score semanal
    Então o cálculo deve permanecer suspenso até que todas as transações sejam classificadas
```

### US-10 — Meta conjunta (RF10)
```gherkin
Funcionalidade: Metas conjuntas com privacidade individual

  Cenário: Criar meta conjunta com privacidade individual (RN05)
    Dado que estou vinculado a uma conta conjunta com meu cônjuge
    Quando crio uma meta conjunta e ativo a opção de ocultar o destino de compras individuais
    Então o feed compartilhado deve exibir apenas o valor total debitado e o impacto no orçamento
    E não deve revelar o nome do estabelecimento da compra individual
```
