===================
2. Inserting values
===================

2.1 Inserting values ​​at the end of the array
--------------------------------------------

.. raw:: php
   
   <?php
   
   highlight_string('<?php function push(string ...$values): self');

The ``push()`` method takes a variable number of arguments and is used to add values ​​to the end of the array.

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

2.2 Inserting values ​​at the beginning of the array
--------------------------------------------------

The ``unshift()`` method takes a variable number of arguments and is used to add values ​​at the beginning of the array

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

2.3 Associating values ​​with keys
--------------------------------

The `` set () `` method is used to associate a value with a key.
It also supports the dot notation described in section 6.

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

Performing the association in a multidimensional way:

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

2.4 Inserting data by reference
-------------------------------

The ``setByReference()`` method allows you to assign content to the class by reference.

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

2.5 Inserting another Collection
--------------------------------

You will notice that if we insert a Collection object inside another one,
it will not be inserted as an object, but as an array. This is a characteristic of this class.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['first' => new Collection(['lorem', 'ipsum', 'dolor'])]);

   $collection->set('second', new Collection(['lorem', 'ipsum', 'dolor']));

   print_r($collection);

   /*
   Cajudev\Collection Object
      (
         [content:protected] => Array
            (
               [first] => Array
                  (
                     [0] => lorem
                     [1] => ipsum
                     [2] => dolor
                  )

               [second] => Array
                  (
                     [0] => lorem
                     [1] => ipsum
                     [2] => dolor
                  )
            )
         [length:protected] => 2
      )
   */