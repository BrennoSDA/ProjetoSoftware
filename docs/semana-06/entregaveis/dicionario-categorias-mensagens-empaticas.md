# Dicionário de Categorização Orçamentária e Mensagens Empáticas de Push

**Semana:** [Semana 6 — Design System "Mindful Finance UX"](../README.md)
**Responde a:** Entregável 2 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 6") — *"Dicionário de Categorização Orçamentária e Mensagens Empáticas de Push"*
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

## 1. Categorias de gasto (base para o Motor de Classificação, RF02/RNF-08)

| Categoria | Exemplos de Estabelecimento/MCC | Observação |
| --- | --- | --- |
| Alimentação — Delivery | iFood, Rappi, Uber Eats | Categoria de maior atenção para Gatilho Antigasto (RN02). |
| Alimentação — Mercado | Supermercados, hortifrúti | Gasto essencial, não gera gatilho de impulso. |
| Transporte | Uber, 99, combustível | — |
| Lazer/Assinaturas | Streaming, apps de jogos | Candidato a compra por impulso recorrente. |
| Moradia | Aluguel, condomínio, contas | Gasto essencial fixo — usado no cálculo de custo de vida básico (RN03). |
| Saúde | Farmácias, planos de saúde | — |
| Compras — Vestuário/Eletrônicos | Lojas de roupa, e-commerce | Candidato a compra por impulso pontual (ex.: tênis de R$600 do cenário de teste). |
| A Classificar | — | Estado transitório (RN04), não é uma categoria de negócio, é um status. |

> **Pendência:** lista de categorias é um rascunho inicial baseado nos exemplos do README.md e estudo_caso5.md; a lista final e o mapeamento MCC→Categoria completo dependem de dados reais do provedor Open Finance escolhido. Ver [BACKLOG.md](../../../BACKLOG.md).

## 2. Mensagens Empáticas de Push (Gatilho Antigasto, RN02)

Princípio: nunca usar tom de julgamento moral (confirmado como critério de aceite no roteiro de testes de usabilidade, [Semana 12](../../semana-12/README.md)).

* "Ei! Notamos que às sextas à noite o delivery costuma aparecer por aqui 🍕. Sem pressão — só um lembrete de que sua meta [Nome da Meta] agradece um dia sem pedido."
* "Reserva para [Nome da Meta] está a X% do objetivo. Se hoje não for o dia do delivery, você chega lá Y dias mais rápido."
* Tom: 2ª pessoa, sem exclamação de alarme, sempre citando o benefício futuro (a meta), nunca o "erro" cometido.
