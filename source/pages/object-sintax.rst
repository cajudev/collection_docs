================
5. Object Syntax
================

It is possible to manipulate the values ​​of the internal array of this class as if they were properties.

5.1 Setting values
------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection->lorem = 'ipsum';

   print_r($collection);

   /*
      Cajudev\Collection Object
         (
            [content:protected] => Array
               (
                  [lorem] => ipsum
               )

            [length:protected] => 1
         )
   */

Only the reserved word ``length`` cannot be used because it is a read-only attribute of the class.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection->length = 10; // InvalidArgumentException: length property is readonly

5.2 Getting values
------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection->lorem = 'ipsum';

   echo $collection->lorem; // ipsum

.. note::

   It is not mandatory to perform a verification with the ``isset()`` function when accessing positions in this way, because internally a check is performed and if the position has not been 
   initialized, the value ``null`` is returned.

5.3 Checking null values
------------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection->lorem = 'ipsum';

   echo isset($collection->lorem); // true

   echo isset($collection->ipsum); // false

5.4 Removing values
-------------------

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection->lorem = 'ipsum';

   unset($collection->lorem);

   echo isset($collection->lorem); // false

5.5 Brackets Sintax
-------------------

Properties in php cannot be named with special characters like '.' or '-'. In such cases it is necessary to observe the following syntax.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection->lorem-ipsum = 'dolor'; // sintax error

   $collection->{'lorem-ipsum'} = 'dolor'; // works perfectly

   print_r($collection);

   /*
   Cajudev\Collection Object
      (
         [content:protected] => Array
            (
               [lorem-ipsum] => dolor
            )

         [length:protected] => 1
      )
   */

5.6 Dot notation
----------------

It is possible to manipulate data in a multidimensional way using the dot notation described in section 6.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();

   $collection->{'lorem.ipsum'} = 'dolor';

   print_r($collection);

   /*
   Cajudev\Collection Object
   (
      [content:protected] => Array
         (
            [lorem] => Array
               (
                  [ipsum] => dolor
               )

         )

      [length:protected] => 1
   )
   */