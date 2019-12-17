===================
6. Notação de Ponto
===================

Uma característica muito interessante que essa classe possui é a possibilidade
de navegar entre seu conteúdo utilizando a notação de ponto.

6.1 Inserindo valores
---------------------

Para criar collections multidimensionais facilmente, sem a utilização de milhares de colchetes,
basta realizar a atribuição com a notação de ponto, como no exemplo abaixo:

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection['lorem.ipsum.dolor'] = 'amet';

   print_r($collection);

   /*
   Cajudev\Collection Object
      (
         [content:protected] => Array
            (
               [lorem] => Array
                  (
                     [ipsum] => Array
                        (
                           [dolor] => amet
                        )

                  )

            )

         [length:protected] => 1
      )
   */


6.2 Acessando valores
---------------------

Da mesma forma, é possível facilmente percorrer o objeto para acessar seu conteúdo.

.. code:: php
   
   // Navegando entre os valores

   echo $collection['lorem.ipsum.1.sit.amet']; // dolor

   // Também é possível misturar as sintaxes se assim o preferir.

   echo $collection['lorem.ipsum'][1]['sit.amet']; //dolor

.. note::

   Diversos métodos também suportam essa notação, como **get**, **set**, **isset**, **empty**, entre outros.
   Todos estão descritos nessa documentação.