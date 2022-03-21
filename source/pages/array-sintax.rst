===============
4. Array Sintax
===============

It is possible to manipulate this class with the array syntax ``$array[$key]``.

4.1 Setting values
------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection['lorem'] = 'ipsum';
   $collection['sit']['amet'] = 'consectetur';
   $collection[] = 'dolor';

   print_r($collection);

   /*
    Cajudev\Collection Object
    (
        [content:protected] => Array
            (
                [lorem] => ipsum
                [sit] => Array
                    (
                        [amet] => consectetur
                    )

                [0] => dolor
            )

        [length:protected] => 3
    )
   */

4.2 Getting values
------------------

To access a previously set key, just do as usual:

.. code:: php

   $collection = new Collection();

   $collection['lorem'] = 'ipsum';
   $collection['sit']['amet'] = 'consectetur';

   echo $collection['lorem']; // ipsum
   echo $collection['sit']['amet']; // consectetur

Unlike the ``get`` method that returns ``null`` in cases of non-existing key,
the array syntax requires a little care.

If you try to access a non-existing position, that position will be initialized as an array.
This occurs to allow chained access with this sintax.

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

In such cases always check the existence of a key using the ``isset()`` method, or the coalescence operator ``??``.

.. code:: php

   $collection = new Collection();

   echo $collection->isset('lorem') ? $collection['lorem'] : null; // null

   echo $collection['lorem'] ?? null; // null