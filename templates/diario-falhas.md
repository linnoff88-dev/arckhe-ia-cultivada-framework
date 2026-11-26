# Diario de Falhas

## Agente: [nome]

Mais recente no topo. Uma linha por falha.

| Data | O que quebrou | Menor correcao possivel | Prompt / Infra |
|------|-------------|------------------------|----------------|
| | | | |

## Como preencher

- **Data:** YYYY-MM-DD
- **O que quebrou:** fato, sem narrativa. "Marcou consulta fora do horario."
- **Menor correcao possivel:** a proteçêo que faltava. "Consultar agenda antes de propor horario."
- **Prompt / Infra:**
  - `prompt` = instrucao/contexto induziu o erro, modelo entendeu errado
  - `infra` = maquina, rede, servico, permissao, processo
  - `ambos` = quando for os dois

## Regras

1. Escrever na hora que corrigir, nao no fim do dia
2. Se a correcao foi "reescrever tudo", provavelmente era so um guard faltando — registrar o guard
3. Depois de 10 linhas, revisar padroes: erros repetidos indicam falha estrutural
4. Falhas corrigidas nao saem da tabela — historico e evidencia de cultivo
