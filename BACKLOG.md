# Backlog — Conselheiro Financeiro Comportamental (Grupo 5)

Atualizado em 2026-09-02, após reorganizar todo o conteúdo em `docs/semana-01` a `docs/semana-14` (ver [RESUMO.md](RESUMO.md) e [ROTEIRO_COMMITS.md](ROTEIRO_COMMITS.md)). Este backlog lista **apenas o que não foi preparado** nesta rodada — ou porque depende de ferramenta/pessoas fora do alcance desta sessão (Figma, usuários reais, revisão jurídica), ou porque é uma decisão de produto/infra que só a equipe pode tomar.

---

## 🎨 Artefatos que dependem de ferramenta de design (Figma) — por semana

| Semana | Item | Origem |
| --- | --- | --- |
| 4 | Wireframes Lo-Fi (Dashboard, Seletor de Metas, Quiz) | [docs/semana-04](docs/semana-04/README.md) |
| 5 | Wireframes Mid-Fi (Simulador, Feed do Casal, Limbo "A Classificar") | [docs/semana-05](docs/semana-05/README.md) |
| 6 | Componentes visuais reais do Design System (Figma/Flutter) | [docs/semana-06](docs/semana-06/README.md) |
| 8 | Telas Hi-Fi do Bloco A | [docs/semana-08](docs/semana-08/README.md) |
| 9 | Telas Hi-Fi do Bloco B | [docs/semana-09](docs/semana-09/README.md) |
| 10 | Layouts visuais dos estados especiais (RN01, RN03, RN05) | [docs/semana-10](docs/semana-10/README.md) |
| 11 | Protótipo navegável interativo no Figma | [docs/semana-11](docs/semana-11/README.md) |
| 14 | Pacote Final Figma + Design System Flutter | [docs/semana-14](docs/semana-14/README.md) |

## 🧑‍🤝‍🧑 Itens que dependem de pessoas reais (testes de usabilidade)

| Semana | Item | Origem |
| --- | --- | --- |
| 12 | Execução das sessões de teste, planilha de métricas e gravações reais | [docs/semana-12](docs/semana-12/README.md) — instrumento (roteiro) já pronto desde a Semana 11 |
| 13 | Relatório de usabilidade (Score SUS real) e ajustes baseados em feedback real | [docs/semana-13](docs/semana-13/README.md) — só a estrutura do relatório está pronta |

## ⚖️ Itens que dependem de revisão jurídica

| Semana | Item | Origem |
| --- | --- | --- |
| 1 | Texto legal definitivo de Termos de Uso (Open Finance) | [docs/semana-01](docs/semana-01/README.md) §1 — especificação técnica pronta, falta o texto contratual |
| 1 | Prazo legal exato de notificação à ANPD e texto formal aos usuários (LGPD-02) | [docs/semana-01](docs/semana-01/README.md) §2 |

## 🏗️ Decisões técnicas/de infraestrutura pendentes

| Semana | Item | Origem |
| --- | --- | --- |
| 4 | Limiar de confiança, modelo de ML e fonte da tabela MCC→Categoria do motor de classificação | [docs/semana-04](docs/semana-04/README.md) §1 |
| 7 | Provedor de KMS e política de rotação de chaves (RNF-09) | [docs/semana-07](docs/semana-07/README.md) §1 |
| 11 | Escolha final AWS vs. GCP e topologia de rede | [docs/semana-11](docs/semana-11/README.md) §1 |

## 🧭 Decisões de produto pendentes

| Semana | Item | Origem |
| --- | --- | --- |
| 2 | Nº mínimo de ocorrências para considerar um padrão de compra "recorrente" (RN02) | [docs/semana-02](docs/semana-02/README.md) §2 |
| 3 | Fonte do dado "custo de vida básico" (autodeclarado vs. inferido) usado na RN03 | [docs/semana-03](docs/semana-03/README.md) §2 |
| 6 | Lista final de categorias de gasto (depende do provedor Open Finance real) | [docs/semana-06](docs/semana-06/README.md) §1.1 |
| 10 | Política de retenção/exclusão de dados após ocultação por revogação (RN01) | [docs/semana-10](docs/semana-10/README.md) §3 |
| 1 | Necessidade (ou não) de um texto de benchmarking real de concorrentes com pesquisa de mercado atualizada | [docs/semana-01](docs/semana-01/README.md) §4 |

---

## 🔍 Achados de auditoria (inconsistências no material do professor)

Não são itens de trabalho, mas pontos a esclarecer — mantidos da auditoria anterior:

1. **Matriz de Rastreabilidade de `estudo_caso5.md` marca "Concluído" sem evidência.** Interpretado como exemplo ilustrativo do professor (confirmado pela equipe); as matrizes reais e atualizadas estão em [docs/semana-08](docs/semana-08/README.md) e [docs/semana-09](docs/semana-09/README.md), com status real.
2. **Erro de formatação na tabela de `estudo_caso5.md`** (linha REQ-03 mistura colunas "RN03" e "US-03" sem separador). Não corrigido no arquivo do professor; sinalizado aqui.
3. **Vínculo de RNF-03 a requisitos não relacionados a performance** na mesma matriz — possivelmente proposital (RNF transversal), mantido como observação.

## Itens fora de escopo total (dependem de terceiros/negócio)

* Contrato real com provedor certificado de Open Finance.
* Publicação nas lojas (Google Play / Apple App Store).
* Desenvolvimento do app Flutter real (código-fonte) — este repositório, até o momento, cobre apenas os artefatos de análise/design da disciplina.
