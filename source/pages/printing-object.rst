======================
8. Printing the Object
======================

When trying to use language constructors like ``echo`` or ``print`` on an object,
php language throws an error, as it does not know how to handle this.

Fortunately in our case, we returned the contents of the internal content in JSON format.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit', 'amet' => 'consectetur']);
   echo $collection; 
   
   // {"lorem":"ipsum","dolor":"sit","amet":"consectetur"}