===========================
13. Operações com Conjuntos
===========================

Todos os métodos descritos nesta seção seguem a seguinte lógica: Cada index do objeto equivale à um conjunto.

O que significa que o objeto abaixo...

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection([
       [1, 2, 3],
       [3, 4, 5],
   ]);

... possui dois conjuntos de números inteiros.

13.1 União
----------

O método ``union()`` realiza a união entre todos os conjuntos do objeto. Valores repetidos são removidos.

.. code:: php

   $collection->union(); // [1, 2, 3, 4, 5]

13.2 Diferença
--------------

O método ``diff()`` realiza a diferença entre todos os conjuntos do objeto. 
A ordem dos conjuntos altera diretamente o valor final.

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

13.3 Diferença Total
--------------------

O método ``outer()`` realiza a diferença total entre conjuntos.

.. code:: php

   $collection = new Collection([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $collection->outer(); // [[1, 2], [4, 5]]

13.4 Intersecção
----------------

O método ``intersect()`` realiza a intersecção entre todos os conjuntos do objeto.

.. code:: php

   $collection = new Collection([
      [1, 2, 3, 4],
      [3, 4, 5, 6],
   ]);

   $collection->intersect(); // [3, 4]

13.5 Produto cartesiano
-----------------------

O método ``cartesian()`` realiza o produto cartesiano entre todos os conjuntos do objeto.

.. code:: php

   $collection = new Collection([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $collection->cartesian(); // [[1,3], [1,4], [1,5], [2,3], [2,4], [2,5], [3,3], [3,4], [3,5]]