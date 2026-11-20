# Caso completo: Agente de atendimento de clinica

Um caso do zero mostrando o ciclo inteiro de cultivo.

## Contexto

Clinica medica quer um agente para agendamento de consultas via chat. O agente recebe:

- horarios de funcionamento
- lista de medicos e especialidades
- procedimentos oferecidos
- regras de agendamento
- politica de cancelamento

## Etapa 1 — Plantio (nivel 1: so recomenda)

O agente recebe contexto basico e comeca sugerindo horarios. Humano aprova cada sugestao antes de confirmar com o paciente.

**Scorecard semana 1:**
- 20 interacoes
- 15 acertos
- 5 erros
- Taxa: 75%

## Etapa 2 — Primeira falha

**Erro:** agente marca consulta fora do horario disponivel do medico.

**Diario de falhas:**

| Data | O que quebrou | Menor correcao | Tipo |
|------|-------------|----------------|------|
| 2026-01-15 | Marcou consulta fora do horario do Dr. Silva | Regra: sempre consultar agenda antes de propor horario | prompt |

## Etapa 3 — Correcao

Nova regra adicionada ao contexto do agente:

> "Antes de propor qualquer horario, consultar a agenda do medico. Nunca sugerir horario sem verificar disponibilidade."

## Etapa 4 — Nova execucao

**Scorecard semana 2:**
- 20 interacoes
- 18 acertos
- 2 erros
- Taxa: 90%

Erros restantes: confusao entre procedimentos similares.

## Etapa 5 — Segundo ciclo de correcao

**Diario de falhas:**

| Data | O que quebrou | Menor correcao | Tipo |
|------|-------------|----------------|------|
| 2026-01-22 | Confundiu "limpeza" (estetica) com "limpeza de pele" (dermatologia) | Adicionar tabela de procedimentos com descricao e especialidade | prompt |

Nova ferramenta: tabela de procedimentos com descricao, duracao e medico responsavel.

## Etapa 6 — Estabilidade

**Scorecard semanas 3-4:**
- 40 interacoes
- 40 acertos
- 0 erros
- Taxa: 100%
- Duas semanas consecutivas sem erro

## Etapa 7 — Aumento de autonomia (nivel 2 → nivel 3)

Criterios atendidos:
- [x] 20+ execucoes sem erro consecutivas (40)
- [x] Taxa > 90% (100%)
- [x] 2+ semanas de estabilidade
- [x] Gravidade dos erros recentes: nenhum
- [x] Intervencoes humanas em queda

**Antes:** agente sugere → humano aprova → confirma com paciente

**Depois:** agente executa → humano revisa excecoes (cancelamentos, urgencias, primeira consulta)

## O que mudou no sistema (nao no modelo)

O modelo e o mesmo do dia 1. O que evoluiu:

1. **Contexto:** regra de verificar agenda
2. **Ferramentas:** tabela de procedimentos
3. **Regras:** lista de excecoes que exigem humano
4. **Memoria:** historico de preferencias dos pacientes
5. **Autonomia:** de nivel 1 pra nivel 3

> O modelo nao mudou. O jardim ao redor dele, sim.

## Linha do tempo resumida

```
Semana 1: planta (nivel 1, 75% acerto)
Semana 2: poda (correcao agenda, 90%)
Semana 3: poda (tabela procedimentos, 100%)
Semana 4: estabilidade confirmada
Semana 5: aumenta autonomia (nivel 3)
```
