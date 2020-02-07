==================
13. Set Operations
==================

All methods described in this section follows the following rule: **Each object's index is equivalent to a set of elements**

13.1 Union
----------

The ``union()`` method performs the union between all sets of the object. Repeated values ​​are removed.

.. code:: php

   $collection->union(); // [1, 2, 3, 4, 5]

13.2 Difference
---------------

The ``diff()`` method calculates the difference between all sets of the object.
The order of the sets directly changes the final value.

.. code:: php

   $collection = new Collection([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $collection->diff(); // [1, 2]

   $collection = new Collection([
      [3, 4, 5],
      [1, 2, 3],
   ]);

   $collection->diff(); // [4, 5]

13.3 Outer Difference
---------------------

The ``outer()`` method makes the outer difference between sets.

.. code:: php

   $collection = new Collection([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $collection->outer(); // [[1, 2], [4, 5]]

13.4 Intersection
-----------------

The ``intersect()`` method performs the intersection between all sets of the object.

.. code:: php

   $collection = new Collection([
      [1, 2, 3, 4],
      [3, 4, 5, 6],
   ]);

   $collection->intersect(); // [3, 4]

13.5 Cartesian Product
----------------------

The ``cartesian()`` method calculates the cartesian product between all sets of the object.

.. code:: php

   $collection = new Collection([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $collection->cartesian(); // [[1,3], [1,4], [1,5], [2,3], [2,4], [2,5], [3,3], [3,4], [3,5]]