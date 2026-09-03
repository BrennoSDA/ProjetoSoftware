# Especificação: Gatilho Antigasto (RN02) e Registro Manual (RF05)

**Semana:** [Semana 2 — Elicitação do Bloco A (Requisitos 01 a 05)](../README.md)
**Responde a:** Entregável 2 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 2") — *"Especificação do Gatilho Antigasto 1h Antes (RN02) e Registro Manual em <3 Clics (REQ-05)"*
**Status:** Feito
**Responsável:** Brenno (AR1)

---

* **RN02 — Gatilho Antigasto:** o envio da notificação preventiva deve ocorrer **exatamente 1 hora antes** do horário habitual mapeado de consumo do usuário. Exemplo: hábito de pedir delivery às sextas 20h → notificação enviada às sextas 19h.
  * Pré-condição: o Detector de Padrão de Impulso (ver [fluxograma do motor de classificação, Semana 4](../../semana-04/entregaveis/fluxograma-motor-classificacao.md)) precisa ter identificado pelo menos N ocorrências recorrentes do mesmo dia/horário/categoria antes de agendar o gatilho.
  * **Pendência:** o valor de N (nº mínimo de ocorrências para considerar "recorrente") não está definido em README.md — decisão de produto pendente da equipe, ver [BACKLOG.md](../../../BACKLOG.md).
* **RF05 — Registro manual em <3 cliques:** fluxo alvo: (1) toque no atalho de registro rápido na tela inicial → (2) campo de valor já em foco, teclado numérico aberto automaticamente → (3) toque em "Confirmar". Três toques no total, sem etapas intermediárias de categoria obrigatória (categoria pode ser default "Dinheiro/Outros" e reclassificada depois).
