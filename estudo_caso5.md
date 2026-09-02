# 🎯 Projeto: Conselheiro Financeiro Comportamental

* **A oportunidade:** Planilhas de gastos tradicionais falham porque dependem de preenchimento manual ou apenas mostram o dinheiro sumindo.
* **O app:** Um app financeiro que atua como um "coach" baseado em gatilhos psicológicos. Ele analisa os hábitos de consumo e, ao notar uma compra por impulso recorrente (ex: compras em apps de entrega nas noites de sexta-feira), envia uma notificação preventiva e amigável para ajudar o usuário a manter o foco em suas metas de longo prazo (como uma viagem ou reserva de emergência).

#### Requisitos Funcionais (RF)

1. O sistema deve se conectar às contas bancárias e cartões de crédito do usuário via Open Finance institucional.
2. O sistema deve categorizar automaticamente todas as transações financeiras em tempo real.
3. O sistema deve permitir que o usuário defina metas financeiras de curto, médio e longo prazo.
4. O sistema deve enviar notificações push contextuais preventivas nos dias e horários históricos de compras por impulso do usuário.
5. O sistema deve permitir o registro manual de gastos em dinheiro em menos de três cliques na tela inicial.
6. O sistema deve simular o impacto de um gasto supérfluo atual no alcance das metas de longo prazo do usuário.
7. O sistema deve rodar testes psicológicos simples (via quiz no app) para determinar o perfil comportamental de gastos do usuário.
8. O sistema deve oferecer trilhas de educação financeira gamificadas baseadas nos erros de consumo identificados no perfil.
9. O sistema deve calcular uma "pontuação de saúde financeira comportamental" semanal para o usuário.
10. O sistema deve permitir a criação de uma meta conjunta para casais ou famílias com saldos compartilhados.

#### Requisitos Não Funcionais (RNF)

1. **Segurança Bancária:** O sistema deve utilizar infraestrutura certificada de Open Finance e nunca ter acesso às senhas de movimentação bancária do usuário.
2. **Latência de Sincronização:** A atualização dos saldos via Open Finance deve ocorrer em background ao menos duas vezes ao dia.
3. **Usabilidade Móvel:** O aplicativo deve ser desenvolvido usando tecnologias nativas ou frameworks de alto desempenho (como Flutter) para garantir animações fluidas a 60 FPS.
4. **Disponibilidade:** O gateway de processamento de notificações de gatilhos financeiros deve operar com latência inferior a 500ms.
5. **Privacidade Financeira:** Os dados financeiros do usuário nunca devem ser vendidos ou compartilhados com corretoras, bancos ou anunciantes terceiros.
6. **Suporte de Plataforma:** O app deve estar disponível nas lojas Google Play Store e Apple App Store simultaneamente.
7. **Escalabilidade:** O microsserviço de classificação de transações por IA deve suportar picos de tráfego que ocorrem em datas comerciais (ex: Black Friday).
8. **Confiabilidade:** O sistema de categorização de transações bancárias deve atingir uma precisão superior a 92% sem intervenção do usuário.
9. **Criptografia:** Chaves de criptografia exclusivas devem ser geradas por usuário para a cifragem dos dados confidenciais de transações.
10. **Acessibilidade:** Cores usadas para denotar saldos e alertas devem possuir alternativas visuais (ícones) para usuários daltonistas.

#### Regras de Negócio (RN)

1. **RN01 (Revogação Open Finance):** Se o usuário revogar o consentimento de acesso ao Open Finance, o sistema deve congelar as análises preditivas imediatamente e ocultar os dados antigos da interface principal após 30 dias, caso o acesso não seja restabelecido.
2. **RN02 (Gatilho Antigasto):** O envio da notificação preventiva de gastos por impulso deve ocorrer exatamente 1 hora antes do horário habitual mapeado de consumo do usuário (ex: se o usuário pede delivery às 20h de sexta, a notificação deve chegar às 19h).
3. **RN03 (Margem de Segurança):** O sistema não deve sugerir investimentos ou aportes em metas de longo prazo se o saldo atual da conta corrente/poupança do usuário for inferior ao equivalente a 1 mês de seu custo de vida básico (reserva mínima).
4. **RN04 (Classificação de Erros):** Transações que não puderem ser categorizadas automaticamente por falta de dados do estabelecimento devem entrar em um limbo de "A Classificar", suspendendo os cálculos de pontuação comportamental até que o usuário as defina.
5. **RN05 (Privacidade de Casal):** Em contas conjuntas/família, os usuários podem optar por ocultar o destino detalhado de compras individuais, compartilhando no feed comum apenas o valor total debitado e o impacto no orçamento geral.

#### LGPD

1. **LGPD-01 (Finalidade Vinculada):** Os dados bancários capturados via Open Finance só podem ser utilizados para as finalidades explícitas de gestão orçamentária e aconselhamento comportamental do usuário, sendo expressamente vedado o uso desses dados para traçar perfis de crédito (*credit scoring*) comercializados para bancos parceiros sem autorização específica.
2. **LGPD-02 (Segurança de Incidentes):** Em caso de qualquer suspeita de vazamento de dados ou acesso não autorizado ao banco de dados de transações, o sistema deve acionar um plano de contingência para notificar a ANPD (Autoridade Nacional de Proteção de Dados) e os usuários afetados no prazo legal determinado.

---

## 👬 Planejamento Completo de Análise de Requisitos e Design UI/UX (14 Semanas)

## 👥 1. Matriz de Atribuição e Distribuição dos 10 Requisitos

Para cobrir o projeto em 14 semanas (14 iterações) com 2 Analistas de Requisitos (AR1 e AR2) e 2 UI/UX Designers (D1 e D2), dividimos o escopo em dois blocos funcionais paralelos:

* **Bloco A (Requisitos 01 ao 05 — Open Finance, Categorização, Metas & Gatilhos Preventivos):**  
Conexão bancária via Open Finance, categorização em tempo real, definição de metas financeiras, notificações preventivas antidesperdício e registro rápido de gastos em dinheiro.
* **Bloco B (Requisitos 06 ao 10 — Simuladores, Perfil Psicológico, Gamificação & Finanças Conjuntas):**  
Simulador de impacto de compras no longo prazo, quiz de perfil comportamental, trilhas gamificadas, score de saúde financeira e gestão de metas para casais/famílias.

```Plaintext       [ CONSELHEIRO FINANCEIRO COMPORTAMENTAL (FINTECH) ]
                               │
         ┌─────────────────────┴─────────────────────┐
         ▼                                           ▼
   [ BLOCO A: Open Finance & Gatilhos ]        [ BLOCO B: Psicologia & Metas ]
   Dupla: AR1 + Designer 1                     Dupla: AR2 + Designer 2
   ├── REQ-01: Integração Open Finance (RN01)  ├── REQ-06: Simulador de Impacto
   ├── REQ-02: Categorização Automática (RN04) ├── REQ-07: Quiz de Perfil Comportamental
   ├── REQ-03: Metas de Curto/Longo Prazo      ├── REQ-08: Trilhas Gamificadas
   ├── REQ-04: Notificações Preventivas (RN02) ├── REQ-09: Score de Saúde Comportamental
   └── REQ-05: Registro Manual em < 3 Clics    └── REQ-10: Metas Conjuntas (RN05)
```

## 🗓️ 2. Cronograma de Atividades Semanais (14 Semanas)

|Semana|Início|Fim|
|:---|:---|:---|
|01|10/08/2026|16/08/2026|
|02|17/08/2026|23/08/2026|
|03|24/08/2026|30/08/2026|
|04|31/08/2026|06/09/2026|
|05|07/09/2026|13/09/2026|
|06|14/09/2026|20/09/2026|
|07|21/09/2026|27/09/2026|
|08|28/09/2026|04/10/2026|
|09|05/10/2026|11/10/2026|
|10|12/10/2026|18/10/2026|
|11|19/10/2026|25/10/2026|
|12|26/10/2026|01/11/2026|
|13|02/11/2026|08/11/2026|
|14|09/11/2026|15/11/2026|

* **Fase 1: Descoberta, Conformidade e Arquitetura**  
(Semanas 1 a 3)
  * **Semana 1 (Iteração 1): Kickoff, Open Finance e Privacidade Financeira**
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Elicitação de requisitos da infraestrutura certificada de Open Finance sem retenção de senhas (RNF-01), regras de revogação de consentimento (RN01), vedação de venda para credit scoring (LGPD-01) e protocolo de incidentes (LGPD-02).
      * **D1 / D2**: Benchmarking de FinTechs (Nubank, Klarna, Cleo), estudo de paletas acessíveis para daltonistas com ícones auxiliares (RNF-10) e definição da arquitetura de informação do app.
    * **Entregáveis**:
      * **Entregável 1**: Termos de Uso e Especificação do Open Finance sem Retenção de Senhas (RNF-01).
      * **Entregável 2**: Política de Veto ao Credit Scoring Commercial (LGPD-01) e Plano de Incidentes (LGPD-02).
      * **Entregável 3**: Guia de Design para Daltonistas (Alternativas Visuais por Ícones - RNF-10).
      * **Entregável 4**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 2 (Iteração 2): Elicitação do Bloco A (Req. 01 ao 05)**
    * **Equipe/Atividades**:
      * **AR1**: Especificação das User Stories (US-01 a US-05), definição da notificação preventiva exatamente 1h antes do hábito mapeado (RN02), suspensão de score para transações sem categoria (RN04) e registro manual em até 3 toques (REQ-05).
      * **D1**: Mapeamento das jornadas de consentimento Open Finance, recepção de push contextual e widget de atalho para inserção de dinheiro físico na home.
      * **AR2 / D2**: Mapeamento prévio do Bloco B e desenho de personas de consumidores por impulso vs. casais dividindo orçamento.
    * **Entregáveis**:
      * **Entregável 1**: Especificação BDD/Gherkin das User Stories US-01 a US-05.
      * **Entregável 2**: Especificação do Gatilho Antigasto 1h Antes (RN02) e Registro Manual em <3 Clics (REQ-05).
      * **Entregável 3**: Regra de Congelamento por Revogação Open Finance (RN01) e Limbo "A Classificar" (RN04).
      * **Entregável 4**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 3 (Iteração 3): Elicitação do Bloco B (Req. 06 ao 10)**
    * **Equipe/Atividades**:
      * **AR2**: Detalhamento das User Stories (US-06 a US-10), especificação da trava de segurança de 1 mês de custo de vida para sugestão de aportes (RN03) e mascaramento de compras em contas conjuntas (RN05).
      * **D2**: User flows do quiz psicológico de finanças, simulador visual do impacto de compras na viagem/reserva e feed compartilhado de casais.
    * **Entregáveis**:
      * **Entregável 1**: Especificação BDD/Gherkin das User Stories US-06 a US-10.
      * **Entregável 2**: Trava de Margem de Segurança de 1 Mês de Custo de Vida (RN03) e Privacidade do Casal (RN05).
      * **Entregável 3**: Personas (Comprador por Impulso vs. Casal) e User Flows de Contas Conjuntas.
      * **Entregável 4**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
* **Fase 2: Prototipagem Lo-Fi/Mid-Fi e Design System**  
(Semanas 4 a 7)
  * Semana 4 (Iteração 4): Wireframes em Baixa Fidelidade (Lo-Fi)
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Fluxogramas do algoritmo de identificação de compras por impulso recorrentes e diagramas de classificação de transações via IA.
      * **D1 / D2**: Wireframes Lo-Fi do dashboard principal, seletor de metas, fluxo do quiz comportamental e modal de registro rápido de gastos.
    * **Entregáveis**:
      * **Entregável 1**: Fluxogramas do Motor de Classificação de Transações por IA (Precisão >92% - RNF-08).
      * **Entregável 2**: Wireframes Lo-Fi do Dashboard FinTech, Seletor de Metas e Quiz Comportamental.
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 5 (Iteração 5): Wireframes de Média Fidelidade (Mid-Fi)**
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Validação das travas de tela para a regra de privacidade de casais (RN05).
      * **D1 / D2**: Mid-Fi do simulador de "Gasto Atual vs. Adiamento da Meta", indicador visual do Score Comportamental e tela do limbo de transações "A Classificar" (RN04).
  * **Entregáveis**:
      * **Entregável 1**: Wireframes Mid-Fi do Simulador de Impacto de Gastos Futuros e Feed do Casal.
      * **Entregável 2**: Protótipo Mid-Fi do Painel do Limbo de Transações "A Classificar" (RN04).
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 6 (Iteração 6): Design System "Mindful Finance UX"**
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Mapeamento do dicionário de categorias de gastos e estruturas de mensagens amigáveis de coerção antidesperdício.
      * **D1 / D2**: Design Tokens para Flutter/Mobile nativo (RNF-03 a 60 FPS), componentes sem barreiras para daltonistas, badges de nivelamento gamificado e cards de metas.
    * **Entregáveis**:
      * **Entregável 1**: Design System "Mindful Finance UX" (Compatível com Flutter a 60 FPS - RNF-03).
      * **Entregável 2**: Dicionário de Categorização Orçamentária e Mensagens Empáticas de Push.
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 7 (Iteração 7): Consolidação e Especificação Técnica**
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Especificação da latência de sincronização em background 2x/dia (RNF-02) e chave de criptografia individual (RNF-09).
    * D1 / D2: Finalização dos componentes reutilizáveis no Figma (gráficos de pizza/barras acessíveis, modais de revogação Open Finance e seletores de privacidade).
    * **Entregáveis**:
      * **Entregável 1**: Especificação de Sincronização Open Finance 2x/dia (RNF-02) e Criptografia (RNF-09).
      * **Entregável 2**: Componentes UI de Cards de Metas, Indicadores de Score e Alternativas Daltonistas.
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
* **Fase 3: Design Visual Hi-Fi e Protótipo Navegável**  
(Semanas 8 a 11)
  * **Semana 8 (Iteração 8): UI High-Fidelity — Bloco A (Req. 01 ao 05)**
    * **Equipe/Atividades**:
      * **AR1**: Construção da Matriz de Rastreabilidade do Bloco A.
      * **D1**: UI Final das telas de conexão Open Finance, feed de transações em tempo real, editor de metas e banner de notificação antidesperdício.
    * **Entregáveis**:
      * **Entregável 1**: Matriz de Rastreabilidade Preenchida do Bloco A (REQ-01 ao REQ-05).
      * **Entregável 2**: Telas Hi-Fi de Conexão Open Finance, Categorização e Notificação Preventiva.
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 9 (Iteração 9): UI High-Fidelity — Bloco B (Req. 06 ao 10)**
    * **Equipe/Atividades**:
      * **AR2**: Construção da Matriz de Rastreabilidade do Bloco B.
      * **D2**: UI Final do simulador de impacto futuro, telas do quiz psicológico, trilhas de educação gamificada e painel de metas conjuntas para casais.
    * **Entregáveis**:
      * **Entregável 1**: Matriz de Rastreabilidade Preenchida do Bloco B (REQ-06 ao REQ-10).
      * **Entregável 2**: Telas Hi-Fi do Simulador de Metas, Quiz de Perfil, Trilhas e Metas Conjuntas.
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 10 (Iteração 10): Validação de Regras de Negócio e Estados Especiais**
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Auditoria para garantir o acionamento da trava de margem de segurança de 1 mês antes de sugerir aportes (RN03).
      * **D1 / D2**: Telas para o estado congelado após revogação de Open Finance (RN01), visualização de transações ocultas no feed do casal (RN05) e avisos de desconexão bancária.
    * **Entregáveis**:
      * **Entregável 1**: Layouts de Transações Ocultadas no Feed do Casal (RN05) e Trava da Reserva (RN03).
      * **Entregável 2**: Protótipo UI da Tela de Revogação e Congelamento de Análises (RN01).
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
  * **Semana 11 (Iteração 11): Montagem do Protótipo Interativo**
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Elaboração do plano e casos para os testes de usabilidade com participantes reais.
      * **D1 / D2**: Ligação completa do protótipo no Figma, com simulação do recebimento do push preventivo e interação com a calculadora de impacto nas metas.
    * **Entregáveis**:
      * **Entregável 1**: Protótipo Navegável Interativo no Figma com Simulação de Push Antidesperdício.
      * **Entregável 2**: Roteiro de Testes de Usabilidade com Consumidores e Casais.
      * **Entregável 3**: Diagramas UML, conforme especificado no documento diagramasUML.md, se for o caso.
* **Fase 4: Testes de Usabilidade, Refinamento e Handoff**  
(Semanas 12 a 14)
  * **Semana 12 (Iteração 12): Execução dos Testes com Usuários**
    * **Equipe/Atividades**:
      * **AR1 / AR2** (Facilitadores): Condução das sessões de teste com jovens adultos e casais.
      * **D1 / D2** (Observadores): Registro de tempo para registrar um gasto manual, clareza das cores acessíveis e tom das notificações preventivas.
    * **Entregáveis**:
      * **Entregável 1**: Planilha de Métricas de Teste (Velocidade do Registro Manual, Compreensão de Metas).
      Entregável 2: Gravações e Notas do Feedback sobre o Aconselhamento Comportamental.
  * Semana 13 (Iteração 13): Consolidação e Ajustes de UX
    * **Equipe/Atividades**:
      * **AR1 / AR2**: Atualização das especificações com os feedbacks coletados.
    * D1 / D2: Ajustes nas micro-interações, refinamento dos cards de metas e ajuste nas mensagens coercitivas para garantir empatia sem julgamento moral.
    * **Entregáveis**:
      * **Entregável 1**: Relatório de Usabilidade com Score SUS e Avaliação de Linguagem Empática.
      * **Entregável 2**: Protótipo Hi-Fi Ajustado com Redesenho do Quick-Action de Dinheiro Físico.
  * **Semana 14 (Iteração 14): Handoff Técnico Final**
    * **Equipe/Atividades**:
      * **Equipe Integrada**: Entrega do pacote consolidado: Matriz de Rastreabilidade completa, arquivo Figma Hi-Fi com Design System acessível, Roteiro de Testes e Especificações de Conformidade Open Finance e LGPD.
    * **Entregáveis**:
      * **Entregável 1**: Dossiê Completo de Requisitos, Normas Open Finance e Termos LGPD.
      * **Entregável 2**: Pacote Final Figma, Design System Flutter e Termo de Conclusão do Projeto.

## 📊 3. Matriz de Rastreabilidade Prática (10 Requisitos → UI/UX)

|ID Req|Descrição do Requisito|Regras / LGPD / RNFs Vinculados|User Story|Tela / Módulo no Figma|ID Tela|Responsáveis|Status UI/UX|
|:---|:---|:---|:---|:---|:---|:---|:---|
|REQ-01|Integração via Open Finance institucional|RN01, RNF-01, LGPD-01|US-01|Modal de Conexão Open Finance & Consentimento|SCR-01|AR1 / D1|Concluído|
|REQ-02|Categorização automática de transações em tempo real|RN04, RNF-07, RNF-08|US-02|Feed de Transações & Tela "A Classificar"|SCR-02|AR1 / D1|Concluído|
|REQ-03|Definição de metas de curto, médio e longo prazo|RN03US-03|Painel de Gestão e Criação de Metas|SCR-03|AR1 / D1|Concluído|
|REQ-04|Notificações push preventivas em horários de impulso|RN02, RNF-04|US-04|Banner / Notification Push Antidesperdício|SCR-04|AR1 / D1|Concluído|
|REQ-05|Registro manual de dinheiro em menos de 3 cliques|RNF-03|US-05|Quick-Action Modal: Lançar Dinheiro|SCR-05|AR1 / D1|Concluído|
|REQ-06|Simulador de impacto de gasto no alcance das metas|RNF-03|US-06|Calculadora e Simulador de Adiamento de Meta|SCR-06|AR2 / D2|Concluído|
|REQ-07|Quiz de perfil comportamental de gastos|RNF-10|US-07|Quiz Interativo de Perfil Psicológico|SCR-07|AR2 / D2|Concluído|
|REQ-08|Trilhas de educação financeira gamificadas|RNF-06|US-08|Hub de Trilhas & Micro-Aulas Gamificadas|SCR-08|AR2 / D2|Concluído|
|REQ-09|Pontuação de Saúde Financeira Comportamental|RN04, RNF-10|US-09|Dashboard de Score Comportamental Semanal|SCR-09|AR2 / D2|Concluído|
|REQ-10|Metas conjuntas para casais com saldos compartilhados|RN05, RNF-05, LGPD-02|US-10|Painel da Meta do Casal & Controle de Privacidade|SCR-10|AR2 / D2|Concluído|

## 🧪 4. Roteiro Prático de Teste de Usabilidade (Semana 12)

### 📋 Ficha Técnica

  * Perfil do Participante: Pessoas que desejam controlar compras por impulso e casais que gerenciam finanças em conjunto.
  * Papéis: AR1 ou AR2 (Facilitador da Sessão) | D1 ou D2 (Observador e Anotador de UX).
  * Duração: 45 minutos por participante.
  * Ambiente de Teste: Protótipo interativo no Figma rodando em dispositivo móvel com padrões visualmente acessíveis.

### 🚀 Passos da Sessão de Teste1.

1. Introdução e Alinhamento de Privacidade (5 min)
  * Facilitador: "Bem-vindo! Hoje você testará o protótipo do Conselheiro Financeiro Comportamental. Ele busca ajudar na tomada de decisões sem fazer julgamentos morais dos seus gastos. Fique à vontade para verbalizar seus pensamentos.
  * "Explicar que os dados exibidos são fictícios e obter o aceite verbal para a gravação da sessão.


2. Execução dos Cenários Práticos (30 min)  
Passar as instruções dos cenários baseados nos 10 requisitos e regras de negócio sem indicar onde clicar.


3. Avaliação Pós-Teste (10 min)
  * Aplicação da escala padronizada System Usability Scale (SUS).
  * Perguntas abertas: "*Como você se sentiu ao receber o alerta de notificação preventiva antes do horário habitual de impulso?*" e "*A regra de ocultar o destino de compras individuais na conta conjunta trouxe conforto?*"

### 🎯 Cenários de Teste Mapeados aos Requisitos e Regras de Negócio

|Tarefa|Requisitos & Regras Avaliadas|Instrução Exata para o Usuário|Critério de Aceite & Validação de UX|
|:---|:---|:---|:---|
|01|REQ-01 REQ-05 RN01|"Conecte sua conta bancária fictícia via Open Finance. Em seguida, registre manualmente um gasto de R$ 20 em dinheiro usando no máximo 3 toques.|"• Completa a conexão Open Finance (SCR-01).<br>• Localiza o botão de atalho e registra o valor sem ultrapassar 3 cliques na SCR-05.|
|02|REQ-02 REQ-04 RN02 RN04|"Imagine que é sexta-feira, 19h. Observe a notificação preventiva recebida e resolva a pendência de uma compra que ficou no limbo 'A Classificar'."|• Visualiza a notificação enviada exatamente 1h antes do hábito (RN02) na SCR-04.<br>• Acessa a SCR-02 para categorizar a transação pendente e destravar o score (RN04).|
|03|REQ-03 REQ-06 RN03|"Acesse sua meta 'Viagem de Fim de Ano'. Simule o impacto que a compra de um tênis de R$ 600 causará no prazo dessa meta."|• Visualiza o simulador na SCR-06 e compreende o adiantamento/atraso em dias.<br>• Confirma o aviso da RN03 caso sua reserva básica seja inferior a 1 mês.|
|04|REQ-07 REQ-08 REQ-09|"Responda ao quiz de perfil comportamental para descobrir seu estilo de gastos e acesse a trilha recomendada para o seu perfil."|• Responde ao quiz na SCR-07.<br>• Descobre seu perfil, consulta o score na SCR-09 e acessa a micro-aula correspondente na SCR-08.|
|05|REQ-10 RN05|"Acesse o painel da meta conjunta com seu cônjuge e ajuste a configuração para ocultar o nome da loja de um gasto individual, mantendo visível apenas o valor."|• Entra no painel compartilhado na SCR-10.<br>• Ativa o toggle de privacidade individual permitindo compartilhar apenas o valor e categoria (RN05).|

### 📝 Planilha de Registro de UX e Erros (Para o Designer Anotador)Durante a sessão da Semana 12, o designer preencherá a tabela para direcionar os refinamentos da Semana 13:
|ID Usuário|Tarefa|Requisito / RN|Severidade|Comportamento Observado|Ação Corretiva para a Semana 13|
|:---|:---|:---|:---|:---|:---|
|USR-01|T1|REQ-05|🟡 Média|Leva 4 toques para salvar o gasto em dinheiro porque o teclado não abria automaticamente.|Focar o cursor no campo de valor numérico assim que a modal de registro rápido abrir.|
|USR-02|T3|RN03|🔴 Alta|Ficou confuso ao ver o botão de investimento desativado sem entender o motivo.|Exibir caixa informativa em destaque: "Aporte bloqueado: sua reserva básica precisa cobrir pelo menos 1 mês de custo de vida antes de investir em metas longas."|
|USR-03|T5|RN05|🟢 Baixa|Teve dúvida se o parceiro iria ver o nome do estabelecimento ou apenas a categoria.|Adicionar preview em tempo real mostrando exatamente como o item aparecerá no feed do casal.|
