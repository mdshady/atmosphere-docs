Framework Overview
==================

What is ``update``?
-------------------
``Update`` is an object which Telegram API works with. (`Visit this link <https://core.telegram.org/bots/api#update>`_)


What will I do with this framework?
-----------------------------------
Typically, you should answer this question: What do you exactly do if you
receive an ``update`` from Telegram? What logic does your application use?

The framework meets all your needs. Thus, suppose an incoming ``update`` and
try to think about your application logic (defining middlewares and scenarios).


Incoming ``update``'s lifecycle
-------------------------------
1. In the first step, the framework automatically gets ``updates`` from Telegram, 
and pass them through middlewares. The middlewares are some classes in your application
which defines some general conditions on ``updates``. If an incoming update does not match
with these conditions, middleware in which the condition is violated, terminates the ``update`` 
So this incoming ``update`` no longer goes to scenarios. Once all middlewares accepted the 
incoming ``update``, it will go to the next level.

.. important:: The ``update`` goes through **all** **of** **middlewares** and must match with their conditions to be accepted!

.. figure:: ../_static/middlewares.png

| 

2. In this step, the ``update`` goes to the scenarios. Each scenario has 
some conditions. If the conditions are right for the ``update``, that scenario and it's children
(sub scenarios) take future control of ``update``'s lifecycle.

.. attention:: The first scenario that can accept the ``update`` will be executed and others won't work.

.. figure:: ../_static/scenarios.png
