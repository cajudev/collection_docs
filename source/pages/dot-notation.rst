===============
6. Dot Notation
===============

A very interesting feature of this library is the possibility
to navigate between your content using dot notation.

6.1 Setting values
------------------

To create multidimensional collections easily, without using thousands of square brackets,
just perform the assignment with dot notation, as in the example below:

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection['lorem.ipsum.dolor'] = 'amet';

   print_r($collection);

   /*
   Cajudev\Collection Object
      (
         [content:protected] => Array
            (
               [lorem] => Array
                  (
                     [ipsum] => Array
                        (
                           [dolor] => amet
                        )

                  )

            )

         [length:protected] => 1
      )
   */


6.2 Getting values
------------------

Likewise, it is very easy getting values of any dimension

.. code:: php
   
   // Navigating between values

   echo $collection['lorem.ipsum.1.sit.amet']; // dolor

   // It is also possible to mix the syntax if you prefer.

   echo $collection['lorem.ipsum'][1]['sit.amet']; //dolor

.. note::

   Several methods also support this notation, such as **get**, **set**, **isset**, **empty**, among others.
   All are described in this documentation.