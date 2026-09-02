# Semana 1 — Kickoff, Open Finance e Privacidade Financeira

**Período:** 10/08/2026 – 16/08/2026 · **Fase:** 1. Descoberta, Conformidade e Arquitetura
**Fonte do enunciado:** [estudo_caso5.md](../../estudo_caso5.md), seção "Semana 1 (Iteração 1)"
**Equipe:** Brenno & Joel (AR1/AR2 — elicitação) · Ian & Davi (D1/D2 — design)

> <!-- ATENÇÃO: os papéis AR1=Brenno, AR2=Joel, D1=Ian, D2=Davi foram atribuídos por decisão da equipe em 2026-09-02; ajustar aqui se a divisão real for outra. -->

## Status dos entregáveis

| # | Entregável (conforme estudo_caso5.md) | Status | Observação |
| --- | --- | --- | --- |
| 1 | Termos de Uso e Especificação do Open Finance sem Retenção de Senhas (RNF-01) | Parcial | Especificação técnica pronta abaixo; texto jurídico de Termos de Uso não produzido (requer revisão jurídica — ver [BACKLOG.md](../../BACKLOG.md)). |
| 2 | Política de Veto ao Credit Scoring Comercial (LGPD-01) e Plano de Incidentes (LGPD-02) | Parcial | Especificação técnica/de processo pronta abaixo; validação jurídica formal e prazo legal exato de notificação à ANPD ficam pendentes. |
| 3 | Guia de Design para Daltonistas (RNF-10) | Feito | Ver seção 3 abaixo. |
| 4 | Diagramas UML, "se for o caso" | Não se aplica | Pela matriz de [diagramasUML.md](../../diagramasUML.md), nenhum diagrama tem entrega prevista na Semana 1 (Casos de Uso é Semana 2). |

---

## 1. Especificação Técnica: Open Finance sem Retenção de Senhas (RNF-01)

> Responsável pela elicitação: Brenno (AR1)

**Requisito:** "O sistema deve utilizar infraestrutura certificada de Open Finance e nunca ter acesso às senhas de movimentação bancária do usuário." (README.md, RNF-01)

* **Fluxo de autorização:** o app nunca coleta usuário/senha do banco. A conexão ocorre via protocolo OAuth2/Open Finance Brasil, redirecionando o usuário para o ambiente autenticado do próprio banco; o app recebe apenas um token de consentimento com escopo limitado (leitura de extrato/faturas).
* **Dados nunca armazenados pelo app:** senha bancária, PIN, dados de cartão físico completos.
* **Dados armazenados:** token de consentimento (criptografado, ver RNF-09), identificador da instituição, escopo autorizado, data de expiração/revogação.
* **Certificação exigida do provedor:** homologação oficial no Open Finance Brasil (Diretório de Participantes) — critério de seleção de fornecedor, não decisão técnica desta equipe.
* **Regra associada:** RN01 (revogação) — ver seção 2 abaixo para o fluxo de congelamento.

<!-- ATENÇÃO: confirmar com a equipe/professor se é necessário produzir também o texto legal de "Termos de Uso" (contrato de adesão do usuário) nesta entrega, ou se essa especificação técnica é suficiente para a Semana 1. -->

## 2. Especificação de Processo: Veto ao Credit Scoring (LGPD-01) e Plano de Incidentes (LGPD-02)

> Responsável pela elicitação: Joel (AR2)

### 2.1 Veto ao Credit Scoring (LGPD-01)
* **Regra:** dados bancários captados via Open Finance só podem ser usados para gestão orçamentária e aconselhamento comportamental do próprio usuário.
* **Proibição explícita:** é vedado usar esses dados para gerar perfis de crédito (*credit scoring*) comercializados a bancos parceiros sem autorização específica e separada do usuário.
* **Implementação sugerida:** flag de finalidade (`purpose = "aconselhamento_comportamental"`) associada a todo dado ingerido via Open Finance; qualquer processo de exportação/agregação para terceiros deve validar essa flag antes de liberar dados, e falhar por padrão (*deny by default*) na ausência de autorização específica.

### 2.2 Plano de Incidentes (LGPD-02)
* **Gatilho:** qualquer suspeita de vazamento de dados ou acesso não autorizado à base de transações.
* **Passos do plano (rascunho técnico):**
  1. Isolamento imediato do componente/serviço afetado (kill-switch).
  2. Avaliação de escopo do incidente (quantidade de usuários/dados afetados).
  3. Notificação à ANPD e aos usuários afetados "no prazo legal determinado" (README.md, LGPD-02).
  4. Registro do incidente e ações corretivas em log de auditoria imutável.

<!-- ATENÇÃO: o prazo legal exato de notificação à ANPD e o texto formal de notificação aos usuários dependem de revisão jurídica que não foi feita nesta sessão — confirmar antes de publicar como política oficial. Ver item correspondente em BACKLOG.md. -->

## 3. Guia de Design para Daltonistas (RNF-10)

> Responsável: Ian & Davi (D1/D2)

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

Este guia alimenta o Design System "Mindful Finance UX" da Semana 6 (ver [../semana-06](../semana-06/README.md)).

## 4. Benchmarking e Arquitetura de Informação (D1/D2)

<!-- ATENÇÃO: benchmarking de concorrentes (Nubank, Klarna, Cleo) depende de pesquisa de mercado atualizada (screenshots/capturas reais dos apps) que não foi feita nesta sessão. A arquitetura de informação abaixo é um rascunho textual inicial, não substitui a pesquisa. -->

Rascunho inicial de arquitetura de informação (IA) do app, por área:
* **Home:** feed de transações + atalho de registro manual + resumo de metas.
* **Metas:** lista de metas, simulador de impacto, meta conjunta.
* **Comportamento:** score semanal, quiz de perfil, trilhas gamificadas.
* **Conexões:** status Open Finance, gestão de consentimento, contas conectadas.
* **Configurações:** privacidade, acessibilidade, notificações.
