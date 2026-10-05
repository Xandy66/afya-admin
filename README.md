# afya-admin
# Afya Admin — Dashboard com Blazor WebAssembly e MudBlazor

## Identificação

| | |
|---|---|
| **Aluno(a)** | Alexandre Bruno de Sousa Sutil |
| **Matrícula** | 000000 |
| **Faculdade** | Afya São Lucas |
| **Curso** | Programação para Sistemas WEB |
| **Disciplina** | Ciência da Computação |
| **Professor(a)** | Liluyoud Cury Lacerda |
| **Semestre** | 2026.2 |

## Objetivo do projeto

Explique com suas palavras o objetivo do projeto e o que a página faz (2 a 4 parágrafos).

## Tecnologias utilizadas

- **.NET 10** — framework de destino `net10.0`.
- **Blazor WebAssembly standalone** — execução do código C# no navegador.
- **MudBlazor 9** — componentes visuais, gráficos, tema e utilitários de layout.
- **C# e Razor** — modelos, parâmetros, eventos e composição da interface.
- **HTML e SVG** — estrutura da página hospedeira e texto central do gráfico de rosca.
- **Google Fonts: Inter e Roboto** — fontes carregadas pelo `index.html` e aplicadas pelo tema.
- **Git e GitHub** — versionamento e publicação do código.

## Como executar

Passo a passo para outra pessoa clonar e rodar o projeto:

```bash
git clone https://github.com/Xandy66/afya-admin.git
cd afya-admin
dotnet watch
```

Informe também a versão do .NET SDK necessária.
`net10.0`

## Telas

### Tema claro
![Dashboard — tema claro](docs/prints/tema-claro.png)

### Tema escuro
![Dashboard — tema escuro](docs/prints/tema-escuro.png)

### Versão mobile
![Dashboard — celular](docs/prints/mobile.png)

### HTML gerado (DevTools)
![Inspeção do HTML no DevTools](docs/prints/devtools.png)

Explique em poucas linhas o que o print do DevTools mostra: qual componente você inspecionou, qual HTML ele gerou e quais classes apareceram.
O print do DevTools mostra a inspeção do nó principal da aplicação Blazor WebAssembly dentro da tag `<body>`.
• Componente inspecionado: O componente principal da aplicação (raiz), injetado no escopo global do documento.
• HTML gerado: A tag de marcação selecionada é a `<div id="app">`, que serve como o container onde toda a árvore de componentes do Blazor é renderizada no navegador.
• Classes e estilos que apareceram: No painel da direita (Styles), aparecem as variáveis CSS globais de tema do MudBlazor (como --mud-palette-black, --mud-palette-primary, --mud-palette-surface, entre outras), aplicadas no escopo do body e herdadas pela aplicação, definindo as cores de fundo, textos e identidade visual padrão do painel. Também é visível uma tag `<style id="mud-style">` no HTML contendo classes utilitárias internas do framework (como .mud-btn, .mud-btn-root).



## Estrutura do projeto

```text
afya-admin/
├── Components/
│   ├── AtividadesRecentes.razor
│   ├── CabecalhoPagina.razor
│   ├── DashboardCard.razor
│   ├── GraficoDistribuicaoClientes.razor
│   ├── GraficoReceita.razor
│   ├── KpiCard.razor
│   ├── PerformanceProjetos.razor
│   ├── ProjetosRecentes.razor
│   ├── SeletorPeriodo.razor
│   └── Ui.cs
├── Data/
│   └── DashboardData.cs
├── Layout/
│   ├── MainLayout.razor
│   └── NavMenu.razor
├── Pages/
│   ├── Dashboard.razor
│   └── NotFound.razor
├── Properties/
│   └── launchSettings.json
├── docs/
│   └── prints/
├── wwwroot/
│   ├── css/app.css
│   ├── img/alex-morgan.jpg
│   ├── favicon.png
│   ├── icon-192.png
│   └── index.html
├── .gitignore
├── _Imports.razor
├── afya-admin.csproj
├── App.razor
├── Program.cs
└── README.md
```

| Pasta/arquivo | Responsabilidade |
|---|---|
| `Components` | Blocos reutilizáveis de apresentação e funções auxiliares de interface. |
| `Data` | Records dos modelos e coleções de dados fictícios. |
| `Layout` | Moldura da aplicação: sidebar, AppBar, navegação, tema e providers MudBlazor. |
| `Pages` | Componentes associados a rotas; `Dashboard.razor` monta a página inicial. |
| `wwwroot` | Arquivos estáticos, página HTML hospedeira, imagens e CSS original do template. |
| `docs/prints` | Capturas usadas na documentação. |
| `Properties/launchSettings.json` | Perfis de execução, URLs e configuração de depuração. |
| `Program.cs` | Inicialização do host WebAssembly e registro dos serviços. |
| `App.razor` | Roteador que associa a URL à página e ao layout. |
| `_Imports.razor` | Namespaces compartilhados pelos arquivos Razor. |
| `afya-admin.csproj` | Framework, namespace raiz e referências aos pacotes NuGet. |

`bin/` e `obj/` são gerados pelo build e ficam fora do versionamento. As páginas de exemplo `Home`, `Counter` e `Weather` e o CSS isolado do layout foram removidos.

## Componentes criados


| Componente | Responsabilidade | Parâmetros que recebe |
|---|---|---|
| `DashboardCard` | Estrutura comum de card com título, subtítulo, ações, menu e conteúdo. | `Titulo` (`string`, obrigatório), `Subtitulo` (`string?`), `Acoes`, `Menu` e `ChildContent` (`RenderFragment?`). |
| `CabecalhoPagina` | Cabeçalho com título, subtítulo e espaço para ações. | `Titulo` (`string`, obrigatório), `Subtitulo` (`string?`) e `Acoes` (`RenderFragment?`). |
| `SeletorPeriodo` | Menu para selecionar o período e comunicar a mudança à página. | `Opcoes` (`IReadOnlyList<string>`, obrigatório), `Valor` (`string`) e `ValorChanged` (`EventCallback<string>`). |
| `KpiCard` | Indicador com ícone, valor, variação e sparkline. | `Kpi` (`Kpi`, obrigatório). |
| `GraficoReceita` | Gráfico de linha/área com as séries de receita e meta e legenda própria. | `Meses` (`string[]`), `Receita` e `Meta` (`double[]`), todos obrigatórios. |
| `GraficoDistribuicaoClientes` | Rosca com percentuais dos segmentos, legenda e total no centro. | `Total` (`int`) e `Segmentos` (`IReadOnlyList<SegmentoCliente>`), ambos obrigatórios. |
| `PerformanceProjetos` | Lista de projetos com progresso, percentuais e tarefas concluídas. | `Projetos` (`IReadOnlyList<ProjetoPerformance>`, obrigatório). |
| `AtividadesRecentes` | Feed com pessoa, ação, horário relativo e avatares. | `Atividades` (`IReadOnlyList<Atividade>`, obrigatório). |
| `ProjetosRecentes` | Tabela responsiva de projetos com status, progresso e menu de ações. | `Projetos` (`IReadOnlyList<ProjetoRecente>`, obrigatório). |
| `MainLayout` | Layout compartilhado, tema, providers, AppBar e sidebar. | `Body` (`RenderFragment`, herdado de `LayoutComponentBase`). |
| `NavMenu` | Links, separadores e badges da navegação lateral. | Nenhum parâmetro próprio. |

Os componentes de entrada e rota `App`, `Dashboard` e `NotFound` não declaram parâmetros próprios. `Ui.cs` é uma classe auxiliar, não um componente Razor: `Iniciais(string nome)` gera as iniciais dos avatares e `FundoSuave(Color cor)` retorna uma classe utilitária nativa para o fundo dos ícones.

## O que aprendi

Responda **com suas próprias palavras** (um parágrafo curto por pergunta):

1. Como uma aplicação Blazor WebAssembly inicia no navegador? Qual é o papel do `index.html`, da `<div id="app">` e do `Program.cs`?
A inicialização do Blazor WebAssembly ocorre quando o navegador baixa e executa o motor do .NET via WebAssembly. O arquivo index.html serve como a casca HTML inicial da página, contendo a `<div id="app">`, que funciona como o marcador de posição onde a aplicação Blazor será renderizada após o carregamento; já o arquivo Program.cs é o ponto de entrada do código C#, responsável por configurar os serviços da aplicação e indicar ao Blazor que ele deve injetar o componente principal justamente dentro daquela div com ID app.

2. Qual é a diferença entre um **Layout**, uma **Page** e um **Component** neste projeto? Dê um exemplo de cada.
A diferença entre eles está no escopo e na responsabilidade estrutural dentro da interface. Um Layout define a estrutura visual global e repetitiva do sistema (ex: MainLayout.razor, que contém o menu lateral e o topo); uma Page representa uma tela acessível por uma URL específica através da diretiva @page (ex: Dashboard.razor); e um Component é um bloco visual isolado e reutilizável que não possui rota própria, criado para executar uma função específica dentro de uma página (ex: DashboardCard.razor).

3. O que é um `RenderFragment` e como o `DashboardCard` usa esse recurso para ser reutilizado por vários cards?
O RenderFragment é um tipo de dado no Blazor que permite passar um bloco inteiro de código HTML ou outros componentes como parâmetro para dentro de outro componente. O DashboardCard utiliza esse recurso (geralmente através de uma propriedade chamada ChildContent) para atuar como uma moldura genérica, permitindo que qualquer conteúdo customizado — como textos, ícones do MudBlazor ou gráficos — seja inserido dinamicamente dentro dele por quem o estiver chamando.

4. Como funciona o `@bind-Valor` no `SeletorPeriodo`? Qual é o papel do `ValorChanged`?
O @bind-Valor funciona como uma via de mão dupla (two-way data binding) que sincroniza automaticamente o estado do componente pai com o componente filho. Quando o valor selecionado muda internamente dentro do SeletorPeriodo, o Blazor dispara um evento obrigatório nomeado como ValorChanged (do tipo EventCallback), que avisa o componente pai sobre a modificação, atualizando a variável correspondente no pai de forma imediata e automática

5. Por que os dados ficam na pasta `Data`, separados dos componentes? Que vantagem isso traz se, no futuro, os dados vierem de uma API?
A separação dos dados na pasta Data isola a lógica de negócios e as regras de busca de informação da camada visual, seguindo o princípio de responsabilidade única. Se no futuro os dados passarem a vir de uma API, os componentes visuais não precisarão sofrer alterações estruturais ou estéticas; bastará modificar as classes de repositório ou serviços dentro da pasta Data para realizarem requisições HTTP, mantendo o restante do sistema intacto

6. Como o `MudGrid` com `xs`, `sm` e `lg` faz os cards de KPI se reorganizarem em telas de tamanhos diferentes?
O MudGrid organiza os cards de KPI utilizando um sistema de colunas responsivo baseado em um total de 12 espaços disponíveis na tela. As propriedades xs (telas muito pequenas), sm (telas médias/tablets) e lg (telas grandes/monitores) determinam quantas dessas 12 colunas cada card vai ocupar; por exemplo, definir xs="12" faz o card ocupar a largura inteira no celular (empilhando os cards), enquanto lg="3" permite exibir até quatro cards lado a lado em telas de computador

7. Como foi possível estilizar a página inteira sem escrever CSS? Explique o papel do tema (`MudTheme`) e das classes utilitárias.
A estilização sem CSS manual foi possível graças ao ecossistema do MudBlazor, que gerencia o design de forma programática. O MudTheme centraliza as configurações globais de identidade visual (como a paleta de cores primárias, secundárias e tipografia da marca), enquanto as classes utilitárias do MudBlazor aplicam espaçamentos, alinhamentos e comportamentos visuais diretamente nas tags HTML via atributos, eliminando a necessidade de criar arquivos .css customizados.

8. Por que o namespace do projeto é `afya_admin` e não `afya-admin`?
O namespace utiliza afya_admin com underline porque o caractere hífen (-) é um operador de subtração na linguagem C# e em várias outras linguagens de programação, sendo inválido para a nomeação de identificadores de código. Para garantir que o compilador do .NET consiga ler o nome do projeto e organizar suas classes corretamente sem gerar erros de sintaxe, o hífen é automaticamente substituído por um caractere válido, como o sublinhado.

## Dificuldades e soluções

Descreva pelo menos **dois problemas** que você enfrentou durante o desenvolvimento e como resolveu cada um.

## Melhorias futuras (opcional)

O que você implementaria a seguir? Se fez algum dos desafios da seção 20 do tutorial, descreva aqui.
