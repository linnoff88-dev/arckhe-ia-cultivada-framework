# Autonomia Progressiva

Criterios para aumentar (ou reduzir) a autonomia de um agente.

## Niveis

### Nivel 1 — So recomenda

O agente analisa e sugere. Humano decide e executa.

**Quando usar:** agente novo, dominio critico, sem historico.

### Nivel 2 — Executa com aprovacao

O agente executa apos aprovacao humana explicita.

**Quando usar:** agente com historico curto, erros ainda frequentes.

### Nivel 3 — Executa, humano revisa excecoes

O agente opera sozinho. Humano so intervem em casos fora do padrao.

**Quando usar:** scorecard consistente, taxa de erro baixa por 2+ semanas.

### Nivel 4 — Autonomo dentro de limites

O agente opera automaticamente dentro de regras definidas. Escala pro humano so em situacoes pre-definidas.

**Quando usar:** historico longo, taxa de erro minima, custo de erro baixo.

## Criterios para subir de nivel

| Criterio | Minimo sugerido |
|----------|----------------|
| Execucoes sem erro consecutivas | 20+ |
| Taxa de acerto no periodo | > 90% |
| Semanas de estabilidade | 2+ |
| Gravidade dos erros recentes | Baixa |
| Custo maximo de um erro | Aceitavel pro dominio |
| Intervencoes humanas | Tendencia de queda |

## Criterios para descer de nivel

- Erro grave (perda de dados, acao irreversivel errada)
- Taxa de erro subiu em relacao ao periodo anterior
- Novo tipo de erro nao previsto nas regras
- Mudanca no dominio (novos procedimentos, novos usuarios)

## Regra de ouro

> Autonomia deve ser conquistada por evidencia, nao por confianca.

Nao aumente autonomia porque "parece que esta funcionando". Aumente porque os numeros mostram que esta funcionando.
