Class **Phalcon\\Mvc\\Model\\Query\\Builder**
=============================================

*implements* :doc:`Phalcon\\Mvc\\Model\\Query\\BuilderInterface <Phalcon_Mvc_Model_Query_BuilderInterface>`, :doc:`Phalcon\\DI\\InjectionAwareInterface <Phalcon_DI_InjectionAwareInterface>`

Helps to create PHQL queries using an OO interface  

.. code-block:: php

    <?php

    $resultset = $this->modelsManager->createBuilder()
       ->from('Robots')
       ->join('RobotsParts')
       ->limit(20)
       ->orderBy('Robots.name')
       ->getQuery()
       ->execute();



Methods
-------

public  **__construct** ([*array* $params], [:doc:`Phalcon\\DI <Phalcon_DI>` $dependencyInjector])

Phalcon\\Mvc\\Model\\Query\\Builder constructor 

.. code-block:: php

    <?php

     $params = array(
        'models'     => array('Users'),
        'columns'    => array('id', 'name', 'status'),
        'conditions' => "created > '2013-01-01' AND created < '2014-01-01'",
        'group'      => array('id', 'name'),
        'having'     => "name = 'Kamil'",
        'order'      => array('name', 'id'),
        'limit'      => 20,
        'offset'     => 20,
    );
    $queryBuilder = new Phalcon\Mvc\Model\Query\Builder($params);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector)

Sets the DependencyInjector container



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ()

Returns the DependencyInjector container



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **columns** (*string|array* $columns)

Sets the columns to be queried 

.. code-block:: php

    <?php

    $builder->columns(array('id', 'name'));




public *string|array*  **getColumns** ()

Return the columns to be queried



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **from** (*string|array* $models)

Sets the models who makes part of the query 

.. code-block:: php

    <?php

    $builder->from('Robots');
    $builder->from(array('Robots', 'RobotsParts'));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **addFrom** (*string* $model, [*string* $alias])

Add a model to take part of the query 

.. code-block:: php

    <?php

    $builder->addFrom('Robots', 'r');




public *string|array*  **getFrom** ()

Return the models who makes part of the query



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **join** (*string* $model, [*string* $conditions], [*string* $alias], [*string* $type])

Adds a INNER join to the query 

.. code-block:: php

    <?php

    $builder->join('Robots');
    $builder->join('Robots', 'r.id = RobotsParts.robots_id');
    $builder->join('Robots', 'r.id = RobotsParts.robots_id', 'r');
    $builder->join('Robots', 'r.id = RobotsParts.robots_id', 'r', 'LEFT');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **innerJoin** (*string* $model, [*string* $conditions], [*string* $alias])

Adds a INNER join to the query 

.. code-block:: php

    <?php

    $builder->innerJoin('Robots');
    $builder->innerJoin('Robots', 'r.id = RobotsParts.robots_id');
    $builder->innerJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');
    $builder->innerJoin('Robots', 'r.id = RobotsParts.robots_id', 'r', 'LEFT');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **leftJoin** (*string* $model, [*string* $conditions], [*string* $alias])

Adds a LEFT join to the query 

.. code-block:: php

    <?php

    $builder->leftJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **rightJoin** (*string* $model, [*string* $conditions], [*string* $alias])

Adds a RIGHT join to the query 

.. code-block:: php

    <?php

    $builder->rightJoin('Robots', 'r.id = RobotsParts.robots_id', 'r');




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **where** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Sets the query conditions 

.. code-block:: php

    <?php

    $builder->where('name = "Peter"');
    $builder->where('name = :name: AND id > :id:', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **andWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using a AND operator 

.. code-block:: php

    <?php

    $builder->andWhere('name = "Peter"');
    $builder->andWhere('name = :name: AND id > :id:', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **orWhere** (*string* $conditions, [*array* $bindParams], [*array* $bindTypes])

Appends a condition to the current conditions using a OR operator 

.. code-block:: php

    <?php

    $builder->orWhere('name = "Peter"');
    $builder->orWhere('name = :name: AND id > :id:', array('name' => 'Peter', 'id' => 100));




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **betweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum)

Appends a BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->betweenWhere('price', 100.25, 200.50);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **notBetweenWhere** (*string* $expr, *mixed* $minimum, *mixed* $maximum)

Appends a NOT BETWEEN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->notBetweenWhere('price', 100.25, 200.50);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **inWhere** (*string* $expr, *array* $values)

Appends an IN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->inWhere('id', [1, 2, 3]);




public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **notInWhere** (*string* $expr, *array* $values)

Appends a NOT IN condition to the current conditions 

.. code-block:: php

    <?php

    $builder->notInWhere('id', [1, 2, 3]);




public *string|array*  **getWhere** ()

Return the conditions for the query



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **orderBy** (*string* $orderBy)

Sets a ORDER BY condition clause 

.. code-block:: php

    <?php

    $builder->orderBy('Robots.name');
    $builder->orderBy(array('1', 'Robots.name'));




public *string|array*  **getOrderBy** ()

Returns the set ORDER BY clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **having** (*string* $having)

Sets a HAVING condition clause. You need to escape PHQL reserved words using [ and ] delimiters 

.. code-block:: php

    <?php

    $builder->having('SUM(Robots.price) > 0');




public *string|array*  **getHaving** ()

Return the current having clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **limit** (*int* $limit, [*int* $offset])

Sets a LIMIT clause, optionally a offset clause 

.. code-block:: php

    <?php

    $builder->limit(100);
    $builder->limit(100, 20);




public *string|array*  **getLimit** ()

Returns the current LIMIT clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **offset** (*int* $offset)

Sets an OFFSET clause 

.. code-block:: php

    <?php

    $builder->offset(30);




public *string|array*  **getOffset** ()

Returns the current OFFSET clause



public :doc:`Phalcon\\Mvc\\Model\\Query\\Builder <Phalcon_Mvc_Model_Query_Builder>`  **groupBy** (*string* $group)

Sets a GROUP BY clause 

.. code-block:: php

    <?php

    $builder->groupBy(array('Robots.name'));




public *string*  **getGroupBy** ()

Returns the GROUP BY clause



public *string*  **getPhql** ()

Returns a PHQL statement built based on the builder parameters



public :doc:`Phalcon\\Mvc\\Model\\Query <Phalcon_Mvc_Model_Query>`  **getQuery** ()

Returns the query built



