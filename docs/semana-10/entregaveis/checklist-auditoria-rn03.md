# Checklist de Auditoria — RN03 (Margem de Segurança)

**Semana:** [Semana 10 — Validação de Regras de Negócio e Estados Especiais](../README.md)
**Responde a:** material de apoio às atividades de auditoria de AR1/AR2 desta semana — **não é um dos 3 entregáveis numerados** em [estudo_caso5.md](../../../estudo_caso5.md) (seção "Semana 10"), mas é conteúdo real produzido pela equipe (checklist de critérios de aceite), mantido aqui para rastreabilidade.
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

| # | Critério de Aceite | Verificável por |
| --- | --- | --- |
| 1 | Sistema nunca sugere aporte/investimento se `saldoAtual < ReservaMinima` | Teste automatizado sobre `ValidadorDeReservaMinima` |
| 2 | Aviso explicando o bloqueio é sempre exibido junto ao bloqueio (não é um bloqueio silencioso) | Teste de UI / revisão de UX copy |
| 3 | Assim que `saldoAtual >= ReservaMinima`, a sugestão de aporte volta a ficar disponível automaticamente, sem ação manual do usuário | Teste automatizado |
| 4 | `custoDeVidaBasico` usado no cálculo é auditável (o usuário pode ver de onde veio o valor) | Revisão de UX — depende de decisão de produto sobre a fonte do dado (ver [Semana 3](../../semana-03/entregaveis/spec-margem-seguranca-privacidade-casal.md)) |
