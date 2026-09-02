# Semana 10 — Validação de Regras de Negócio e Estados Especiais

**Período:** 12/10/2026 – 18/10/2026 · **Fase:** 3. Design Visual Hi-Fi e Protótipo Navegável
**Fonte do enunciado:** [estudo_caso5.md](../../estudo_caso5.md), seção "Semana 10 (Iteração 10)"
**Equipe:** Brenno & Joel (AR1/AR2 — auditoria de regras) · Ian & Davi (D1/D2 — telas de estado)

## Status dos entregáveis

| # | Entregável | Status | Observação |
| --- | --- | --- | --- |
| 1 | Auditoria da trava de margem de segurança (RN03) | Feito | Seção 1 — checklist de critérios de aceite. |
| 2 | Layouts de transações ocultadas no feed do casal (RN05) e trava da reserva (RN03) | Não iniciado (layout visual) | Especificação funcional (conteúdo/lógica da tela) feita na Seção 2; produção visual real depende de Figma — ver [BACKLOG.md](../../BACKLOG.md). |
| 3 | Protótipo UI da Tela de Revogação e Congelamento (RN01) | Não iniciado (layout visual) | Especificação funcional feita na Seção 3. |

---

## 1. Checklist de Auditoria — RN03 (Margem de Segurança)

| # | Critério de Aceite | Verificável por |
| --- | --- | --- |
| 1 | Sistema nunca sugere aporte/investimento se `saldoAtual < ReservaMinima` | Teste automatizado sobre `ValidadorDeReservaMinima` |
| 2 | Aviso explicando o bloqueio é sempre exibido junto ao bloqueio (não é um bloqueio silencioso) | Teste de UI / revisão de UX copy |
| 3 | Assim que `saldoAtual >= ReservaMinima`, a sugestão de aporte volta a ficar disponível automaticamente, sem ação manual do usuário | Teste automatizado |
| 4 | `custoDeVidaBasico` usado no cálculo é auditável (o usuário pode ver de onde veio o valor) | Revisão de UX — depende de decisão de produto sobre a fonte do dado (ver [Semana 3](../semana-03/README.md) §2) |

## 2. Especificação Funcional — Feed do Casal com Privacidade (RN05) e Trava de Reserva (RN03)

* **Feed do Casal:** cada item do feed exibe, no mínimo: valor total, categoria, data. Se `ConfiguracaoPrivacidadeIndividual.ocultarEstabelecimento = true` para o autor da compra, o campo "estabelecimento" não deve estar presente no payload retornado ao outro participante (ocultação no back-end, não só no front-end, para evitar vazamento via inspeção de rede).
* **Trava de Reserva:** ao tentar simular ou confirmar um aporte, se bloqueado por RN03, a interface deve comunicar: (a) que está bloqueado, (b) o motivo (reserva mínima não atingida), (c) quanto falta para desbloquear.

## 3. Especificação Funcional — Revogação e Congelamento (RN01)

Estados que a tela de status de conexão deve refletir (ver máquina de estados em [Semana 6](../semana-06/README.md) §3.2):
1. **Ativo:** exibe dados normalmente, todas as análises preditivas ativas.
2. **Revogado (dentro de 30 dias):** banner de aviso "Sua conexão foi revogada. Restabeleça em até X dias para manter seu histórico visível." Análises preditivas (simulador, gatilhos, score) desabilitadas.
3. **Dados Ocultos (após 30 dias):** dashboard mostra estado vazio com CTA para reconectar; dados antigos não aparecem mas não são excluídos do banco (retenção interna).

<!-- ATENÇÃO: política de retenção/exclusão definitiva de dados após ocultação não está definida em README.md — depende de decisão de produto + LGPD, ver BACKLOG.md. -->
