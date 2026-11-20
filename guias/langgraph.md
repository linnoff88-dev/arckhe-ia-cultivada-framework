# Cultivando com LangGraph

Como implementar IA cultivada usando LangGraph com memoria e human-in-the-loop.

## Por que LangGraph e naturalmente cultivavel

LangGraph foi desenhado pra grafos de estado com ciclos — exatamente o que cultivo precisa:

- **Estado persistente** — cada execucao carrega e modifica estado
- **Checkpoints** — snapshots do estado em cada no do grafo
- **Human-in-the-loop** — interrupcao e intervencao humana nativa
- **Memoria** — curta (thread) e longa (cross-thread)
- **Ciclos** — o grafo pode voltar a nos anteriores (retry, correcao)

## Ciclo de cultivo no LangGraph

### 1. Ficha do agente = Estado + nos do grafo

O agente e um grafo com:

- **Estado:** dados que persistem entre nos (contexto, regras, historico)
- **Nos:** funcoes que processam e transformam o estado
- **Arestas:** decisoes de roteamento (condicional ou fixo)

### 2. Memoria = Store

LangGraph tem dois tipos:

**Memoria de thread (curta):**
- Checkpoints dentro de uma conversa
- Permite voltar a qualquer ponto

**Memoria cross-thread (longa):**
- Persiste entre conversas
- Guarda: preferencias, regras aprendidas, historico de falhas

Use memoria longa pra guardar o jardim cultivado.

### 3. Human-in-the-loop = poda em tempo real

```python
# Interromper antes de executar acao critica
graph.add_node("confirmar", interrupt_before=True)
```

Modos:

- **Approve/reject:** humano aprova acao antes de executar
- **Edit:** humano modifica a acao proposta
- **Feedback:** humano avalia resultado e da input

Isso e o nivel 2 de autonomia (executa com aprovacao).

### 4. Avaliacao = no de avaliacao no grafo

Adicione um no que avalia o resultado:

```
agente executa
  ↓
no de avaliacao (outro LLM, regras, ou metricas)
  ↓
resultado bom → segue
resultado ruim → volta pro agente com feedback
```

### 5. Feedback loop no grafo

```
input → agente → acao → avaliacao → ok? 
                                      ↓ sim: output
                                      ↓ nao: feedback → agente (ciclo)
```

O grafo naturalmente suporta ciclos — o agente pode tentar de novo com o feedback.

### 6. Observabilidade = LangSmith

LangSmith (ou equivalente) registra:

- cada execucao do grafo
- cada no visitado
- estado em cada checkpoint
- tempo e custo por no
- resultado final

## Exemplo pratico

```python
from langgraph.graph import StateGraph

# Estado do agente cultivado
class AgentState:
    messages: list       # conversa
    rules: list         # regras aprendidas
    failures: list      # historico de falhas
    scorecard: dict     # metricas acumuladas
    autonomy_level: int # nivel atual

# Grafo
graph = StateGraph(AgentState)
graph.add_node("agent", agent_node)
graph.add_node("evaluate", evaluate_node)
graph.add_node("learn", learn_from_failure)
graph.add_node("human_review", interrupt_before=True)

# Fluxo
graph.add_edge("agent", "evaluate")
graph.add_conditional_edges("evaluate", {
    "pass": "output",
    "fail": "learn"
})
graph.add_edge("learn", "agent")  # ciclo
```

## Padrao: autonomia progressiva no grafo

```python
def route_by_autonomy(state):
    if state.autonomy_level <= 2:
        return "human_review"  # precisa aprovacao
    elif is_exception(state):
        return "human_review"  # excecao
    else:
        return "execute"       # autonomo
```

Conforme o scorecard melhora, aumente `autonomy_level` — o grafo automaticamente pula a revisao humana.

## Diferencas pros outros

| Aspecto | LangGraph | Claude Code | Codex |
|---------|-----------|-------------|-------|
| Ciclos nativos | Sim (grafo) | Nao | Parcial |
| Human-in-the-loop | Nativo | Manual | Parcial |
| Memoria longa | Store | Arquivos | API |
| Estado tipado | Sim | Nao | Parcial |
| Observabilidade | LangSmith | Logs | Traces |
| Ambiente | Codigo Python | CLI | Cloud |

## Armadilhas

- **Grafo complexo demais:** comece simples, adicione nos conforme erros aparecem
- **Memoria longa sem limpeza:** acumula ruido. Versione e pode periodicamente
- **Human-in-the-loop em tudo:** se tudo precisa de aprovacao, o agente nao evolui
- **Avaliacao so por LLM:** LLM avaliando LLM pode ter os mesmos vieses. Misture com regras deterministicas
- **Checkpoints sem uso:** guardar estado sem nunca voltar a ele e desperdicio
