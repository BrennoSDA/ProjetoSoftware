# Diagrama de Pacotes / Componentes

**Semana:** [Semana 7 — Consolidação e Especificação Técnica](../README.md)
**Responde a:** entrega oficial de Diagrama de Pacotes/Componentes conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 2, "Entrega: Semana 7")
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

```mermaid
flowchart TB
    subgraph Core["Core Domain: Aconselhamento Comportamental"]
        Detector[Detector de Padrão de Impulso]
        Simulador[Simulador de Impacto de Metas]
        ScoreSvc[Calculadora de Score Comportamental]
    end
    subgraph SupA["Supporting: Open Finance & Transações"]
        Conexao[Conexão e Consentimento Open Finance]
        Categorizacao[Motor de Classificação IA]
    end
    subgraph SupB["Supporting: Metas & Educação Financeira"]
        Metas[Gestão de Metas Individuais/Conjuntas]
        Trilhas[Trilhas Gamificadas]
        Quiz[Quiz de Perfil Comportamental]
    end
    subgraph Generic["Generic Domain"]
        Auth[Autenticação / Consentimento LGPD]
        Notif[Gateway de Notificações Push]
    end
    subgraph ACL["Camada Anticorrupção (ACL)"]
        ACLOF[Adapter Open Finance]
        ACLPush[Adapter Push Provider]
    end

    SupA --> Core
    SupB --> Core
    Generic --> SupA
    Generic --> SupB
    Categorizacao --> ACLOF
    ACLOF --> Conexao
    Notif --> ACLPush
```
