# Everything - file search and indexer (gratuito)

Everything é um indexer/searcher de arquivos (gráfico). O programa indexa todos os nomes (e seus atributos) de arquivos e diretórios em poucos minutos, sem causar lentidão no sistema durante o processo. Após a indexação inicial ele continua a indexar em background, [e é tão leve que você nem sente](https://www.voidtools.com/faq/#does_everything_hog_my_system_resources).

As vantagens desse buscador é que após a indexação a pesquisa ou filtragem por qualquer arquivo ou diretório no seu sistema é instantânea, não importa quantos arquivos são retornados pela busca. Por exemplo, eu tenho no meu HD quase 2 milhões de arquivos e levou menos de 3 minutos para indexar tudo. Pesquisar, filtrar e ordenar é um procedimento instantâneo para o programa.

Já utilizei outros indexadores e search tools antes, mas Everything é de longe a ferramenta mais impressionante nesta categoria.

**Download:** https://www.voidtools.com

![Everything main screen](https://res.cloudinary.com/llagerlof/image/upload/v1543322783/github/Everything.Search.Window.png)

## Exemplos

Após a indexação que leva de 1 a 2 minutos na maioria dos sistemas, você poderá começar a fazer suas pesquisas.

Por padrão a tela inicial do aplicativo lista todos os arquivos do seu HD.

#### Pesquisar todos os nomes de arquivos e diretórios contendo "foto"

```foto```

#### Todos os arquivos com "foto" em seu nome e com extensão .jpg

```foto .jpg```

#### Todos os arquivos com "foto", com extensão .jpg e com mais de 1 MB

```foto .jpg size:>1MB```

#### Todos os arquivos contendo "index.htm"

```index.htm```

#### Todos os arquivos chamados exatamente "index.htm"

```wfn:index.htm```

#### Todos os arquivos .mp4 com mais de 1 GB

```.mp4 size:>1GB```

#### Todos os arquivos .txt com exatamente 1024 bytes

```.txt size:1024```

#### Arquivos .txt dentro do diretório do Windows com exatamente 3307 bytes

```\windows .txt size:3307```

#### Diretórios com a palavra "win" no nome

```win folder:```

#### Arquivos com a palavra "win" no nome

```win !folder:```

#### Diretórios vazios

```empty:```

obs: Não é necessário usar ```folder: empty:``` neste caso. o ```empty:``` vale somente para diretórios.

#### Arquivos vazios

```size:0```

#### Diretórios que contém exatamente 50 arquivos dentro, no primeiro nível (não conta os subdiretórios)

```childfilecount:50```

#### Diretórios que contém arquivos que batem com o critério pesquisado (por exemplo, encontrar os diretórios contendo algum arquivo ou subdiretório "teste")

```child:teste```

## Dicas

 - Ordene a sua listagem clicando na coluna Size.
 - Ordene por Date Modified, sem filtro, e você verá quais arquivos estão sendo criados e atualizados em tempo real.
 - O programa possui muitas outras [opções de busca e configurações para todos os gostos](https://www.voidtools.com/support/everything/searching/).
 
---

*keywords: file, search, indexer, index, windows, filter, pesquisa, pesquisar, arquivos, hd*

*references:*

*https://www.voidtools.com/support/everything/searching/*
