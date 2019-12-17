==================================
8. Verificando e Removendo Valores
==================================

8.1 Verificando Nulidade
------------------------

Para verificar a existência de uma chave no objeto, você pode utilizar o método ``isset()``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit']);

   var_dump($collection->isset('lorem')); // bool(true)
   var_dump($collection->isset('ipsum')); // bool(false)

.. hint::

   Em todos os métodos dessa página, é possível aplicar o uso da notação de ponto,
   explicada na seção 5, como no exemplo abaixo:

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([
      'lorem' => [
         'ipsum' => [
            'dolor' => [
               'sit' => 'amet'
            ]
         ],
      ]
   ]);

   var_dump($collection->isset('lorem.ipsum.dolor.sit'));     // bool(true)
   var_dump($collection['lorem.ipsum.dolor']->isset('sit')); // bool(true)

   var_dump($collection->isset('lorem.ipsum.amet'));       // bool(false)
   var_dump($collection['lorem.ipsum']->isset('amet'));   // bool(false)

Caso queira executar a lógica inversa, você pode utilizar o método ``noset()``.

.. code:: php

   var_dump($collection->noset('lorem')); // bool(false)
   var_dump($collection->noset('ipsum')); // bool(true)

8.2 Verificando Valores Vazios
------------------------------

Para verificar se uma chave do objeto é vazia, utilize o método ``empty()``.

Esse método equivale à utilização de ``!isset($collection[$key]) || $collection[$key] == false``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection['lorem'] = false;
   var_dump($collection->empty('lorem')); //bool(true);

Para verificar se um valor não é vazio, você pode utilizar o método ``filled()``, que nada mais é
do que a negação do método anterior.

Esse método equivale à utilização de ``isset($collection[$key]) && $collection[$key] == true``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection['lorem'] = false;
   var_dump($collection->filled('lorem')); //bool(false);

8.3 Removendo Valores
---------------------

Para remover um elemento do objeto utilize o método ``unset()``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([  
      'lorem' => [
         'ipsum' => [
            'dolor' => [
               'sit' => 'amet'
            ]
         ],
      ]
   ]);

   echo $collection; // {"lorem":{"ipsum":{"dolor":{"sit":"amet"}}}}

   $collection->unset('lorem.ipsum.dolor');

   echo $collection; // {"lorem":{"ipsum":[]}}
   