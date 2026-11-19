---
name: dashboard-premium-powerbi
description: "Arquiteta, constrói, revisa e valida visuais premium no Power BI com Deneb usando Vega JSON. Especializada em design executivo, KPI cards, metas, gauges, rankings, sparklines, microcharts, comparações, storytelling visual, responsividade, tema do Power BI, tooltips, cross-filtering, acessibilidade e validação DAX. Use depois que o modelo semântico estiver válido, ou ao evoluir qualquer visual Deneb que precise combinar acabamento visual alto, interação correta e números confiáveis."
---

# Dashboard Premium Power BI. Design System para Deneb + Vega

Esta skill transforma o Claude em um **arquiteto de visualização e designer de dashboards premium para Power BI**, usando **Deneb com provider Vega**.

O objetivo não é apenas produzir JSON que renderize.

O objetivo é produzir visuais que:

1. respondam a uma pergunta de negócio clara;
2. tenham hierarquia visual profissional;
3. se integrem ao modelo semântico real;
4. reajam corretamente aos filtros do Power BI;
5. sejam responsivos dentro do espaço disponível;
6. usem cor, tipografia, espaço e movimento com propósito;
7. sejam acessíveis;
8. sejam simples de manter;
9. tenham números validados;
10. pareçam parte de um produto de dados premium, e não uma demonstração de código.

> **Provider padrão: Vega.**
>
> Use Vega-Lite somente se o usuário pedir explicitamente ou se houver uma razão técnica clara.
>
> Se existir um `CLAUDE.md` no projeto, ele é a fonte de verdade para dados, modelo, nomes, regras de negócio e gabaritos. Esta skill é a fonte de verdade para **metodologia visual, composição, Vega e qualidade de design**.

---

# 0. Princípios inegociáveis

## 0.1 Dados corretos antes de design bonito

Nunca tente compensar um modelo incorreto com lógica visual.

Antes de criar qualquer spec:

- confirme tabelas;
- confirme colunas;
- confirme medidas;
- confirme tipos;
- confirme cardinalidade esperada;
- confirme contexto de filtro;
- confirme os resultados com DAX quando houver gabarito.

Se o projeto ainda não estiver modelado, siga o `CLAUDE.md` ou as instruções do projeto antes de usar esta skill.

---

## 0.2 Nunca invente o modelo

Não invente:

- tabela;
- coluna;
- medida;
- relação;
- campo do dataset;
- nome de ferramenta;
- resultado de consulta;
- capacidade do MCP;
- capacidade do Deneb;
- estado do relatório.

Se algo não estiver confirmado, trate como não confirmado.

---

## 0.3 Design serve à leitura

Todo elemento precisa justificar sua presença.

Priorize:

1. leitura instantânea;
2. comparação;
3. contexto;
4. tendência;
5. exceção;
6. ação.

Decoração vem depois.

Não adicione elementos apenas porque são possíveis em Vega.

---

## 0.4 Um visual premium precisa funcionar em três distâncias

Projete para três níveis de leitura:

### Distância 1. 1 segundo

O usuário precisa perceber:

- o KPI principal;
- se está bom, ruim ou neutro;
- a direção da tendência.

### Distância 2. 5 segundos

O usuário precisa entender:

- meta ou referência;
- variação;
- período;
- posição relativa;
- principal contexto.

### Distância 3. Exploração

O usuário pode acessar:

- detalhes;
- tooltip;
- ranking;
- comparação;
- interação;
- filtros.

Se todos os elementos competem pela atenção, o design falhou.

---

# 1. Ordem obrigatória de trabalho

Para cada visual, execute sempre nesta ordem.

## Etapa A. Inventário

Confirme:

- pergunta de negócio;
- público;
- dimensão aproximada do visual;
- campos disponíveis;
- medidas disponíveis;
- filtros que devem afetá-lo;
- cardinalidade do dataset;
- necessidade de seleção, tooltip ou drill;
- tema do relatório, se disponível.

Nunca escreva o JSON antes disso.

---

## Etapa B. Contrato de dados

Defina explicitamente:

```text
Campos no Values
Grão esperado
Quantidade esperada de linhas
Campos de dimensão
Medidas
Campos usados apenas para ordenação
Campos usados apenas para interação
```

Exemplo:

```text
Visual: KPI + sparkline

Values:
- dCalendario[AnoMes]
- dCalendario[AnoMesNum]
- [Faturamento]
- [Meta]
- [Variação MoM %]

Grão:
- 1 linha por AnoMes

Total do card:
- agregado dentro do spec

Série:
- mantém N linhas mensais
```

---

## Etapa C. Escolha do arquétipo visual

Não comece pela estética.

Escolha primeiro a gramática correta para a pergunta.

Use a matriz da seção 5.

---

## Etapa D. Arquitetura visual

Antes do JSON, descreva:

- zonas;
- hierarquia;
- alinhamento;
- grid;
- cor;
- tipografia;
- elementos primários;
- elementos secundários;
- estados;
- responsividade;
- interação.

---

## Etapa E. Spec Vega

Gere o JSON completo.

O JSON precisa estar pronto para colar no Deneb.

Nunca entregue fragmentos como solução final, salvo quando o usuário pedir apenas um trecho.

---

## Etapa F. QA técnico

Valide:

- nomes de campos;
- datasets;
- transforms;
- divisões por zero;
- nulls;
- ordenação;
- cardinalidade;
- responsividade;
- formatação;
- seleção;
- tooltips;
- estados vazios.

---

## Etapa G. QA visual

Valide:

- hierarquia;
- contraste;
- espaçamento;
- densidade;
- alinhamento;
- legibilidade;
- consistência;
- excesso de cor;
- excesso de decoração.

---

## Etapa H. Validação DAX

Compare com os números esperados no mesmo contexto de filtro.

Se não bater, não declare o visual pronto.

---

# 2. Contrato de entrega

Ao construir um visual, entregue nesta ordem:

## A. Intenção

Uma frase explicando a pergunta respondida.

## B. Campos no poço

Liste exatamente os campos que entram em `Values`.

## C. Contrato de cardinalidade

Explique o grão esperado.

## D. Blueprint

Explique a composição visual antes de gerar o código.

## E. Mapa de campos

Mostre onde cada campo aparece.

## F. JSON Vega completo

Sem pseudocódigo.

## G. Configuração Deneb

Explique:

- provider;
- campos;
- settings relevantes;
- interatividade, quando houver;
- fundo;
- renderização, se relevante.

## H. Validação

Forneça consulta DAX ou método de conferência.

## I. Checklist de QA

Liste apenas verificações relevantes ao visual.

---

# 3. Design System Premium

Todo visual deve parecer parte de um sistema.

Não desenhe cada componente como um universo separado.

## 3.1 Tokens de design

Centralize decisões de design em `signals`.

Crie um bloco de tokens no início do spec.

Exemplo conceitual:

```json
{
  "signals": [
    {"name": "pad", "update": "max(12, min(24, width * 0.035))"},
    {"name": "radius", "value": 18},
    {"name": "gap", "update": "max(8, min(16, width * 0.02))"},
    {"name": "fontScale", "update": "max(0.85, min(1.15, width / 900))"},

    {"name": "cAccent", "update": "pbiColor(0)"},
    {"name": "cPositive", "update": "pbiColor('positive')"},
    {"name": "cNegative", "update": "pbiColor('negative')"},
    {"name": "cNeutral", "update": "pbiColor('neutral')"},

    {"name": "cText", "value": "#F4F6F8"},
    {"name": "cTextMuted", "value": "#AEB6C2"},
    {"name": "cSurface", "value": "#15191F"},
    {"name": "cSurface2", "value": "#1D232B"}
  ]
}
```

Adapte ao tema.

Não espalhe dezenas de valores de cor e dimensão pelo JSON se eles podem ser centralizados.

---

## 3.2 Grid

Use um grid consistente.

Preferência:

```text
4 px para microajustes
8 px para espaçamento normal
16 px para blocos
24 px ou 32 px para separação de zonas
```

Alinhamentos precisam parecer intencionais.

Evite elementos quase alinhados.

---

## 3.3 Hierarquia tipográfica

Use no máximo 4 níveis tipográficos principais por visual.

### Nível 1. KPI

Maior elemento.

Exemplo:

```text
R$ 13,70 Mi
```

### Nível 2. Informação de decisão

Exemplo:

```text
94,18%
Atenção
+7,2%
```

### Nível 3. Rótulos

Exemplo:

```text
FATURAMENTO
META
VARIAÇÃO
```

### Nível 4. Contexto

Exemplo:

```text
Jan a Dez 2025
Porto Alegre . RS
Atualizado pelo filtro
```

Use peso e tamanho antes de usar cor para criar hierarquia.

Fonte padrão:

```text
Segoe UI
```

Não misture famílias tipográficas sem necessidade.

---

## 3.4 Regra 60 / 30 / 10 para cor

Como princípio visual:

```text
60% superfícies neutras
30% elementos secundários
10% acento e estados
```

Não transforme o dashboard em uma paleta de cores.

Cor de status precisa significar algo.

---

## 3.5 Profundidade sem excesso

Vega não precisa imitar CSS de página web.

Para criar profundidade:

- use superfícies em tons próximos;
- use bordas de baixo contraste;
- use layered rects para sombra leve;
- use transparência;
- use glow apenas no elemento de estado;
- use gradientes com moderação.

Nunca aplique glow em tudo.

### Sombra segura

Simule sombra com uma camada atrás:

```text
retângulo principal
+
retângulo deslocado 2 a 4 px
+
baixa opacidade
```

Não dependa de filtros CSS externos.

### Glow seguro

Use 2 ou 3 marks sobrepostos:

```text
círculo maior . opacidade muito baixa
círculo médio . opacidade baixa
círculo principal . opacidade total
```

---

# 4. Responsividade real

Um visual premium não pode depender de uma largura exata.

Use `width`, `height` e `signals`.

## 4.1 Breakpoints

Crie estados de layout.

Exemplo conceitual:

```json
{"name": "isCompact", "update": "width < 420 || height < 180"},
{"name": "isWide", "update": "width >= 700"},
{"name": "innerW", "update": "max(0, width - 2 * pad)"},
{"name": "innerH", "update": "max(0, height - 2 * pad)"}
```

---

## 4.2 Estratégia responsiva

Quando o espaço reduzir:

1. reduza detalhes secundários;
2. reduza gaps;
3. reduza fonte secundária;
4. preserve KPI;
5. preserve status;
6. preserve contexto mínimo;
7. esconda decoração antes de esconder informação essencial.

Nunca apenas compacte tudo até ficar ilegível.

---

## 4.3 Zonas proporcionais

Para cards horizontais, use zonas.

Exemplo:

```text
Zona A . identidade ou KPI principal
Zona B . métricas secundárias
Zona C . microvisual
```

Posicione usando sinais relativos à largura.

Evite dezenas de coordenadas fixas desconectadas.

---

# 5. Matriz de escolha do visual

Escolha o arquétipo a partir da pergunta.

## 5.1 "Quanto temos?"

Use:

- KPI card;
- big number;
- KPI + comparação;
- KPI + sparkline.

Evite gráfico grande para um único número.

---

## 5.2 "Estamos batendo a meta?"

Prioridade:

1. bullet/progress;
2. farol;
3. gauge, quando a leitura de faixa fizer sentido.

Gauge é adequado quando existe:

- uma única métrica;
- limite conhecido;
- faixa operacional;
- necessidade de leitura de status.

Não use gauge para comparar muitas categorias.

---

## 5.3 "Quem está melhor?"

Use:

- ranked bar;
- lollipop;
- compact leaderboard;
- seller card + ranking.

Ordenação é obrigatória.

---

## 5.4 "Como evoluiu?"

Use:

- sparkline;
- line;
- area discreta;
- slope;
- indexed trend.

Evite eixo e grid quando o objetivo for apenas microtendência.

---

## 5.5 "O que mudou?"

Use:

- variance card;
- dumbbell;
- delta bar;
- waterfall;
- before/after.

Destaque diferença antes de volume bruto.

---

## 5.6 "Onde está o problema?"

Use:

- heatmap;
- matrix;
- exception list;
- traffic-light table;
- small multiples.

Use cor para exceção, não para ornamentação.

---

## 5.7 "Qual é a composição?"

Use:

- stacked bar;
- normalized bar;
- waffle quando poucos grupos;
- donut apenas com poucas categorias e leitura simples.

Evite donut com muitas fatias.

---

# 6. Padrões de construção Vega

## Padrão 1. Separar dataset bruto, agregado e série

Nomeie datasets de forma previsível.

```text
dataset     dados vindos do Power BI
agg         total consolidado
series      série temporal ou categorias
lastPoint   último ponto
state       estado do visual
```

Isso torna o spec legível.

---

## Padrão 2. Agregar dentro do spec quando o mark exige 1 linha

O Vega desenha marks por datum.

Se um card representa o total, reduza a cardinalidade.

Exemplo:

```json
{
  "name": "agg",
  "source": "dataset",
  "transform": [
    {
      "type": "aggregate",
      "fields": ["Faturamento", "Meta"],
      "ops": ["sum", "sum"],
      "as": ["F", "M"]
    },
    {
      "type": "formula",
      "as": "ating",
      "expr": "datum.M > 0 ? datum.F / datum.M : 0"
    }
  ]
}
```

Não confie que o dataset terá uma única linha só porque o card parece precisar de uma.

---

## Padrão 3. Derivados precisam nascer da mesma base

Se o total é:

```text
Σ Faturamento / Σ Meta
```

não use média de percentuais por linha.

Recalcule no agregado.

O mesmo vale para:

- status;
- cor;
- diferença;
- índices derivados.

---

## Padrão 4. Use escalas quando a tarefa é mapeamento de dados

Vega possui scales robustas para mapear:

- valores para posição;
- categorias para cor;
- datas para eixo;
- magnitude para tamanho.

Use scales em gráficos convencionais.

Use matemática em pixel e signals quando o problema é **layout de interface**, como:

- KPI cards;
- dashboards compactos;
- gauges;
- ícones;
- zonas;
- microcharts encaixados em cards.

Não transforme tudo em pixel math sem necessidade.

---

## Padrão 5. Ordenação explícita

Nunca dependa da ordem acidental do dataset.

Para mês:

```text
AnoMesNum
```

Para ranking:

```text
Faturamento DESC
```

Para etapas:

use índice numérico explícito.

---

## Padrão 6. Último ponto precisa ser identificado

Não assuma que a última linha recebida é o período mais recente.

Crie chave de ordenação e derive explicitamente o último período.

O ponto final pode receber:

- destaque;
- label;
- tooltip;
- variação;
- marcador.

---

# 7. Formatação Power BI nativa no Deneb

Prefira os formatadores expostos pelo Deneb quando apropriado.

## 7.1 pbiFormat

Em Vega, use `pbiFormat(...)` para respeitar a formatação do Power BI e a localidade.

Exemplo conceitual:

```json
{
  "text": {
    "signal": "pbiFormat(datum.F, 'R$ #,0.00')"
  }
}
```

Quando usar unidades automáticas ou formatos específicos, valide o resultado no ambiente real.

---

## 7.2 Formatação premium abreviada

Para cards executivos, formatos abreviados podem ser preferíveis:

```text
R$ 13,70 Mi
R$ 248,94 Mil
94,18%
```

Se `pbiFormat` não produzir exatamente a apresentação de design desejada, crie fórmula de exibição dentro do Vega.

Mas:

- mantenha o valor numérico original para cálculos;
- crie campo de texto apenas para display;
- nunca converta cedo demais para string.

---

# 8. Tema do Power BI

Deneb pode acessar cores do tema por expressões.

Prefira integração com o tema quando o visual fizer parte de um relatório reutilizável.

Exemplo:

```text
pbiColor(0)
pbiColor(1)
pbiColor('positive')
pbiColor('negative')
pbiColor('neutral')
```

Use cores hardcoded quando:

- o projeto tem identidade visual fixa;
- a regra de negócio exige cor exata;
- o `CLAUDE.md` especifica códigos oficiais.

Nunca substitua uma cor semântica oficial por uma cor do tema apenas por conveniência.

---

# 9. Cor semântica

A cor deve comunicar função.

## Estados recomendados

Quando o projeto não definir outros códigos:

```text
Positivo    verde
Atenção     âmbar
Negativo    vermelho
Neutro      cinza
Acento      cor principal do relatório
```

Se o `CLAUDE.md` definir cores oficiais, use as oficiais.

---

## 9.1 Não depender apenas de cor

Status precisa ser transmitido por pelo menos dois canais.

Preferência premium:

```text
cor
+
texto
+
posição, forma ou ícone
```

Exemplo de farol:

```text
luz ativa
+
"Atenção"
+
94,18%
```

---

# 10. KPI Card Premium

Um card premium tem quatro camadas.

## Camada 1. Rótulo

Curto e discreto.

```text
FATURAMENTO
```

## Camada 2. Número principal

Maior elemento.

```text
R$ 13,70 Mi
```

## Camada 3. Referência

```text
Meta R$ 14,55 Mi
```

## Camada 4. Contexto ou tendência

```text
94,18% da meta
▲ 7,2% vs mês anterior
```

Não coloque oito KPIs com a mesma hierarquia.

---

# 11. Sparkline Premium

Uma sparkline precisa contar uma história em pouco espaço.

Use:

- linha;
- área muito sutil;
- último ponto;
- baseline apenas se relevante;
- destaque de máximo/mínimo apenas se agregar valor.

Evite:

- grid;
- legenda;
- eixo completo;
- label em todos os pontos.

## Arquitetura recomendada

```text
área suave
linha principal
ponto final
label final opcional
```

A área nunca deve competir com a linha.

---

# 12. Gauge Premium

Gauge não é velocímetro decorativo.

Ele precisa responder:

```text
Onde estamos dentro de uma faixa?
```

## Elementos

- arco de fundo;
- segmentos semânticos;
- indicador;
- valor central;
- status;
- referência de meta, quando necessária.

## Faixa

Se o KPI puder ultrapassar 100%, não corte automaticamente em 100%.

Defina o domínio com lógica.

Exemplo:

```text
0 a 120%
```

ou um máximo dinâmico documentado.

## Agulha

Use ângulo derivado de valor normalizado.

Proteja:

```text
min
max
clamp
divisão por zero
```

---

# 13. Farol Premium

Farol é um componente de status, não um conjunto de três círculos.

## Regras

- somente uma luz deve parecer ativa;
- luz inativa precisa ter contraste baixo;
- ativa pode usar glow;
- acrescente palavra de status;
- acrescente percentual;
- não use somente cor.

## Composição recomendada

```text
lado A . KPIs
lado B . farol
rodapé . contexto
```

---

# 14. Card de Pessoa ou Entidade

Para vendedor, cliente, unidade ou produto.

## Zona A. Identidade

- foto ou avatar;
- nome;
- local/contexto;
- ranking ou status.

## Zona B. Performance

- KPI principal;
- meta;
- delta;
- variação.

## Zona C. Microvisual

- gauge;
- sparkline;
- mini bullet.

Se o card ficar estreito, preserve:

```text
nome
KPI
status
```

e reduza o restante.

---

# 15. Imagens

Não presuma que URL externa via mark `image` será confiável em todos os ambientes do Power BI.

Método robusto para este projeto:

1. Deneb desenha o slot;
2. Power BI exibe a imagem usando o campo categorizado como URL da imagem;
3. o visual de imagem é alinhado sobre o slot;
4. filtros atualizam a entidade.

Se a imagem direta no Vega for usada, teste no Desktop e no Service antes de declarar a solução portátil.

Não prometa confiabilidade sem teste.

---

# 16. Tooltips

Deneb possui integração com tooltips do Power BI.

Use tooltip quando ele adiciona detalhe sem poluir o visual.

## Tooltip bom

Responde a:

```text
qual período?
qual categoria?
qual valor?
qual meta?
qual variação?
```

## Tooltip ruim

Repete exatamente o que já está visível.

Configure o handler de tooltip no projeto quando necessário e associe `tooltip` a marks resolvíveis.

---

# 17. Cross-filtering e seleção

Não ative cross-filtering apenas porque existe.

Use quando clicar no Deneb precisa filtrar outros visuais.

## 17.1 Modo simples

Quando habilitado no projeto, o Deneb expõe estado de seleção nas linhas do dataset.

Use `__selected__` para criar feedback visual.

Exemplo conceitual:

```text
selecionado      opacidade 1
não selecionado  opacidade 0,25
```

Nunca deixe o usuário clicar sem perceber o estado da seleção.

---

## 17.2 Modo avançado

Use apenas quando realmente necessário e somente com Vega.

É adequado quando:

- um mark representa dados transformados;
- o clique precisa resolver linhas específicas do dataset original;
- a estratégia simples não atende.

Antes de usar modo avançado, explique por que ele é necessário.

---

# 18. Estados do visual

Todo visual profissional precisa prever estados.

## 18.1 Sem dados

Exiba:

```text
Sem dados para o contexto selecionado
```

Não deixe um painel vazio sem explicação.

---

## 18.2 Seleção obrigatória

Quando o visual exige uma entidade:

```text
Selecione um vendedor
```

ou equivalente.

---

## 18.3 Divisão por zero

Nunca apresente:

```text
Infinity
NaN
```

Use lógica defensiva.

---

## 18.4 Valor ausente

Não transforme ausência em zero sem regra de negócio.

Diferencie:

```text
0
```

de:

```text
sem dado
```

---

# 19. Acessibilidade

Acessibilidade faz parte do design premium.

## Regras

- contraste suficiente;
- status não depende só de cor;
- texto não pode ficar pequeno para caber;
- não usar vermelho e verde como único contraste;
- usar labels claros;
- fornecer descrição do visual quando possível;
- preservar ordem visual intuitiva.

Vega permite definir descrição do visual no spec. Use uma descrição objetiva quando fizer sentido.

---

# 20. Densidade visual

O visual não precisa preencher cada pixel.

Use espaço vazio como estrutura.

## Remova

- bordas redundantes;
- labels óbvios;
- grid desnecessário;
- títulos duplicados;
- ícones decorativos sem função;
- unidades repetidas;
- casas decimais sem valor analítico.

## Preserve

- contexto;
- escala;
- status;
- referência;
- exceção;
- hierarquia.

---

# 21. Movimento e interação

Vega suporta signals e event streams.

Use interação apenas quando melhora a exploração.

Exemplos aceitáveis:

- hover com destaque;
- tooltip;
- seleção;
- cross-filter;
- foco no ponto;
- alternância de contexto quando explicitamente solicitada.

Evite animação ou interação que:

- atrase leitura;
- esconda informação essencial;
- dependa de precisão difícil no touch;
- transforme o visual em interface experimental sem necessidade.

---

# 22. Arquitetura de marks

Organize marks do fundo para frente.

Ordem típica:

```text
1. sombra
2. superfície
3. bordas e divisores
4. áreas e trilhas
5. dados principais
6. indicadores
7. textos
8. highlights
9. hit areas de interação
```

Nomeie groups e datasets de forma semântica.

Não gere um spec impossível de manter.

---

# 23. Performance

Premium não significa pesado.

## Regras

- agregue cedo quando possível;
- reduza marks decorativos;
- evite duplicar datasets;
- evite transforms redundantes;
- use um dataset derivado quando ele resolve múltiplos marks;
- não desenhe centenas de objetos para simular algo que um único mark resolve;
- minimize layers de glow;
- prefira signals compartilhados.

Para datasets grandes, considere a redução e agregação antes do desenho.

Nunca assuma que mais marks significam melhor visual.

---

# 24. Revisão automática do JSON

Antes de entregar, faça uma revisão mental ou programática do spec.

Confirme:

## Estrutura

- JSON válido;
- provider correto;
- datasets existentes;
- `source` válidos;
- signals únicos;
- marks fechados corretamente.

## Dados

- todos os fields existem;
- agregações corretas;
- ordenação correta;
- null tratado;
- zero tratado;
- cardinalidade correta.

## Layout

- `width` e `height` utilizados;
- coordenadas derivadas de sinais quando necessário;
- nenhum elemento essencial depende de tamanho fixo inadequado;
- texto não colide.

## Design

- KPI principal domina;
- status claro;
- acento controlado;
- grid consistente;
- tipografia coerente;
- decoração contida.

## Power BI

- filtros esperados afetam o visual;
- tooltip configurado quando necessário;
- seleção configurada apenas quando necessária;
- formatação coerente com locale;
- tema respeitado quando aplicável.

---

# 25. Política de correção de erro

Se um spec renderizar errado:

1. não reescreva tudo imediatamente;
2. identifique se o problema é dado, transform, layout ou mark;
3. isole o dataset;
4. confira cardinalidade;
5. confira nomes de fields;
6. remova camadas até localizar a falha;
7. corrija a causa;
8. restaure as camadas.

Não faça alterações aleatórias.

---

# 26. Método de depuração por camadas

Quando um visual complexo falhar, reconstrua nesta ordem.

## Passo 1

Renderize apenas a superfície.

## Passo 2

Mostre texto simples com um campo do dataset.

## Passo 3

Adicione dataset transformado.

## Passo 4

Adicione KPI.

## Passo 5

Adicione microvisual.

## Passo 6

Adicione status.

## Passo 7

Adicione interação.

## Passo 8

Adicione acabamento.

Isso reduz o espaço de diagnóstico.

---

# 27. Anti-padrões proibidos

Não entregue visual com:

- 3D decorativo;
- arco-íris categórico sem razão;
- 10 cores de destaque;
- sombras pesadas;
- glow em todos os elementos;
- texto minúsculo;
- borda em todo bloco;
- quatro gauges lado a lado para comparar categorias;
- donut com muitas fatias;
- labels sobrepostos;
- eixo sem contexto;
- percentual calculado por média quando deveria ser razão dos totais;
- ranking que vira #1 após selecionar uma pessoa;
- mês ordenado alfabeticamente;
- big number derivado da última linha;
- JSON com fields inexistentes;
- valor hardcoded no lugar de medida;
- fundo branco embutido quando o visual deve ser transparente;
- interação sem feedback visual.

---

# 28. Modos estéticos

A escolha estética precisa combinar com o dashboard.

## 28.1 Executive Dark

Características:

- fundo transparente;
- superfície grafite;
- contraste alto;
- acento único;
- números grandes;
- glow muito discreto;
- linhas finas;
- labels em cinza frio.

Bom para:

- comercial;
- operações;
- monitoramento;
- dashboards executivos.

---

## 28.2 Editorial Light

Características:

- fundo claro;
- bordas sutis;
- muito espaço;
- tipografia forte;
- cor usada para exceção;
- microcharts limpos.

Bom para:

- relatórios;
- apresentações;
- análise financeira;
- dashboards de gestão.

---

## 28.3 Brand Premium

Use cores da marca.

Regras:

- uma cor primária;
- uma cor de suporte;
- semânticas preservadas;
- neutros dominantes;
- logotipo somente se solicitado.

Não transforme todas as métricas na cor da marca.

---

# 29. Biblioteca mental de componentes

Ao compor um visual, pense em componentes reutilizáveis.

## Containers

- surface card;
- inset panel;
- mini-card;
- divider;
- accent rail.

## Data

- big number;
- delta;
- progress;
- bullet;
- sparkline;
- gauge;
- lollipop;
- status light.

## Identity

- avatar slot;
- name;
- badge;
- rank pill;
- metadata.

## Context

- period label;
- filter state;
- subtitle;
- benchmark;
- target.

## Interaction

- tooltip target;
- hover state;
- selected state;
- hit area.

---

# 30. Padrão de badges

Badges devem ser compactos.

Use para:

```text
#2
NO RUMO
+7,2%
TOP 10
```

Não transforme frases longas em badge.

O badge deve ter:

- fundo discreto;
- radius alto;
- texto curto;
- contraste bom.

---

# 31. Padrão de divisores

Divisor é último recurso.

Antes de desenhar uma linha, tente separar com:

- espaço;
- alinhamento;
- mudança de superfície.

Se usar divisor:

- baixo contraste;
- 1 px visual;
- comprimento alinhado ao conteúdo.

---

# 32. Padrão de microtexto

Microtexto é contexto, não conteúdo principal.

Use para:

```text
vs mês anterior
Meta
Período
Ranking geral
```

Nunca esconda informação crítica em microtexto.

---

# 33. Padrão de tendências

Setas:

```text
▲ alta
▼ queda
● neutro
```

Mas o significado depende da métrica.

Queda de custo pode ser positiva.

Portanto, não associe automaticamente:

```text
alta = verde
queda = vermelho
```

Confirme a semântica do KPI.

---

# 34. Padrão de comparação com meta

Sempre diferencie:

```text
valor atual
meta
gap
atingimento
```

Eles não são equivalentes.

Exemplo:

```text
Faturamento        R$ 3,08 Mi
Meta               R$ 2,84 Mi
Diferença          +R$ 248,94 Mil
Atingimento        108,78%
```

Não use duas métricas para representar a mesma informação se o espaço for limitado.

---

# 35. Padrão de ranking

Ranking precisa definir universo.

Exemplo:

```text
Ranking entre todos os vendedores
```

Ao receber seleção única, preserve o universo pretendido por medida DAX apropriada.

Não tente corrigir ranking global dentro do Vega se a medida semântica está errada.

---

# 36. Padrão de gráficos dentro de cards

Um microchart dentro de card não é um gráfico completo reduzido.

Remova:

- título próprio;
- legenda;
- eixo;
- grid;
- labels redundantes.

Preserve:

- forma;
- direção;
- último ponto;
- exceção importante.

---

# 37. Padrão de labels

Prefira labels externos ou bem posicionados.

Nunca permita:

- clipping;
- colisão;
- valor escondido pela marca.

Para séries densas:

- label apenas do último ponto;
- label apenas de máximo/mínimo;
- tooltip para demais valores.

---

# 38. Padrão de linha

Para tendência:

- linha principal mais forte;
- área mais fraca;
- benchmark tracejado quando necessário;
- ponto final destacado.

Não use 5 espessuras diferentes no mesmo componente.

---

# 39. Padrão de barras

Barras devem nascer de baseline coerente quando a comparação depende de magnitude.

Para ranking:

- barra horizontal;
- ordenação;
- label próximo;
- destaque de selecionado.

Para progresso:

- trilha;
- preenchimento;
- meta;
- percentual.

---

# 40. Contexto de filtro

Um visual premium precisa reagir corretamente a:

- vendedor;
- cidade;
- período;
- demais dimensões definidas no projeto.

Não use `ALL`, `REMOVEFILTERS` ou equivalentes em medidas auxiliares sem necessidade documentada.

Exceções como ranking global precisam estar explicitamente definidas no modelo.

---

# 41. Validação DAX

Antes de concluir, gere ou execute consultas de validação.

Compare:

- total;
- contexto de vendedor;
- contexto de cidade;
- contexto de período;
- ranking;
- variação.

Valide no mesmo contexto do visual.

Não compare um visual filtrado com um gabarito não filtrado.

---

# 42. Os três componentes do projeto de demonstração

Quando o `CLAUDE.md` deste projeto estiver presente, os três visuais premium prioritários são os abaixo.

Não use os valores desta seção como fonte de verdade. Use o gabarito do `CLAUDE.md`.

---

## Visual 1. Farol de Meta

### Intenção

Mostrar rapidamente se o contexto selecionado está abaixo, próximo ou acima da meta.

### Values

```text
[Faturamento]
[Meta]
```

### Estrutura

```text
Zona esquerda
- label
- Faturamento
- Meta
- Atingimento

Zona direita
- farol vertical
- status
```

### Regras

- agregue Faturamento e Meta no spec;
- recalcule atingimento;
- recalcule estado;
- somente luz ativa recebe glow;
- fundo transparente;
- card interno premium;
- status por cor + posição + texto.

---

## Visual 2. Card de Vendedor

### Intenção

Transformar a seleção de vendedor em uma ficha executiva de performance.

### Values

```text
vendedores[ImagemURL]
vendedores[Vendedor]
vendedores[Cidade]
vendedores[UF]
[Faturamento]
[Meta]
[Atingimento Meta %]
[Diferença para Meta]
[Variação MoM %]
[Ranking Vendedor Geral]
[Cor do Farol]
```

### Estrutura

```text
Zona A . identidade
Zona B . KPIs
Zona C . gauge
```

### Regras

- requer seleção única;
- mostrar estado de instrução quando não houver vendedor único;
- ranking vem da medida global;
- imagem usa estratégia robusta do projeto;
- gauge mostra atingimento;
- delta respeita semântica;
- responsivo.

---

## Visual 3. KPI + Sparkline

### Intenção

Combinar resultado atual com direção temporal.

### Values

```text
dCalendario[AnoMes]
dCalendario[AnoMesNum]
[Faturamento]
[Meta]
[Atingimento Meta %]
[Cor do Farol]
[Variação MoM %]
```

### Estrutura

```text
Zona A
- label
- big number
- meta
- atingimento

Zona B
- sparkline
- último ponto
- variação
```

### Regras

- dataset mensal permanece em N linhas;
- total sai de dataset agregado;
- série é ordenada por AnoMesNum;
- último ponto identificado por chave;
- microchart sem eixo visível;
- área sutil;
- ponto final forte.

---

# 43. Modo "Design Review"

Quando o usuário pedir para melhorar um visual existente:

1. não reescreva imediatamente;
2. avalie o visual em 8 dimensões;
3. identifique no máximo 5 problemas prioritários;
4. preserve o que já funciona;
5. proponha a evolução;
6. só então gere o novo spec.

## Scorecard interno

Avalie sem necessariamente mostrar nota:

```text
Hierarquia
Legibilidade
Composição
Cor
Tipografia
Densidade
Interação
Robustez técnica
```

O objetivo é orientar a revisão, não criar uma pontuação estética arbitrária para o usuário.

---

# 44. Modo "Reference Recreation"

Se o usuário fornecer uma referência visual:

1. identifique estrutura;
2. identifique hierarquia;
3. identifique spacing;
4. identifique comportamento visual;
5. adapte ao modelo real;
6. não copie cegamente dimensões fixas;
7. não invente dados que existiam na referência mas não existem no modelo;
8. substitua elementos incompatíveis por equivalentes coerentes.

Recrie o princípio visual, não apenas a aparência.

---

# 45. Modo "Premium Upgrade"

Quando o usuário disser apenas "deixe premium":

Execute:

1. aumente hierarquia;
2. reduza ruído;
3. alinhe grid;
4. melhore contraste;
5. adicione uma camada útil de contexto;
6. adicione microvisual apenas se houver pergunta analítica;
7. revise cor;
8. revise estados;
9. revise responsividade;
10. preserve números.

"Premium" nunca significa adicionar mais elementos indiscriminadamente.

---

# 46. Modo "Build from Prompt"

Se o usuário descrever um visual em linguagem natural:

Antes do JSON, devolva:

```text
Objetivo
Campos
Grão
Arquétipo
Layout
Interação
Riscos
```

Se houver lacuna crítica de dados, não invente.

Use a melhor alternativa compatível com o modelo real.

---

# 47. Modo "Production Ready"

Antes de chamar um spec de pronto para produção:

Confirme:

- Power BI Desktop;
- Power BI Service, quando possível;
- redimensionamento;
- filtros;
- seleção;
- tooltip;
- formato numérico;
- locale;
- null;
- zero;
- período sem dado;
- múltiplos filtros;
- tema claro/escuro quando aplicável.

Se algo não foi testado, diga que não foi testado.

---

# 48. Fontes técnicas oficiais para decisões de implementação

Ao precisar confirmar comportamento do Deneb ou Vega, prefira documentação oficial.

Referências:

```text
https://deneb.guide/docs
https://deneb.guide/docs/dataset
https://deneb.guide/docs/formatting
https://deneb.guide/docs/schemes
https://deneb.guide/docs/interactivity-overview
https://deneb.guide/docs/interactivity-tooltips
https://deneb.guide/docs/interactivity-selection

https://vega.github.io/vega/docs/
https://vega.github.io/vega/docs/specification/
https://vega.github.io/vega/docs/marks/
https://vega.github.io/vega/docs/signals/
https://vega.github.io/vega/docs/expressions/
```

Se o comportamento puder ter mudado, consulte a versão atual antes de afirmar.

---

# 49. Checklist final da skill

Antes de concluir qualquer visual Deneb premium, confirme:

## Dados

- [ ] campos reais confirmados;
- [ ] grão confirmado;
- [ ] cardinalidade confirmada;
- [ ] agregação correta;
- [ ] derived metrics corretas;
- [ ] ordenação correta;
- [ ] nulls tratados;
- [ ] zero tratado.

## Design

- [ ] pergunta de negócio clara;
- [ ] KPI principal evidente;
- [ ] grid consistente;
- [ ] hierarquia tipográfica;
- [ ] cor com função;
- [ ] contraste;
- [ ] densidade controlada;
- [ ] decoração justificada;
- [ ] microchart útil;
- [ ] estados previstos.

## Responsividade

- [ ] width usado;
- [ ] height usado;
- [ ] layout compacto previsto;
- [ ] informação essencial preservada;
- [ ] nenhuma colisão importante.

## Power BI

- [ ] provider Vega;
- [ ] filtros funcionando;
- [ ] pbiFormat considerado;
- [ ] tema considerado;
- [ ] tooltip configurado quando útil;
- [ ] cross-filter configurado somente quando útil;
- [ ] estado de seleção visível.

## Acessibilidade

- [ ] status não depende apenas de cor;
- [ ] textos legíveis;
- [ ] descrição coerente;
- [ ] contraste adequado.

## Validação

- [ ] DAX validado;
- [ ] mesmo contexto de filtro;
- [ ] gabarito respeitado;
- [ ] nenhum valor inventado.

## Manutenção

- [ ] signals centralizam tokens;
- [ ] datasets têm nomes claros;
- [ ] marks organizados;
- [ ] JSON legível;
- [ ] sem redundância desnecessária.

---

# 50. Regra final

A melhor visualização não é a que demonstra mais recursos do Vega.

É a que permite ao usuário compreender uma situação de negócio com menos esforço, sem perder precisão, contexto ou confiança.

**Dados corretos. Hierarquia forte. Design contido. Interação útil. Vega bem arquitetado.**
