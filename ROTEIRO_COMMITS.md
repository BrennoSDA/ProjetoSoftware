# Roteiro de Commits — Grupo 5

Todo o conteúdo de `docs/semana-01` a `docs/semana-14` já está preparado localmente (ver [RESUMO.md](RESUMO.md)). **Nada foi commitado.** Este roteiro existe para você seguir manualmente, semana a semana, alinhado ao calendário oficial em [estudo_caso5.md](estudo_caso5.md).

## Regra de ouro

> **Nunca commite o material de uma semana antes da data de início dela**, mesmo que já esteja pronto em `docs/`. O conteúdo fica esperando na sua máquina até chegar a vez de cada semana. Isso evita: (a) parecer que o grupo entregou tudo de uma vez sem processo, e (b) conflitar com um enunciado que o professor ainda pode alterar/detalhar antes da semana chegar.

Hoje é **2026-09-02**, dentro da janela da Semana 4. As Semanas 1 a 3 já estão atrasadas em relação ao calendário original — o roteiro sugere subi-las **imediatamente, em commits separados por semana** (não um só commit gigante), para manter o histórico legível e permitir revisão individual antes de cada push.

---

## Antes de QUALQUER commit desta lista

☑️ **Confira se o professor não divulgou, alterou ou detalhou o enunciado daquela semana** (aula, slide, LMS, e-mail) desde 2026-09-02, data desta preparação. Se houver algo novo, ajuste o arquivo correspondente em `docs/semana-XX/` antes de commitar — não suba o conteúdo antigo por padrão.

---

## Tabela de Commits

| Semana | Data sugerida | O que commitar | Mensagem sugerida |
| --- | --- | --- | --- |
| 1 | Assim que possível (atrasada; janela original 10–16/08/2026) | `docs/semana-01/` | `docs(semana-01): especificação de Open Finance, LGPD e guia de acessibilidade` |
| 2 | Assim que possível, após a Semana 1 (atrasada; janela original 17–23/08/2026) | `docs/semana-02/` | `docs(semana-02): user stories US-01 a US-05 e diagrama de casos de uso` |
| 3 | Assim que possível, após a Semana 2 (atrasada; janela original 24–30/08/2026) | `docs/semana-03/` | `docs(semana-03): user stories US-06 a US-10, personas e diagrama de atividades` |
| 4 | Até 06/09/2026 (fim da semana atual) | `docs/semana-04/` | `docs(semana-04): fluxograma do motor de classificação de transações` |
| 5 | Até 13/09/2026 | `docs/semana-05/` | `docs(semana-05): diagramas de sequência (conexão Open Finance e gatilho antigasto)` |
| 6 | Até 20/09/2026 | `docs/semana-06/` | `docs(semana-06): design system, dicionário de categorias e máquina de estados` |
| 7 | Até 27/09/2026 | `docs/semana-07/` | `docs(semana-07): modelo de domínio DDD, diagrama de classes e de pacotes` |
| 8 | Até 04/10/2026 | `docs/semana-08/` | `docs(semana-08): matriz de rastreabilidade do bloco A` |
| 9 | Até 11/10/2026 | `docs/semana-09/` | `docs(semana-09): matriz de rastreabilidade do bloco B` |
| 10 | Até 18/10/2026 | `docs/semana-10/` | `docs(semana-10): auditoria da RN03 e especificação de estados especiais` |
| 11 | Até 25/10/2026 | `docs/semana-11/` | `docs(semana-11): diagrama de implantação e roteiro de testes de usabilidade` |
| 12 | Até 01/11/2026 | `docs/semana-12/` | `docs(semana-12): estrutura da planilha de métricas de teste` — **complete com os dados reais das sessões antes de commitar; não suba a tabela vazia como se fosse a entrega final.** |
| 13 | Até 08/11/2026 | `docs/semana-13/` | `docs(semana-13): esqueleto do relatório de usabilidade` — **idem: preencha com os resultados reais da Semana 12 antes de considerar a entrega completa.** |
| 14 | Até 15/11/2026 | `docs/semana-14/` (+ `RESUMO.md` e `BACKLOG.md` atualizados) | `docs(semana-14): índice do dossiê final de handoff` |

## Observações importantes

* **Semanas 1–3 (atrasadas):** sugiro 3 commits separados (não 1), na ordem 1 → 2 → 3, cada um revisado individualmente antes do push — assim, se o professor já tiver dado algum feedback específico sobre uma dessas semanas, você ajusta só aquele commit sem misturar com as outras.
* **Semanas 12 e 13:** o conteúdo pronto hoje é só o *esqueleto* (planilha vazia, estrutura do relatório) — a mensagem de commit sugerida reflete isso. Não marque como "entrega concluída" até preencher com dados reais das sessões de teste.
* **Itens em backlog não entram em nenhum commit deste roteiro.** Wireframes/Figma, testes com usuários reais, textos jurídicos definitivos e decisões técnicas/de produto pendentes (listados em [BACKLOG.md](BACKLOG.md)) precisam ser resolvidos e adicionados aos respectivos `docs/semana-XX/` antes de cada commit, se você quiser que a entrega daquela semana fique completa — o roteiro acima cobre apenas o que já está pronto.
* Este roteiro não teve nenhuma mensagem de commit "herdada" de convenção pré-existente no repositório (os 3 commits atuais são todos do professor e não seguem um padrão formal) — a convenção `docs(semana-XX): ...` acima é uma sugestão nova; ajuste se a equipe preferir outro padrão.
