=====================
15. Métodos Estáticos
=====================

15.1 isCollection
-----------------

Verifica se dado objeto é uma instância da classe Collection ou que extenda dela

.. code:: php

   use Cajudev\Collection;

   Collection::isCollection(new Collection()); // true

   Collection::isCollection(10); // false

15.2 Combine
-------------

Combina dois arrays/objetos em um novo objeto, utilizando o primeiro para chaves e o segundo para valores.
Ambos os argumentos podem ser simples arrays ou objetos dessa classe.

.. code:: php

   use Cajudev\Collection;

   $array = ['lorem', 'ipsum', 'dolor'];

   $collection = new Collection([1, 2, 3]);

   $result = Collection::combine($array, $collection);

   echo $result; // {"lorem":1,"ipsum":2,"dolor":3}

15.3 Range
-------------

Cria um objeto collection a partir de um intervalo

.. code:: php

   use Cajudev\Collection;

   $numbers = Collection::range($start = 10, $end = 20, $step = 2);

   echo $numbers; // [10, 12, 14, 16, 18, 20]
   

   $letters = Collection::range($start = 'A', $end = 'F');

   echo $letters; // ["A", "B", "C", "D", "E", "F"]
