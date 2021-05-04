Installation
============

To create a new project use this composer syntax:

.. code-block:: bash

    $ composer create-project pialechini/atmosphere <your-project-name>

Now, your project should be like this:

::

    <your-project-name>
    ├── Providers/ 
        ├── MiddlewareProvider.php
        ├── ScenarioProvider.php
        ├── SchemaProvider.php
    ├── handler.php
    ├── composer.json        
    ├── config.env
    ├── assistant

Finally, with the command below, you finish the installation steps

.. code-block:: bash

    $ php assistant init


.. important:: After creating project, we highly recommend to execute the following shell command because if you don't do that, other ``assistant`` commands **won't** **work**
.. note:: If you lose the project structure at any time, it is possible to use ``init`` again to generate all necessary directories
