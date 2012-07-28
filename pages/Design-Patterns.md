---
layout: page
title: Padrões de Design
---

# Padrões de Design

Existem inúmeras formas de estruturar o código e o projeto de sua aplicação web, e você pode colocar tanto quanto
quiser em sua arquitetura. Mas, normalmente, é uma boa ideia seguir alguns padrões de design comuns, porque isso
fará com que seu código fique mais fácil para manter e também para que outros entendam.

* [Padrões de arquitetura na Wikipedia](https://en.wikipedia.org/wiki/Architectural_pattern)
* [Padrões de design de software na Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern)

## Factory

Um dos padrões de design mais comumente utilizados é o padrão Factory, ou fábrica. Nesse padrão, uma classe apenas
cria uma instância do objeto que você deseja utilizar. Considere o seguinte exemplo do padrão Factory:

{% highlight php %}
<?php
class Automobile
{
    private $vehicle_make;
    private $vehicle_model;

    public function __construct($make, $model)
    {
        $this->vehicle_make = $make;
        $this->vehicle_model = $model;
    }

    public function get_make_and_model()
    {
        return $this->vehicle_make . ' ' . $this->vehicle_model;
    }
}

class AutomobileFactory
{
    public static function create($make, $model)
    {
        return new Automobile($make, $model);
    }
}

// have the factory create the Automobile object
$veyron = AutomobileFactory::create('Bugatti', 'Veyron');

print_r($veyron->get_make_and_model()); // outputs "Bugatti Veyron"
{% endhighlight %}

Esse código utiliza uma fábrica para criar o objeto Automobile. Existem dois benefícios ao escrever seu código dessa
forma, o primeiro é que se você precisar modificar, renomear ou substituir a classe Automobile, você pode fazê-lo
e precisará apenas modificar apenas a fábrica, em vez de ter que modificar diversos pontos no seu código que utilizam
a classe Automobile. O segundo benefício é que, se a criação do objeto for algo complexo, você pode deixar toda essa
complexidade dentro da fábrica em vez de ter que ficar repetindo essa tarefa diversas vezes, sempre que precisar de
uma nova instância daquele objeto.

Utilizar o padrão factory nem sempre é algo necessário (ou inteligente). O exemplo utilizado aqui é tão simples que
a fábrica apenas adicionaria uma complexidade desnecessária. Contudo, se você estiver trabalhando em um projeto muito
grande ou complexo você poderá evitar problemas se estiver utilizando fábricas.

* [Padrão Factory na Wikipedia](https://en.wikipedia.org/wiki/Factory_pattern)

## Front Controller

O padrão front controller é quando você tem apenas um ponto de entrada para sua aplicação (ex: index.php) que faz
a manipulação de todas as requisições. Este código é responsável por carregar todas as dependências, processar a
requisição e enviar respostas para o navegador. O padrão front controller pode ser benéfico porque encoraja a 
escrever código modular e lhe dá um ponto central para lidar com o código que deverá ser executado para cada 
requisição (como sanitização das entradas do usuário).

* [Padrão Front Controller na Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Model-View-Controller

O padrão model-view-controller (MVC) e suas derivações HMVC e MVVM permitem que você divida seu código em objetos 
lógicos que servem para propósitos específicos. As models servem como uma camada de acesso onde dados são obtidos
e retornados em formatos utilizáveis pela sua aplicação. Controllers manipulam requisições, processam os dados
retornados pelas models e carregam as Views para serem enviadas na resposta. E as Views são templates para exibição
(marcação, xml, etc) que serão enviadas na resposta para o navegador.  

MVC é o padrão arquitetural mais comumente utilizado nos [frameworks PHP](https://github.com/codeguy/php-the-right-way/wiki/Frameworks) 
mais populares.

Aprenda mais sobre MVC e suas derivações:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
