=====================
11. Ordenando o Array
=====================

11.1 Ordenando valores
----------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([3, 4, 8, 7, 1, 5]);
   $collection->sort(); //[1,3,4,5,7,8]

11.2 Ordenando valores em ordem inversa
---------------------------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([3, 4, 8, 7, 1, 5]);
   $collection->rsort(); //[8,7,5,4,3,1]

11.3 Ordenando valores mantendo associação
------------------------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->asort(); //{"dolor":"amet","sit":"consectetur","lorem":"ipsum"}

11.4 Ordenando valores em ordem inversa mantendo associação
-----------------------------------------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->arsort(); // {"lorem":"ipsum","sit":"consectetur","dolor":"amet"}

11.5 Ordenando por chaves
-------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->ksort(); //{"dolor":"amet","lorem":"ipsum","sit":"consectetur"}

11.6 Ordenando por chaves em ordem inversa
------------------------------------------

.. code:: php

   use Cajudev\Collection;

    $collection = new Collection([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $collection->krsort(); //{"sit":"consectetur","lorem":"ipsum","dolor":"amet"}