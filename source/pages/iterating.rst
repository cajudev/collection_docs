===========================
10. Iterando sobre o Objeto
===========================

10.1 Iterando em um laço for-each
---------------------------------

A utilização da classe em um laço for-each é a mesma a de um array comum

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit']);

   foreach ($collection as $key => $value) {
        // ...
   }

10.2 Iterando com o método each
-------------------------------

O método ``each()`` performa um loop for-each internamente através de uma função callback.

10.2.1 Percorrendo o objeto
...........................

Neste primeiro caso o valor será fornecido como um array comum.

.. code:: php

   $collection = new Collection(['lorem' => ['ipsum', 'dolor', 'sit']]);

   $collection->each(function($key, $value) {
        echo gettype($value); // array
   });

Mas podemos alterar esse comportamento para que o valor fornecido seja um Collection.

.. code:: php

    $collection->each(function($key, $value) {
        echo get_class($value); // Cajudev\Collection;
    }, Collection::ARRAY_TO_COLLECTION);

        // ou 

    $collection->each(function($key, $value) {
        echo get_class($value); // Cajudev\Collection;
    }, true);
   
10.2.2 Parando a iteração
.........................

Para pular uma iteração basta utilizar um ``return``.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([0, 1, 2, 3, 4, 5]);

    $collection->each(function($key, $value) {
        if ($value > 2) {
            return;
        }
        echo $value . ' ';    // 0 1 2
    });

10.3 Iterando em um laço while
------------------------------

O objeto responsável por iterar entre os valores dessa classe é o ``CollectionIterator``.

No exemplo abaixo, vocẽ poderá observar sua utilização em um laço while.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection->push('lorem', 'ipsum', 'dolor', 'sit');

   $iterator = $collection->getIterator();

    while ($iterator->valid()) { // verifica se a posição atual é válida

        echo "key {$iterator->key()}"; //acessa a chave da posição atual

        echo "value: {$iterator->current()}"; //acessa o valor da posição atual
        
        $iterator->next(); // avança para a próxima posição
    }

    $iterator->previous(); //retorna uma posição
    $iterator->rewind(); // retorna ao inicio

10.4 Iterando com o método for
------------------------------

O método ``for()`` permite iterar um objeto Collection através de passos.

Ele recebe três argumentos: O ponto de partida, o incremento e uma função que recebe chave e valor.

10.4.1 Iterando "para frente"
.............................

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(0, 2, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

   /*
        key: 0 value: lorem
        key: 2 value: dolor
        key: 4 value: amet
   */

10.4.2 Iterando "para trás"
...........................

Caso você queira iterar inversamente o objeto, basta informar como
segundo argumento um valor negativo.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(3, -1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

    /*
        key: 3 value: sit
        key: 2 value: dolor
        key: 1 value: ipsum
        key: 0 value: lorem
    */   

Tome o cuidado de não informar um valor inválido, como no exemplo abaixo:

.. code:: php

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(7, -1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

    // Undefined offset: 7

Assim como o método ``each``, o valor fornecido por padrão (caso seja um array) será um array comum.
Para alterar esse comportamento, você pode informar um segundo parâmetro.

.. code:: php

    $collection = new Collection([['lorem', 'ipsum'], ['dolor', 'sit']]);

    $collection->for(0, 2, function($key, $value) {
        echo get_class($value); // Cajudev\Collection;
    }, Collection::ARRAY_TO_COLLECTION);

        // ou 

    $collection->for(0, 2, function($key, $value) {
        echo get_class($value); // Cajudev\Collection;
    }, true);

10.4.3 Realizando modificações
..............................

Caso você necessite fazer modificações internas ao invés de somente obter dados,
você precisará adicionar um ``use`` passando o próprio objeto:

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(0, 2, function($key, $value) use ($collection) {
        $collection[$key] = 'Hello World';
    });

    print_r($collection);

    /*
        Cajudev\Collection Object
        (
            [content:protected] => Array
                (
                    [0] => Hello World
                    [1] => ipsum
                    [2] => Hello World
                    [3] => sit
                    [4] => Hello World
                    [5] => consectetur
                )
                
            [length:Cajudev\Collection:protected] => 
        )
    */

10.5 Iterando recursivamente
----------------------------

O método ``walk()`` permite percorrer recursivamente todos os elementos do objeto.

10.5.1 Percorrendo folhas
.........................

O modo padrão deste método é LEAVES_ONLY, ou seja, percorre apenas nós-folha, como no exemplo abaixo:

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem', ['ipsum', 'dolor'], ['sit' => ['amet' => 'consectetur']]]);

    $collection->walk(function($key, $value) {
        var_dump($key, $value);
    });

    /*
        int(0)
        string(5) "lorem"

        int(0)
        string(5) "ipsum"

        int(1)
        string(5) "dolor"

        string(4) "amet"
        string(11) "consectetur"
    */

10.5.2 Demais modos
...................

Quatro constantes da classe ``RecursiveIteratorIterator`` podem ser passadas como segundo parâmetro desse método.

São elas: ``LEAVES_ONLY``, ``SELF_FIRST``, ``CHILD_FIRST`` e ``CATCH_GET_CHILD``.

Veja o mesmo exemplo anterior, porém desta vez utilizando outro modo.

.. code:: php

    $collection->walk(function($key, $value) {
        var_dump($key, $value);
    }, RecursiveIteratorIterator::CHILD_FIRST);

    /*
        int(0)
        string(5) "lorem"

        int(0)
        string(5) "ipsum"

        int(1)
        string(5) "dolor"

        int(1)
        array(2) {
            [0] => string(5) "ipsum"
            [1] => string(5) "dolor"
        }

        string(4) "amet"
        string(11) "consectetur"

        string(3) "sit"
        array(1) {
            'amet' => string(11) "consectetur"
        }

        int(2)
        array(1) {
            'sit' => array(1) {
                'amet' => string(11) "consectetur"
            }
        }
    */

Assim como os métodos anteriores, o valor fornecido por padrão (caso seja um array) será um array comum.
Para alterar esse comportamento, você pode informar um terceiro parâmetro.

.. code:: php

    $collection = new Collection([['lorem', 'ipsum'], ['dolor', 'sit']]);

    $collection->walk(function($key, $value) {
        // ...
    }, RecursiveIteratorIterator::CHILD_FIRST, Collection::ARRAY_TO_COLLECTION);

        // ou 

    $collection->walk(function($key, $value) {
        // ...
    }, RecursiveIteratorIterator::CHILD_FIRST, true);