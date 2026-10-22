<!-- TEXTO CORRETO DE PROPÓSITO — contra-teste. A regra NÃO deve disparar aqui.
     NÃO 'melhore' este texto — ver AGENTS.md.

     Rótulo não é oração. Título de seção, título de tarefa, resumo de alerta e
     item de checklist são sintagma nominal (ou título com verbo), e a PTC-1
     ("sujeito lexical em toda oração finita") não tem o que exigir deles.
     Num teste com textos reais, a skill transformou rótulos assim em frase
     completa — `Os testes de aceitação cobrem...`, `A tarefa corrige...`.

     Cada âncora leva o que vem antes do núcleo (`tarefa:`, `alerta:`, `[ ]`)
     porque a comparação ignora caixa: `Testes de aceitação` sozinho
     sobreviveria a `Os testes de aceitação cobrem`, que é o falso positivo
     procurado. Com o prefixo, a âncora morre exatamente quando um sujeito ou
     artigo entra na frente do rótulo.

     Sem título com verbo de propósito. A primeira versão tinha `Título da
     tarefa: Corrige a falha...`, e a skill trocou por `Corrija` em 5/5 — citando
     PTC-2 (forma verbal da instrução), não PTC-1. Título com verbo na 3ª pessoa
     lido como imperativo de `tu` é fronteira da PTC-2, e fica para a sessão
     dela (loop-state, 2026-10-22).

     Sem gerúndio de propósito. O texto real tinha `Testes de aceitação
     cobrindo os erros 400 e 403`, e o gerúndio adjetivo dentro de rótulo é
     terreno da PTC-2 — se a skill reescrevesse esse item, o caso não diria
     qual das duas regras disparou (AGENTS.md, "uma regra por sessão").

     Sem limiar de legibilidade — contra-teste de `espera:` vazia tem saída ≈
     entrada, e o número asseraria a entrada. -->
# caso: contra-teste PTC-1 — rótulo não é oração (título, alerta, checklist)
nivel: estrito
espera:
contra-teste: PTC-1
nao-marca: ## Rotação de credenciais, tarefa: Falha na exportação, alerta: Fila de pagamentos, [ ] Testes de aceitação, [ ] Mensagem de erro

## entrada
## Rotação de credenciais

Título da tarefa: Falha na exportação de relatórios

Resumo do alerta: Fila de pagamentos acima de 1.000 mensagens

Critérios de aceite:

- [ ] Testes de aceitação para os erros 400 e 403
- [ ] Mensagem de erro com o código da falha
