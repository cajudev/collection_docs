========================
14. Métodos de Uso Geral
========================

14.1 First
----------

Retorna o primeiro elemento do array (A partir da versão 3, não reinicia mais o ponteiro)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');

   echo $collection->first(); // 'lorem'

14.2 Last
---------

Retorna o último elemento do array (A partir da versão 3, não reinicia mais o ponteiro)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');

   echo $collection->last(); // 'dolor'

14.3 Shift
----------

Remove o primeiro elemento do array retornando o elemento removido (reinicia o ponteiro)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');
   $value  = $collection->shift();

   echo $value;  // lorem;
   echo $collection; // ["ipsum","dolor"]

14.4 Pop
--------

Remove o último elemento do array retornando o elemento removido (reinicia o ponteiro)

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', 'dolor');
   $value  = $collection->pop();

   echo $value;  // dolor
   echo $collection; // ["lorem","ipsum"]

14.5 Count
----------

Retorna a quantidade de elementos do array. 

Não há necessidade de utilizar esse método (exceto em modo recursivo)
visto que o atributo length armazena o tamanho atual do array.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $collection->count(); // 3
   echo $collection->length; // 3

   $collection = new Collection([1, [2, 3], [2 => [1, 2, 3]]]);

   echo $collection->count(COUNT_RECURSIVE); // 9
   echo $collection->length; // 3

14.6 Keys
---------

Retorna um objeto contento as chaves do array atual

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['three' => 3, 'eight' => 8, 'two' => 2]);

    $keys = $collection->keys();

    echo $keys; // ["three", "eight", "two"]

14.7 Values
-----------

Retorna um objeto contento os valores do array atual

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['three' => 3, 'eight' => 8, 'two' => 2]);

    $values = $collection->values();

    echo $values; // [3, 8, 2]

14.8 Chunk
----------

Quebra o array em partes iguais. Caso receba ``true`` como segundo parâmetro preservará as chaves do array.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);

    $chunk = $collection->chunk(2);

    print_r($chunk);

    /*
    Cajudev\Collection Object
        (
            [content:Cajudev\Collection:protected] => Array
                (
                    [0] => Array
                        (
                            [0] => 1
                            [1] => 2
                        )
                    [1] => Array
                        (
                            [0] => 3
                            [1] => 4
                        )
                    [2] => Array
                        (
                            [0] => 5
                        )
                )
            [length:protected] => 3
        )
    */

14.9 Join
----------

Junta os elementos do array em uma string.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);

    $result = $collection->join('-');

    echo $result; // 1-2-3-4-5

14.10 Column
------------

Retorna um objeto contento os valores da coluna informada.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection[] = ['lorem' => '1234', 'ipsum' => 8000];
    $collection[] = ['lorem' => '4321', 'ipsum' => 1500];
    $collection[] = ['lorem' => '9999', 'ipsum' => 0015];
    $collection[] = ['lorem' => '1111', 'ipsum' => 3315];

    echo $collection->column('lorem'); // ["1234","4321","9999","1111"]

14.11 Lower
-----------

Altera recursivamente as chaves do array para minúsculo.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['LOREM' => 1, 'IPSUM' => 2]);

    echo $collection->lower(); // {"lorem":1,"ipsum":2}

14.12 Upper
-----------

Altera recursivamente as chaves do array para maiúsculo.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem' => 1, 'ipsum' => 2]);

    echo $collection->upper(); // {"LOREM":1,"IPSUM":2}

14.13 Contains
--------------

Checa se determinado valor existe no array

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);
    $collection->contains(2) //true
    $collection->contains(6) //false

14.14 Sum
---------

Soma os elementos do array

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);
    $collection->sum(); //15

14.15 Flip
----------

Inverte as relações do array, ou seja, as chaves 
passam a ser os valores e os valores passam a ser as chaves.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem' => 'ipsum']);
    $collection->flip(); //['ipsum' => 'lorem]

14.16 Search
------------

Procura por um valor no array e se o encontra, retorna sua chave correspondente.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem' => 'ipsum']);
    $collection->search('ipsum'); //lorem
    $collection->search('dolor'); //null

14.17 Reverse
-------------

Inverte o array.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([1, 2, 3, 4, 5]);
    $collection->reverse(); //[5, 4, 3, 2, 1]

14.18 Unique
------------

Remove valores duplicados.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['a', 'c', 'a', 'c', 'a', 'c', 'c', 'b']);
    $collection->unique(); //[0 => 'a', 1 => 'c', 7 => 'b']

14.19 Merge
-----------

Mescla todas as dimensões do array

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([
        [1, 2, 'a', 4],
        ['a', '2', 'c'],
        [3, 'c', 'd']
    ]);

    $collection->merge(); //[1, 2, 'a', 4, 'a', '2', 'c', 3, 'c', 'd']

14.20 Coalesce
--------------

Retorna o primeiro valor não nulo

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([null, null, null, 'lorem', null]);

    $collection->coalesce(); //lorem

14.21 Random
------------

Retorna um elemento aleatório

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem', 'ipsum', 'dolor']);

    $collection->random(); //ipsum

14.22 Shuffle
-------------

Embaralha os valores do objeto

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(['lorem', 'ipsum', 'dolor']);

    $collection->shuffle(); // ['dolor', 'lorem', 'ipsum']