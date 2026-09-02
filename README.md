# ps-es-20262-g5
Repositório definido para a manutenção do controle de versões do projeto desenvolvido pelos alunos do grupo 5, da disciplina Projeto de Software, no semestre 2026/2.

## 💸 Finanças e Economia de Contexto (FinTech)

### 5. Conselheiro Financeiro Comportamental

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
