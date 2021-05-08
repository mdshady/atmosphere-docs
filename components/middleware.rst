Middleware
==========

Philosophy
----------

Middlewares are one of most common usage feature in this framework. 
Like Laravel middlewares, with this component you can handle every thing
you want to process before the ``update`` reaches your application logic.

Each middleware has ``allow`` method which accepts an ``update`` instance
(automatically injected by framework) and returns a boolean value.

.. note::

    if ``allow()`` returns

    * ``true``: update will be passed to next middleware.

    * ``false``: update will be terminated.


Look at this fun middleware:

.. code-block:: php

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

With the code above, the bot only accepts messages which contains
the word 'please' !

Use cases:
----------
* Store every incoming update (in database or file) regardless of which scenario will be apply on
* Block unwanted updates/messages
* Report every update to administrator of bot
* Limit message sending time (ex: servicing at night or from 16:00 to 16:30)


Create a new middleware
-----------------------
You have to ways to create a new middleware.

* Automatic: with ``assistant``.
* Manual


Automatic way
^^^^^^^^^^^^^
.. code-block:: shell

    $ php assistant make:middleware <NAME>

or create multiple middlewares at once:

.. code-block:: shell

    $ php assistant make:middleware <NAME1> <NAME2> ...

Then you can find your middleware/middlewares in 'Middlewares' directory.

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

Manual way
^^^^^^^^^^
Create middleware class manually and register it in 
``Middlewares/MiddlewareProvider.php``.


.. hint:: 
    We highly recommend to use ``assistant`` because of it's **reliability**,
    **speed** and **automation** **in** **class** **registrations**.

