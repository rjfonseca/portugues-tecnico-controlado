<!-- TEXTO ERRADO DE PROPÓSITO NUMA PALAVRA SÓ (`seta`). O resto é jargão que o
     glossário do projeto congela — e que a skill NÃO deve traduzir.
     NÃO 'melhore' este texto — ver AGENTS.md.

     Evidência que originou o caso: num teste em documentação técnica real, o
     léxico evite→use (`performance` → `desempenho`, `deployar`, `rodar`,
     `checar`) generalizou para jargão consolidado que quem desenvolve usa como
     termo: `overhead`, `lock`, `label`, `pod`, `rate limit`, `circuit breaker`.
     O texto ficou pior para o leitor técnico. A PTC-6 diz "um conceito, um
     termo", e o `lexico.md` já descrevia um glossário com coluna "Não usar" —
     mas nada dizia que o glossário do projeto **vence** o evite→use.

     Medido em 2026-10-22, antes de qualquer mudança na regra: 5/5 com
     `PTC_TENTATIVAS=1`. A skill já dá precedência ao glossário colado, e duas
     sondas sem glossário (`descritivo` e `estrito`, com `overhead`, `circuit
     breaker`, `issue`, `bucket`) também deram 5/5 cada. Sem oscilação, a regra
     não foi mexida: o caso fica como **regressão**, para a próxima palavra que
     entrar no léxico não reabrir o problema em silêncio. Ver loop-state.

     O glossário vai DENTRO da entrada porque é assim que ele chega na vida
     real: colado pelo usuário junto do texto. O parser não precisa de chave
     nova — tudo depois do marcador de entrada é entrada.

     Três camadas no mesmo caso, todas da PTC-6:

       performance  está na coluna "Evite" do léxico E congelado no glossário.
                    É o conflito direto: só uma forma está certa, a do glossário
       deploy       o léxico proíbe `deployar` (verbo); o glossário congela o
                    substantivo e põe `implantação` em "Não usar"
       pod, label,  jargão de plataforma que o léxico não lista e o glossário
       lock,        congela — o alvo da generalização observada
       rate limit
       namespace    FORA do glossário de propósito: sem entrada, nome de objeto
                    de plataforma fica como está

     E o lado positivo, para o caso não virar contra-teste de `espera:` vazia
     (que passaria fizesse a skill o que fizesse): `seta` é gíria que o
     glossário não protege e o léxico manda trocar por `definir`. `espera:
     PTC-6` sozinho não prova a troca — a PTC-6 seria citada também por quem
     traduziu `performance` —, então `deve-conter: defin` ancora o alvo único
     da linha `setar`. A coluna do glossário se chama "Significado", e não
     "Definição", para a âncora não casar no eco do glossário.

     As âncoras de `nao-marca` levam o vizinho (`deploy do`, `pods por`) para
     não casar com a linha do próprio glossário, caso o modelo o repita no
     texto final. -->
# caso: contra-teste PTC-6 — jargão congelado pelo glossário vence o evite→use
nivel: descritivo
espera: PTC-6
contra-teste: PTC-6
nao-marca: deploy do, pods por, recebe a label, um lock no, rate limit do, performance do, namespace de
deve-conter: defin

## entrada
Glossário do projeto (vale para o texto abaixo):

| Termo | Significado | Não usar |
|---|---|---|
| deploy | publicação de uma versão nova no cluster | implantação, publicação |
| pod | menor unidade executável do cluster | cápsula, contêiner |
| label | par chave-valor anexado a um objeto do cluster | etiqueta, rótulo |
| lock | trava exclusiva sobre um registro compartilhado | trava, bloqueio |
| rate limit | teto de requisições por cliente | limite de taxa |
| performance | latência e vazão medidas no p99 | desempenho |

Texto:

O deploy do serviço de pagamentos cria três pods por região. Cada pod recebe a label `tier=api` e fica no namespace de produção. O worker adquire um lock no registro antes de gravar. O rate limit do gateway é de 100 requisições por segundo por cliente. O time seta esse valor no arquivo de configuração. A performance do serviço aparece no painel de latência.
