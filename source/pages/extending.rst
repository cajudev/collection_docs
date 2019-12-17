=======================
16. Extendendo a Classe
=======================

Atualmente sempre que chamada uma função como ``filter`` por exemplo, o comportamento padrão da classe é
retornar um novo objeto com os novos dados.

Se esse não é o comportamento desejado, você pode sobrescrever o método ``return``, como no exemplo abaixo,
que ao invés de retornar um novo objeto passa a alterar o valor interno da classe retornando a sua própria instância.

.. code:: php

    use Cajudev\Collection;

    class CollectionChild extends Collection {

        /** @Override */
        public function return($content) {
            $this->content = $content instanceof Collection ? $content->get() : $content;
            return $this;
        }
    }