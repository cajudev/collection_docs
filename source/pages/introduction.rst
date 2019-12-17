=============
1. Introdução
=============

1.1 Analisando a estrutura da classe
------------------------------------

Esta classe possui dois atributos: ``content``, e ``length``.

Ambos possuem visibilidade ``protected``, permitindo com que você use herança caso necessite.

O atributo ``content`` armazena todo o conteúdo adicionado ao objeto, enquanto 
o atributo ``length``, armazena o tamanho atual do array, tornando
desnecessário o uso de funções como ``count()``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   print_r($collection);

   /*
      Cajudev\Collection Object
      (
         [content:protected] => Array
            (
            )

         [length:protected] => 0
      )
   */

1.2 Criando uma instância a partir de um array
----------------------------------------------

Você pode inicializar o objeto passando um array para o seu construtor.

.. code:: php

   use Cajudev\Collection;

   $array = [1, '2', 'three' => 3];

   $collection = new Collection($array);
   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                     [0] => 1
                     [1] => 2
                     [three] => 3
               )
            [length:Cajudev\Collection:protected] => 3
         )
   */

1.3 Criando uma instância a partir de outro Collection
------------------------------------------------------

Você também pode sem problemas passar como argumento um objeto desta classe
para o construtor, ele será convertido internamente.

.. code:: php

   use Cajudev\Collection;

   $oldCollection = new Collection([1, 2, 3, 4, 5]);

   $newCollection = new Collection($oldCollection);

   print_r($newCollection); exit;

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                     [0] => 1
                     [1] => 2
                     [2] => 3
                     [3] => 4
                     [4] => 5
               )

            [length:protected] => 5
         )
   */

1.4 Criando uma instância a partir de outros objetos
----------------------------------------------------

Outros objetos passados por parâmetro serão tratados de forma especial,
sendo parseados internamente.

Observe que a visibilidade dos atributos não afeta o parseamento.

.. code:: php

   use Cajudev\Collection;

   $object = new Class() {
      protected $lorem  = 1;
      protected $ipsum  = 2;
      public    $dolor  = 3;
   };

   $collection = new Collection($object);

   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                     [lorem] => 1
                     [ipsum] => 2
                     [dolor] => 3
               )

            [length:protected] => 3
         )
   */