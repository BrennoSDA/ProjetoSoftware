# Especificação: Sincronização 2x/dia (RNF-02) e Criptografia por Usuário (RNF-09)

**Semana:** [Semana 7 — Consolidação e Especificação Técnica](../README.md)
**Responde a:** Entregável 1 do enunciado ([estudo_caso5.md](../../../estudo_caso5.md), seção "Semana 7") — *"Especificação de Sincronização Open Finance 2x/dia (RNF-02) e Criptografia (RNF-09)"*
**Status:** Feito
**Responsável:** Brenno & Joel (AR1/AR2)

---

* **RNF-02 — Latência de Sincronização:** a atualização de saldos/transações via Open Finance ocorre em background pelo menos 2 vezes ao dia. Proposta técnica: job agendado a cada 12h (ex.: 06h e 18h) por usuário, com re-tentativa exponencial em caso de falha do provedor Open Finance; sincronização adicional sob demanda quando o usuário abre o app manualmente (pull-to-refresh), sem contar como uma das 2 obrigatórias.
* **RNF-09 — Criptografia:** cada usuário possui uma chave de criptografia exclusiva para cifrar dados confidenciais de transações em repouso (envelope encryption: chave de dados por usuário, cifrada por uma chave mestra gerenciada em KMS). Chaves nunca compartilhadas entre usuários; revogação de acesso (RN01) não implica descarte imediato da chave (dados continuam cifrados e ocultos, não perdidos, dentro da janela de 30 dias).

> **Pendência:** escolha do provedor de KMS (AWS KMS, GCP KMS, HashiCorp Vault) e política exata de rotação de chaves são decisões de infraestrutura ainda não tomadas pela equipe. Ver [BACKLOG.md](../../../BACKLOG.md).
