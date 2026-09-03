# Especificação de Processo: Veto ao Credit Scoring (LGPD-01) e Plano de Incidentes (LGPD-02)

**Semana:** [Semana 1 — Kickoff, Open Finance e Privacidade Financeira](../README.md)
**Responde a:** Entregável 2 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 1") — *"Política de Veto ao Credit Scoring Comercial (LGPD-01) e Plano de Incidentes (LGPD-02)"*
**Status:** Feito — base legal (LGPD art. 48 e Resolução CD/ANPD nº 15/2024) citada com fontes abaixo; sem validação jurídica profissional real (fora do escopo acadêmico do projeto)
**Responsável pela elicitação:** Joel (AR2)

---

## 1. Veto ao Credit Scoring (LGPD-01)
* **Regra:** dados bancários captados via Open Finance só podem ser usados para gestão orçamentária e aconselhamento comportamental do próprio usuário.
* **Proibição explícita:** é vedado usar esses dados para gerar perfis de crédito (*credit scoring*) comercializados a bancos parceiros sem autorização específica e separada do usuário.
* **Implementação sugerida:** flag de finalidade (`purpose = "aconselhamento_comportamental"`) associada a todo dado ingerido via Open Finance; qualquer processo de exportação/agregação para terceiros deve validar essa flag antes de liberar dados, e falhar por padrão (*deny by default*) na ausência de autorização específica.

## 2. Plano de Incidentes (LGPD-02)
* **Gatilho:** qualquer suspeita de vazamento de dados ou acesso não autorizado à base de transações.
* **Passos do plano (rascunho técnico):**
  1. Isolamento imediato do componente/serviço afetado (kill-switch).
  2. Avaliação de escopo do incidente (quantidade de usuários/dados afetados).
  3. Notificação à ANPD e aos usuários afetados dentro do prazo legal (ver §2.1 abaixo).
  4. Registro do incidente e ações corretivas em log de auditoria imutável.

### 2.1 Prazo legal de comunicação (LGPD art. 48 + Resolução CD/ANPD nº 15/2024)

O **art. 48, caput, da Lei nº 13.709/2018 (LGPD)** estabelece que "o controlador deverá comunicar à autoridade nacional e ao titular a ocorrência de incidente de segurança que possa acarretar risco ou dano relevante aos titulares", em "prazo razoável, conforme definido pela autoridade nacional" (art. 48, §1º).

Esse "prazo razoável" foi regulamentado pela **Resolução CD/ANPD nº 15, de 24 de abril de 2024** (Regulamento de Comunicação de Incidente de Segurança):

* **Art. 6º, caput:** a comunicação à ANPD deve ser feita em **3 (três) dias úteis**, contados da data em que o controlador toma conhecimento de que o incidente afetou dados pessoais.
* **Art. 6º, §8º:** esse prazo é **contado em dobro (6 dias úteis)** para agentes de tratamento de pequeno porte.
* **Art. 9º:** a comunicação aos titulares afetados segue o mesmo prazo (3 dias úteis, ou 6 dias úteis para agentes de pequeno porte).
* Comunicação preliminar com informações incompletas é admitida, com complementação em até 20 dias úteis (art. 6º).

**Aplicação ao projeto:** adotamos o prazo geral de **3 dias úteis** (ANPD e titulares) como meta do plano de incidentes, sujeito a confirmação sobre o porte da empresa fictícia do estudo de caso (que definiria se o prazo dobrado de 6 dias úteis se aplica).

### 2.2 Texto Formal de Notificação aos Usuários Afetados (minuta)

> ⚠️ Minuta de estudante para fins acadêmicos, escrita a partir do conteúdo obrigatório exigido pelo art. 48, §1º, da LGPD. Não é uma validação jurídica real.

> **Assunto: Comunicado sobre incidente de segurança em seus dados**
>
> Olá, [Nome do Usuário],
>
> Identificamos um incidente de segurança que pode ter afetado dados pessoais associados à sua conta no [Nome do App], em [data/hora aproximada de ocorrência]. Como é nosso compromisso agir com transparência, informamos:
>
> * **Natureza dos dados possivelmente afetados:** [ex.: histórico de transações categorizadas, valores de metas financeiras — nunca senha bancária, que nunca é armazenada por nós].
> * **O que já fizemos:** isolamos o componente afetado e interrompemos o acesso não autorizado em [data/hora].
> * **Medidas de segurança já em vigor:** seus dados de transação são cifrados em repouso com chave exclusiva por usuário; sua senha bancária nunca é armazenada por nós, apenas um token de consentimento Open Finance.
> * **O que estamos fazendo agora:** apuramos o escopo completo do incidente e comunicamos a Autoridade Nacional de Proteção de Dados (ANPD), conforme exigido pela LGPD.
> * **O que recomendamos que você faça:** [ex.: revisar/revogar o consentimento Open Finance nas Configurações, trocar a senha do app, monitorar extratos].
>
> Qualquer dúvida, fale com nosso canal de privacidade em [contato do encarregado de dados / DPO].
>
> Equipe [Nome do App]

> **Nota:** esta minuta cobre o conteúdo mínimo exigido pelo art. 48, §1º, da LGPD (natureza dos dados, titulares envolvidos, medidas de segurança adotadas, riscos e medidas de mitigação). O texto final de produção deve ser revisado por um profissional jurídico e pelo encarregado de dados (DPO) real da empresa — fora do escopo acadêmico deste projeto.

---

### Fontes
* [Lei nº 13.709/2018 (LGPD), art. 48 — Planalto](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm)
* [Art. 48 da LGPD — texto do caput e parágrafos, lgpd-brasil.info](https://lgpd-brasil.info/capitulo_07/artigo_48)
* [Resolução CD/ANPD nº 15/2024 — Comunicado de Incidente de Segurança (CIS), gov.br/ANPD](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis)
* [Resolução CD/ANPD Nº 15 DE 24/04/2024, arts. 6º e 9º — LegisWeb](https://www.legisweb.com.br/legislacao/?id=458235)
* [ANPD publica Regulamento de Comunicação de Incidente de Segurança — Souto Correa Advogados](https://www.soutocorrea.com.br/client-alerts/regulamentacao-de-comunicacao-de-incidente-de-seguranca/)
