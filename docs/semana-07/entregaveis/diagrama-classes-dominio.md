# Diagrama de Classes de Domínio

**Semana:** [Semana 7 — Consolidação e Especificação Técnica](../README.md)
**Responde a:** entrega oficial de Diagrama de Classes de Domínio conforme [diagramasUML.md](../../../diagramasUML.md) (Fase 2, "Entrega: Semanas 6 e 7"); ilustra o [Modelo de Domínio (DDD)](modelo-dominio.md) completo
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

```mermaid
classDiagram
    class Usuario {
        +UUID id
        +String nome
        +ValorMonetario custoDeVidaBasico
        definirMeta()
        registrarGastoManual()
    }
    class ContaConjunta {
        +UUID id
        +List~Usuario~ participantes
        +ValorMonetario saldoCompartilhado
        ocultarDestinoIndividual()
    }
    class ConsentimentoOpenFinance {
        +UUID id
        +StatusConsentimento status
        +Date dataRevogacao
        revogar()
        restabelecer()
    }
    class Transacao {
        +UUID id
        +ValorMonetario valor
        +Date data
        +StatusTransacao status
        +String categoria
        classificar(categoria)
    }
    class MetaFinanceira {
        +UUID id
        +PrazoMeta prazo
        +ValorMonetario valorAlvo
        +ValorMonetario progresso
        simularImpacto(gasto)
    }
    class PerfilComportamental {
        +UUID id
        +TipoGastador tipo
    }
    class ScoreComportamental {
        +UUID id
        +Date semana
        +Integer pontuacao
        calcular()
    }
    class TrilhaEducacional {
        +UUID id
        +String titulo
        +Integer progresso
    }
    class GatilhoAntigasto {
        +UUID id
        +JanelaHorariaHabitual janela
        +Boolean enviado
        disparar()
    }
    class ValorMonetario {
        <<ValueObject>>
        +BigDecimal quantia
        +String moeda
    }
    class JanelaHorariaHabitual {
        <<ValueObject>>
        +DiaSemana dia
        +Time horario
    }
    class ReservaMinima {
        <<ValueObject>>
        +ValorMonetario valor
        atingida(saldoAtual) Boolean
    }

    Usuario "1" --> "0..*" Transacao
    Usuario "1" --> "0..*" MetaFinanceira
    Usuario "1" --> "1" PerfilComportamental
    Usuario "1" --> "0..*" ScoreComportamental
    Usuario "1" --> "0..*" TrilhaEducacional
    Usuario "1" --> "1" ConsentimentoOpenFinance
    Usuario "2..*" --> "1" ContaConjunta
    ContaConjunta "1" --> "1" MetaFinanceira
    Transacao "0..*" --> "0..1" GatilhoAntigasto
    MetaFinanceira --> ReservaMinima
    Transacao --> ValorMonetario
    GatilhoAntigasto --> JanelaHorariaHabitual
```
