# Cultivando com Claude Code

Como implementar IA cultivada usando Claude Code e Claude Agent SDK.

## Pecas disponiveis

Claude Code ja tem as pecas pro cultivo:

- **CLAUDE.md** — contexto persistente, regras, licoes aprendidas
- **Hooks** — pre/pos execucao, validacao automatica
- **Skills** — comportamentos encapsulados e reutilizaveis
- **Subagentes** — agentes especializados coordenados
- **MCP** — ferramentas externas integradas
- **Memoria** — session resumption, arquivos de memoria

## Ciclo de cultivo no Claude Code

### 1. Ficha do agente = CLAUDE.md

O `CLAUDE.md` e a ficha do agente. Coloque:

- funcao do agente
- regras que nunca quebra
- ferramentas disponiveis
- licoes aprendidas (secao `## Lessons`)
- erros conhecidos e como evitar

### 2. Diario de falhas = FALHAS.md

Crie um `FALHAS.md` na raiz do projeto:

```
| Data | O que quebrou | Menor correcao | Prompt / Infra |
```

Regra: escrever na hora que corrigir, nao no fim do dia.

### 3. Avaliacao = hooks + testes

Use hooks pra validar automaticamente:

- **Pre-commit hook:** roda testes antes de aceitar mudanca
- **Pre-push hook:** valida build
- **Custom hooks:** qualquer validacao especifica do dominio

### 4. Feedback = secao Lessons no CLAUDE.md

Quando o agente erra e voce corrige, adicione uma regra na secao `## Lessons`:

```markdown
## Lessons
- NUNCA fazer X porque Y
- Sempre verificar Z antes de W
```

O agente carrega essas regras em toda sessao futura.

### 5. Skills = comportamento encapsulado

Crie skills pra padroes que se repetem:

```
skills/
  minha-skill/
    SKILL.md    # instrucoes
    script.sh   # automacao
```

Skills sao como "podas bem sucedidas" que viram parte permanente do jardim.

### 6. Subagentes = especializacao

Use subagentes pra separar responsabilidades:

- Um agente revisa codigo
- Outro roda testes
- Outro avalia qualidade

O agente principal coordena. Cada subagente tem seu proprio contexto e regras.

## Exemplo pratico

```
Claude cria codigo
  ↓
Testes executam (hook)
  ↓
Subagente avalia qualidade
  ↓
Erros registrados em FALHAS.md
  ↓
Regra adicionada em CLAUDE.md ## Lessons
  ↓
Proxima execucao ja carrega a regra
```

## O que Claude Code NAO faz sozinho

- **Scorecard automatico:** voce precisa construir (script, planilha, ou template deste framework)
- **Avaliacao estruturada entre versoes:** precisa ser construida com testes + metricas
- **Autonomia progressiva automatica:** a decisao de aumentar autonomia e humana

O ciclo de avaliacao precisa ser construido — Claude Code da as pecas, mas a arquitetura de cultivo e sua.

## Armadilhas

- **CLAUDE.md muito grande:** vira ruido. Mantenha enxuto, mova detalhes pra skills.
- **Lessons sem contexto:** "nao fazer X" sem dizer por que. Sempre inclua o motivo.
- **Hooks que travam:** hooks pesados atrasam o fluxo. Mantenha rapidos.
- **Subagentes sem escopo claro:** subagente generico e so mais um agente. Defina funcao precisa.
