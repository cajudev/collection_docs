=======================
7. Notação de Intervalo
=======================

7.1 Acessando Valores
---------------------

É possível receber parte de um objeto Arrays, através da notação de intervalo.

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'zero'  => 0, 'one'  => 1, 'two' => 2, 'three' => 3,
        'four'  => 4, 'five' => 5, 'six' => 6, 'seven' => 7,
        'eight' => 8, 'nine' => 9, 'ten' => 10
    ]);

    echo $collection['2:5']; // {"two":2,"three":3,"four":4,"five":5}

Caso você informe um valor inicial maior que o valor final, o resultado será
um array inverso do intervalo definido. 

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'zero'  => 0, 'one'  => 1, 'two' => 2, 'three' => 3,
        'four'  => 4, 'five' => 5, 'six' => 6, 'seven' => 7,
        'eight' => 8, 'nine' => 9, 'ten' => 10
    ]);

    echo $collection['6:3']; // {"six":6,"five":5,"four":4,"three":3}
    

7.2 Inserindo Valores
---------------------

Uma maneira fácil de inicializar várias posições no array com um valor padrão.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection['0:5'] = 'lorem';
   echo $collection; // ["lorem","lorem","lorem","lorem","lorem","lorem"]

7.3 Verificando Nulidade
------------------------

Verifique a existência de multiplas posições no array.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['a', 'b', 'c', 'd', 'e']);

   $collection->isset('0:4'); // true
   isset($collection['0:4']); // true

   $collection->isset('0:5'); // false
   isset($collection['0:5']); // false

7.4 Apagando Intervalos
-----------------------

Remova diversos valores do array.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['a', 'b', 'c', 'd', 'e']);

   $collection->unset('0:2');
   echo $collection; // {"3":"d","4":"e"}