# Diagrama de Atividades — Gatilho Antigasto (RN02)

**Semana:** [Semana 3 — Elicitação do Bloco B (Requisitos 06 a 10)](../README.md)
**Responde a:** Entregável 4 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 3") — entrega oficial de Diagrama de Atividades conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 1, Semanas 1 a 3)
**Status:** Feito
**Responsável:** Davi (D2)

---

```mermaid
flowchart TD
    subgraph Usuario["Raia: Usuário"]
        A1([Histórico de compras por impulso])
        A6[Recebe notificação preventiva]
        A7{Decide adiar a compra?}
        A8[Registra decisão]
    end
    subgraph Sistema["Raia: Sistema"]
        B1[Detector de Padrão de Impulso analisa histórico]
        B2{Padrão recorrente identificado?}
        B3[Mapeia dia/horário habitual]
        B4[Agenda Gatilho para T-1h]
        B5[Gera mensagem empática contextual]
    end
    subgraph Externo["Raia: Serviço Externo de Push"]
        C1[Envia notificação push]
    end

    A1 --> B1 --> B2
    B2 -- Não --> B1
    B2 -- Sim --> B3 --> B4 --> B5 --> C1 --> A6 --> A7
    A7 -- Sim --> A8
    A7 -- Não --> A8
```
