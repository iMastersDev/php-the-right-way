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

O padrão Front Controller implementa um único ponto de entrada para todo o trabalho na sua aplicação(ex index.php) onde selida com todas as requisições.
Tem a responsabilidade de carregar todas as dependências necessárias para o processamento de uma requisição e devolver uma resposta para o cliente(browser).
O Front Controller pode ser benéfico por encorajar código modulas e fornecer um único ponto onde se pode adicionar código a ser utilizado em todas requisição(como limpeza de dados enviados ao servidor).

* [Padrão de Projeto Front Controller na Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Model-View-Controller

O padrão mode-view-controller (MVC) e os padrões relacionados HMVC e MVVM permitem basear o código em objetos lógicos com propósitos bem específicos.
Models são utilizados como camada de acesso a dados. Onde se buscam dados entregues em um formato mais propício para a aplicação.
Controllers lidam com as requisição, processam os dados entregues pelos models e carregam as views para enviar uma resposta formatada ao cliente.
Views são templates (markup, xml e etc) que são preenchidos com dados e entregues para o cliente(browser).
 
MVC é o mais popular entre os padrõeas de projeto arquiteturais. [PHP frameworks](https://github.com/codeguy/php-the-right-way/wiki/Frameworks).

Aprenda mais sobre MVC e outros padrões semelhantes ems:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
