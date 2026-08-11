# Contrato de produção — InfoGeo Insper 2026

Documento de referência para quem produz os roteiros. Toda aula deve obedecer a este contrato.
O arquivo `encontro-02.html` é o exemplar canônico: em caso de dúvida sobre estrutura ou tom, copie o que está lá.

---

## 1. Arquivos que cada aula precisa entregar

| Arquivo | Onde | O que é |
|---|---|---|
| `encontro-XX.html` | raiz de `curso/` | O roteiro completo |
| `assets/img/dXX-*.svg` | pasta de imagens | 3 a 5 diagramas conceituais da aula |
| `assets/img/gera_aXX.py` | pasta de imagens | Script que gera os diagramas, importando `_estilo.py` |
| `dados/semanaXX/*.gpkg` | pasta de dados | Pacote de dados funcional, baixável pelo aluno |
| `dados/semanaXX/LEIA-ME.txt` | pasta de dados | Origem, licença, aviso de dado sintético quando for o caso |
| `mapas_conceituais/mapa_conceitual_aulaXX.txt` | pasta própria | Conteúdo para montar o resumo visual |

---

## 2. Estrutura obrigatória do HTML

Copie o esqueleto de `encontro-02.html`. Na ordem:

1. `<head>` com `<link rel="stylesheet" href="assets/curso.css">`
2. `.topbar` com a navegação, marcando `class="here"` no item da aula
3. `.rail` com os 10 temas. A aula atual recebe `class="now"`, as anteriores `class="done"` e viram `<a>`; as posteriores são `<span class="rl locked">`
4. `header.cover` com etiqueta, pergunta do tema em `<h1>`, subtítulo e quatro `.facts`
5. `.shell` contendo `aside.toc` e `main.body`
6. Seção `#antes` — preparação, bloco `.baixar`, e a pergunta do tema em `.pense`
7. `.partmark` Parte 1 · teoria — 40 min
8. Seções de teoria, com pelo menos **3 diagramas** e **3 caixas `.pense`**
9. `.pense` final da teoria com o escopo de prova
10. `.partmark` Parte 2 · roteiro — 45 min
11. De 6 a 9 blocos `.passo`, numerados
12. `.partmark` Parte 3 · exercício — 15 min, com bloco `.exercicio`
13. `.partmark` Parte 4 · fechamento — 20 min: `.resposta`, discussão em `.pense`, `.limites`
14. Seção `#leituras`
15. `nav.nextprev`, `footer.site` e o script do sumário lateral (copie igual)

---

## 3. Componentes disponíveis no CSS

```html
<!-- pergunta norteadora -->
<div class="pense">
  <div class="lbl">Pergunta norteadora</div>
  <p class="q">A pergunta, em itálico serifado.</p>
  <p>A discussão da resposta, quando houver.</p>
</div>

<!-- definição de conceito -->
<div class="conceito">
  <div class="lbl">Definição</div>
  <h4>Nome do conceito</h4>
  <p>Explicação.</p>
</div>

<!-- passo do roteiro -->
<div class="passo" id="pN">
  <div class="n">N</div>
  <div class="c">
    <h3>Título do passo</h3>
    <ol><li>Ação.</li></ol>
  </div>
</div>

<!-- caminho de menu do QGIS -->
<span class="caminho">Vector <i>▸</i> Geoprocessing Tools <i>▸</i> Buffer</span>

<!-- parâmetros de uma janela de ferramenta -->
<div class="params">
  <div class="hd">Nome da janela</div>
  <dl><dt>Campo</dt><dd>valor</dd></dl>
</div>

<!-- expressão -->
<pre class="expr">"campo_a" / "campo_b" * 100   <span class="cm">-- comentário</span></pre>

<!-- ponto de conferência (verde) -->
<div class="confira"><div class="lbl">Confira</div><p>…</p></div>

<!-- erro comum (âmbar) -->
<div class="cuidado"><div class="lbl">Erro comum</div><p>…</p></div>

<!-- nota de contexto (azul) -->
<div class="contexto"><div class="lbl">Rótulo</div><p>…</p></div>

<!-- diagrama conceitual -->
<figure class="diagrama">
  <img src="assets/img/dXX-nome.svg" alt="descrição funcional para leitor de tela">
  <figcaption><b>Figura N</b> Legenda que explica o que ver, não o que está desenhado.</figcaption>
</figure>

<!-- lugar de captura de tela do QGIS, a ser produzida depois -->
<figure class="ph">captura de tela · descrição do que deve aparecer</figure>

<!-- download de dados -->
<div class="baixar">
  <div class="hd"><b>Dados desta aula</b><span>pasta dados/semanaXX</span></div>
  <div class="fonte">Versão oficial: <b>Instituição · Base</b> · <a href="URL">portal</a> ·
    <code>python3 dados/baixar_dados_reais.py --semana N</code></div>
  <ul>
    <li><div><a class="fn" href="dados/semanaXX/arquivo.gpkg" download>arquivo.gpkg</a>
        <span class="fd">O que é, quantas feições, qual CRS.</span></div>
        <span class="tp prov">provisório</span></li>
  </ul>
  <div class="ft">Estado atual do pacote e o que muda depois do downloader.</div>
</div>

<!-- a resposta do tema -->
<div class="resposta">
  <div class="lbl">A resposta do tema</div>
  <p class="big">Frase de resposta.</p>
  <p>Desdobramento.</p>
</div>

<!-- limitações -->
<div class="limites"><div class="lbl">O que esta aula não resolveu</div><ul><li>…</li></ul></div>

<!-- exercício -->
<div class="exercicio">
  <div class="hd"><b>Faça sozinho</b><span>15 minutos</span></div>
  <div class="bd">…</div>
  <div class="entrega"><b>Entrega</b> …</div>
</div>
```

Etiquetas de dado: a maioria dos arquivos não leva nenhuma. Veja a seção 6.3.

---

## 4. Regras de escrita

O texto é auditado contra o guia *Signs of AI writing*. Não use:

- **Vocabulário inflado**: crucial, fundamental (como enfeite), robusto, abrangente, aprimorar, promover, ressaltar, evidenciar, cenário (abstrato), mergulhar, alavancar, tapeçaria, testemunho, no cerne de.
- **Gerúndio pendurado** no fim da frase: "…, garantindo maior precisão", "…, refletindo a importância de".
- **Regra de três** sistemática: toda frase virando tríade de adjetivos.
- **Paralelismo negativo**: "não é apenas X, é Y".
- **Conclusões genéricas**: "Em resumo", "Em conclusão, o futuro é promissor".
- **Negrito em excesso**: no máximo 2 ou 3 por seção, e nunca como rótulo de item de lista.
- **Travessão em excesso**: prefira vírgula, parênteses ou ponto.
- **Emoji**: nenhum. O símbolo `▸` dentro de `.caminho` não conta.
- **Title Case** em títulos: em português, só a primeira letra é maiúscula.

Use, sempre que possível:

- Número concreto e verificável no lugar de adjetivo. "2.394 hectares" vale mais que "uma diferença considerável".
- Nome próprio brasileiro: Corumbá, MATOPIBA, Luís Eduardo Magalhães, Heliópolis, e não "uma região".
- Frases de comprimento variado. Alterne períodos curtos e longos.
- Consequência concreta: quem decide o quê com esse número, e quanto custa errar.
- Admissão de limite. Toda aula fecha dizendo o que não foi resolvido.

**Tom**: professor experiente falando com aluno de graduação inteligente que nunca abriu um SIG.
Direto, específico, sem condescendência e sem entusiasmo de folheto.

### 4.1 Ritmo e retórica (o slop que a lista de palavras não pega)

O sinal de IA mais resistente não é vocabulário, é cadência: todo parágrafo construído
como frase de efeito. Os padrões proibidos, mesmo quando cada palavra é inocente:

- **Aforismo de abertura**: "X não morre por A. Morre por B." / "Isso não é X. É Y."
  Uma construção dessas por aula, no máximo, e de preferência na `.resposta`, onde uma
  frase memorável tem função. No corpo do texto, abra explicando, não sentenciando.
- **Tríade de exemplos paralelos**: "o arquivo que sumiu, a camada que aponta para um
  caminho que não existe mais, a versão final que na verdade era a penúltima". Mesmo
  com exemplos concretos, três cláusulas espelhadas em sequência é assinatura. Use um
  exemplo bem escolhido, ou dois de tamanhos diferentes.
- **Promessa confiante de fechamento**: "A estrutura abaixo resolve isso." Prefira dizer
  o que a estrutura faz e por quê: o mecanismo convence mais que a promessa.
- **Zinger no fim de toda seção**: se cada seção fecha com sentença lapidar, nenhuma
  delas pesa. A maioria das seções deve terminar em informação, não em efeito.
- **Parágrafo de uma frase dramática**. Raro, e só quando o conteúdo justifica.
- **Manchete de listicle em título de seção**: "As seis operações que fazem o resto",
  "Três centros, três perguntas", "X, e por que ele estraga tudo em silêncio". O molde é
  quantificador + substantivo + promessa vaga, ou o par espelhado, ou a vírgula-tease
  (", e por que..."). Título de seção didática nomeia o conteúdo: "Clip, interseção,
  diferença, união e dissolve" informa; "as seis operações que fazem o resto" vende.
  Se o título não deixa claro o que a seção ensina, reescreva o título.

Antes (cadência de IA):
> Projeto de GIS não morre por falta de conhecimento técnico. Morre por desorganização:
> o arquivo que sumiu, a camada que aponta para um caminho que não existe mais, a versão
> final que na verdade era a penúltima. A estrutura abaixo resolve isso e vai valer para
> o semestre inteiro.

Depois (voz de professor):
> Boa parte dos problemas que você vai ter neste semestre não é de QGIS, é de organização
> de arquivo. O projeto .qgz guarda apenas o caminho até cada camada; basta mover uma
> pasta para o mapa abrir vazio no tema seguinte. Monte a estrutura abaixo uma vez e
> repita o padrão em todos os temas.

O critério de revisão: leia a seção em voz alta. Se soar como palestra de encerramento,
reescreva como explicação de aula.

### 4.2 Nomenclatura fixa

- A unidade de conteúdo chama-se **tema**, nunca "semana": `Tema 4`, "a pergunta do tema",
  "a resposta do tema", "no tema 5 você viu", "Próximo tema" na navegação inferior.
- Os dois últimos encontros são de avaliação e não são temas: `Encontro 11` (revisão e prova)
  e `Encontro 12` (banca de projetos).
- Duas exceções mantêm a palavra: as pastas de dado, que continuam `dados/semanaXX/`, e o
  parâmetro do downloader, que continua `--semana N`. Renomear qualquer das duas quebra
  todos os links do material.
- O `footer.site` das aulas leva apenas o nome da disciplina, a instituição e o nome do
  professor. A nota de versão conferida do QGIS existe uma vez, no rodapé do `index.html`,
  e aqui, na seção 8.
- Nada de etiqueta de venda em capa ou hero: sem contagem de encontros, sem carga horária
  como chamada, sem parágrafo dirigido a "alunos que vão trabalhar em". Capa leva duração,
  fontes e área de estudo, que são informação de uso.

---

## 5. Regras dos diagramas

Gere com Python, importando `_estilo.py`, que já traz a paleta e as funções `novo`, `limpa`, `titulo`, `rodape`, `salva`.
Salve sempre em SVG com fundo transparente.

- De 3 a 5 diagramas por aula, todos conceituais. O diagrama deve ensinar algo que o texto sozinho não ensina.
- Nunca decorativo. Se a figura só ilustra, corte.
- Paleta: preto `#14141A` para o correto ou neutro, vermelho `#E50505` para o erro ou o destaque, âmbar para alerta, azul para água e rede, verde para acerto.
- Rótulos em português, com fonte pequena e cinza para o texto de apoio.
- Rodapé com uma frase que diz o que a figura prova.

Diagramas que funcionam bem neste curso: comparação lado a lado do mesmo dado sob duas decisões diferentes,
sequência de etapas com o que se perde em cada uma, e o mesmo resultado sob três valores de parâmetro.

---

## 6. Regras dos dados

Cada aula precisa de um pacote que o aluno baixe e abra sem depender de portal externo.
Todo pacote nasce **provisório** e é trocado depois pelo dado oficial, pelo downloader.

### 6.1 Como produzir o pacote

- Gere com `geopandas` em coordenadas brasileiras reais e plausíveis para a região do caso.
- Grave em **GeoPackage**, UTF-8, com CRS declarado. Nunca Shapefile.
- Nomeie arquivos com sufixo `_treino`. O nome não muda quando o dado vira oficial:
  o HTML e o LEIA-ME apontam para ele, e trocar o nome quebra os dois.
- O nome da camada dentro do GeoPackage também é contrato. Está registrado no
  `CATALOGO` de `dados/baixar_dados_reais.py`.
- Se o roteiro cita um número específico, esse número tem que sair do arquivo entregue.
  Confira rodando.

### 6.2 O downloader

`dados/baixar_dados_reais.py` substitui os pacotes provisórios pelos oficiais na
máquina do professor. Uma função por tema, independentes. Cada uma baixa, recorta
por município ou UF, reprojeta, renomeia o arquivo atual para `*.provisorio.gpkg`
e grava o oficial com o mesmo nome de arquivo e de camada. Nunca apaga.

```
python3 dados/baixar_dados_reais.py --listar      # o que cada tema entrega
python3 dados/baixar_dados_reais.py --conferir    # estado das pastas, sem rede
python3 dados/baixar_dados_reais.py --semana 4
python3 dados/baixar_dados_reais.py --semana todas --forcar
```

Fonte que só entrega por interface (GeoSampa, MapBiomas, TerraBrasilis, DNIT, Infosiga)
não vira download automático: a função imprime instruções manuais numeradas, com URL,
o que clicar, onde salvar e com que nome. Isso conta como entrega.

### 6.3 Etiquetas no bloco `.baixar`

A maioria dos arquivos **não leva etiqueta**. Só há duas exceções:

| Etiqueta | HTML | Quando usar |
|---|---|---|
| provisório | `<span class="tp prov">provisório</span>` | arquivo sintético hoje que **será** trocado pelo oficial |
| didático | `<span class="tp did">didático</span>` | arquivo que existe de propósito e nunca será trocado |

Sem etiqueta: LEIA-ME, arquivos-armadilha e amostras que não existem em portal nenhum.
`<span class="tp real">oficial</span>` continua no CSS para o dia em que a pasta inteira
já estiver trocada.

### 6.4 Linha de procedência

Logo depois do `<div class="hd">` de cada bloco `.baixar`, uma linha `.fonte` diz de onde
vem a versão oficial e qual comando a busca:

```html
<div class="fonte">Versão oficial: <b>IBGE · Malhas Territoriais</b> ·
  <a href="URL">portal</a> · <code>python3 dados/baixar_dados_reais.py --semana 4</code></div>
```

O rodapé `.ft` diz o estado atual do pacote e o que muda depois do downloader. Não fale
em "dados de treino".

### 6.5 Documentação

- `dados/LEIA-ME.txt` explica por que existem pacotes provisórios e como rodar o downloader.
- `dados/semanaXX/LEIA-ME.txt` abre declarando o estado (provisório ou oficial) e como obter
  o oficial; depois vêm as descrições, o dicionário de campos e a lista de números da aula.
- Depois de rodar o downloader, compare a contagem de feições impressa com o número publicado
  no roteiro. O que mudar, corrija no HTML e no LEIA-ME.

---

## 7. Formato do mapa conceitual

Arquivo `mapas_conceituais/mapa_conceitual_aulaXX.txt`, texto puro, sem markdown pesado.
Serve de insumo para o professor montar um resumo visual depois. Estrutura:

```
AULA XX — <pergunta do tema>
UNIDADE TEÓRICA: <nome>

NÓ CENTRAL
  <a ideia única da aula, em uma frase>

RAMOS PRINCIPAIS
  1. <conceito>
     - <subconceito> : <definição em uma linha>
     - <subconceito> : <definição em uma linha>
     LIGA COM: <outro ramo ou outra aula>

CADEIA DE RACIOCÍNIO
  <passo 1> -> <passo 2> -> <passo 3> -> <conclusão>

NÚMEROS-CHAVE
  <valor> : <o que representa>

ERROS QUE O ALUNO COMETE
  <erro> : <por que acontece> : <como corrigir>

VOCABULÁRIO
  <termo pt> = <termo en> : <definição curta>

PERGUNTAS NORTEADORAS
  <as perguntas usadas na aula>

CONEXÕES COM OUTRAS AULAS
  <- vem de: <aula anterior e o que ela deixou pronto>
  -> vai para: <aula seguinte e o que ela vai exigir>

O QUE CAI NA PROVA
  <escopo declarado>
```

---

## 8. Ambiente de referência

QGIS 4.2.0 Belém do Pará, interface em inglês, macOS, **perfil de usuário limpo**: sem plugins
de terceiros e com a lista XYZ Tiles vazia, que é como ela nasce no QGIS 4. A referência é a
instalação que o aluno terá, não a máquina do professor.

Regra que decorre disso: **todo plugin ou conexão externa que uma aula use precisa do passo de
instalação ou de cadastro dentro da própria aula**, com o caminho de menu e o aviso de que exige
internet. Nada no material pode depender de plugin pré-instalado, conexão pré-cadastrada ou
qualquer outro estado do perfil do professor. A conexão OpenStreetMap é cadastrada no passo 5 do
Encontro 1 e as demais aulas apenas a reutilizam, com lembrete de refazer o cadastro se ela sumir.

Identificadores de algoritmo conferidos nessa versão:
`native:reprojectlayer`, `native:buffer`, `native:dissolve`, `native:intersection`,
`native:joinattributestable`, `native:joinattributesbylocation`, `native:meancoordinates`,
`native:zonalstatisticsfb`, `native:dbscanclustering`, `native:kmeansclustering`,
`native:extractbylocation`, `native:countpointsinpolygon`, `native:voronoipolygons`,
`native:serviceareafrompoint`, `native:serviceareafromlayer`, `native:shortestpathpointtopoint`,
`native:reclassifybytable`, `native:rastercalc`, `qgis:heatmapkerneldensityestimation`,
`qgis:minimumboundinggeometry`. O `sdistance:standarddistance`, de plugin, saiu do material: a
aula 7 calcula a distância padrão por expressão no Field Calculator.

Comportamentos verificados na 4.2.0 que valem citar quando for pertinente:

- Projeto novo continua nascendo com elipsoide `None`: `$area` devolve graus quadrados até que o
  elipsoide seja definido em `Project ▸ Properties ▸ General ▸ Measurements`. `area($geometry)`
  ignora o elipsoide e calcula sempre no plano.
- Os valores da aula 2 saem idênticos aos publicados, dígito a dígito: geodésica 303.514,4555 ha;
  em graus 0,2582; UTM 21S 303.289,18; UTM 22S 305.908,87; Policônica 303.794,24; Albers 303.517,67.
- `native:dbscanclustering` continua devolvendo `CLUSTER_ID` nulo para os pontos de ruído (aula 8).
- Nos algoritmos de rede com estratégia *Fastest*, o custo continua em horas (aula 10). O que
  mudou: na 4.2 o cálculo de rede não depende mais do CRS do projeto; o resultado é o mesmo com o
  projeto em EPSG:31983 ou em EPSG:4674. Na série 3.x a medição era feita no CRS do projeto e, em
  graus, errava por um fator de cem mil. A aula 10 registra isso como nota histórica.
