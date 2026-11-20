# IA Cultivada Framework

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


Framework operacional para implementar IA cultivada nos seus projetos.

**IA cultivada nao e um modelo novo. E uma maneira de construir sistemas com IA.**

O modelo e a semente. O sistema de cultivo esta ao redor dela.

## O ciclo

```
execucao â†’ avaliacao â†’ feedback â†’ ajuste â†’ nova execucao
```

Detalhado:

```
Objetivo
  â†“
Agente executa
  â†“
Resultado
  â†“
Avaliacao (scorecard, observabilidade)
  â†“
Feedback (diario de falhas, revisao humana)
  â†“
Ajuste (memoria, skill, regra, contexto, ferramenta)
  â†“
Nova execucao (melhor)
```

## Quatro niveis de maturidade

| Nivel | Nome | Descricao |
|-------|------|-----------|
| 1 | Executora | Prompt â†’ resposta. Sem memoria, sem avaliacao. |
| 2 | Contextual | Memoria e contexto persistente. Personaliza, mas nao evolui. |
| 3 | Agente | Objetivo + ferramentas + acao. Pode repetir erros. |
| 4 | Cultivada | Execucao + avaliacao + feedback + ajuste + nova execucao. Evolui. |

**Nem todo agente e cultivado. Memoria nao e aprendizado. A ferramenta nao e cultivada â€” a arquitetura e.**

## Estrutura do repo

```
templates/          Templates prontos pra copiar e usar
  scorecard.md        Scorecard de agente
  diario-falhas.md    Diario de falhas
  observabilidade.md  Checklist de observabilidade
  ficha-agente.md     Ficha do agente
  autonomia-progressiva.md  Criterios de autonomia

exemplos/           Casos praticos
  caso-clinica.md     Caso completo do zero
  mapa-sistemas-2026.md  Quem permite IA cultivada hoje

guias/              Como cultivar em cada plataforma
  claude-code.md      Claude Code (hooks, CLAUDE.md, skills, subagentes)
  codex.md            OpenAI Codex (Agents API, Evals)
  langgraph.md        LangGraph (memoria, human-in-the-loop)
```

## Como usar

1. Leia o caso da clinica em `exemplos/caso-clinica.md` pra entender o ciclo completo
2. Copie os templates de `templates/` pro seu projeto
3. Preencha a `ficha-agente.md` do seu agente
4. Comece a registrar no `diario-falhas.md` e no `scorecard.md`
5. Use o checklist de `observabilidade.md` em cada execucao
6. Siga os criterios de `autonomia-progressiva.md` pra aumentar autonomia
7. Consulte o guia da sua plataforma em `guias/`

## Frase central

> O modelo pode ser o mesmo que o do concorrente. O jardim, nao.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>