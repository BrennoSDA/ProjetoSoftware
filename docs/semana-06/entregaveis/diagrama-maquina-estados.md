# Diagrama de Máquina de Estados

**Semana:** [Semana 6 — Design System "Mindful Finance UX"](../README.md)
**Responde a:** entrega oficial de Diagrama de Máquina de Estados conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 2, "Entrega: Semanas 5 e 6")
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

## 1. Ciclo de vida de `Transacao`

```mermaid
stateDiagram-v2
    [*] --> Recebida
    Recebida --> Classificada: categorização automática bem-sucedida (RNF-08)
    Recebida --> AClassificar: dados insuficientes do estabelecimento (RN04)
    AClassificar --> Classificada: usuário classifica manualmente
    Classificada --> ConsideradaNoScore: incluída no cálculo semanal
    AClassificar --> ScoreSuspenso: bloqueia cálculo do score (RN04)
    ScoreSuspenso --> ConsideradaNoScore: transação classificada, score reativado
    ConsideradaNoScore --> [*]
```

## 2. Ciclo de vida de `ConsentimentoOpenFinance`

```mermaid
stateDiagram-v2
    [*] --> Ativo: usuário concede consentimento (LGPD-01)
    Ativo --> Revogado: usuário revoga consentimento
    Revogado --> Ativo: usuário restabelece acesso (< 30 dias)
    Revogado --> DadosOcultos: 30 dias sem restabelecimento (RN01)
    Ativo --> Congelado: suspeita de incidente de segurança (LGPD-02)
    Congelado --> Ativo: incidente resolvido e ANPD notificada
    DadosOcultos --> [*]
```
