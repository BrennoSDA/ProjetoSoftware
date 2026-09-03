# Especificação: Congelamento por Revogação (RN01) e Limbo "A Classificar" (RN04)

**Semana:** [Semana 2 — Elicitação do Bloco A (Requisitos 01 a 05)](../README.md)
**Responde a:** Entregável 3 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 2") — *"Regra de Congelamento por Revogação Open Finance (RN01) e Limbo 'A Classificar' (RN04)"*
**Status:** Feito
**Responsável:** Brenno (AR1)

---

* **RN01:** ao revogar o consentimento Open Finance, o sistema deve **congelar imediatamente** as análises preditivas (score, simuladores, gatilhos). Dados antigos continuam visíveis por até 30 dias corridos; após esse prazo sem o acesso ser restabelecido, os dados antigos são ocultados da interface principal (não excluídos do banco, apenas ocultos — retenção segue política de dados a definir).
* **RN04:** transações sem dados suficientes do estabelecimento entram no estado `AClassificar`. Enquanto houver ao menos uma transação nesse estado na semana corrente, o cálculo do Score Comportamental fica **suspenso** (não é calculado com valor parcial/zerado — fica com status "Suspenso" visível ao usuário, não "0 pontos").

Ambas as regras estão modeladas formalmente no Modelo de Domínio (ver [modelo de domínio, Semana 7](../../semana-07/entregaveis/modelo-dominio.md), agregados `ConexaoOpenFinance` e `PerfilUsuario`).
