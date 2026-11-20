# Mapa de Sistemas — Setembro 2026

Quais sistemas permitem construir IA cultivada hoje.

> A ferramenta nao e cultivada. A arquitetura e.

## Classificacao

| Sistema / Arquitetura | Agente | Memoria | Ferramentas | Avaliacao | Pode ser cultivado |
|---|---|---|---|---|---|
| OpenAI Codex + Agents API + Evals | Sim | Sim | Sim | Sim | Sim |
| Gemini Enterprise Agent Platform + Memory Bank | Sim | Sim | Sim | Sim | Sim |
| LangGraph + memoria + human-in-the-loop | Sim | Sim | Sim | Sim | Sim |
| Claude Code / Claude Agent SDK | Sim | Sim | Sim | Construivel | Sim |
| ChatGPT com Memory | Parcial | Sim | Sim | Parcial | Parcial |
| Gemini pessoal com Memory | Parcial | Sim | Parcial | Nao | Parcial |
| Claude simples no chat | Parcial | Sessao | Nao | Nao | Nao |
| LLM via API (prompt → resposta) | Nao | Nao | Nao | Nao | Nao |
| RAG simples | Nao | Nao | Consulta | Nao | Nao |
| Make/n8n com fluxo fixo | Fluxo | Nao | Sim | Nao | Nao |
| Make/n8n + agentes + memoria + avaliacao | Sim | Sim | Sim | Sim | Sim |

## O que faz a diferenca

O mesmo modelo pode funcionar de maneira tradicional ou cultivada. A diferenca esta na arquitetura ao redor:

- **Tem ciclo de avaliacao?** Executa, mede, registra, ajusta?
- **Tem memoria estruturada?** Nao so "lembra do usuario", mas guarda falhas, regras, evolucao?
- **Tem feedback loop?** Erros viram correcoes que entram na proxima execucao?
- **Tem observabilidade?** Da pra saber o que o agente decidiu e por que?

Se a resposta for sim pra essas quatro, o sistema pode ser cultivado — independente do modelo.

## Observacao

Memoria sozinha nao e cultivo. Personalizar ("usuario prefere respostas curtas") e adaptacao, nao evolucao. Cultivo e quando o sistema muda o comportamento do agente com base em evidencia de desempenho.
