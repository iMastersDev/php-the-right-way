# Guia de estilo de código

A comunidade php é grande e diversificada. Criou inúmeras bibliotécas, frameworks e componentes. É comum para 
programadores PHP terem de escolher e combinar muitos desses componentes em um projeto. Por isso é tão importante 
que o código esteja de acordo com um estilo comum de codificação(tanto quanto possível para facilitar o trabalho 
dos desenvolvedores em integrar todo o código em seu projeto.


O [Framework Interop Group][fig] (formalmente conhecido como o 'PHP Standards Group') propôs e aprovou uma série de
recomendações de estilo conhecidas como [PSR-0][psr0], [PSR-1][psr1] e [PSR-2][psr2]. 
Não deixe que os nomes lhe confudam, essas recomendações são simplismente uma série de regras que alguns projetos
como Drupal, Zend, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium e etc, estão começando a aderir. 
Você pode as utilizar em seus projetos, ou continuar a utilizar seu próprio estilo.

Preferencialmente você deve escrever código que atenda a um ou mais desses padrões para que outros programadores
possam ler seu código e trabalhar com ele mais facilmente.
As regras são escritas de maneira que para utilizar a PSR-1 você tenha que utilizar a PSR-0, mas não da PSR-2.

* [Leia sobre a PSR-0][psr0]
* [Leia sobre a  PSR-1][psr1]
* [Leia sobre a PSR-2][psr2]

Você pode utilizar o [phpcs-psr][phpcs-psr] para verificar seu código com relação a essa regras.
Para evitar fazer as correções manualmente você pode utilizar o [PHP Coding Standards Fixer][phpcsfixer]
criado por Fabien Potencier. Ele vai lhe poupar muito trabalho modificando automaticamente seu código para atender
aos padrões.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[phpcs-psr]: https://github.com/klaussilveira/phpcs-psr
[phpcsfixer]: http://cs.sensiolabs.org/
