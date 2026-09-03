# Especificação Funcional: Revogação e Congelamento (RN01)

**Semana:** [Semana 10 — Validação de Regras de Negócio e Estados Especiais](../README.md)
**Responde a:** Entregável 2 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 10") — *"Protótipo UI da Tela de Revogação e Congelamento de Análises (RN01)"*
**Status:** Não iniciado (layout visual) — especificação funcional pronta abaixo
**Responsável:** Ian & Davi (D1/D2)

---

Estados que a tela de status de conexão deve refletir (ver [máquina de estados, Semana 6, §3.2](../../semana-06/entregaveis/diagrama-maquina-estados.md)):

1. **Ativo:** exibe dados normalmente, todas as análises preditivas ativas.
2. **Revogado (dentro de 30 dias):** banner de aviso "Sua conexão foi revogada. Restabeleça em até X dias para manter seu histórico visível." Análises preditivas (simulador, gatilhos, score) desabilitadas.
3. **Dados Ocultos (após 30 dias):** dashboard mostra estado vazio com CTA para reconectar; dados antigos não aparecem mas não são excluídos do banco (retenção interna).

> **Pendência:** política de retenção/exclusão definitiva de dados após ocultação não está definida em README.md — depende de decisão de produto + LGPD, ver [BACKLOG.md](../../../BACKLOG.md).
