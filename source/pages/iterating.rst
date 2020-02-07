=============================
10. Iterating over the object
=============================

10.1 Iterating with a for-each loop
-----------------------------------

The use of this class in a for-each loop is the same as when you use a common array

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit']);

   foreach ($collection as $key => $value) {
        // ...
   }

10.2 Iterating with the each method
-----------------------------------

The ``each()`` method performs a for-each loop internally through a callback function.

Note that the arguments are passed to the callbacks dynamically depending on the number of arguments requested.

10.2.1 Iterating all content
............................

.. code:: php

   $collection = new Collection(['lorem' => ['ipsum', 'dolor', 'sit']]);

   $collection->each(function($value) {
        // ...
   });

   $collection->each(function($key, $value) {
        // ...
   });

    $collection->each(function($self, $key, $value) {
        // ...
   });

The second parameter defines when the injected value will be an array or an collection:

.. code:: php

    $collection->each(function($key, $value) {
        echo get_type($value); // array
    }, false);

    $collection->each(function($key, $value) {
        echo get_class($value); // Cajudev\Collection;
    }, true);
   
10.2.2 Stopping the iteration
.............................

To skip an iteration just use a ``return``.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([0, 1, 2, 3, 4, 5]);

    $collection->each(function($key, $value) {
        if ($value > 2) {
            return;
        }
        echo $value . ' ';    // 0 1 2
    });

10.3 Iterating with a while loop
--------------------------------

The object responsible for iterating between the values ​​of this class is the ``CollectionIterator``.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection->push('lorem', 'ipsum', 'dolor', 'sit');

   $iterator = $collection->getIterator();

    while ($iterator->valid()) { // check if the position id valid

        echo "key {$iterator->key()}"; // get current key

        echo "value: {$iterator->current()}"; // get current value
        
        $iterator->next(); // go to the next position
    }

    $iterator->previous(); // return to the previous position
    $iterator->rewind(); // return to the beginning

10.4 Iterating with the for method
----------------------------------

The ``for()`` method allows iterating over a Collection object in steps.

It takes three arguments: The starting point, the increment, and a callback function

10.4.1 Iterating forward
........................

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for($start = 0, $step = 2, function($value) {
        // ...
    });

    $collection->for($start = 0, $step = 2, function($key, $value) {
        // ...
    });

    $collection->for($start = 0, $step = 2, function($self, $key, $value) {
        // ...
    });

10.4.2 Iterating backward
.........................

If you want to iterate the object inversely, just pass to the second argument a negative value.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for($start = 3, $step = -1, function($key, $value) {
        // ...
    });

Take care not to enter an invalid value, as in the example below:

.. code:: php

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    // Undefined offset: 7
    $collection->for(7, -1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

The second parameter defines when the injected value will be an array or an collection:

.. code:: php

    $collection->for($start = 0, $step = 2, function($value) {
        echo get_type($value); // array
    }, false);

    $collection->for($start = 0, $step = 2, function($value) {
        echo get_class($value); // Cajudev\Collection;
    }, true);

10.5 Iterating recursively
--------------------------

The ``walk()`` method allows you to recursively walk all the elements of the object.

10.5.1 Iterating over leaves
............................

The default mode for this method is LEAVES_ONLY, that is, it only travels through leaf nodes.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem', ['ipsum', 'dolor'], ['sit' => ['amet' => 'consectetur']]]);

    $collection->walk(function($value) {
        // ...
    });
    
    $collection->walk(function($key, $value) {
        // ...
    });

    $collection->walk(function($self, $key, $value) {
        // ...
    });

10.5.2 Other modes
..................

Four constants of the class `` RecursiveIteratorIterator`` can be passed as the second parameter of this method.

They are: ``LEAVES_ONLY``, ``SELF_FIRST``, ``CHILD_FIRST`` and ``CATCH_GET_CHILD``.

.. code:: php

    $collection->walk(function($value) {
        // ...
    }, RecursiveIteratorIterator::LEAVES_ONLY);

    $collection->walk(function($value) {
        // ...
    }, RecursiveIteratorIterator::SELF_FIRST);

    $collection->walk(function($value) {
        // ...
    }, RecursiveIteratorIterator::CHILD_FIRST);

    $collection->walk(function($value) {
        // ...
    }, RecursiveIteratorIterator::CATCH_GET_CHILD);

The third parameter defines when the injected value will be an array or an collection:

.. code:: php

    $collection->walk(function($value) {
        echo get_type($value); // array
    }, RecursiveIteratorIterator::LEAVES_ONLY, false);

    $collection->walk(function($value) {
        echo get_class($value); // Cajudev\Collection;
    }, RecursiveIteratorIterator::LEAVES_ONLY, true);