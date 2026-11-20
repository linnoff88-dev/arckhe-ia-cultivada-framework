# Checklist de Observabilidade

O que registrar em cada execucao do agente.

## Por execucao

- [ ] Objetivo recebido
- [ ] Decisao tomada pelo agente
- [ ] Raciocinio (chain of thought, se disponivel)
- [ ] Ferramentas usadas
- [ ] Tempo de execucao
- [ ] Custo (tokens, creditos, API calls)
- [ ] Resultado obtido
- [ ] Erro (se houve)
- [ ] Intervencao humana (se houve)
- [ ] Feedback dado
- [ ] Correcao aplicada
- [ ] Versao do agente

## Por ciclo (semanal ou N execucoes)

- [ ] Scorecard atualizado
- [ ] Padroes de erro identificados
- [ ] Regras novas criadas ou modificadas
- [ ] Ferramentas adicionadas ou removidas
- [ ] Contexto/memoria atualizado
- [ ] Decisao sobre autonomia (manter, aumentar, reduzir)

## Sinais de que o cultivo esta funcionando

- Taxa de erro diminui entre versoes
- Intervencoes humanas diminuem
- Novos tipos de erro (os antigos ja foram resolvidos)
- Agente lida com casos que antes falhavam

## Sinais de alerta

- Mesmo erro aparece 3+ vezes sem correcao
- Taxa de erro estavel ou subindo
- Intervencoes humanas aumentando
- Correcoes geram novos erros (regressao)
