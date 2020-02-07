==================
15. Static Methods
==================

15.1 Combine
-------------

Combines two arrays / objects in a new object, using the first for keys and the second for values.
Both arguments can be simple arrays or collections.

.. code:: php

   use Cajudev\Collection;

   $array = ['lorem', 'ipsum', 'dolor'];

   $collection = new Collection([1, 2, 3]);

   $result = Collection::combine($array, $collection);

   echo $result; // {"lorem":1,"ipsum":2,"dolor":3}

15.2 Range
-------------

Creates a collection object from a given range

.. code:: php

   use Cajudev\Collection;

   $numbers = Collection::range($start = 10, $end = 20, $step = 2);

   echo $numbers; // [10, 12, 14, 16, 18, 20]
   

   $letters = Collection::range($start = 'A', $end = 'F');

   echo $letters; // ["A", "B", "C", "D", "E", "F"]
