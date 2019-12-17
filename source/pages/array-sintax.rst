===================
4. Sintaxe de Array
===================

É possível manipular esta classe com a sintaxe de array ``$array[$key]``.

4.1 Inserindo valores
---------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection['lorem'] = 'ipsum';
   $collection[] = 'dolor';

   print_r($collection);

   /*
    Cajudev\Collection Object
        (
            [content:protected] => Array
                (
                    [lorem] => ipsum
                    [0] => dolor
                )
            [length:Cajudev\Collection:protected] => 2
        )
   */

4.2 Acessando valores
---------------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code:: php

   $collection = new Collection();

   $collection['lorem'] = 'ipsum';

   echo $collection['lorem']; // ipsum

Diferentemente do método ``get`` que nos retorna ``null`` em casos de chave inexistente tornando não
necessário o uso de verificações, a sintaxe de array requer um pequeno cuidado.

Caso você tente acessar uma posição inexistente, essa posição será inicializada como um array.

.. code:: php

   $collection = new Collection();

   $var = $collection['lorem'];

   print_r($collection);

   /*
   Cajudev\Collection Object
      (
         [content:protected] => Array
            (
                  [lorem] => Array
                     (
                     )

            )

         [length:protected] => 1
      )
   */


Nesses casos sempre verifique antes utilizando o método ``isset()``, ou o operador de coalescência ``??``.

.. code:: php

   $collection = new Collection();

   echo $array->isset('lorem') ? $array['lorem'] : null; // null

   echo $array['lorem'] ?? null; // null