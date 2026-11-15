# Contador de cromossomos

Ferramenta para **contar cromossomos em fotos de metáfases** marcando cada cromossomo com um traço. O contador soma as marcas, grava a foto marcada (com cada cromossomo numerado) e monta uma planilha com uma linha por célula. No **modo às cegas**, as fotos aparecem embaralhadas e sem nome, para que quem conta não saiba de qual planta ou lâmina é a célula.

É um único arquivo HTML: não precisa instalar nada e funciona sem internet. As fotos e os resultados ficam na pasta do seu computador e **não são enviados para nenhum servidor**, nem quando o contador é aberto pelo link.

**Abrir o contador:** https://joaopedrobsr.github.io/contador-cromossomos/

---

## Sumário

1. [Requisitos](#requisitos)
2. [Como abrir](#como-abrir)
3. [Como usar, passo a passo](#como-usar-passo-a-passo)
4. [Como marcar](#como-marcar)
5. [Classificação de qualidade](#classificação-de-qualidade)
6. [Arquivos gerados](#arquivos-gerados)
7. [Atalhos de teclado](#atalhos-de-teclado)
8. [Problemas comuns](#problemas-comuns)
9. [Origem e como citar](#origem-e-como-citar)
10. [Licença](#licença)

## Requisitos

- Computador com **Google Chrome** ou **Microsoft Edge** (Windows, macOS ou Linux).
- Firefox, Safari e navegadores de celular **não funcionam**, porque não permitem que uma página grave arquivos numa pasta do computador.
- Fotos em JPG, PNG, BMP, WEBP ou TIFF (o TIFF depende do navegador; se não abrir, converta para JPG ou PNG).

## Como abrir

Há dois jeitos, com o mesmo resultado:

- **Pelo link:** abra o endereço acima no Chrome ou no Edge.
- **Baixando o arquivo:** baixe o [`index.html`](index.html) (botão *Download raw file* na página do arquivo), salve no computador e abra com dois cliques no Chrome ou no Edge. Assim funciona também sem internet.

## Como usar, passo a passo

1. **Organize as fotos numa pasta.** Elas podem estar soltas ou em subpastas, por exemplo uma subpasta por planta ou por lâmina. O nome da subpasta vai para a coluna *Subpasta* da planilha.
2. **Escolha a pasta.** Clique em *Escolher pasta…* e selecione a pasta das fotos. O navegador pede permissão para ver e editar a pasta: aceite. O contador só **lê** as fotos e cria uma pasta nova, `Contador - resultados`, onde grava tudo. As fotos originais não são alteradas.
3. **Defina a sessão.**
   - *Modo às cegas* (recomendado para contagem e recontagem): embaralha a ordem e esconde o nome das fotos. Os nomes voltam na planilha.
   - *Deixar de fora:* termos separados por vírgula (por exemplo `_copia, Outros`). Fotos ou subpastas com esses termos no nome não entram na sessão.
4. **Clique em *Começar*.** A primeira foto abre ajustada à tela.
5. **Marque e salve.** Marque cada cromossomo, preencha a classificação da célula e pressione `Enter`. A foto marcada é gravada e a próxima abre.
6. **Pare quando quiser.** As marcas vão sendo guardadas como rascunho a cada poucos segundos. Para continuar outro dia, abra o contador e clique em *Continuar com esta pasta* (ou escolha a mesma pasta de novo).

As opções da sessão valem até o fim. Para começar uma contagem nova do zero com as mesmas fotos (por exemplo, uma segunda pessoa contando às cegas), renomeie ou mova a pasta `Contador - resultados` antes.

O mesmo guia, com mais detalhes, está dentro do contador, no botão **Guia** (ou tecla `?`).

## Como marcar

| Ação | Como fazer |
| :-- | :-- |
| Marcar um cromossomo | arrastar por cima dele, de uma ponta à outra, ou só clicar. Cada marca conta 1 e recebe um número |
| Marcar uma dúvida | segurar `Shift` ao marcar, ou ligar a ferramenta *Dúvida* (`D`). Fica em laranja e é somada à parte |
| Apagar uma marca | botão direito sobre ela. `Ctrl`+`Z` desfaz |
| Outra célula na mesma foto | *+ célula* ou `C`. Cada célula tem cor, contagem e classificação próprias e vira uma linha da planilha |
| Foto sem célula contável | *Descartar foto*, com o motivo. Ela entra na planilha como descartada |
| Conferir a imagem | segurar `H` esconde as marcas; `N` esconde só os números |

**Dúvidas** servem para o que não dá para decidir na foto (dois cromossomos encostados, um possível fragmento). A planilha traz o **n** (marcas normais), as **dúvidas** e o **n máximo** (n + dúvidas), assim a incerteza da contagem fica registrada em vez de escondida.

Brilho, contraste e saturação ajudam a enxergar, mas mudam só a tela: a foto salva sai sempre com as cores originais.

## Classificação de qualidade

Cada célula é classificada em cinco critérios. Com os cinco preenchidos, o contador calcula a qualidade da célula.

| Critério | Opções | O que avaliar |
| :-- | :-- | :-- |
| Espalhamento | Bom, Regular, Ruim | se os cromossomos estão bem separados |
| Sobreposição | Nenhuma, Pouca, Muita | quantos cromossomos se cruzam ou se encostam |
| Célula inteira | Sim, Não, ? | se a célula está completa na foto |
| Fase | Metáfase, Prometáfase, Outra, ? | a fase da divisão |
| Foco | Bom, Ruim | se a nitidez permite separar os cromossomos |

| Qualidade | Regra |
| :-- | :-- |
| **Descartar** | sobreposição Muita **ou** célula inteira Não |
| **Boa** | espalhamento Bom, sobreposição Nenhuma ou Pouca, célula inteira Sim, fase Metáfase **e** foco Bom |
| **Regular** | todos os outros casos |

Se algum critério ficar em branco, a célula é salva, mas a qualidade fica vazia na planilha.

## Arquivos gerados

Tudo fica em `Contador - resultados/`, dentro da pasta escolhida:

| Arquivo | Conteúdo |
| :-- | :-- |
| `contagens.csv` | a planilha, uma linha por célula. Abre direto no Excel (separador ponto e vírgula, acentos em UTF-8) |
| `Imagens marcadas/` | cada foto inteira com as marcas numeradas e uma faixa branca no topo com o nome da foto e o total |
| `Recortes ampliados/` | só a região marcada, ampliada; boa para figuras e para conferência |
| `sessao.json` | tudo o que foi marcado (inclusive rascunhos e a ordem embaralhada). É o que permite continuar a sessão e regravar a planilha. Não apague nem edite |

Os arquivos de imagem levam o nome da subpasta antes do nome da foto (por exemplo `Planta 31 - 31-1.1_contagem.jpg`), para que fotos com o mesmo nome em subpastas diferentes não se sobrescrevam.

**Colunas da planilha**

| Coluna | Conteúdo |
| :-- | :-- |
| Ordem de exibição | posição da foto na sessão (no modo às cegas, a ordem embaralhada) |
| Foto | nome do arquivo, sem extensão |
| Subpasta | subpasta onde a foto está |
| Célula | `1`, ou `a`, `b`, `c`… quando há mais de uma célula na foto |
| n (cromossomos) | marcas normais |
| Dúvidas | marcas de dúvida |
| n máximo (n + dúvidas) | soma das duas |
| Espalhamento, Sobreposição, Célula inteira, Fase, Foco | a classificação |
| Qualidade | Boa, Regular ou Descartar |
| Observações | texto livre, ou o motivo do descarte |
| Situação | Contada ou Descartada |
| Salva em | data e hora |
| Arquivo marcado | nome da foto marcada gerada |
| Caminho | caminho da foto original dentro da pasta escolhida |

## Atalhos de teclado

| Tecla | Ação |
| :-- | :-- |
| `Enter` | salvar e ir para a próxima (nas Observações, `Shift`+`Enter` pula linha) |
| `Shift` + arrastar, `D` | marcar dúvida |
| `Ctrl`+`Z` | desfazer |
| roda do mouse, `+`, `-` | zoom |
| `Espaço` + arrastar, botão do meio | mover a foto |
| `F` | ajustar à tela |
| `[` `]` | espessura da linha |
| segurar `H` | esconder as marcas |
| `N` | mostrar ou esconder os números (só na tela) |
| `C`, `1` a `4` | nova célula, trocar de célula |
| `←` `→` | foto anterior ou próxima, sem salvar (as marcas viram rascunho) |
| `?` | abrir o guia de atalhos |

## Problemas comuns

- **“Este navegador não consegue abrir pastas”**: use o Chrome ou o Edge num computador.
- **A planilha não foi gravada**: ela provavelmente está aberta no Excel, que trava o arquivo. Os dados estão seguros na sessão: feche a planilha e clique em *Regravar planilha*.
- **Quero recomeçar do zero**: renomeie ou mova a pasta `Contador - resultados`.
- **Acrescentei fotos depois de começar**: elas entram automaticamente no fim da fila na próxima vez que a pasta for aberta.
- **O botão *Continuar com esta pasta* não aparece**: o navegador esqueceu a pasta (por exemplo, depois de limpar os dados de navegação). Use *Escolher pasta…* e selecione a mesma pasta; a sessão continua.

## Origem e como citar

O contador foi criado por João Pedro Reis para a recontagem às cegas de metáfases de jabuticabeiras (*Plinia* spp.) no seu Trabalho de Conclusão de Curso, apresentado à Universidade Estadual de Goiás em 2026. A versão usada no trabalho tinha, além do que está aqui, a lista fixa das fotos daquele estudo e a origem de cada planta; elas foram retiradas para que o contador sirva a qualquer conjunto de fotos. A forma de marcar, contar, classificar e gravar é a mesma.

Para citar (ABNT):

> REIS, João Pedro. **Contador de cromossomos**. Versão 1.0. 2026. Disponível em: https://github.com/joaopedrobsr/contador-cromossomos. Acesso em: dia mês ano.

## Licença

[MIT](LICENSE): pode usar, copiar, modificar e distribuir, mantendo o aviso de autoria.

---

### In English

A single-file, offline browser tool for counting chromosomes in metaphase photos. Draw a stroke over each chromosome; the tool numbers the marks, saves an annotated copy of the photo and writes a CSV with one row per cell. A blind mode shuffles and hides file names. Runs in Chrome or Edge (it uses the File System Access API); photos never leave your computer. The interface is in Portuguese. MIT licence.
