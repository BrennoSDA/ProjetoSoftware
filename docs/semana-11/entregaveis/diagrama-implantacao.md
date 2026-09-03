# Diagrama de Implantação

**Semana:** [Semana 11 — Montagem do Protótipo Interativo](../README.md)
**Responde a:** Entregável 3 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 11"); entrega oficial conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 3, "Entrega: Semana 11")
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

```mermaid
flowchart LR
    subgraph Mobile["Dispositivo do Usuário"]
        AppiOS[App iOS - Flutter]
        AppAndroid[App Android - Flutter]
    end
    subgraph Cloud["Infraestrutura em Nuvem (AWS/GCP)"]
        APIGW[API Gateway]
        subgraph Micro["Microsserviços"]
            SvcOF[Integração Open Finance]
            SvcIA[Classificação IA - autoscaling, RNF-07]
            SvcMetas[Metas e Score]
            SvcNotif[Notificações, RNF-04 menor que 500ms]
        end
        DB[(Base de Dados criptografada por usuário, RNF-09)]
        Cache[(Cache de Sessão/Consentimento)]
    end
    subgraph Externos["Sistemas Externos"]
        OFProvider[Provedor Certificado Open Finance]
        PushProvider[APNs / FCM]
    end

    AppiOS --> APIGW
    AppAndroid --> APIGW
    APIGW --> SvcOF
    APIGW --> SvcMetas
    APIGW --> SvcNotif
    SvcOF --> OFProvider
    SvcOF --> DB
    SvcIA --> DB
    SvcMetas --> DB
    SvcNotif --> PushProvider
    SvcOF --> Cache
```

> **Pendência:** escolha final entre AWS/GCP e topologia exata de rede (VPC, regiões) é decisão de infraestrutura da equipe, não assumida aqui. Ver [BACKLOG.md](../../../BACKLOG.md).
