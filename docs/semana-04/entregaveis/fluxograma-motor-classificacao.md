# Fluxograma do Motor de Classificação de Transações (RNF-08)

**Semana:** [Semana 4 — Wireframes em Baixa Fidelidade (Lo-Fi)](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 4") — *"Fluxogramas do Motor de Classificação de Transações por IA (Precisão >92% - RNF-08)"*
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

Lógica proposta para atingir >92% de precisão sem intervenção do usuário (RNF-08), com fallback explícito para o limbo "A Classificar" (RN04) em vez de forçar uma categoria de baixa confiança:

```mermaid
flowchart TD
    A[Transação recebida via Open Finance] --> B[Normalizar dados: estabelecimento, MCC, valor, descrição]
    B --> C{Estabelecimento possui MCC/categoria conhecida?}
    C -- Sim --> D[Classificação determinística por tabela MCC → Categoria]
    C -- Não --> E[Classificação por modelo de ML sobre descrição/histórico]
    D --> F{Confiança da classificação ≥ limiar de aceitação?}
    E --> F
    F -- Sim, confiança alta --> G[Persistir transação como Classificada]
    F -- Não, confiança baixa/dados insuficientes --> H[Marcar transação como 'A Classificar' - RN04]
    G --> I[Disparar evento TransacaoCategorizadaAutomaticamente]
    H --> J[Disparar evento TransacaoEntrouEmLimboAClassificar]
    I --> K[Incluir no cálculo do Score Comportamental]
    H2[Usuário classifica manualmente] --> L[Reclassificar transação]
    J -.aguarda ação do usuário.-> H2
    L --> G
```

> **Pendência:** o valor exato do "limiar de aceitação" de confiança, o modelo de ML a usar e a fonte da tabela MCC→Categoria são decisões técnicas/de produto que a equipe ainda precisa definir e documentar (ex: ADR). RNF-08 exige >92% de precisão *agregada*, não necessariamente por transação individual — a métrica de avaliação (accuracy, precision, recall por categoria) também precisa ser definida antes da implementação real.

### Critério de aceite (RNF-08)
* Precisão agregada da classificação automática ≥ 92%, medida sobre uma amostra de validação rotulada manualmente.
* Toda transação com confiança abaixo do limiar vai para "A Classificar" — nunca é categorizada "no chute" (evita poluir o Score Comportamental com dados errados).
