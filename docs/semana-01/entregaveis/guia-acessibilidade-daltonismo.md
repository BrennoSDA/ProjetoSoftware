# Guia de Design para Daltonistas (RNF-10)

**Semana:** [Semana 1 — Kickoff, Open Finance e Privacidade Financeira](../README.md)
**Responde a:** Entregável 3 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 1") — *"Guia de Design para Daltonistas (Alternativas Visuais por Ícones — RNF-10)"*
**Status:** Feito
**Responsável:** Ian & Davi (D1/D2)

---

### Diretrizes obrigatórias
1. **Nunca comunicar estado apenas por cor** — todo indicador (saldo, alerta, bloqueio) combina cor + ícone + rótulo de texto.
2. **Contraste mínimo WCAG 2.1 AA** — razão ≥ 4.5:1 para texto normal, ≥ 3:1 para ícones/gráficos informativos.
3. **Evitar pares vermelho-verde como único diferenciador** (deuteranopia/protanopia) — preferir azul/laranja ou padrões (hachuras/tracejados) em gráficos.
4. **Testar com simuladores** (Stark, Color Oracle) antes da entrega Hi-Fi (Semanas 8-9).

### Aplicação nos componentes do app

| Componente | Cor | Ícone Redundante | Texto |
| --- | --- | --- | --- |
| Card de Meta no prazo | Verde | Seta ↑ | "No prazo" |
| Card de Meta atrasada | Laranja | Relógio ⏱ | "Atrasada em X dias" |
| Alerta de Reserva Mínima (RN03) | Vermelho | Cadeado 🔒 | "Aporte bloqueado" |
| Transação "A Classificar" (RN04) | Azul/Cinza | Interrogação ❓ | "A Classificar" |
| Notificação Gatilho Antigasto (RN02) | Roxo/Neutro | Sino 🔔 | "Alerta preventivo" |

Este guia alimenta o Design System "Mindful Finance UX" da [Semana 6](../../semana-06/README.md).
