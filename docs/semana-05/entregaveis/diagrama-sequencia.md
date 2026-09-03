# Diagrama de Sequência

**Semana:** [Semana 5 — Wireframes de Média Fidelidade (Mid-Fi)](../README.md)
**Responde a:** entrega oficial de Diagrama de Sequência conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 2, "Entrega: Semanas 4 e 5")
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

## 1. Conexão Open Finance, sincronização e categorização

```mermaid
sequenceDiagram
    actor U as Usuário
    participant App as App Mobile (Flutter)
    participant Auth as Autenticação/Consentimento
    participant OF as Gateway Open Finance
    participant Sync as Serviço de Sincronização
    participant IA as Motor de Classificação (IA)
    participant DB as Base de Transações

    U->>App: Solicita conectar conta bancária
    App->>Auth: Inicia consentimento (2FA + termos LGPD)
    Auth-->>U: Solicita 2FA
    U-->>Auth: Confirma 2FA
    Auth->>OF: Requisita autorização Open Finance
    OF-->>Auth: Token de consentimento (sem senha bancária, RNF-01)
    Auth-->>App: Consentimento registrado
    loop A cada 12h (RNF-02)
        Sync->>OF: Solicita extrato/faturas atualizadas
        OF-->>Sync: Retorna transações
        Sync->>IA: Envia lote de transações
        IA-->>Sync: Transações categorizadas (meta >92%, RNF-08)
        alt Categoria não identificada
            IA-->>DB: Marca como "A Classificar" (RN04)
        else Categoria identificada
            IA-->>DB: Persiste transação categorizada
        end
    end
    DB-->>App: Atualiza feed de transações
```

## 2. Disparo do Gatilho Antigasto (RN02)

```mermaid
sequenceDiagram
    participant Detector as Detector de Padrão de Impulso
    participant Agenda as Agendador de Gatilhos
    participant Gateway as Gateway de Notificações (RNF-04, <500ms)
    participant Push as Serviço Externo de Push
    actor U as Usuário

    Detector->>Detector: Identifica horário habitual da compra por impulso
    Detector->>Agenda: Registra gatilho para (horário_habitual - 1h)
    Note over Agenda: RN02 — disparo exatamente 1h antes
    Agenda->>Gateway: Dispara evento no horário agendado
    Gateway->>Push: Envia payload (<500ms)
    Push-->>U: Notificação preventiva amigável
```
