# Especificação: Margem de Segurança (RN03) e Privacidade do Casal (RN05)

**Semana:** [Semana 3 — Elicitação do Bloco B (Requisitos 06 a 10)](../README.md)
**Responde a:** Entregável 2 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 3") — *"Trava de Margem de Segurança de 1 Mês de Custo de Vida (RN03) e Privacidade do Casal (RN05)"*
**Status:** Feito
**Responsável:** Joel (AR2)

---

* **RN03:** o sistema não sugere investimentos/aportes em metas de longo prazo se o saldo atual (conta corrente + poupança) for inferior ao equivalente a 1 mês do custo de vida básico do usuário (a "Reserva Mínima"). Ver Value Object `ReservaMinima` no [Modelo de Domínio](../../semana-07/entregaveis/modelo-dominio.md).
  * **Pendência:** "custo de vida básico" precisa de uma fonte de dado — README.md não especifica se é autodeclarado pelo usuário no onboarding ou inferido do histórico de gastos essenciais. Decisão de produto pendente, ver [BACKLOG.md](../../../BACKLOG.md).
* **RN05:** em contas conjuntas, usuários podem optar por ocultar o destino detalhado de compras individuais; o feed comum mostra apenas valor total debitado e impacto no orçamento geral. O toggle de privacidade é por usuário, não por conta (cada participante decide sobre suas próprias compras).
