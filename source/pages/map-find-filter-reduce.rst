12. Map, Find, Filter and Reduce
================================

12.1 Map
--------

The ``map`` method allows you to apply a callback function to all elements of the array.

.. code:: php

    $collection = new Collection(['lorem' => 'ipsum']);
    $map = $collection->map(function($value) {
        return strtoupper($value);
    });

Its also possible map the keys

.. code:: php

    $collection = new Collection(['lorem' => 'ipsum']);
    $map = $collection->map(function($key, $value) {
        return [strtoupper($key) => strtoupper($value)]; // attention to the return intax
    });

The second parameter defines when the injected value will be an array or an collection:

.. code:: php

    $collection = new Collection(['lorem' => 'ipsum']);

    $map = $collection->map(function($key, $value) {
        return get_type($value); // array
    }, false);

    $map = $collection->map(function($key, $value) {
        return get_class($value); // \Cajudev\Collection
    }, true);

12.2 Find
---------

The ``find`` method allows you to search for a especific element of a collection.

.. code:: php

    $collection = new Collection([
        [
            'lorem' => 'ipsum',
            'ipsum => 'sit',
        ],
        [
            'lorem' => 'consectetur',
            'ipsum => 'amet',
        ],
        [
            'lorem' => 'lorem',
            'ipsum => 'dolor',
        ]
    ]);

    $element = $collection->find(function($element) {
        return $element['lorem'] === 'consectetur');
    }

    $element = $collection->find(function($key, $element) {
        // ...
    }

    $element = $collection->find(function($self, $key, $element) {
        // ...
    }

The second parameter defines when the injected value will be an array or an collection:

.. code:: php

    $collection = new Collection(['lorem' => 'ipsum']);

    $element = $collection->find(function($value) {
        return get_type($value); // array
    }, false);

    $element = $collection->find(function($value) {
        return get_class($value); // \Cajudev\Collection
    }, true);

12.3 Filter
-----------

The ``filter`` method allows you to filter the elements of the array through a callback function.

.. code:: php

    $collection = new Collection([1, 2, 3, 4, 5, 6, 7, 8, 9]);

    $filter = $collection->filter(function($value) {
        return $value < 5;
    });

    $filter = $collection->filter(function($key, $value) {
        // ...
    });

    $filter = $collection->filter(function($self, $key, $value) {
        // ...
    });

The second parameter defines when the injected value will be an array or an collection:

.. code:: php

    $collection = new Collection(['lorem' => 'ipsum']);

    $element = $collection->filter(function($value) {
        return get_type($value); // array
    }, false);

    $element = $collection->filter(function($value) {
        return get_class($value); // \Cajudev\Collection
    }, true);

12.4 Reduce
-----------

The ``reduce`` method allows you to reduce the object by a single value. It receives by parameter a callback function to be executed,
and always receive two arguments, the first is the previous value and the second is the current value.

Unlike the traditional implementation, the initial value provided will be the **first element of the array** and not `` null`` as usual.

.. code:: php

    $collection = new Collection([1, 2, 3, 4]);
    
    $result = $collection->reduce(function($a, $b) {
        return $a + $b;
    });

    echo $result; // 10

The second parameter defines when the injected values will be an array or an collection:

.. code:: php

    $collection = new Collection(['lorem' => 'ipsum']);

    $map = $collection->reduce(function($a, $b) {
        return get_type($a); // array
        return get_type($b); // array
    }, false);

    $map = $collection->reduce(function($a, $b) {
        return get_class($a); // \Cajudev\Collection
        return get_class($b); // \Cajudev\Collection
    }, true);