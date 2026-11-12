# Redes de personagens: La Casa de Papel (1ª temporada)

Trabalho da disciplina **45RPE: Resolução de Problemas com Estruturas de Dados**
Departamento de Engenharia de Software, UDESC. Professor: Marcelo de Souza.

## Sobre o projeto

Este trabalho aplica conceitos, métricas e algoritmos de Teoria dos Grafos e Análise de Redes Complexas às interações entre personagens da série **La Casa de Papel (Money Heist)**, considerando a primeira temporada (assalto à Casa da Moeda) [delimitação a confirmar com o professor].

A base de dados foi construída **manualmente**, assistindo à série e registrando cada interação direta entre dois personagens. A partir dela são construídas redes que respondem a perguntas sobre a estrutura social da obra: quem são os personagens centrais, quais grupos se formam, como aliados e inimigos se organizam e como a rede muda ao longo dos episódios.

A metodologia segue as diretrizes de Labatut e Bost (2019) para extração e análise de redes de personagens fictícios.

## Integrantes

- [Nome 1]
- [Nome 2]
- [Nome 3]

## Estrutura do repositório

```
.
├── dados/
│   ├── interacoes.txt        # base de interações (uma por linha)
│   └── personagens.csv       # dicionário: id -> nome canônico
├── notebook/
│   └── analise.ipynb         # notebook com as análises
├── docs/
│   └── manual_anotacao.md    # critérios de anotação
├── requirements.txt
└── README.md
```

## A base de dados

Cada registro representa **uma interação direta** entre dois personagens (estar na mesma cena não conta).

Formato de cada linha do `interacoes.txt`, com campos separados por espaço:

```
personagem1 personagem2 sinal ambiente [localizador certeza tempo meio]
```

| Campo | Descrição |
| --- | --- |
| `personagem1`, `personagem2` | Identificadores únicos (sem acento e sem espaço), definidos em `personagens.csv` |
| `sinal` | `+` interação positiva, `-` negativa, `0` neutra |
| `ambiente` | Local ou contexto da cena |
| `localizador` | Temporada/parte, episódio e minuto, para conferir na obra (ex.: `P1E01_00:14:30`) |
| `certeza` | `C` (certo) ou `I` (incerto); incertos ficam fora das análises de sinal |
| `tempo` | `P` (presente) ou `F` (flashback) |
| `meio` | `R` (rádio/telefone) ou `-` (pessoalmente) |

Linhas que começam com `#` são comentários, com a descrição da cena e a justificativa do sinal.

Os critérios completos (o que é interação, início e fim, cenas com três ou mais personagens, tratamento de sinal ambíguo, flashbacks) estão em [`docs/manual_anotação.md`](docs/manual_anotacao.md).

**Versão da obra usada:** [Netflix, áudio original, legenda ___]. As marcas temporais se referem a essa versão.

## Modelagem das redes

- **Vértice:** personagem.
- **Aresta:** existência de ao menos uma interação direta entre dois personagens.
- **Direção:** [a definir: não direcionada / direcionada].
- **Peso:** [a definir: número de interações entre o par].
- **Sinal:** representado por contagens de interações positivas, negativas e neutras em cada aresta.
- **Interações incertas e ambíguas:** [a definir].

Redes construídas: [global, positiva, negativa, por episódio, ...].

## Análises

O notebook reúne [8 ou mais] análises, entre elas:

- [Caracterização geral da rede]
- [Distribuição de graus]
- [Centralidades (grau, intermediação, proximidade, PageRank)]
- [Detecção de comunidades]
- [Comparação entre interações positivas e negativas]
- [Evolução ao longo dos episódios]

## Como executar

Requisitos: Python 3.10+ [conferir versão usada].

```bash
git clone [URL DO REPOSITÓRIO]
cd [NOME-DA-PASTA]
pip install -r requirements.txt
jupyter notebook notebook/analise.ipynb
```

O notebook lê os arquivos da pasta `dados/` por caminho relativo. Para reproduzir tudo do zero, use *Restart & Run All*.

Bibliotecas principais: `networkx`, `pandas`, `matplotlib`.

## Originalidade

Não foi encontrado estudo publicado que analise esta obra por redes de interação entre personagens nas bases consultadas ([listar bases]) em [data]. A tabela de buscas está no notebook, na seção de delimitação do corpus.

## Referências

- Labatut, V.; Bost, X. *Extraction and Analysis of Fictional Character Networks: A Survey.* ACM Computing Surveys, 52(5), 2019.
- [demais referências]

## Observação

Projeto acadêmico (avaliação de recuperação). Todos os direitos sobre a obra analisada pertencem aos seus detentores; este repositório contém apenas os registros de interações construídos pela equipe.
