# Design System "Mindful Finance UX" — Especificação de Tokens

**Semana:** [Semana 6 — Design System "Mindful Finance UX"](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 6") — *"Design System 'Mindful Finance UX' (Compatível com Flutter a 60 FPS - RNF-03)"*
**Status:** Parcial — especificação de tokens (texto) pronta abaixo; componentes visuais reais (Figma/código Flutter) ficam pendentes (ver [BACKLOG.md](../../../BACKLOG.md))
**Responsável:** Ian & Davi (D1/D2)

---

> Especificação textual dos tokens visuais, para tradução posterior em Figma/Flutter (`ThemeData`). Compatibilidade com RNF-03 (60 FPS) é responsabilidade da implementação (evitar rebuilds desnecessários, usar `const` widgets), não do valor dos tokens em si.

## 1. Cores (com alternativa não-cromática, RNF-10 — ver [Semana 1](../../semana-01/entregaveis/guia-acessibilidade-daltonismo.md))

| Token | Uso | Cor | Ícone/Padrão redundante |
| --- | --- | --- | --- |
| `color.success` | Meta no prazo, saldo positivo | Verde | Seta ↑ |
| `color.warning` | Meta em risco | Laranja | Relógio ⏱ |
| `color.danger` | Bloqueio de aporte (RN03) | Vermelho | Cadeado 🔒 |
| `color.pending` | Transação "A Classificar" (RN04) | Azul/Cinza | Interrogação ❓ |
| `color.notice` | Gatilho Antigasto (RN02) | Roxo/Neutro | Sino 🔔 |

## 2. Tipografia
* `type.display` — títulos de dashboard e score semanal.
* `type.body` — texto padrão (contraste mínimo AA sobre `color.background`).
* `type.caption` — rótulos de acessibilidade que acompanham cor+ícone (nunca omitir).

## 3. Componentes previstos
* `CardMeta` (estados: no prazo / atrasada / concluída)
* `BadgeStatusTransacao` (Classificada / A Classificar)
* `IndicadorScoreComportamental` (0-100, com faixa de cor + ícone)
* `ModalRegistroRapido` (RF05, otimizado para ≤3 toques)
* `BannerGatilhoAntigasto` (RF04/RN02)
