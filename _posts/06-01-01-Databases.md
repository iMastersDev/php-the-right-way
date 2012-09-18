---
title: Databases
---

# Bancos de dados

Muitas vezes seu código PHP usará um banco de dados para dar persistência à informação. Você tem alguma opções para conectar e interagir com seu banco de dados. A opção recomendada _até o PHP PHP 5.1.0_ era usar drivers nativos como [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql], etc.

Drivers nativos são ótimos se você está usando apenas UM banco de dados em sua aplicação, mas se, por exemplo, você está usando MySQL e um pouco de MSSQL, ou precisa se conectar a um banco de dados Oracle, então você não será capaz de usar os mesmos drivers. Você precisará aprender uma API totalmente nova para cada banco de dados &mdash; e isso pode se tornar chato.

Como uma nota extra sobre os drivers nativos, a extensão mysql para o PHP não está mais em desenvolvimento e o status oficial desde o PHP 5.4.0 é "Long term deprecation". Isso significa que ela será removida dentro de alguns próximos release, então no PHP 5.6 (ou qualquer um depois do 5.5) ela deverá estar fora. Se você está usando `mysql_connect()` e `mysql_query()` em suas aplicações, então você irá deparar em algum momento com a necessidade de reescrita, logo a melhor opção é substituir o uso de de mysql por mysqli ou PDO em suas aplicações ou dentro de seu próprio esquema de desenvolvimento para evitar reescrever às pressas mais tarde. _Se você está começando do zero então definitivamente não use a extensão mysql: use a [extensão MySQLi][mysqli], ou use PDO._

* [PHP: Escolhendo uma API para MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO é uma biblioteca de abstração a conexão com banco de dados &mdash;  presente no PHP desde 5.1.0 &mdash; ela fornce uma interface comum para se comunicar com vários bancos de dados diferentes. PDO não traduzirá suas consultas SQL nem simulará funções que estejam faltando; é puramente para se conectar a múltiplos tipos de bancos de dados com a mesma API.

Mais importante ainda, `PDO` lhe permite usar entradas desconhecidas(IDs, por exemplo) em suas consultas SQL sem precisar se preocupar com ataques de SQL inject.
Isso é possível usando declarações PDO e parâmetros associados.

Vamos pensar num script PHP que recebe uma ID numérica como o parâmetro de uma consulta. Esta ID deve ser usada para pegar o registro de um usuário no banco de dados. Esta é a maneira errada de fazê-lo:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

Este código é horrível. Você está inserindo um parâmetro desprotegido dentro de uma consulta SQL. Isso vai fazer você ser _hackeado_ num piscar de olhos. Em vez disso, você deve limpar a entrada ID usando parâmetros associados do PDO.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Automaticamente limpa pelo PDO
$stmt->execute();
{% endhighlight %}

Este código é correto. Ele usa um parâmetro associado em uma declaração PDO. Isto _escapa_ a entrada desconhecida de ID antes que ela seja introduzida ao banco de dados, prevenindo potenciais ataques de SQL inject.

* [Aprenda sobre PDO][1]

## Camadas de abstração

Many frameworks provide their own abstraction layer which may or may not sit on top of PDO.  These will often emulate features for
one database system that another is missing form another by wrapping your queries in PHP methods, giving you actual database abstraction.
This will of course add a little overhead, but if you are building a portable application that needs to work with MySQL, PostgreSQL and
SQLite then a little overhead will be worth it the sake of code cleanliness.

Some abstraction layers have been built using the PSR-0 namespace standard so can be installed in any application you like:

* [Doctrine2 DBAL][2]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db

[mysql]: http://uk.php.net/mysql
[mysqli]: http://uk.php.net/mysqli
[pgsql]: http://uk.php.net/pgsql
