Framework Overview
==================


Incoming ``update``'s lifecycle
-------------------------------

Let's start with this. Typically, you should answer this
question: What do you exactly do if you receive an ``update`` from Telegram?
What logic do you have in your application?

The framework meets all your needs. Thus, suppose an incoming ``update`` and
try to think about your application logic (defining middlewares and scenarios).

1. In the first step, the framework automatically gets ``updates`` from telegram, 
and pass them through middlewares. The middlewares are some classes in your application
which defines some general conditions on ``updates``. If an incoming update does not match
with these conditions, middleware in which the condition is violated, terminates the ``update`` 
So this incoming ``update`` no longer goes to scenarios. Once all middlewares accepted the 
incoming ``update``, it will go to the next level.

.. attention:: The ``update`` goes through **all** **of** **middlewares** and must match with their conditions to be accepted!

.. figure:: ../_static/middlewares.png

| 

1. In this step, the ``update`` goes to the scenarios. Each scenario has 
some conditions. If the conditions are right for the ``update``, that scenario and it's children
(sub scenarios) take future control of ``update``'s lifecycle.

.. important:: The first scenario that can accept the ``update`` will be executed and others won't work.

.. image:: ../_static/scenarios.png


