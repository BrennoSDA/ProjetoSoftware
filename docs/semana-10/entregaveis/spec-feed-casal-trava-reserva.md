# Especificação Funcional: Feed do Casal com Privacidade (RN05) e Trava de Reserva (RN03)

**Semana:** [Semana 10 — Validação de Regras de Negócio e Estados Especiais](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 10") — *"Layouts de Transações Ocultadas no Feed do Casal (RN05) e Trava da Reserva (RN03)"*
**Status:** Não iniciado (layout visual) — especificação funcional (conteúdo/lógica da tela) pronta abaixo; produção visual real depende de Figma (ver [BACKLOG.md](../../../BACKLOG.md))
**Responsável:** Ian & Davi (D1/D2)

---

* **Feed do Casal:** cada item do feed exibe, no mínimo: valor total, categoria, data. Se `ConfiguracaoPrivacidadeIndividual.ocultarEstabelecimento = true` para o autor da compra, o campo "estabelecimento" não deve estar presente no payload retornado ao outro participante (ocultação no back-end, não só no front-end, para evitar vazamento via inspeção de rede).
* **Trava de Reserva:** ao tentar simular ou confirmar um aporte, se bloqueado por RN03, a interface deve comunicar: (a) que está bloqueado, (b) o motivo (reserva mínima não atingida), (c) quanto falta para desbloquear.
