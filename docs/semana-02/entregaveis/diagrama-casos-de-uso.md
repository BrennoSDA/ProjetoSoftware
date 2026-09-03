# Diagrama de Casos de Uso

**Semana:** [Semana 2 — Elicitação do Bloco A (Requisitos 01 a 05)](../README.md)
**Responde a:** Entregável 4 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 2") — entrega oficial de Diagrama de Casos de Uso conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 1, Semanas 1 a 3)
**Status:** Feito
**Responsável:** Brenno (AR1)

---

```mermaid
flowchart LR
    U[Usuário Final]
    OF[(Sistema Externo: Open Finance)]
    PN[(Serviço Externo: Push Notification Gateway)]

    subgraph Sistema["Conselheiro Financeiro Comportamental"]
        UC1((Conectar Contas via Open Finance))
        UC2((Categorizar Transações Automaticamente))
        UC3((Definir Metas Financeiras))
        UC4((Enviar Notificação Preventiva))
        UC5((Registrar Gasto Manual em Dinheiro))
        UC6((Simular Impacto de Gasto))
        UC7((Responder Quiz de Perfil Comportamental))
        UC8((Acompanhar Trilhas Gamificadas))
        UC9((Consultar Score Comportamental))
        UC10((Gerenciar Meta Conjunta))
        UC11((Autenticar com 2FA))
        UC12((Registrar Consentimento LGPD))
        UC13((Revogar Consentimento Open Finance))
        UC14((Classificar Transação Pendente))
    end

    U --> UC1
    U --> UC3
    U --> UC5
    U --> UC6
    U --> UC7
    U --> UC8
    U --> UC9
    U --> UC10
    U --> UC13
    U --> UC14
    U --> UC4

    UC1 -. include .-> UC11
    UC1 -. include .-> UC12
    UC2 -. extend .-> UC14
    UC1 <--> OF
    UC2 <--> OF
    UC4 <--> PN
```

> Nota de notação: Mermaid não tem um tipo nativo de Diagrama de Casos de Uso; a representação acima é uma aproximação via `flowchart`. Ver observação em [diagramasUML.md](../../../diagramasUML.md) e item correspondente em [BACKLOG.md](../../../BACKLOG.md) caso a entrega formal exija notação UML estrita (ex. PlantUML).
