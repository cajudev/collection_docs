===============
1. Introduction
===============

1.1 Analyzing the class structure
---------------------------------

This class has two attributes: ``content``, and ``length``.

Both have ``protected`` visibility, allowing you to use inheritance if you need to.

The ``content`` attribute stores all values added to the object, while
the ``length`` attribute, stores the current size of the array, making
unnecessary the use of the function ``count()``.

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

1.2 Creating an instance from an array
--------------------------------------

You can initialize the object by passing an array to the constructor

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

1.3 Creating an instance from another Collection
------------------------------------------------

You can also easily pass an object of this class as an argument
for the constructor, it will be converted.

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

1.4 Creating an instance from other objects
-------------------------------------------

Other objects passed by parameter will be treated in a special way,
being parsed internally.

Note that the visibility of attributes does not affect parsing.

.. code:: php

   use Cajudev\Collection;

   $object = new Class() {
      private $lorem  = 1;
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