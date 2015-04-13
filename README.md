# Sass [![Gem Version](https://badge.fury.io/rb/sass.png)](http://badge.fury.io/rb/sass) [![Inline docs](http://inch-ci.org/github/sass/sass.svg)](http://inch-ci.org/github/sass/sass)

**Sass deixa o CSS divertido novamente **. Sass é uma extensão para CSS3,
que adiciona regras segmentares, variáveis, mixins, seletores com herança e mais.
Ele traduz para um CSS padrão e bem formatado, usando a linha comando ou web-frameworks.

Sass tem duas sintaxes. A principal sintaxe (a partir do Sass 3)
é conhecida como "SCSS" ("Sassy CSS"),
e é um super conjuto de sintaxes de CSS3's.
Isto significa que toda validação de estilo de CSS3 é válida no SCSS também.
Os arquivos de SCSS usam a extensão `.scss`.

A segunda, é uma sintaxe mais antiga e conhecida como independete (popularmente chamada de "Sass").
Inspirada por Haml's Terseness, é recomendada para pessoas
que preferem uma similaridade e consição como o CSS.
Em vez de conchetes e pontos e vírgulas,
ela usa a identação de linhas para definir os blocos.
Embora não se tenha mais uma linguagem semelhante,
a sintaxe identada ainda será suportada.
Arquivos que usam este tipo sintaxe tem extensão `.sass`.

## Usando

Sass pode ser usado a partir da linha de comando
ou como parte de um web-framework.
O primeiro passo é instalar-lo com gem:

    gem install sass

Depois você converte algum CSS para Sass, você pode executar

    sass style.scss

Compilá-lo de volta para CSS.
Para mais informações sobre os comandos, confira

    sass --help

Para instalar o Sass no Rails 2,
adicione `config.gem "sass"` no `config/environment.rb`.
No Rails 3, adicione `gem "sass"` no seu Gemfile.
`.sass` ou `.scss` arquivos devem ser colocados no `public/stylesheets/sass`,
onde eles serão automaticamente compilados
para correspondentes arquivos CSS em `public/stylesheets` quando necessário
(o diretório de template do Sass é customizável...
veja [A referência do Sass](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#template_location-option) para detalhes).

```ruby
require 'sass/plugin/rack'
use Sass::Plugin::Rack
```

Para `config.ru`.
Então quaisquer arquivos Sass no `public/stylesheets/sass`
serão compilados em arquivos CSS no `public/stylesheets` a cada pedido.

Para usar Sass programaticamente,
confira a [documentação YARD](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#using_sass).

## Formatando

Sass é uma extensão de CSS
que adiciona elegância e potência para a linguagem básica.
Ele permite que você use [variáveis][vars], [regras segmentares][nested],
[mixins][mixins], [importações em linha][imports],
e mais, todos com uma sintaxe totalmente compátivel com CSS.
Sass ajuda manter longas stylesheets bem organizadas,
e pequenas stylesheets rodando rapidamente,
particularmente com a ajuda da
[livrária de estilo Compass](http://compass-style.org).

[vars]:    http://sass-lang.com/documentation/file.SASS_REFERENCE.html#variables_
[nested]:  http://sass-lang.com/documentation/file.SASS_REFERENCE.html#nested_rules
[mixins]:  http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixins
[imports]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#import

Sass tem duas sintaxes.
A primeira aqui apresentada, conhecida como "SCSS" ("Sassy CSS"),
é completamente compatível com CSS.
A outra (mais velha) sintaxe, conhecida como a sintaxe indentada ou apenas "Sass",
é sensível ao espaço em branco e baseado em indentação.
Para mais informações, veja a [documentação de referência][syntax].

[syntax]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#syntax

Começe a seguir exemplos e veja o CSS que eles produzem,
coloque ele em um arquivo chamado `test.scss` e rode `sass test.scss`.

### Segmentos

Sass evita repetição de seletores um dentro do outro.
A mesma coisa funciona para as propiedades.

```scss
table.hl {
  margin: 2em 0;
  td.ln { text-align: right; }
}

li {
  font: {
    family: serif;
    weight: bold;
    size: 1.2em;
  }
}
```

### Variáveis

Usa a mesma cor em todos os lugares?
Precisa fazer cálculos com height e width e text size?
Sass suporta variáveis, faz cálculos e muitas outras funções.

```scss
$blue: #3bbfce;
$margin: 16px;

.content_navigation {
  border-color: $blue;
  color: darken($blue, 10%);
}

.border {
  padding: $margin / 2;
  margin: $margin / 2;
  border-color: $blue;
}
```

### Mixins

Ainda mais poderoso que as variáveis,
com mixins você reutilizará pedaços inteiros de CSS,
propriedades ou seletores.
Você pode até mesmo dar-lhes argumentos.

```scss
@mixin table-scaffolding {
  th {
    text-align: center;
    font-weight: bold;
  }
  td, th { padding: 2px; }
}

@mixin left($dist) {
  float: left;
  margin-left: $dist;
}

#data {
  @include left(10px);
  @include table-scaffolding;
}
```

Uma grande lista de característica está disponível
na [referência de Sass](http://sass-lang.com/documentation/file.SASS_REFERENCE.html).

## Executáveis

O Sass gem inclui vários executáveis que são utéis
para lidar com Sass pela linha de comando.

### `sass`

A execução de `sass` transforma um código Sass em um arquivo CSS.
Veja `sass --help` para mais informações e opções.

### `sass-convert`

A execução de `sass-convert` converte entre CSS, Sass, e SCSS.
Quando convertido de CSS para Sass ou SCSS,
as regras segmentares são aplicados onde apropriado.
Veja `sass-convert --help` para mais informações e opções.

### Rodando localmente

Para rodar um comandando Sass em um código confira o rubygems:

```
$ cd <SASS_CHECKOUT_DIRECTORY>
$ bundle
$ bundle exec sass ...
$ bundle exec scss ...
$ bundle exec sass-convert ...
```

## Autores

Sass é idealizado por [Hampton Catlin](http://www.hamptoncatlin.com)
(@hcatlin). Entretando, agora Hampton não está por dentro do código, porém
ocasualmente consulta questões sobre a linguagem. Hampton mora em São
Francisco, na Califórnia e trabalha como Vice-Presidente de tecnologia
no [Moovweb](http://www.moovweb.com/).

[Natalie Weizenbaum](http://nex-3.com) é o primeira desenvolvedora e arquiteta de
Sass. Seu trabalho tem mantido o projeto vivo indeterminavelmente respondendo posts em fóruns, concertando bugs, refactorando, encontrando melhorias, escrevendo documentações, implementando novas característica, e recebendo café de Hampton (uma tarefa adequada para uma menina gênia). Natalie mora em Seattle, Washington e trabalha na
[Dart](http://dartlang.org) biblioteca de aplicativos da Google.

[Chris Eppstein](http://acts-as-architect.blogspot.com) é o contribuidor principal do
Sass e é o criador do Compass, o primeiro framework baseado em SASS. Chris foca
em deixar o Sass mais poderoso, fácil de usar e de maneiras rápidas, que sejam aprovadas
através da comunidade de desenvolvimento web. Chris mora em São José, na Califórnia com
sua esposa e filha. Ele é um engenheiro no
[LinkedIn.com](http://linkedin.com), onde uma de suas responsabilidades é de
manter Sass & Compass.

Se você usa este software, você deve elogiar Hampton. E pagar alguns doces
para Natalie. Talvez um gatinho!

Além disso, a implementação é lincencia sob a licença MIT.
Ok, certo, eu acho que os elogios não são __necessários__.

Este README foi traduzido por [Rodrigo Boniatti](https://github.com/boniattirodrigo),
contribua também para deixar essa tradução melhor.
