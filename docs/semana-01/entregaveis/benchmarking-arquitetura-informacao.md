# Benchmarking e Arquitetura de Informação

**Semana:** [Semana 1 — Kickoff, Open Finance e Privacidade Financeira](../README.md)
**Responde a:** material de apoio das atividades de D1/D2 desta semana — **não é um dos 4 entregáveis numerados** em [estudo_caso5.md](../../../estudo_caso5.md) (seção "Semana 1"), mas é conteúdo produzido pela equipe, mantido aqui para rastreabilidade.
**Status:** Feito — benchmarking real com pesquisa de mercado (fontes citadas abaixo); sem screenshots/capturas reais dos apps concorrentes (ver ressalva ao final)
**Responsável:** Ian & Davi (D1/D2)

---

## 1. Benchmarking de Concorrentes

> Pesquisa feita via busca web em 2026-09-02 (fontes ao final da seção). Não inclui screenshots/capturas reais dos apps — apenas informações publicadas por essas empresas, imprensa especializada e lojas de aplicativo. Onde a fonte não detalhava um ponto, isso fica marcado como não encontrado, em vez de estimado.

### 1.1 Nubank — Open Finance

* **Funcionalidades relevantes:** o Nubank é participante voluntário do Open Finance desde setembro de 2022 e lidera o ecossistema brasileiro, com cerca de 15 milhões de consentimentos ativos; oferece agregação de contas de outras instituições dentro do próprio app (quase 10 milhões de clientes únicos usam essa função) e atua como iniciador de pagamento (mais de 420 mil usuários únicos já iniciaram pagamentos via Open Finance pelo app, somando ~R$ 250 milhões).
* **UX de consentimento/privacidade:** o consentimento é dado pelo app ou internet banking, especificando a instituição que vai receber os dados e o período de validade (até 1 ano); apenas instituições autorizadas pelo Banco Central podem participar, e todo o fluxo é supervisionado pelo BC.
* **Ponto aplicável ao projeto:** o desafio de UX de consentimento citado por executivos do Nubank (especialmente para contas PJ) reforça a decisão de projeto de manter o fluxo de consentimento o mais simples possível para o usuário final (ver [especificação Open Finance](especificacao-open-finance-sem-senha.md)) — evitar telas de permissão longas/confusas é um risco de UX real, não só teórico.

### 1.2 Klarna — Budgeting e insights de gasto

* **Funcionalidades relevantes:** o app permite definir e acompanhar um orçamento mensal e visualizar quanto foi gasto por mês e por categoria; a funcionalidade "Money Story" resume os gastos por mês, varejista e categoria, incentivando o usuário a refletir sobre para onde o dinheiro foi e converter isso em metas financeiras (uso da função cresceu 68% ano a ano, segundo a própria Klarna).
* **UX:** descrita pelos usuários como interface intuitiva e de configuração rápida, combinando ferramentas de gestão financeira com funcionalidades de compra (comparação de preço, rastreio de entrega).
* **Privacidade/consentimento:** a coleta de dados comportamentais anonimizados para entender hábitos de compra é opt-in e depende de permissão do usuário, segundo a própria Klarna.
* **Ponto aplicável ao projeto:** o modelo "resumo por categoria + reflexão + meta" do Money Story é diretamente comparável ao par Score Comportamental + Simulador de Impacto do projeto (RF06, RF09) — a categorização por período/categoria já é uma prática validada de mercado, o que reforça o Dicionário de Categorias da [Semana 6](../../semana-06/entregaveis/dicionario-categorias-mensagens-empaticas.md).

### 1.3 Cleo — Finanças comportamentais e notificações

* **Funcionalidades relevantes:** classifica automaticamente as despesas do usuário em categorias em tempo real; monitora hábitos de gasto e alerta quando o usuário se aproxima do limite orçamentário ou quando uma conta está prestes a vencer, identificando padrões em pagamentos recorrentes.
* **UX/tom de voz:** interação baseada em chat, com notificações "de personalidade" (tom informal/humorístico, às vezes provocador — "rouba" o usuário de leve pelo excesso de gasto) em vez do aviso genérico "você excedeu o orçamento"; a proposta de mercado é que esse tom emocionalmente engajado aumenta a chance de o usuário realmente prestar atenção ao alerta.
* **Ponto aplicável ao projeto:** confirma que o princípio de "mensagem empática, sem julgamento moral" definido para o Gatilho Antigasto ([Semana 6](../../semana-06/entregaveis/dicionario-categorias-mensagens-empaticas.md), RN02) é uma escolha de tom deliberada e diferente da do Cleo — o projeto opta por empatia/apoio em vez de humor ácido, o que deve ser tratado como decisão de produto documentada (não uma lacuna), já que ambos os tons são estratégias válidas de mercado para o mesmo problema (engajamento com alertas de gasto).

### Fontes
* [Open Finance — Nubank](https://nubank.com.br/nu/open-finance-nubank)
* [Em menos de dois anos, Nubank atinge 15 milhões de consentimentos no Open Finance — Finsiders Brasil](https://finsidersbrasil.com.br/regulamentacao/nubank-atinge-15-milhoes-de-consentimentos-no-open-finance/)
* [Open Finance trava na "engrenagem", aponta executiva do Nubank — Finsiders Brasil](https://finsidersbrasil.com.br/economia-open/open-finance-trava-na-engrenagem-aponta-executiva-do-nubank/)
* [2023 Spending decoded: Klarna's Money Story guides smarter budgeting — Klarna International](https://www.klarna.com/international/press/2023-spending-decoded-klarnas-money-story-guides-smarter-budgeting/)
* [Klarna Brings Back Money Story Tool to 'Inspire' Users to Manage Their Spending — The Fintech Times](https://thefintechtimes.com/klarna-brings-back-money-story-tool-to-inspire-users-to-manage-their-spending/)
* [Meet Cleo: Your Very Own AI Budgeting Assistant — Cleo](https://web.meetcleo.com/blog/meet-cleo-your-very-own-ai-budgeting-assistant)
* [How Does the Cleo App Work? Meet the AI That Roasts Your Spending Habits](https://vocal.media/01/how-does-the-cleo-app-work-meet-the-ai-that-roasts-your-spending-habits)
* [Cleo App Review 2026: Is the AI Budgeting Chatbot Worth It? — The Penny Hoarder](https://www.thepennyhoarder.com/budgeting/cleo-app-review/)

> **Ressalva:** esta pesquisa é baseada em conteúdo publicado (sites oficiais, imprensa especializada, lojas de app), não em uso direto/screenshots dos três apps pela equipe. Se a entrega exigir evidência visual (capturas de tela reais), isso continua pendente — ver [BACKLOG.md](../../../BACKLOG.md).

## 2. Arquitetura de Informação

Rascunho inicial de arquitetura de informação (IA) do app, por área:
* **Home:** feed de transações + atalho de registro manual + resumo de metas.
* **Metas:** lista de metas, simulador de impacto, meta conjunta.
* **Comportamento:** score semanal, quiz de perfil, trilhas gamificadas.
* **Conexões:** status Open Finance, gestão de consentimento, contas conectadas.
* **Configurações:** privacidade, acessibilidade, notificações.

> **Pendência:** esta arquitetura de informação continua sendo um rascunho textual inicial — validação com wireframes reais (Figma) é tratada nas Semanas 4-5, ver [BACKLOG.md](../../../BACKLOG.md).
