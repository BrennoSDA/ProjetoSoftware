# 📐 Documento de Modelo de Domínio (DDD)

**Semana:** [Semana 7 — Consolidação e Especificação Técnica](../README.md)
**Responde a:** entregável implícito das Semanas 6-7 em [estudo_caso5.md](../../../estudo_caso5.md) (template padrão em [template_modelo_dominio.md](../../../template_modelo_dominio.md)); também cobre o Diagrama de Classes de Domínio, entrega oficial da Semana 7 conforme [diagramasUML.md](../../../diagramasUML.md)
**Status:** Feito

**Projeto:** Conselheiro Financeiro Comportamental

**Módulo / Contexto:** Aconselhamento Comportamental & Open Finance

**Versão do Modelo:** `0.1.0` (rascunho inicial — sujeito a revisão da equipe)

**Data:** 2026-09-02

**Autores:** Grupo 5 (Brenno, Joel, Ian, Davi) — a partir do template em [template_modelo_dominio.md](../../../template_modelo_dominio.md) e dos requisitos em [README.md](../../../README.md)

> Este documento preenche o template padrão do grupo para o Estudo de Caso 5, entregável previsto para as Semanas 6-7 em [estudo_caso5.md](../../../estudo_caso5.md). É um rascunho técnico derivado diretamente dos Requisitos Funcionais (RF), Não Funcionais (RNF), Regras de Negócio (RN) e cláusulas LGPD já definidos pelo professor em `README.md`. Nomes de entidades, agregados e serviços são propostas de modelagem, não decisões de produto — devem ser validados/ajustados pela equipe antes da entrega.

---

## 1. 🌐 Linguagem Onipresente (*Ubiquitous Language*)

| Termo do Negócio | Conceito / Definição | Sinônimos Não Permitidos | Contexto de Uso |
| --- | --- | --- | --- |
| **Compra por Impulso Recorrente** | Padrão de gasto identificado pelo sistema como recorrente em dia/horário/categoria específicos (ex.: delivery às sextas 20h). | Gasto aleatório, compra qualquer. | Motor de Detecção de Padrão. |
| **Gatilho Antigasto** | Notificação preventiva enviada exatamente 1h antes do horário habitual mapeado de uma compra por impulso (RN02). | Lembrete, alerta genérico. | Módulo de Notificações. |
| **Limbo "A Classificar"** | Estado transitório de uma transação sem categoria automática; suspende o cálculo do Score Comportamental (RN04). | Transação pendente, erro de leitura. | Motor de Classificação / Score. |
| **Reserva Mínima de Segurança** | Saldo equivalente a 1 mês do custo de vida básico do usuário, abaixo do qual investimentos/aportes não podem ser sugeridos (RN03). | Colchão financeiro, poupança. | Simulador de Metas. |
| **Score de Saúde Financeira Comportamental** | Pontuação semanal (0–100) que resume a saúde comportamental de gastos do usuário (RF09). | Nota de crédito, score de crédito. | Dashboard / Gamificação. |
| **Meta Conjunta** | Meta financeira compartilhada entre dois ou mais usuários (casal/família), com saldo e progresso compartilhados (RF10). | Meta em grupo, meta familiar genérica. | Contas Conjuntas. |
| **Consentimento Open Finance** | Autorização formal, granular e revogável do usuário para acesso a dados bancários via Open Finance, sem exposição de senha (RNF-01). | Login bancário, integração bancária. | Conexão de Contas. |

---

## 2. 🗺️ Mapeamento de Contextos Delimitados (*Bounded Contexts*)

```
 ┌───────────────────────────────────────────────────────────────┐
 │        CORE DOMAIN: Aconselhamento Comportamental              │
 │  Detecção de Impulso · Score Comportamental · Simulador        │
 └─────────────▲───────────────────────────────────▲──────────────┘
               │ upstream                          │ upstream
 ┌─────────────┴─────────────┐        ┌────────────┴───────────────┐
 │ SUPPORTING: Open Finance   │        │ SUPPORTING: Metas & Educação│
 │ & Transações                │        │ Financeira Gamificada       │
 │ (conexão, sync, IA de       │        │ (metas, trilhas, quiz)      │
 │ categorização)              │        │                              │
 └─────────────▲──────────────┘        └────────────▲─────────────────┘
               │ ACL                                │
 ┌─────────────┴─────────────────────────────────────┴───────────────┐
 │ GENERIC DOMAIN: Autenticação/Consentimento LGPD, Notificações Push  │
 └───────────────────────────────────────────────────────────────────┘
```

### 2.1. Lista de Contextos Delimitados do Sistema

* **Contexto Central (Core Domain):** Detecção de padrões de impulso, cálculo do score comportamental semanal e simulação de impacto de gastos sobre metas — é o diferencial do produto frente a planilhas tradicionais.
* **Contexto de Suporte A (Open Finance & Transações):** Conexão bancária via Open Finance, sincronização periódica (RNF-02) e categorização automática de transações via IA (RNF-08).
* **Contexto de Suporte B (Metas & Educação Financeira):** Definição de metas individuais/conjuntas, quiz de perfil comportamental e trilhas gamificadas.
* **Contexto Genérico (Generic Domain):** Autenticação/2FA, gestão de consentimento LGPD e envio de notificações push — reaproveitáveis de qualquer fornecedor genérico.
* **Camada Anticorrupção (ACL):** Isola o domínio dos contratos externos do provedor certificado de Open Finance e do provedor de push (APNs/FCM), evitando vazamento de modelos externos para o Core Domain.

---

## 3. 🧩 Elementos do Modelo de Domínio

### 3.1. Entidades (*Entities*)

#### `Usuario`
* **ID:** `usuarioId`
* **Atributos:** `nome`, `email`, `custoDeVidaBasico: ValorMonetario`, `configuracaoPrivacidade`
* **Comportamentos:** `definirMeta()`, `registrarGastoManual()`, `responderQuizComportamental()`

#### `ConsentimentoOpenFinance`
* **ID:** `consentimentoId` (associado a `usuarioId`)
* **Atributos:** `status: StatusConsentimento`, `dataRevogacao`, `dataLimiteOcultacao` (+30 dias, RN01)
* **Ciclo de Vida:** `[Ativo] → [Revogado] → [DadosOcultos]` (ver [diagrama de máquina de estados, Semana 6](../../semana-06/entregaveis/diagrama-maquina-estados.md))
* **Comportamentos:** `revogar()`, `restabelecer()`

#### `Transacao`
* **ID:** `transacaoId`
* **Atributos:** `valor: ValorMonetario`, `data`, `estabelecimento`, `categoria`, `status: StatusTransacao`
* **Ciclo de Vida:** `[Recebida] → [AClassificar] → [Classificada]` (RN04)
* **Comportamentos:** `classificar(categoria)`

#### `MetaFinanceira`
* **ID:** `metaId`
* **Atributos:** `prazo: PrazoMeta (curto/médio/longo)`, `valorAlvo: ValorMonetario`, `progresso: ValorMonetario`
* **Comportamentos:** `simularImpacto(gasto: ValorMonetario)`, `verificarReservaMinima()` (RN03)

#### `ContaConjunta`
* **ID:** `contaConjuntaId`
* **Atributos:** `participantes: List<Usuario>`, `saldoCompartilhado`, `configuracaoPrivacidadeIndividual`
* **Comportamentos:** `ocultarDestinoIndividual()` (RN05)

#### `PerfilComportamental`
* **ID:** `perfilId` (1:1 com `Usuario`)
* **Atributos:** `tipoGastador`, `respostasQuiz`

#### `ScoreComportamental`
* **ID:** `scoreId`
* **Atributos:** `semanaReferencia`, `pontuacao (0-100)`, `status: Calculado | Suspenso`
* **Comportamentos:** `calcular()` — bloqueado enquanto houver `Transacao` em `AClassificar` (RN04)

#### `TrilhaEducacional`
* **ID:** `trilhaId`
* **Atributos:** `titulo`, `modulos`, `progressoUsuario`

#### `GatilhoAntigasto`
* **ID:** `gatilhoId`
* **Atributos:** `janelaHorariaHabitual: JanelaHorariaHabitual`, `enviadoEm`
* **Comportamentos:** `disparar()` — deve ocorrer exatamente 1h antes da janela mapeada (RN02)

---

### 3.2. Objetos de Valor (*Value Objects*)

* **`ValorMonetario`** — `{ quantia: BigDecimal, moeda: String }`. Imutável; toda operação retorna nova instância.
* **`JanelaHorariaHabitual`** — `{ diaSemana, horario, categoriaAssociada }`. Usada para agendar o `GatilhoAntigasto` (RN02).
* **`ReservaMinima`** — `{ valor: ValorMonetario }`, calculada a partir do `custoDeVidaBasico` do usuário; expõe `atingida(saldoAtual): Boolean` (RN03).
* **`ConfiguracaoPrivacidadeIndividual`** — `{ ocultarEstabelecimento: Boolean }`, aplicada no feed da `ContaConjunta` (RN05).

---

### 3.3. Agregados e Raízes de Agregação

```
 ┌───────────────────────────────────────────┐   ┌───────────────────────────────┐
 │ AGREGADO: ConexaoOpenFinance                │   │ AGREGADO: MetaFinanceira        │
 │  ★ ConsentimentoOpenFinance (raiz)          │   │  ★ MetaFinanceira (raiz)        │
 │      └── Transacao[]                        │   │      └── ReservaMinima (VO)     │
 └───────────────────────────────────────────┘   └───────────────────────────────┘

 ┌───────────────────────────────────────────┐
 │ AGREGADO: PerfilUsuario                     │
 │  ★ Usuario (raiz)                           │
 │      ├── PerfilComportamental                │
 │      └── ScoreComportamental[]               │
 └───────────────────────────────────────────┘
```

* **Invariantes de Negócio:**
  1. Uma `Transacao` só pode transicionar para `Classificada` com uma categoria não vazia (RN04).
  2. Um `ScoreComportamental` não pode ser calculado (status `Calculado`) enquanto existir `Transacao` da mesma semana em `AClassificar` (RN04).
  3. `MetaFinanceira.simularImpacto()` não pode sugerir aporte se `ReservaMinima.atingida(saldoAtual)` for falso (RN03).
  4. `ConsentimentoOpenFinance` em estado `Revogado` bloqueia qualquer nova leitura de `Transacao` via Open Finance.
  5. Em `ContaConjunta`, se `ConfiguracaoPrivacidadeIndividual.ocultarEstabelecimento` for verdadeiro, o feed compartilhado nunca deve expor o campo `estabelecimento` da `Transacao` (RN05).

---

### 3.4. Serviços de Domínio

* **`DetectorDePadraoDeImpulso`** — Entradas: histórico de `Transacao`. Responsabilidade: identificar recorrência de dia/horário/categoria e produzir `JanelaHorariaHabitual` (ver [fluxograma, Semana 4](../../semana-04/entregaveis/fluxograma-motor-classificacao.md)).
* **`MotorDeClassificacaoDeTransacoes` (IA)** — Entradas: `Transacao` bruta. Responsabilidade: categorizar automaticamente com precisão-alvo >92% (RNF-08); se não conseguir, delega para o estado `AClassificar`.
* **`CalculadoraDeImpactoDeMeta`** — Entradas: `MetaFinanceira`, `ValorMonetario` do gasto simulado. Responsabilidade: recalcular prazo estimado da meta.
* **`CalculadoraDeScoreComportamental`** — Entradas: `Transacao[]` da semana, `PerfilComportamental`. Responsabilidade: computar a pontuação semanal, respeitando a invariante de suspensão por RN04.
* **`ValidadorDeReservaMinima`** — Entradas: saldo atual, `custoDeVidaBasico`. Responsabilidade: aplicar a trava da RN03 antes de qualquer sugestão de aporte.

---

## 4. ⚡ Eventos de Domínio

| Nome do Evento | Gatilho Disparador | Payload | Contextos Notificados |
| --- | --- | --- | --- |
| `TransacaoCategorizadaAutomaticamente` | IA classifica com sucesso | `transacaoId`, `categoria` | Score Comportamental |
| `TransacaoEntrouEmLimboAClassificar` | Falta de dados do estabelecimento (RN04) | `transacaoId` | Score Comportamental, Notificações |
| `GatilhoAntigastoDisparado` | Agendamento atinge T-1h (RN02) | `usuarioId`, `janelaHorariaHabitual` | Notificações Push |
| `ConsentimentoOpenFinanceRevogado` | Usuário revoga acesso (RN01) | `usuarioId`, `dataRevogacao` | Open Finance, Score, Dashboard |
| `DadosAntigosOcultadosPorRevogacao` | 30 dias sem restabelecimento (RN01) | `usuarioId` | Dashboard |
| `InvestimentoBloqueadoPorReservaMinima` | Saldo abaixo da reserva mínima (RN03) | `usuarioId`, `metaId` | Simulador de Metas |
| `ScoreComportamentalCalculado` | Fechamento semanal sem pendências | `usuarioId`, `semanaReferencia`, `pontuacao` | Dashboard, Gamificação |

---

## 5. 🛡️ Regras de Negócio e Invariantes

* **RN01 (Revogação Open Finance):** ver `ConsentimentoOpenFinance` §3.1 e evento `ConsentimentoOpenFinanceRevogado`.
* **RN02 (Gatilho Antigasto):** disparo exatamente 1h antes da `JanelaHorariaHabitual` — invariante de agendamento no `GatilhoAntigasto`.
* **RN03 (Margem de Segurança):** ver `ValidadorDeReservaMinima` e invariante #3 do agregado `MetaFinanceira`.
* **RN04 (Classificação de Erros):** ver ciclo de vida de `Transacao` e invariante #2 do agregado `PerfilUsuario`.
* **RN05 (Privacidade de Casal):** ver `ConfiguracaoPrivacidadeIndividual` e invariante #5 do agregado `ContaConjunta`.
* **LGPD-01 / LGPD-02:** aplicam-se transversalmente ao `ConsentimentoOpenFinance` (finalidade vinculada — proibição de uso para credit scoring) e ao processo de resposta a incidentes especificado em [Semana 1](../../semana-01/entregaveis/politica-credit-scoring-plano-incidentes.md).

---

## 6. 📊 Rastreabilidade com Requisitos e Telas

| Agregado / Entidade | Requisito (RF) | Tela (ID de referência) | Ação da Interface que Altera o Domínio |
| --- | --- | --- | --- |
| `ConexaoOpenFinance` | RF01 | SCR-01 | Confirmação do consentimento Open Finance. |
| `Transacao` | RF02 | SCR-02 | Classificação manual de transação pendente. |
| `MetaFinanceira` | RF03, RF06 | SCR-03, SCR-06 | Criação de meta / simulação de gasto. |
| `GatilhoAntigasto` | RF04 | SCR-04 | Recebimento e interação com notificação. |
| `Usuario` (registro manual) | RF05 | SCR-05 | Envio do formulário de registro rápido. |
| `PerfilComportamental` | RF07 | SCR-07 | Envio das respostas do quiz. |
| `TrilhaEducacional` | RF08 | SCR-08 | Progresso em módulo da trilha. |
| `ScoreComportamental` | RF09 | SCR-09 | Consulta do dashboard semanal. |
| `ContaConjunta` | RF10 | SCR-10 | Ativação do toggle de privacidade individual. |

> Nota: os IDs de tela (SCR-XX) são referências lógicas para uso futuro quando as telas reais forem produzidas (Figma, Semanas 4-11); nenhuma tela real existe ainda — ver [BACKLOG.md](../../../BACKLOG.md).
