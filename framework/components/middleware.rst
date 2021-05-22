Middleware
==========

* `Philosophy <Philosophy_>`_
* `Use cases <Use cases_>`_
* `Creating a new middleware <Creating a new middleware_>`_

  * `Automatically <Automatically_>`_
  * `Manually <Manually_>`_


Philosophy
----------
Middlewares are one of the most common used features in this framework. 
Like Laravel middlewares, with help of this component you can handle every thing
you want to process before an ``update`` reaches your application's logic.

Each middleware has an ``allow`` method which accepts an ``update`` instance
(automatically injected by framework) and returns a boolean value.

.. note::

    if ``allow()`` returns

    * ``true``: update will be passed to next middlewar
  
    * ``false``: the update will be terminated


Look at this fun middleware:

.. code-block:: php
    :caption: ~/Middlewares/NAME.php

    <?php

    namespace Bot\Middlewares;


    use BotFramework\Middlewares\Middleware;
    use Longman\TelegramBot\Entities\Update;

    class CheckPoliteness extends Middleware
    {
        public function allow (Update $update) : bool
        {
            return str()->contains($update->getMessage()->getText(), 'please'))
        }
    }

With the code above, the bot only accepts messages which contain
the word 'please' !


Use cases
---------
* Store every upcoming update (in database or file) regardless of which scenario will be applied on
* Block unwanted updates/messages
* Report every update to administrator of bot
* Limit message sending time (ex: servicing at night or from 16:00 to 16:30)


Creating a new middleware
-----------------------
there are two ways for creating a new middleware.

* `Automatically <Automatically_>`_ (with ``assistant``)
* `Manually <Manually_>`_

Automatically
^^^^^^^^^
.. code-block:: console

    $ php assistant make:middleware <NAME>

or creating multiple middlewares at once:

.. code-block:: console

    $ php assistant make:middleware <NAME1> <NAME2> ...


Middleware class (*Middlewares/NAME.php*):

.. code-block:: php

    <?php

    namespace Bot\Middlewares;


    use BotFramework\Middlewares\Middleware;
    use Longman\TelegramBot\Entities\Update;

    class NAME extends Middleware
    {
        public function allow (Update $update) : bool
        {
            // handle
        }
    }

Provider (*Providers/MiddlewareProvider.php*):

.. code-block:: php

    <?php
    
    namespace Bot\Providers;


    class MiddlewareProvider
    {
        public static function register () : array
        {
            return [
                \Bot\Middlewares\NAME::class,
            ];
        }
    }


Manually
^^^^^^
Creating a middleware class manually and register it in 
``Middlewares/MiddlewareProvider.php``.


.. hint:: 
    We highly recommend you to use ``assistant`` because of it's **reliability**,
    **speed** and **automation** **in** **class** **registrations**.
