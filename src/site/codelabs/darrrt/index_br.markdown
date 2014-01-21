---
layout: default
title: "Experimente Dart"
description: "Escreva um pouco de código com Dart. Aprenda algumas coisas."
snippet_img: images/piratemap.jpg
has-permalinks: true
tutorial:
  id: trydart
js:
- url: /js/os-switcher.js
  defer: true
- url: /js/editor-downloads-analytics.js
  defer: true
- url: /js/editor-version.js
  defer: true
header:
  css: ["/codelabs/darrrt/darrrt.css"]
---

# {{ page.title }}

Neste laboratório de código, 
você vai criar um gerador de crachá pirata a partir de uma aplicação inicial.
A aplicação exemplo provê uma olhar geral sobre a linguagem Dart e as funcionalidades de suas bibliotecas.
Este laboratório de código assume que você tem alguma experiência com programação.

<strong>Construa esta aplicação.!</strong>

<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/6-piratebadge_json/piratebadge.html">
</iframe>

<hr>

<div class="piratemap" markdown="1" style="min-height:325px">

## Map

* [Passo 0: Prepare-se](#set-up)
* [Passo 1: Execute a aplicação básica](#step-one)
* [Passo 2: Inclua um campo de texto](#step-two)
* [Passo 3: Inclua um botão](#step-three)
* [Passo 4: Crie uma classe](#step-four)
* [Passo 5: Salve em um repositório local ](#step-five)
* [Passo 6: Leia um arquivo JSON utilizando o HttpRequest](#step-six)
* [Passo 7: Vá em frente e aprenda mais sobre Dart](#step-seven)

</div>


<hr>

## Step 0: Prepare-se {#set-up}

Neste passo, você irá baixar o Dart e pegar o código exemplo.


### <i class="fa fa-anchor"> </i> Get Dart.

<div class="trydart-step-details" markdown="1">
Se você não tiver feito ainda,
vá e baixe os Arquivos do Dart.
Descompacte o arquivo ZIP, que irá criar um diretório chamado `dart`.

{% include downloads/_dart-editor.html buttonclass="btn btn-primary btn-lg" %}

<p class="os-choices" markdown="1">
As ferramentas do Dart 
trabalham com as recentes versões do
  {% include os-choices.html %}
</p>
</div>

### <i class="fa fa-anchor"> </i> Inicialize o editor.

<div class="trydart-step-details" markdown="1">
Va até o diretório `dart` e der um duplo clique no **DartEditor**.

**Tem alguma pergunta? Esta com problemas?** Vá até página
[Soluções de problemas do Dart Editor](/tools/editor/troubleshoot.html) .

</div>

### <i class="fa fa-anchor"> </i> Pege o código exemplo.

<div class="trydart-step-details" markdown="1">
<a href="https://github.com/dart-lang/one-hour-codelab/archive/master.zip">Baixar</a>
o código exemplo.
Descompacte o arquivo ZIP, 
que irá criar a pasta chamada `one-hour-codelab-master`.
</div>

### <i class="fa fa-anchor"> </i> abra o exemplo one-hour-codelab-master.

<div class="trydart-step-details" markdown="1">
No Dart Editor, 
utilize **File > Open Existing Folder…**
para abrir o diretório `one-hour-codelab-master`.
</div>

<div class="row"> <div class="col-md-7" markdown="1">

![Os arquivos e pastas dentro da pasta piratebadge.](images/filesanddirs.png)

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* A pasta `packages`, como também os arquivos `pubspec.yaml` e `pubspec.lock` são relacionados as dependências de pacote.
Este projeto tem todas as dependências configuradas para você.
O Dart Editor instala automaticamente as dependências necessárias.

* Varias pastas numeradas contem o código completo de cada passo.
`1-blankbadge` contem a estrutura inicial da aplicação que você vai começar.
`6-piratebadge_json` contem a versão final da aplicação.

* o arquivo `piratebadge.css`
prove os estilos CSS para todos os passos.
Você pode mudar o arquivo durante o laboratório de código.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<hr>

##Step 1: Execute a aplicação básica {#step-one}

Neste passo, você abrirá o código fonte,
vai se familiarizar com o Dart e o código HTML,
e rodará a aplicação.

### <i class="fa fa-anchor"> </i> Expanda a pasta 1-blankbadge.

<div class="trydart-step-details" markdown="1">
No Dart Editor, expanda a pasta `1-blankbadge`  
clicando no setinha 
![wee arrow](images/wee-arrow.png) no lado esquerdo do nome.
A pasta contem dois arquivos,  `piratebadge.html` e `piratebadge.dart`.
</div>

### <i class="fa fa-anchor"> </i> Abra os arquivos.

<div class="trydart-step-details" markdown="1">
Abra ambos os arquivos, `piratebadge.html` e `piratebadge.dart`,
clicando duas vezes no nome de cada arquivo no Dart Editor.
</div>

### <i class="fa fa-anchor"> </i> Revise o código.

<div class="trydart-step-details" markdown="1">
Familiarize com o HTML e o código Dart da versão básica da aplicação.
</div>

<div class="trydart-step-details" markdown="1">
#### piratebadge.html
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details" markdown="1">
{% prettify html%}
<html>
  <head>
    <meta charset="utf-8">
    <title>Pirate badge</title>
    <link rel="stylesheet" href="../piratebadge.css">
  </head>
  <body>
    <h1>Pirate badge</h1>
    
    [[highlight]]<div class="widgets">[[/highlight]]
      [[highlight]]TO DO: Put the UI widgets here.[[/highlight]]
    [[highlight]]</div>[[/highlight]]
    <div class="badge">
      <div class="greeting">
        Arrr! Me name is
      </div>
      <div class="name">
        [[highlight]]<span id="badgeName"> </span>[[/highlight]]
      </div>
    </div>

    [[highlight]]<script type="application/dart" src="piratebadge.dart"></script>[[/highlight]]
    [[highlight]]<script src="packages/browser/dart.js"></script>[[/highlight]]
  </body>
</html>
{% endprettify %}

</div>
<div class="trydart-filename">piratebadge.html</div>

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* Durante este laboratório de código,
todas as alterações realizadas em `piratebadge.html` 
serão dentro do elemento &lt;div&gt; identificado pela classe `widgets`.

* Em passos futuros,
o elemento &lt;span&gt; com ID `badgeName`
é atualizado programaticamente pelo código Dart 
baseado na entrada do usuário .

* O código `piratebadge.dart` provê o programa principal da aplicação.

* O código `packages/browser/dart.js` é um código de inicialização 
que toma conta da inicialização da Dart VM,
como também com a compatibilidade com navegadores que não rodam Dart.

</div> </div>

<div class="trydart-step-details" markdown="1">
#### piratebadge.dart
</div>

<div class="row"> <div class="col-md-7" markdown="1">

<div class="trydart-step-details" markdown="1">
{% prettify dart %}
[[highlight]]void main() {
  // Your app starts here.
}
[[/highlight]]
{% endprettify %}
</div>
<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Este arquivo é o código principal da aplicação.
Ele é referenciado pela tag &lt;script&gt; no arquivo `piratebadge.html`.

* A função `main()` é uma uma função de alto nível. 
  Dart chama esta função quando a aplicação inicia.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}
</div> </div>

### <i class="fa fa-anchor"> </i> Executando a aplicação.

<div class="trydart-step-details" markdown="1">
Para executar a aplicação no Dart Editor, selecione  `piratebadge.html`
e clique no botão Run
<img src="images/run.png" width="16" height="16"
     alt="Run button">.

![Clique no botão Run](images/clickrun.png)

Dart Editor abre o _Dartium_, uma versão especial do Chromium
que tem a maquina virtual do Dart inbutida, e carrega a aplicação.

Você dever ver o comentário TO DO comment no lado esquerdo
e um nome vermelho e branco painel na direita.
</div>

<div class="trydart-step-details" markdown="1">
<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/1-blankbadge/piratebadge.html">
</iframe>
</div>

<hr>

##Passo 2: Inclua um campo de texto{#step-two}

<div class="trydart-note" markdown="1">
<strong>Nota:</strong> Durante este laboratório de código,
continue editando os arquivos da pasta `1-blankbadge`.
Você pode utilizar os arquivos das outras pastas para comparar o código 
ou para voltar ao caminho correto caso você saia dos trilhos.
</div>

Neste passo, você incluirá um campo de texto na aplicação.
Enquanto o usuário digita no campo de texto,
o código Dart atualizará o crachá com o valor digitado no campo de texto.

### <i class="fa fa-anchor"> </i> Altere o arquivo piratebadge.html.

<div class="row"> <div class="col-md-7" markdown="1">

<div class="trydart-step-details" markdown="1">

Inclua a tag &lt;input&gt; no cógigo HTML
dentro do &lt;div&gt; `widgets`.

{% prettify html %}
...
<div class="widgets">
[[highlight]]  <div>
    <input type="text" id="inputName" maxlength="15">
  </div>[[/highlight]]
</div>
...
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.html</div>

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* O ID do elemento input é `inputName`.
O Dart utiliza o seletor CSS, como por exemplo o ID,
para recuperar um elemento do DOM.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

### <i class="fa fa-anchor"> </i> Altere o arquivo piratebadge.dart.

<div class="trydart-step-details" markdown="1">

Importe o biblioteca `dart:html`
no topo do arquivo
(abaixo do direitos autorais).

</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details" markdown="1">

{% prettify dart %}
[[highlight]]import 'dart:html';[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Este treixo importa todas as classes e outros recursos do dart:html,
que prover elementos HTML e acesso ao DOM.

* O Dart Editor é prestativo ao avisar quando uma importação não esta sendo utilizada.
Não se preocupe com isto. Você corrigirá no próximo passo.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Registre uma função para gerenciar os eventos que ocorrem no campo texto.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details" markdown="1">

{% prettify dart %}
void main() {
  [[highlight]]querySelector('#inputName').onInput.listen(updateBadge);[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* A função `querySelector()`, definida no
dart:html, recupera um elemento do DOM.
Aqui, o código utiliza o ID `#inputName`
para especificar o campo Texto.

* `onInput`registra um gerenciador de eventos para eventos de inserção.

* Um evento de inserção ocorre quando o usuário preciona uma tecla.

* Você pode criar strings utilizar tanto cota simples como composta.

* Dart Editor avisa você que a função não existe.
Vamos corrifir agora.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Impementando o gerenciador de eventos como uma função de alto nivel.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details" markdown="1">

{% prettify dart %}
...

[[highlight]]void updateBadge(Event e) { 
  querySelector('#badgeName').text = (e.target as InputElement).value;
}[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Esta função configura o texto do elemento `badgeName` do valor do campo de  texto.

* Você pode dizer que `updateBadge()` é um gerenciamento de evento porque isto necessita de um objeto `Event`.

* O elemento que gera o evento, o campo texto, é `e.target`.

* A palavra chave converte `e.target` para um
`InputElement` para silencar os avisos do Dart Editor.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

### <i class="fa fa-anchor"> </i> Executando a aplicação.

<div class="trydart-step-details" markdown="1">

Salve seus arquivos com **File > Save All**.

Use o botão Run
<img src="images/run.png" width="16" height="16"
     alt="Run button">
no Dart Editor para executar a aplicação.

Compare sua aplicação com a que esta rodando abaixo.

Digite no campo de texto.

<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/2-inputnamebadge/piratebadge.html">
</iframe>

#### Problemas?

Valide seu código utilizando os arquivos em `2-inputbadge`.

* [piratebadge.html](https://github.com/dart-lang/one-hour-codelab/blob/master/web/2-inputnamebadge/piratebadge.html)

* [piratebadge.dart](https://github.com/dart-lang/one-hour-codelab/blob/master/web/2-inputnamebadge/piratebadge.dart)
</div>


<hr> 

##Passo 3: Inclua um botão {#step-three}

Neste passo, você incluirá um botão a aplicação.
O botão é habilitado quando a caixa de texto não possuir texto.
Quando o usuário clicar no botão,
a aplicação colocará o nome `Anne Bonney` no crachá.

### <i class="fa fa-anchor"> </i> Editando o piratebadge.html.

<div class="trydart-step-details" markdown="1">
Inclua a tag &lt;button&gt; abaixo do campo de texto.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify html %}
...
<div class="widgets">
  <div>
    <input type="text" id="inputName" maxlength="15">
  </div>
[[highlight]]  <div>
    <button id="generateButton">Aye! Gimme a name!</button>
  </div>[[/highlight]]
</div>
...
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.html</div>

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* O botão tem o ID `generateButton` portado
o código Dart pode recuperar o elemento.

</div> </div>

### <i class="fa fa-anchor"> </i> Editando o piragebadge.dart.

<div class="trydart-step-details" markdown="1">
Abaixo do import, declare váriavel de alto level que conterá o `ButtonElement`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
import 'dart:html';

[[highlight]]ButtonElement genButton;[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Variáveis de alto level são nomeadas a nivel de bibliotecas.

* ButtonElement é um dos diferentes tipos de elementos DOM 
fornecidos pela biblioteca.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Prepare o botão com um gerenciador de eventos.
Wire up the button with an event handler.

</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void main() {
  querySelector('#inputName').onInput.listen(updateBadge);
  [[highlight]]genButton = querySelector('#generateButton');
  genButton.onClick.listen(generateBadge);[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* `onClick` registra um gestors de clickes de mouse.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Inclua uma função de alto nivel que altere o nome do crachá.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
...

[[highlight]]void setBadgeName(String newName) {
  querySelector('#badgeName').text = newName;
} [[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* A função atualiza a página HTML com o novo nome.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Implementando o gerenciador de clique do botão.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
...

[[highlight]]void generateBadge(Event e) {
  setBadgeName('Anne Bonney');
}[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Esta função configura o crachá com o nome `Anne Bonney`.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>
Modificando o `updateBadge()` para chamar `setBadgeName()`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void updateBadge(Event e) {
[[highlight]]  String inputName = [[/highlight]](e.target as InputElement).value;
[[highlight]]  setBadgeName(inputName);[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Atribuindo valor do campo de texto a uma variável string local.

</div></div>


<div class="trydart-step-details" markdown="1">

<hr>

Incluindo um comando if-else no `updateBadge()`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void updateBadge(Event e) {
  String inputName = (e.target as InputElement).value;
  setBadgeName(inputName);
[[highlight]]  if (inputName.trim().isEmpty) {
    // To do: add some code here.
  } else {
    // To do: add some code here.
  }[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* A class `String` possui funções e propriedades uteis
para se trabalhar com informações de texto,
como por exemplo `trim()` e `isEmpty`.

* String vem da biblioteca `dart:core`,
que é importada automaticamente em todos os programas Dart.

* Dart tem comandos padrões das linguagens de programação como `if`-`else`.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Agora preencha o comando if-else para modificar o botão como preciso.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void updateBadge(Event e) {
  String inputName = (e.target as InputElement).value;
  setBadgeName(inputName);
  if (inputName.trim().isEmpty) {
    [[highlight]]genButton..disabled = false
             ..text = 'Aye! Gimme a name!';[[/highlight]]
  } else {
    [[highlight]]genButton..disabled = true
             ..text = 'Arrr! Write yer name!';[[/highlight]]
  }
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* O opetador cascata (`..`) permite que você realize multiplas
operações no 'membros' de um objeto simples.

* o código do `updateBadge()` utiliza o operador cascata
para configura duas propriedades do elemento botão.
O resultado é o mesmo que mais extenso a seguir:

<pre>
genButton.disabled = false;
genButton.text = 'Aye! Gimme a name!';
</pre>

</div></div>


### <i class="fa fa-anchor"> </i> Executando a aplicação.

<div class="trydart-step-details" markdown="1">

Salve seus arquivos no **File > Save All**.

Utilize o botão Run
<img src="images/run.png" width="16" height="16"
     alt="Run button">
no Dart Editor para executar a aplicação.

Compare sua aplicação com a que esta rodando abaixo.

Digite no campo de texto.
Remova o texto do campo de texto.
Clique no botão.

<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/3-buttonbadge/piratebadge.html">
</iframe>


#### Problemas?

Verifique seu código utilizando os arquivos na pasta `3-buttonbadge`.

* [piratebadge.html](https://github.com/dart-lang/one-hour-codelab/blob/master/web/3-buttonbadge/piratebadge.html)

* [piratebadge.dart](https://github.com/dart-lang/one-hour-codelab/blob/master/web/3-buttonbadge/piratebadge.dart)

</div>


<hr>

##Passo 4: Crie uma classe PirateName {#step-four}

Neste passo, você modificará apenas o código Dart.
Você criará a classe que representa o nome de pirata.
Quando criado, uma instancia desta classe
selecionará um nome aleatoriamente e uma apelido da lista,
ou opcionalmente você informará um nome
e um apelido para o construtor.

### <i class="fa fa-anchor"> </i> Edite o piratebadge.dart.

<div class="trydart-step-details" markdown="1">
Incluindo um importe no topo do arquivo.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
import 'dart:html';

[[highlight]]import 'dart:math' show Random;[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* Usando a palavra chave `show`,
você pode importar apenas as classes, funções ou propriedades que precise.

* `Random` prove um gerador de números aleatórios.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Incluindo uma declaração de classe no final do arquivo.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
...

[[highlight]]class PirateName {
}[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* A declaração de classe prove um nome de classe.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Criando um objeto Random como atributo da classe.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  [[highlight]]static final Random indexGen = new Random();[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* `static` define um atributo pertencente a classe. Isto é,
o gerador de numero aleatório é compartilhado com todas
as instancias desta classe.

* Dart Editor deixa italico os nomes estaticos.

* Utilize `new` para chamar o construtor.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Incluindo duas variáveis de instancias na classe,
uma para o primeiro nome e outra para o apelido.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  static final Random indexGen = new Random();
[[highlight]]  String _firstName;
  String _appellation;[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Variáveis privadas começa com underscore (`_`).

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Criando duas listas estaticas dentro da classe
que proverá uma pequena coleção de nomes e apelidos para se escolher.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...
[[highlight]]  static final List names = [
    'Anne', 'Mary', 'Jack', 'Morgan', 'Roger',
    'Bill', 'Ragnar', 'Ed', 'John', 'Jane' ];
  static final List appellations = [
    'Black','Damned', 'Jackal', 'Red', 'Stalwart', 'Axe',
    'Young', 'Old', 'Angry', 'Brave', 'Crazy', 'Noble'];[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Variáveis `final` não podem ser alteradas.

* Lists são criadas dentro da linquagem.
Estas listas são criadas utilizando listas literais.

* A classe `List` prover APIs para listas.

</div></div>


<div class="trydart-step-details" markdown="1">

<hr>

Provendo um construtor para a classe.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...
[[highlight]]  PirateName({String firstName, String appellation}) {
    if (firstName == null) {
      _firstName = names[indexGen.nextInt(names.length)];
    } else {
      _firstName = firstName;
    }
    if (appellation == null) {
      _appellation = appellations[indexGen.nextInt(appellations.length)];
    } else {
      _appellation = appellation;
    }
  }[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Os construtores possuem o mesmo nome da classe.

* Os parametros entre as chaves (`{` and `}`) são opcionais, parametros nominados.

* A função `nextInt()` recupera um novo inteiro aleatório
de gerador de número aleatório.

* Utiliza-se colchetes (`[` and `]`) como indice de uma lista.

* A propriedade `length` retorna o numero de itens na lista.

* O código utiliza um número aleatório como indice da lista.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Providenciando um 'acessor' para o nome do pirata.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...
[[highlight]]  String get pirateName =>
    _firstName.isEmpty ? '' : '$_firstName the $_appellation';[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div><div class="col-md-5" markdown="1">

* Acessores são um metodo especial que prover acesso de escrita a um atributo do objeto.

* O operador ternario `?:` é um atalho para a estrutura if-then-else.

* Interpolação de texto
(`'$_firstName the $_appellation'`)
permite que você construa strings de outros objetos.

* A sintaxe seta (` => expr; `) é um atalho para `{ return expr; }`.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Modifique a função `setBadgeName()` para utilizar o PirateName em vez de uma string:
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void setBadgeName([[highlight]]PirateName[[/highlight]] newName) {
  querySelector('#badgeName').text = newName[[highlight]].pirateName[[/highlight]];
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div><div class="col-md-5" markdown="1">

* Este código chama os acessores para recuperar os PirateName com o um texto.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Alterando `updateBadge()` para gerar o PirateName baseado no valor do campo de texto.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void updateBadge(Event e) {
  String inputName = (e.target as InputElement).value;
  
  [[highlight]]setBadgeName(new PirateName(firstName: inputName));[[/highlight]]
  ...
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div><div class="col-md-5" markdown="1">

* A chamada o construtor prover um valor para um parametro nominal opcional.

</div></div>

<div class="trydart-step-details" markdown="1">

<hr>

Alterando `generateBadge()` para gerar uma instancia PirateName utilizando `Anne Bonney`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void generateBadge(Event e) {
  setBadgeName([[highlight]]new PirateName()[[/highlight]]);
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div><div class="col-md-5" markdown="1">

* Neste caso, a chamada ao construtor não passa parametros.

</div></div>

### <i class="fa fa-anchor"> </i> Run the app.

<div class="trydart-step-details" markdown="1">
  
Salve seus arquivos com **File > Save All**.

Use o botão Run
<img src="images/run.png" width="16" height="16"
     alt="Run button">
no Dart Editor para executar a aplicação.

Compare sua aplicação com a que roda abaixo.

Digite no campo de texto.
Remova o texto do campo de texto.
Clique no botão.

<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/4-classbadge/piratebadge.html">
</iframe>


#### Problemas?

Verifique seu código utilizando os arquivos em `4-classbadge`.

* [piratebadge.html](https://github.com/dart-lang/one-hour-codelab/blob/master/web/4-classbadge/piratebadge.html)

* [piratebadge.dart](https://github.com/dart-lang/one-hour-codelab/blob/master/web/4-classbadge/piratebadge.dart)

</div>


<hr>


##Step 5: Salvando no repositório local {#step-five}

Neste passo, você dará a aplicação alguma forma de armazenamento
salvando o nome do crachá no repositório local após cada mudança.
Quando você reiniciar a aplicação,
essa inicializará com o crachá com o nome salvo.

### <i class="fa fa-anchor"> </i> Editando o piratebadge.dart.

<div class="trydart-step-details" markdown="1">
Impotando o conversor JSON da biblioteca `dart:convert`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
import 'dart:html';
import 'dart:math' show Random;
[[highlight]]
import 'dart:convert' show JSON;[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* `JSON` prove acessos aos mais comuns casos de uso do JSON.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Incluindo um construtor nominado a classe PirateName.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...
[[highlight]]  PirateName.fromJSON(String jsonString) {
    Map storedName = JSON.decode(jsonString);
    _firstName = storedName['f'];
    _appellation = storedName['a'];
  }[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* O construtor criada uma nova instancia do PirateName da string contendo JSON.

* `PirateName.fromJson` é um construdor nominado.

* `JSON.decode()` converte uma string com json em objetos Dart.

* O nome pirata é decodificado em um objeto `Map`.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Inclua um acessor a classe PirateName
que codifique o nome pirata em uma string JSON.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...
  [[highlight]]String get jsonString => '{ "f": "$_firstName", "a": "$_appellation" } ';[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* O acessor formata a texto JSON utilizando o formato de mapa.

</div> </div>


<div class="trydart-step-details" markdown="1">

<hr>

Declarando uma variável global.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
[[highlight]]final String TREASURE_KEY = 'pirateName';[[/highlight]]

void main() {
  ...
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Você guarda o par chave-valor no repositório local. Este texto é uma chave.
O valor é o nome de pirata.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Salvando o nome pirata quando o nome do crachá mudar.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void setBadgeName(PirateName newName) {
  [[highlight]]if (newName == null) {
    return;
  }[[/highlight]]
  querySelector('#badgeName').text = newName.pirateName;
  [[highlight]]window.localStorage[TREASURE_KEY] = newName.jsonString;[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* O repositório local é disponibilizado pelo `Window` do navegador.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Incluindo um função global chamada `getBadgeNameFromStorage()`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void setBadgeName(PirateName newName) {
  ...
}

[[highlight]]PirateName getBadgeNameFromStorage() {
  String storedName = window.localStorage[TREASURE_KEY];
  if (storedName != null) {
    return new PirateName.fromJSON(storedName);
  } else {
    return null;
  }
}[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* A função recupera o nome pirata do repositório local
e cria um objeto PirateName com isto.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

<div class="trydart-step-details" markdown="1">
<hr>
Chamando a função da função `main()`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void main() {
  ...
  [[highlight]]setBadgeName(getBadgeNameFromStorage());[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Inicializando o nome do crachá utilizando o repositório local.

&nbsp; {% comment %} non-breaking space required for bootstrap/markdown bogosity {% endcomment %}

</div> </div>

### <i class="fa fa-anchor"> </i> Execute a aplicação.

<div class="trydart-step-details" markdown="1">
  
Salve seus arquivos com  **File > Save All**.

Use o botão Run
<img src="images/run.png" width="16" height="16"
     alt="Run button">
no Dart Editor para executar a aplicação.

Compare sua aplicação com a que roda abaixo.

Clique no botão para incluir um nome no crachá.
Inicie a aplicação novamente duplicando a janela.

<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/5-localbadge/piratebadge.html">
</iframe>


#### Problemas?

Verifique seu código utilizando os arquivos em `5-localbadge`.

* [piratebadge.html](https://github.com/dart-lang/one-hour-codelab/blob/master/web/5-localbadge/piratebadge.html)

* [piratebadge.dart](https://github.com/dart-lang/one-hour-codelab/blob/master/web/5-localbadge/piratebadge.dart)

</div>


<hr>


##Passo 6: Lendo nome no arquivo json {#step-six}

Neste passo, vamos alterar a classe PirateName para recuperar
a lista de nomes e apelidos do arquivo JSON.
Isto nos da a chance de incluir mais nomes e
apelidos ao programa.

### <i class="fa fa-anchor"> </i> Criando piratenames.json.

<div class="trydart-step-details" markdown="1">
Use **File > New File...** para criar um arquivo do tipo JSON
com o nome `piratenames.json` com os dados a seguir.

Coloque o arquivo na pasta `1-blankbadge` junto com o código Dart
e o arquivo HTML que editamos.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
{ "names": [ "Anne", "Bette", "Cate", "Dawn",
            "Elise", "Faye", "Ginger", "Harriot",
            "Izzy", "Jane", "Kaye", "Liz",
            "Maria", "Nell", "Olive", "Pat",
            "Queenie", "Rae", "Sal", "Tam",
            "Uma", "Violet", "Wilma", "Xana",
            "Yvonne", "Zelda",
            "Abe", "Billy", "Caleb", "Davie",
            "Eb", "Frank", "Gabe", "House",
            "Icarus", "Jack", "Kurt", "Larry",
            "Mike", "Nolan", "Oliver", "Pat",
            "Quib", "Roy", "Sal", "Tom",
            "Ube", "Val", "Walt", "Xavier",
            "Yvan", "Zeb"],
  "appellations": [ "Awesome", "Black", "Captain", "Damned",
            "Even", "Fighter", "Great", "Hearty",
            "Irate", "Jackal", "King", "Lord",
            "Mighty", "Noble", "Old", "Powerful",
            "Quick", "Red", "Stalwart", "Tank",
            "Ultimate", "Vicious", "Wily", "aXe",
            "Young", "Zealot",
            "Angry", "Brave", "Crazy", "Damned",
            "Eager", "Fool", "Greedy", "Hated",
            "Idiot", "Jinxed", "Kind", "Lame",
            "Maimed", "Naked", "Old", "Pale",
            "Queasy", "Rat", "Sandy", "Tired",
            "Ugly", "Vile", "Weak", "Xeric",
            "Yellow", "Zesty"]}
{% endprettify %}
</div>

<div class="trydart-filename">piratenames.json</div>

</div> <div class="col-md-5" markdown="1">

<i class="fa fa-key"> </i> <strong> Informações importantes </strong>

* O arquivo contem um map no formato JSON,
que contem duas listas de strings.

</div> </div>

### <i class="fa fa-anchor"> </i> Editando piratebadge.html.

<div class="trydart-step-details" markdown="1">
Desabilitando o campo de texto e o botão.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify html %}
...
  <div>
    <input type="text" id="inputName" maxlength="15" [[highlight]]disabled[[/highlight]]>
  </div>
  <div>
    <button id="generateButton" [[highlight]]disabled[[/highlight]]>Aye! Gimme a name!</button>
  </div>
...
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.html</div>

</div> <div class="col-md-5" markdown="1">


* O código Dart habilita o campo de texto e
o botão após os nomes de pirata serem recuperados com sucesso
do arquivo JSON.

</div> </div>

### <i class="fa fa-anchor"> </i> Editando piratebadge.dart.

<div class="trydart-step-details" markdown="1">

Incluindo uma importação no topo do arquivo.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
import 'dart:html';
import 'dart:math' show Random;
import 'dart:convert' show JSON;

[[highlight]]import 'dart:async' show Future;[[/highlight]]
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* A biblioteca `dart:async` é dispobilizada para programação assincrona.

* O `Future` disponibiliza uma forma de recuperar um valor no futuro.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>
Substituindo as listas `names` e `appellations` por listas lista vazias e estaticas.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...
  [[highlight]]static List<String> names = [];
  static List<String> appellations = [];[[/highlight]]
  ...
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* **Certifique-se de remover o `final` das declarações das listas.**

* `[]` é equivalente a `new List()`.

* A lista é uma tipo _generico_&mdash;a de lista que pode ter qualquer tipo de objeto.
Se a intenção for de ter apenas textos,
deve-se declarar como `List<String>`.

</div> </div>

<div class="trydart-step-details" markdown="1">

<hr>

Incluindo duas funções estaticas a classe PirateName:
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
class PirateName {
  ...

  [[highlight]]static Future readyThePirates() {
    var path = 'piratenames.json';
    return HttpRequest.getString(path)
        .then(_parsePirateNamesFromJSON);
  }
  
  static _parsePirateNamesFromJSON(String jsonString) {
    Map pirateNames = JSON.decode(jsonString);
    names = pirateNames['names'];
    appellations = pirateNames['appellations'];
  }[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* `HttpRequest` é utilizado para recuperar dados de uma URL.

* `getString()` é um metodo que simplifica a requisição 
utilizando GET que retorne um texto.

* O código utiliza `Future` para realizar um GET assincrono.

* A função de retorno para `.the()` é chamada quando
o Future completa com sucesso.

* Quando o Future completa com sucesso,
os nomes de pirata são lidos do arquivo JSON.

* `readyThePirates` retorna um Future assim o programa principal tem a
possibilidade de fazer algo após o arquivo ser lido.

</div> </div>

<div class="trydart-step-details" markdown="1">
<hr>
Add a top-level variable.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
[[highlight]]SpanElement badgeNameElement;[[/highlight]]

void main() {
  ...
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Atribuindo o elemento span a uma variável em vez de procurar por ele no DOM.

</div> </div>

<div class="trydart-step-details" markdown="1">
<hr>
Realize estas alterações na função `main()`.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void main() {
  [[highlight]]InputElement inputField = querySelector('#inputName');
  inputField.onInput.listen(updateBadge);[[/highlight]]
  genButton = querySelector('#generateButton');
  genButton.onClick.listen(generateBadge);
  
  [[highlight]]badgeNameElement = querySelector('#badgeName');[[/highlight]]
  ...
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Atribuindo o elemento span a uma variável global.
Tambem, atribuiremos o elemento input a uma variável global.


</div> </div>

<div class="trydart-step-details" markdown="1">
<hr>
Após, inclua o código para recuperar os nomes do arquivo JSON,
manipule tanto o sucesso como tambem a falha.
</div>

<div class="row"> <div class="col-md-7">

<div class="trydart-step-details">
{% prettify dart %}
void main() {
  ...
  
[[highlight]]  PirateName.readyThePirates()
    .then((_) {
      //on success
      inputField.disabled = false; //enable
      genButton.disabled = false;  //enable[[/highlight]]
      setBadgeName(getBadgeNameFromStorage());
    [[highlight]]})
    .catchError((arrr) {
      print('Error initializing pirate names: $arrr');
      badgeNameElement.text = 'Arrr! No names.';
    });[[/highlight]]
}
{% endprettify %}
</div>

<div class="trydart-filename">piratebadge.dart</div>

</div> <div class="col-md-5" markdown="1">

* Chame a função `readyThePirates()`,
que retorna uma Future.

* Quando a Future completar com sucesso,
a função de retorno `then()` é chamada.

* Use o sublilhado (`_`) como um nome de parametro
que indica que o parametro é ignorado.

* A função de retorno habilita a UI
e pega os nomes guardados.

* Se a Future encontrar um erro
a função de retorno `catchError` é chamada
e o programa mostra uma mensagem de erro,
deixando a UI desabilitada.

* A função de retorno para o `then()` e `catchError`

* The callback functions for `then()` and `catchError` são definidos na hora.

</div> </div>

### <i class="fa fa-anchor"> </i> Run the app.

<div class="trydart-step-details" markdown="1">
  
Salve seus arquivos com  **File > Save All**.

Use o botão Run
<img src="images/run.png" width="16" height="16"
     alt="Run button">
no Dart Editor para executar a aplicação.

Se você quiser quiser ver o que acontece quando a aplicação não acha o arquivo `.json`,
altere o nome do arquivo no código e rode o programa novamente.

Compare seu programa com a versão final rodando a seguir.

<iframe class="running-app-frame"
        style="height:220px;width:550px;"
        src="examples/6-piratebadge_json/piratebadge.html">
</iframe>


#### Problemas?

Verifique seu código utilizando os arquivos em `6-piratebadge_json`.

* [piratebadge.html](https://github.com/dart-lang/one-hour-codelab/blob/master/web/6-piratebadge_json/piratebadge.html)

* [piratebadge.dart](https://github.com/dart-lang/one-hour-codelab/blob/master/web/6-piratebadge_json/piratebadge.dart)

</div>

### <i class="fa fa-anchor"> </i> Share your pirate name.

<div class="trydart-step-details" markdown="1">

Parabens! Você finalizou o laboratório de código crachá de pirata.

Compartilhe seu nome de pirata com o mundo.

<p class="share-button twitter">
<a href="https://twitter.com/share"
   class="twitter-share-button external-link"
   data-count="none"
   data-text="Arrr! I've generated me pirate name and learnt Dart, to boot. http://dartlang.org/darrrt"
   data-hashtags="dartlang">Tweet</a>
 </p>

<script src="https://apis.google.com/js/plusone.js"></script>
<g:plus action="share"></g:plus>

</div>


<hr>

##Passo 7: Vá em frente e aprenda mais sobre Dart {#step-seven}

### <i class="fa fa-anchor"> </i> Pense no que você fez.

<div class="trydart-step-details" markdown="1">

O código do laboratório prove um passeio por muitos recursos da linguagem Dart
e muitas recusos das bibliotecas.
Aqui esta alguns locais onde podemos aprender mais.

#### The Dart language

<a href="https://www.dartlang.org/docs/dart-up-and-running/contents/ch02.html">
Um passeio pela linguagem Dart</a>
te mostra como usar os recursos mais importantes do Dart,
de variáveis e operadores a classes e bibliotecas.
Este laboratório de código  introduziu os seguintes recursos,
todos os quais são cobertos com mais detalhes no passeio pela linguagem.

* interpolação de strings (`'$_firstName the $_appellation'`)
* o operador 'cascade' (`..`)
* o operador seta (`=>`) sintaxe da função
* o operador ternário (`?:`)
* costrutores nominados (`PirateName.fromJSON(...)`)
* parenteses optionais
* a classe
* acessores
* metodos e campos de instancia
* metodos e campos de class
* variáveis e funções de nível superior
* conversão de tipo com `as` (`(e.target as InputElement)`)
* importação, e importação com `show` (`import 'dart:math' show Random;`)
* generics

#### The Dart libraries

<a href="https://www.dartlang.org/docs/dart-up-and-running/contents/ch03.html">
A Tour of the Dart Libraries</a>
shows you how to use the major features in Dart’s libraries.

#### API documentation for classes

<a href="https://api.dartlang.org/dart_core/String.html" target="_blank">String</a>,
<a href="https://api.dartlang.org/dart_core/List.html" target="_blank">List</a>,
<a href="https://api.dartlang.org/dart_core/Map.html" target="_blank">Map</a>,
<a href="https://api.dartlang.org/dart_math/Random.html" target="_blank">Random</a>,
<a href="https://api.dartlang.org/dart_html/InputElement.html" target="_blank">InputElement</a>,
<a href="https://api.dartlang.org/dart_html/ButtonElement.html" target="_blank">ButtonElement</a>,
<a href="https://api.dartlang.org/dart_html/Event.html" target="_blank">Event</a>,
<a href="https://api.dartlang.org/dart_html/HttpRequest.html" target="_blank">HttpRequest</a>, and
<a href="https://api.dartlang.org/dart_async/Future.html" target="_blank">Future</a>

#### API documentation for libraries

<a href="https://api.dartlang.org/dart_core.html" target="_blank">dart:core</a>,
<a href="https://api.dartlang.org/dart_math.html" target="_blank">dart:math</a>,
<a href="https://api.dartlang.org/dart_html.html" target="_blank">dart:html</a>,
<a href="https://api.dartlang.org/dart_async.html" target="_blank">dart:async</a>, and
<a href="https://api.dartlang.org/dart_convert.html" target="_blank">dart:convert</a>

#### API documentation for JSON and local storage

<a href="https://api.dartlang.org/dart_html/Window.html#localStorage" target="_blank">LocalStorage</a>, and
<a href="https://api.dartlang.org/dart_convert.html#JSON" target="_blank">JSON</a>


</div>

### <i class="fa fa-anchor"> </i> Check out the samples.

<div class="trydart-step-details" markdown="1">

Run some Dart programs online and check out the source code
on our [Samples page](/samples/).
</div>

### <i class="fa fa-anchor"> </i> Read the tutorials.

<div class="trydart-step-details" markdown="1">
Learn more about Dart from
the [Dart tutorials](/docs/tutorials/).
</div>

