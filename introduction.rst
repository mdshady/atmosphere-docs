Introduction
============

Why Atmosphere?
-----------
It is **UserFriendly** because:

	1. High level interactions with Telegram API (based on `php-Telegram-bot <https://github.com/php-telegram-bot/core>`_)
	2. Laravel-like structure (**middlewares**, **models**, **views**, etc.)
	3. It uses Laravel **Eloquent** **ORM** (a fast and clean way to deal with databases).
	4. Fast in development process. You have an **assistant** **script** to generate your classes as fast as possible.

	5. Easy to use syntax
			
	.. code-block:: php

		<?php

		// will reply to current user message
		response()->reply()->send('I have gotten your message!');
