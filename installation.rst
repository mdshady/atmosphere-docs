Installation
============

* `Create new project <Create new project_>`_
* `Configurations <Configurations_>`_

  * `Bot configuration <Bot configuration_>`_

  * `Database configuration <Database configuration_>`_

    * `Mysql configuration <Mysql configuration_>`_
    * `Sqlite configuration <Sqlite configuration_>`_


Create new project
------------------
To create a new project use this composer syntax:

.. code-block:: console

    $ composer create-project pialechini/atmosphere <your-project-name>

Now, your project should be like this:

::

    <your-project-name>
    ├── Providers/ 
        ├── MiddlewareProvider.php
        ├── ScenarioProvider.php
        ├── SchemaProvider.php
    ├── handler.phpq
    ├── composer.json        
    ├── config.env
    ├── assistant

Finally, with the command below, you finish the installation steps

.. code-block:: console

    $ php assistant init


.. important:: After creating project, we highly recommend to execute the following shell command because if you don't do that, other ``assistant`` commands **won't** **work**
.. note:: If you lose the project structure at any time, it is possible to use ``init`` again to generate all necessary directories


Configurations
--------------

Bot configuration
^^^^^^^^^^^^^^^^^

::

    BOT_API_TOKEN = <YOUR_API_TOKEN>
    BOT_USERNAME = <BOT_USERNAME>



Database configuration
^^^^^^^^^^^^^^^^^^^^^^
In ``config.env``, there are several keys that define communication with database.

.. important:: Atmosphere uses Laravel Eloquent and because of its features it's available to use PostgreSQL or SQL Server


Mysql configuration
~~~~~~~~~~~~~~~~~~~

::

    DB_DRIVER = mysql
    DB_HOST = localhost
    DB_DATABASE = <YOUR_DB_NAME>
    DB_USERNAME = <YOUR_USERNAME>
    DB_PASSWORD = <YOUR_PASSWORD>
    DB_CHARSET = utf8
    DB_COLLATION = utf8_unicode_ci
    DB_PREFIX =


Sqlite configuration
~~~~~~~~~~~~~~~~~~~~

::

    DB_DRIVER = sqlite
    DB_DATABASE = /absolute/path/to/database.sqlite


