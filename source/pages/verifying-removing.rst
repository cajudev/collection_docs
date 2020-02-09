===============================
8. Checking and Removing Values
===============================

8.1 Checking null values
------------------------

To check when a key is not null, you can use the ``isset()`` method.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit']);

   var_dump($collection->isset('lorem')); // bool(true)
   var_dump($collection->isset('ipsum')); // bool(false)

.. hint::

   In all methods on this page, you can apply the use of dot notation, 
   explained in section 6, as in the example below:

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

If you want to perform the reverse logic, you can use the ``noset()`` method.

.. code:: php

   var_dump($collection->noset('lorem')); // bool(false)
   var_dump($collection->noset('ipsum')); // bool(true)

8.2 Checking empty values
-------------------------

To check if an object position is empty, use the ``empty()`` method.

This method is equivalent to using ``!isset($collection[$key]) || $collection[$key] == false``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection['lorem'] = false;
   var_dump($collection->empty('lorem')); //bool(true);

To check if a value is not empty, you can use the ``filled()`` method, which is nothing more
than the negation of the previous method.

This method is equivalent to using ``isset($collection[$key]) && $collection[$key] == true``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection['lorem'] = false;
   var_dump($collection->filled('lorem')); //bool(false);

8.3 Removing values
-------------------

To remove an element from the object use the ``unset()`` method.

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
   