Welcome to Atmosphere Framework's documentation!
================================================

A PHP Framework for telegram bot developers.
--------------------------------------------

.. image:: _static/logo.jpg


Why to use?
-----------
First is **UserFriendly** because:

	1. The High level interactions with telegram API (based on `php-telegram-bot <https://github.com/php-telegram-bot/core>`_)
	2. The Laravel-like structure (**middlewares**, **models**, **views**, etc.)
	3. It uses Laravel Eloquent ORM (fast and clean way to deal with database)
	4. Easy to use syntax
			
	.. code-block:: php

		<?php

		// will reply to current user message
		response()->reply()->send('I have gotten your message!');

	2. Fast in development process:
		You have an **assistant** **script** to generate your classes as fast as possible


.. toctree::
	:maxdepth: 2
	:caption: Table of Contents:

	installation
	framework/overview
