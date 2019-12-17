====================
2. Inserindo valores
====================

2.1 Inserindo valores ao final do array
---------------------------------------

.. raw:: php
   
   <?php
   
   highlight_string('<?php function push(string ...$values): self');

O método ``push()`` aceita um número variável de argumentos e serve para adicionar (empurrar) valores ao final do array.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem', 'ipsum', 'dolor']);
   $collection->push('sit', 'amet', 'consectetur');
   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                  [0] => lorem
                  [1] => ipsum
                  [2] => dolor
                  [3] => sit
                  [4] => amet
                  [5] => consectetur
               )
            [length:Cajudev\Collection:protected] => 6
         )
   */

2.2 Inserindo valores no início do array
----------------------------------------

O método ``unshift()`` aceita um número variável de argumentos e serve para adicionar valores no início do array

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem', 'ipsum', 'dolor']);
   $collection->unshift('sit', 'amet', 'consectetur');
   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                  [0] => sit
                  [1] => amet
                  [2] => consectetur
                  [3] => lorem
                  [4] => ipsum
                  [5] => dolor
               )
               [length:Cajudev\Collection:protected] => 6
         )
   */

2.3 Associando valores à chaves
-------------------------------

O método ``set()`` é usado para associar uma chave à um valor.
Ele também suporta a notação de ponto descrita na seção 5.

.. code:: php

   $collection->set('lorem', 'ipsum');
   
   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                     [lorem] => ipsum
               )

            [length:protected] => 1
         )
   */

Realizando a associação de maneira multidimensional:

.. code:: php

   $collection->set('ipsum.dolor.amet', 'lorem');

   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                     [ipsum] => Array
                        (
                           [dolor] => Array
                                 (
                                    [amet] => lorem
                                 )

                        )

               )

            [length:protected] => 1
         )
   */

2.4 Inserindo dados por referência
----------------------------------

O método ``setByReference()`` permitir atribuir por referência um conteúdo à classe.

.. code:: php

   use Cajudev\Collection;

   $session = new Collection();

   $session->setByReference($_SESSION);
   
   $session->set('hello.world', 'Lorem');

   print_r($_SESSION);

   /*
      Array
         (
            [hello] => Array
               (
                  [world] => Lorem
               )

         )
   */

2.5 Inserindo outro Collection
------------------------------

Você irá reparar que se nós inserirmos um objeto Collection dentro de outro, 
ele não será inserido como um objeto, mas sim como um array. Isso é uma característica dessa classe.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['primeiro' => new Collection(['lorem', 'ipsum', 'dolor'])]);

   $collection->set('segundo', new Collection(['lorem', 'ipsum', 'dolor']));

   print_r($collection);

   /*
   Cajudev\Collection Object
      (
         [content:protected] => Array
            (
               [primeiro] => Array
                  (
                     [0] => lorem
                     [1] => ipsum
                     [2] => dolor
                  )

               [segundo] => Array
                  (
                     [0] => lorem
                     [1] => ipsum
                     [2] => dolor
                  )
            )
         [length:protected] => 2
      )
   */