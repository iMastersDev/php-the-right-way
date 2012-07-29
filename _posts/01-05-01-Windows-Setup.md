---
title: Configuração no Windows
isChild: true
---

## Configuração no Windows

O PHP está disponível em diversas formas para Windows. Você pode [baixar os binários](php-downloads) e, até recentemente,
você podia utilizar um instalador '.msi'. O instalador não é mais suportado, e parou na versão 5.3.0 do PHP.

Para aprendizado e para desenvolvimento local, você pode utilizar o servidor web embutido no PHP 5.4, dessa forma você
não precisará se preocupar com configuração. Se você quiser um "pacote" no qual está incluso um servidor web completo e MySQL,
então, ferramentas como o [Web Platform Installer][wpi], [Zend Server CE][zsce], [XAMPP][xampp] e [WAMP][wamp] irão ajudá-lo
a ter um ambiente de desenvolvimento rodando rapidamente no Windows. Dito isso, essas ferramentas serão um pouco diferentes
do ambiente de produção, então tome cuidado com as diferenças de ambiente, se você estiver trabalhando no Windows e
desenvolvendo para Linux.

Se você precisar rodar seu ambiente de produção no Windows, então o IIS7 dará a você um desempenho mais estável e com
maior performance. Você pode utilizar o [phpmanager][phpmanager] (um plugin de interface gráfica para IIS7) para simplificar
a configuração e gerenciamento do PHP. O IIS7 vem com FastCGI nativo e pronto para rodar, você só precisa configurar o
PHP como um manipulador.

Geralmente a execução da sua aplicação em um ambiente diferente do desenvolvimento e produção, pode levar a aparição
de bugs estranhos quando você a coloca em produção. Se você estiver desenvolvendo em um ambiente Windows e implantando
em um ambiente Linux (ou qualquer outro que não seja o Windows), então você deve considerar o uso de uma máquina virtual. Isso pode
parecer complicado, mas usando [Vagrant][vagrant] você pode configurar wrappers simples, em seguida, usando [Puppet][puppet]
ou [Chef][chef] você pode disponibilizar essas máquinas e compartilhá-las com seus colegas, para ter certeza de que todos estão trabalhando
no mesmo lugar. Mais sobre isso em breve.

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
