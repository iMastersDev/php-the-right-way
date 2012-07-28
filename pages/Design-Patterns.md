---
layout: page
title: Padrões de Projeto 
---

# Padrões de Projeto 

Existem várias maneiras de organizar código e projeto para suas aplicações web, e você pode subutiliza-las ou utiliza-las exagerar no uso.

Pense em você como um arquiteto. Normalmente é uma boa idéia seguir os padrões por que isso facilita a manutenção do código e o torna mais facil de entender para os outros.
 
* [Padrões de Arquitetura na Wikipedia](https://en.wikipedia.org/wiki/Architectural_pattern)
* [Design de Software na Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern)

## Factory

Um dos design patterns mais utilizados é o Factory. Nesse padrão uma classe simplesmente cria os objetos que você necessita. Considere o exemplo a seguir de implementação do Design Pattern Factory.

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

// A Factory criou o Objeto Automobile
$veyron = AutomobileFactory::create('Bugatti', 'Veyron');

print_r($veyron->get_make_and_model()); // mostrou "Bugatti Veyron"
{% endhighlight %}

O código acima utiliza uma facotry para criar instancias do objeto Automobile e existem dois possiveis benefícios em se programar assim.
O primeiro é que em caso de mudança, mudança de nome ou substituição da classe Automobile você só tem que alterar o código da factory, ao invés do trabalho de alterar em cada lugar de seu programa em que usava diretamente a classe Automobile.
O segundo benefício possível é que se criar o objeto não for uma operação simples, a factory pode fazer todo o trabalho para você, ao invés de ficar repetindo toda a complexidade toda vez que precisar de uma instância no código. 

Utilizar o padrão factory nem sempre é necessário (ou a melhor escolha) O código utilizado como exemplo é tão simples que, nesse caso, utilizar uma factory pode ser considerado adicionar complexidade uma desnecessária, entretanto, se você estiver trabalhando em um projeto de complexidade maior, utilizar a factory pode lhe poupar muito trabalho.


* [Padrão Factory na Wikipedia](https://en.wikipedia.org/wiki/Factory_pattern)

## Front Controller

The front controller pattern is where you have a single entrance point for you web application (e.g. index.php) that
handles all of the requests. This code is responsible for loading all of the dependencies, processing the request and
sending the response to the browser. The front controller pattern can be beneficial because it encourages modular code
and gives you a central place to hook in code that should be run for every request (such as input sanitization).

* [Front Controller pattern on Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Model-View-Controller

The model-view-controller (MVC) pattern and its relatives HMVC and MVVM let you break up code into logical objects that
serve very specific purposes. Models serve as a data access layer where data it fetched and returned in formats usable
throughout your application. Controllers handle the request, process the data returned from models and load views to
send in the response. And views are display templates (markup, xml, etc) that are sent in the response to the web
browser.

MVC is the most common architectural pattern used in the popular [PHP frameworks](https://github.com/codeguy/php-the-right-way/wiki/Frameworks).

Learn more about MVC and its relatives:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
