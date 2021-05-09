Database
========

* `Interact with database <Interact with database_>`_

  * `With QueryBuilder <With QueryBuilder_>`_
  * `With Eloquent <With Eloquent_>`_


Interact with database
----------------------

With QueryBuilder
^^^^^^^^^^^^^^^^^
See full reference here: `Laravel QueryBuilder <https://laravel.com/docs/8.x/queries>`_ 

.. attention:: Replace **DB::table()** in Laravel docs with helper function **db_table()** as shown below

.. code-block:: php

    <?php

    // Laravel docs example
    $user = DB::table('users')->where('name', 'John')->first();

    // How you should use in this framework
    $user = db_table('users')->where('name', 'John')->first();


With Eloquent
^^^^^^^^^^^^^
See full reference here: `Laravel Eloquent ORM <https://laravel.com/docs/8.x/eloquent>`_ 
