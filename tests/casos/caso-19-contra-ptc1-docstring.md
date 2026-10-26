<!-- TEXTO MISTO DE PROPÓSITO. Três trechos estão corretos e um está errado.
     NÃO corrija o português deste arquivo — ver AGENTS.md.

     Docstring, descrição de ferramenta e comentário de documentação em Go têm
     sujeito, e ele é o identificador documentado. A PTC-2 prescreve isso com
     todas as letras (`Retorna a lista de pedidos abertos.`), e a PTC-1 exige
     "sujeito lexical em toda oração finita" sem dizer onde o sujeito mora
     numa docstring. Os dois textos vão no mesmo prompt — a mesma família do
     `apenas` e do `Verifica-se` em `loop-state.md`.

     Em Go, a convenção do `godoc` é começar o comentário pelo nome do
     identificador (`// ParseConfig lê...`): ali o sujeito está escrito, e
     acrescentar outro quebra a convenção.

     O `faz-se` da última frase é PTC-1 real, em prosa de procedimento, e tem
     de continuar sendo pego: é o que impede uma cláusula de fronteira de virar
     licença geral. Sem ele, o caso passaria verde com uma PTC-1 desligada.

     Âncoras com o que vem antes do verbo (`"""`, `//`, o nome da ferramenta)
     porque a comparação ignora caixa: `Retorna a lista` sozinho sobreviveria a
     `A função retorna a lista`, que é o falso positivo procurado. -->
# caso: contra-teste PTC-1 — docstring e godoc têm sujeito; `-se` em prosa não
nivel: estrito
espera: PTC-1
contra-teste: PTC-1
nao-marca: """Retorna a lista, // ParseConfig lê, `buscar_pessoas`: Busca pessoas

## entrada
Documentação do módulo de pedidos:

```python
def listar_pedidos_abertos(cliente_id):
    """Retorna a lista de pedidos abertos do cliente."""
```

```go
// ParseConfig lê o arquivo de configuração e devolve a struct Config.
func ParseConfig(caminho string) (Config, error)
```

Descrição da ferramenta `buscar_pessoas`: Busca pessoas por nome.

Antes da migração, faz-se o backup do banco de dados.
