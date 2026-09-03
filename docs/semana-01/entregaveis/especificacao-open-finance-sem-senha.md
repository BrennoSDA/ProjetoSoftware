# Especificação Técnica: Open Finance sem Retenção de Senhas (RNF-01)

**Semana:** [Semana 1 — Kickoff, Open Finance e Privacidade Financeira](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 1") — *"Termos de Uso e Especificação do Open Finance sem Retenção de Senhas (RNF-01)"*
**Status:** **Status:** Feito — minuta de Termos de Uso incluída; validação jurídica formal fora do escopo acadêmico deste grupo (ver Termos de Uso abaixo)
**Responsável pela elicitação:** Brenno (AR1)

---

**Requisito:** "O sistema deve utilizar infraestrutura certificada de Open Finance e nunca ter acesso às senhas de movimentação bancária do usuário." (README.md, RNF-01)

* **Fluxo de autorização:** o app nunca coleta usuário/senha do banco. A conexão ocorre via protocolo OAuth2/Open Finance Brasil, redirecionando o usuário para o ambiente autenticado do próprio banco; o app recebe apenas um token de consentimento com escopo limitado (leitura de extrato/faturas).
* **Dados nunca armazenados pelo app:** senha bancária, PIN, dados de cartão físico completos.
* **Dados armazenados:** token de consentimento (criptografado, ver RNF-09), identificador da instituição, escopo autorizado, data de expiração/revogação.
* **Certificação exigida do provedor:** homologação oficial no Open Finance Brasil (Diretório de Participantes) — critério de seleção de fornecedor, não decisão técnica desta equipe.
* **Regra associada:** RN01 (revogação) — ver [especificação de congelamento por revogação](../../semana-02/entregaveis/spec-congelamento-revogacao-limbo-classificar.md).

---

## Termos de Uso — Conexão via Open Finance (minuta)

> ⚠️ **Aviso:** esta é uma **minuta de estudante, para fins acadêmicos**, escrita pela equipe a partir da especificação técnica acima. **Não é uma validação jurídica real** e não deve ser usada como Termos de Uso de um produto em produção sem revisão por um advogado. Ver pendência correspondente em [BACKLOG.md](../../../BACKLOG.md).

**1. Objeto.** Estes Termos regulam a conexão do usuário às suas contas bancárias e cartões de crédito por meio do Open Finance Brasil, para fins de categorização automática de transações, definição de metas financeiras e aconselhamento comportamental, conforme descrito no README do projeto (RF01 a RF10).

**2. Como a conexão funciona.** Ao autorizar a conexão, o usuário é redirecionado ao ambiente autenticado da própria instituição financeira. O aplicativo **nunca solicita, coleta ou armazena** a senha de acesso à conta bancária, PIN ou dados completos de cartão físico do usuário — apenas recebe um token de consentimento com escopo de leitura (extrato, faturas), emitido pela instituição financeira via protocolo do Open Finance Brasil.

**3. Escopo e prazo do consentimento.** O usuário escolhe, no momento da autorização, quais instituições compartilham dados e por quanto tempo o consentimento é válido. O consentimento pode ser revogado a qualquer momento pelo usuário, diretamente no aplicativo.

**4. Efeitos da revogação.** Ao revogar o consentimento, as análises preditivas do aplicativo (score comportamental, simuladores, gatilhos de notificação) são congeladas imediatamente. O histórico de dados já coletado permanece visível por até 30 dias corridos; após esse prazo sem que o acesso seja restabelecido, os dados antigos deixam de ser exibidos na interface principal, mas não são excluídos da base (retenção interna, sujeita à política de dados do produto).

**5. Uso dos dados.** Os dados obtidos via Open Finance são usados exclusivamente para gestão orçamentária e aconselhamento comportamental do próprio usuário. É vedado usar esses dados para gerar perfis de crédito comercializados a terceiros sem autorização específica e separada do usuário (ver [Política de Veto ao Credit Scoring](politica-credit-scoring-plano-incidentes.md)).

**6. Segurança.** A instituição parceira de Open Finance utilizada pelo aplicativo é certificada e homologada no Diretório de Participantes do Open Finance Brasil. Dados confidenciais de transações são cifrados em repouso com chave exclusiva por usuário.

**7. Alterações destes Termos.** Alterações materiais nestes Termos serão comunicadas ao usuário antes de entrarem em vigor, com nova solicitação de aceite quando exigido por lei.

> **Pendência (fora do escopo desta minuta):** cláusulas de foro, legislação aplicável, idade mínima, procedimento de disputa e demais cláusulas-padrão de um contrato de adesão real dependem de revisão jurídica profissional — não incluídas aqui por não serem competência de uma equipe de estudantes.
