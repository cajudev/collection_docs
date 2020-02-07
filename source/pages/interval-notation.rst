===================
7. Interval Notation
===================

7.1 Setting values
------------------

An fast way to initialize multiple positions in the array with a default value.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection['0:5'] = 'lorem';
   echo $collection; // ["lorem","lorem","lorem","lorem","lorem","lorem"]

7.2 Getting values
------------------

It is possible to receive a slice of a collection, using interval notation.

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'zero'  => 0, 'one'  => 1, 'two' => 2, 'three' => 3,
        'four'  => 4, 'five' => 5, 'six' => 6, 'seven' => 7,
        'eight' => 8, 'nine' => 9, 'ten' => 10
    ]);

    echo $collection['2:5']; // {"two":2,"three":3,"four":4,"five":5}

If you enter an initial value greater than the final value, the result will be
an array inverse of the defined range.

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'zero'  => 0, 'one'  => 1, 'two' => 2, 'three' => 3,
        'four'  => 4, 'five' => 5, 'six' => 6, 'seven' => 7,
        'eight' => 8, 'nine' => 9, 'ten' => 10
    ]);

    echo $collection['6:3']; // {"six":6,"five":5,"four":4,"three":3}

7.3 Checking null values
------------------------

Check the existence of multiple positions in the array.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['a', 'b', 'c', 'd', 'e']);

   $collection->isset('0:4'); // true
   isset($collection['0:4']); // true

   $collection->isset('0:5'); // false
   isset($collection['0:5']); // false

7.4 Removing intervals
----------------------

It's easy to remove a slice of the content.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['a', 'b', 'c', 'd', 'e']);

   $collection->unset('0:2');
   echo $collection; // {"3":"d","4":"e"}