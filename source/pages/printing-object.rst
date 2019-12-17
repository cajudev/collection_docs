======================
8. Imprimindo o Objeto
======================

Ao tentarmos utilizar construtores de linguagem como ``echo`` ou ``print`` em um objeto, 
um erro é emitido pelo php, pois o mesmo não sabe como tratar esse retorno. 

Felizmente em nosso caso retornamos o conteúdo do array interno em formato JSON.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit', 'amet' => 'consectetur']);
   echo $collection; 
   
   // {"lorem":"ipsum","dolor":"sit","amet":"consectetur"}