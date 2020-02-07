==========================
11. Sorting the collection
==========================

11.1 Sorting values
-------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([3, 4, 8, 7, 1, 5]);
   $collection->sort(); //[1,3,4,5,7,8]

11.2 Sorting values in reverse order
------------------------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([3, 4, 8, 7, 1, 5]);
   $collection->rsort(); //[8,7,5,4,3,1]

11.3 Sorting values keeping association
---------------------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->asort(); //{"dolor":"amet","sit":"consectetur","lorem":"ipsum"}

11.4 Sorting values in reverse order keeping association
--------------------------------------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->arsort(); // {"lorem":"ipsum","sit":"consectetur","dolor":"amet"}

11.5 Sorting by keys
--------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->ksort(); //{"dolor":"amet","lorem":"ipsum","sit":"consectetur"}

11.6 Sorting by keys in reverse order
-------------------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->krsort(); //{"sit":"consectetur","lorem":"ipsum","dolor":"amet"}

11.7 Sorting by custom callback
-------------------------------

.. code:: php

    use Cajudev\Collection;

    collection = new Collection([3, 4, 8, 7, 1, 5]);
    $collection->usort(fn($a, $b) => $a <=> $b); //[1,3,4,5,7,8]