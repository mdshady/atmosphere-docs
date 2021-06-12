Framework Overview
==================

* `What is update? <What is update?_>`_
* `What is the goal ? what should I do? <What is the goal ? what should I do?_>`_
* `Incoming update lifecycle <Incoming update lifecycle_>`_


What is update?
---------------
Update is an object which Telegram API works with (`Visit this link <https://core.telegram.org/bots/api#update>`_).


What is the goal ? what should I do?
------------------------------------
Typically, you should answer this question: 

    "What do you exactly do if you receive an ``update`` from Telegram?
    What logic does your application use?"

Atmosphere meets all your needs. Thus, suppose an upcoming ``update`` and
try to think about your application's logic (defining middlewares and scenarios).


Upcoming update lifecycle
-------------------------------
1. In the first step, the framework automatically gets ``updates`` from Telegram
and passes them through middlewares. the Middlewares are some classes in your application
which define general conditions on ``updates``. If an upcoming update does not match
with these conditions, the middleware in which condition is violated terminates the ``update``.
So this upcoming ``update`` no longer goes to scenarios. Once all middlewares accept the 
upcoming ``update``, it will go to the next level.

.. important:: The ``update`` goes through **all** **of** **middlewares** and must match with their conditions to be accepted!

.. figure:: ../_static/middlewares.png

| 

2. In this step, the ``update`` goes to the scenarios. Each scenario has 
some conditions. If the ``update`` matches all the conditions, that scenario and it's children
(sub scenarios) take future control of the ``update``'s lifecycle.

.. attention:: The first scenario that can accept the ``update`` will be executed and others won't work.

.. figure:: ../_static/scenarios.png
