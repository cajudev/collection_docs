=================
14. Miscellaneous
=================

14.1 First
----------

Returns the first element of the array (restart the pointer)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');

   echo $collection->first(); // 'lorem'

14.2 Last
---------

Returns the last element of the array (restart the pointer)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');

   echo $collection->last(); // 'dolor'

14.3 Shift
----------

Remove and returns the first element of the array (restart the pointer)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');
   $value  = $collection->shift();

   echo $value;  // lorem;
   echo $collection; // ["ipsum","dolor"]

14.4 Pop
--------

Remove and returns the last element of the array (restart the pointer)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');
   $value  = $collection->pop();

   echo $value;  // dolor
   echo $collection; // ["lorem","ipsum"]

14.5 Count
----------

Calculate the length of the collection

There is no need to use this method (except in recursive mode)
since the length attribute stores the current size of the array.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $collection->count(); // 3
   echo $collection->length; // 3

   $collection = new Collection([1, [2, 3], [2 => [1, 2, 3]]]);

   echo $collection->count(COUNT_RECURSIVE); // 9
   echo $collection->length; // 3

14.6 Keys
---------

Returns an object containing the keys of the current collection

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['three' => 3, 'eight' => 8, 'two' => 2]);

    $keys = $collection->keys();

    echo $keys; // ["three", "eight", "two"]

14.7 Values
-----------

Returns an object containing the values of the current array

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['three' => 3, 'eight' => 8, 'two' => 2]);

    $values = $collection->values();

    echo $values; // [3, 8, 2]

14.8 Chunk
----------

Split the array into equal parts. If it receives ``true`` as a second parameter
it will preserve the array keys.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);

    $chunk = $collection->chunk(2);

    print_r($chunk);

    /*
    Cajudev\Collection Object
        (
            [content:Cajudev\Collection:protected] => Array
                (
                    [0] => Array
                        (
                            [0] => 1
                            [1] => 2
                        )
                    [1] => Array
                        (
                            [0] => 3
                            [1] => 4
                        )
                    [2] => Array
                        (
                            [0] => 5
                        )
                )
            [length:protected] => 3
        )
    */

14.9 Join
----------

Join all elements in a string.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);

    $result = $collection->join('-');

    echo $result; // 1-2-3-4-5

14.10 Column
------------

Returns a new object with the values of a given column.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection[] = ['lorem' => '1234', 'ipsum' => 8000];
    $collection[] = ['lorem' => '4321', 'ipsum' => 1500];
    $collection[] = ['lorem' => '9999', 'ipsum' => 0015];
    $collection[] = ['lorem' => '1111', 'ipsum' => 3315];

    echo $collection->column('lorem'); // ["1234","4321","9999","1111"]

14.11 Lower
-----------

Recursively change the object keys to lowercase.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['LOREM' => 1, 'IPSUM' => 2]);

    echo $collection->lower(); // {"lorem":1,"ipsum":2}

14.12 Upper
-----------

Recursively change the object keys to uppercase.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem' => 1, 'ipsum' => 2]);

    echo $collection->upper(); // {"LOREM":1,"IPSUM":2}

14.13 Contains
--------------

Checks whether a value exists in the collection

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);
    $collection->contains(2) //true
    $collection->contains(6) //false

14.14 Sum
---------

Sum all elements of the collection

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);
    $collection->sum(); //15

14.15 Flip
----------

Inverts the array relations, that is, the keys
become the values ​​and the values ​​become the keys.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem' => 'ipsum']);
    $collection->flip(); //['ipsum' => 'lorem]

14.16 Search
------------

Searches for a value in the array and if it finds it, returns its corresponding key.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem' => 'ipsum']);
    $collection->search('ipsum'); //lorem
    $collection->search('dolor'); //null

14.17 Reverse
-------------

Returns the inverse of the collection.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);
    $collection->reverse(); //[5, 4, 3, 2, 1]

14.18 Unique
------------

Remove duplicated values.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['a', 'c', 'a', 'c', 'a', 'c', 'c', 'b']);
    $collection->unique(); //[0 => 'a', 1 => 'c', 7 => 'b']

14.19 Merge
-----------

Merge all elements of the collection

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([
        [1, 2, 'a', 4],
        ['a', '2', 'c'],
        [3, 'c', 'd']
    ]);

    $collection->merge(); //[1, 2, 'a', 4, 'a', '2', 'c', 3, 'c', 'd']

14.20 Coalesce
--------------

Returns the first non null value

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([null, null, null, 'lorem', null]);

    $collection->coalesce(); //lorem

14.21 Random
------------

Returns a random element of the collection.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem', 'ipsum', 'dolor']);

    $collection->random(); //ipsum

14.22 Shuffle
-------------

Shuffle the collection values.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem', 'ipsum', 'dolor']);

    $collection->shuffle(); // ['dolor', 'lorem', 'ipsum']