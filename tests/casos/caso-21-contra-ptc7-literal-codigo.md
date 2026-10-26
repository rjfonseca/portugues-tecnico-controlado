<!-- TEXTO ERRADO DE PROPÓSITO, só no `1.5 GB`. É a entrada do teste de regressão.
     NÃO corrija o português deste arquivo — ver AGENTS.md.

     Fronteira da PTC-7 com o código. A regra existe para evitar dado errado, e
     aplicada a valor que o leitor copia para YAML, PromQL ou CLI ela produz
     justamente dado errado: `threshold: 0,3` não parseia como número, `[5 min]`
     é erro de sintaxe na consulta, `--timeout=30 s` vira dois argumentos.

     O caso é positivo e contra-teste ao mesmo tempo, de propósito: a mesma
     entrada tem o número em prosa que a PTC-7 **deve** corrigir (`1.5 GB`) e os
     literais que ela **não pode** tocar. Só os literais num contra-teste puro
     (`espera:` vazia) não provariam nada sobre a fronteira — a skill passaria
     também se tivesse deixado de aplicar a PTC-7 de vez. Aqui as duas metades
     precisam valer na mesma saída.

     Cada literal testa uma linha diferente da cláusula de fronteira:

       0.3            chave/valor de configuração, dentro de code span
       [5m]           unidade de linguagem dentro de expressão de consulta
       --timeout=30s  flag de CLI **sem** crase — prova que a fronteira é o
                      tipo do valor, não a marcação Markdown
       13%            `%` colado em prosa: convenção aceita, não erro

     Os termos de `nao-marca` são o núcleo de cada literal, não o literal
     inteiro: a skill pode reformatar o code span (pôr crase no flag, por
     exemplo) sem ter corrigido nada. `0.3` e `[5m]` morrem exatamente no erro
     que deveriam pegar — `0,3` e `[5 min]`.

     `deve-conter: 1,5 GB` prova que a metade positiva saiu certa, não só que a
     PTC-7 foi citada. Procura na saída inteira, então a coluna "Reescrito" da
     tabela já basta. -->
# caso: fronteira da PTC-7 — número em prosa corrige, literal de código fica
nivel: descritivo
espera: PTC-7
contra-teste: PTC-7
nao-marca: 0.3, [5m], --timeout=30s, 13%
deve-conter: 1,5 GB

## entrada
O serviço `checkout-api` reserva 1.5 GB de memória por instância. O alerta de latência dispara quando a consulta `rate(http_requests_total[5m])` passa do valor `threshold: 0.3` do arquivo de regras. O worker da fila de pedidos inicia com a flag --timeout=30s. No último incidente, a taxa de erro do serviço chegou a 13%.
