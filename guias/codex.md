# Cultivando com OpenAI Codex

Como implementar IA cultivada usando OpenAI Codex, Agents API e Evals.

## Por que Codex e naturalmente cultivavel

Codex ja foi desenhado com as pecas do ciclo:

- **Agents API** — agentes com ferramentas, estado e raciocinio
- **Evals** — avaliacao sistematica de comportamento
- **Traces** — observabilidade completa de cada execucao
- **Handoffs** — delegacao entre agentes especializados

## Ciclo de cultivo no Codex

### 1. Ficha do agente = System prompt + configuracao

Defina no agente:

- instrucoes (system prompt)
- ferramentas disponiveis
- guardrails (input/output)
- handoffs (pra quem delega)

### 2. Avaliacao = Evals

Evals sao o scorecard automatizado:

```
Conjunto de casos de teste
  ↓
Agente executa cada caso
  ↓
Resultado comparado com esperado
  ↓
Score gerado
  ↓
Comparacao entre versoes
```

Crie evals que cobrem:

- casos que ja falharam (regressao)
- casos normais (baseline)
- edge cases (robustez)

### 3. Observabilidade = Traces

Cada execucao gera um trace com:

- input recebido
- raciocinio do modelo
- ferramentas chamadas
- output gerado
- tempo e custo

Use traces pra entender POR QUE o agente errou, nao so QUE errou.

### 4. Feedback loop

```
Eval roda → score cai → analisa traces → identifica causa → ajusta prompt/ferramenta/guardrail → eval roda de novo → score sobe
```

### 5. Guardrails = limites do jardim

- **Input guardrails:** validam o que entra (rejeita pedidos fora do escopo)
- **Output guardrails:** validam o que sai (bloqueia respostas perigosas)

Guardrails sao a cerca do jardim — nao deixam o agente crescer pra onde nao deve.

### 6. Handoffs = especializacao

Delegue tarefas especificas pra agentes especializados:

```
Agente principal (triagem)
  ↓ handoff
Agente de agendamento (dominio especifico)
  ↓ handoff
Agente de cancelamento (regras diferentes)
```

Cada agente cultivado separadamente, com seu proprio scorecard.

## Exemplo pratico

```
v1.0: agente responde perguntas sobre produto
  Eval: 70% de acerto
  Trace: confunde plano basic com premium

v1.1: adicionada tabela de planos no contexto
  Eval: 85% de acerto
  Trace: ainda erra em cancelamentos

v1.2: criado agente especializado em cancelamentos (handoff)
  Eval: 95% de acerto

v1.3: adicionados guardrails de output
  Eval: 97% de acerto, 0 respostas fora do escopo
```

## Diferencas pro Claude Code

| Aspecto | Codex | Claude Code |
|---------|-------|-------------|
| Avaliacao | Evals nativo | Construir com testes/hooks |
| Observabilidade | Traces nativo | Logs + journalctl |
| Memoria | API de estado | CLAUDE.md + arquivos |
| Feedback | Eval → ajuste → re-eval | Lessons + FALHAS.md |
| Ambiente | Cloud | Local |

## Armadilhas

- **Evals que nao cobrem falhas reais:** crie eval pra cada erro que acontecer em producao
- **Traces ignorados:** trace sem analise e dado perdido
- **Guardrails muito frouxos:** o agente age fora do escopo sem ser barrado
- **Handoff sem contexto:** agente especializado recebe a tarefa sem o historico
