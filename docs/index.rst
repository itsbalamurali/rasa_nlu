
Language Understanding with rasa NLU
====================================


rasa NLU is an open source tool for intent classification and entity extraction. For example, taking a sentence like 

.. code-block:: console

    "I am looking for a Mexican restaurant in the center of town"

and returning structured data like

.. code-block:: json

    { 
      "intent": "search_restaurant",
      "entities": {
        "cuisine" : "Mexican",
        "location" : "center"
      }
    }


The intended audience is mainly people developing bots. 
You can use rasa as a drop-in replacement for `wit <https://wit.ai>`_ , `LUIS <https://luis.ai>`_ , or `api.ai <https://api.ai>`_, the only change in your code is to send requests to ``localhost`` instead (see :ref:`section_migration` for details). 

Why might you use rasa instead of one of those services?

- you don't have to hand over your data to FB/MSFT/GOOG
- you don't have to make a ``https`` call every time.
- you can tune models to work well on your particular use case.

These points are laid out in more detail in a `blog post <https://medium.com/lastmile-conversations/do-it-yourself-nlp-for-bot-developers-2e2da2817f3d>`_ .


The quickest quickstart in the west
------------------------------------


.. code-block:: console

    $ python setup.py install
    $ python -m rasa_nlu.server -e wit &
    $ curl 'http://localhost:5000/parse?q=hello'
    [{"_text":"hello","confidence":null,"entities":{},"intent":"greet"}]


There you go! you just parsed some text. Next step, do the :ref:`section_tutorial`.

About 
---------------------------------------

You can think of rasa NLU as a set of high level APIs for building your own language parser using existing NLP and ML libraries.
The setup process is designed to be as simple as possible. If you're currently using wit, LUIS, or api.ai, you just:

1. download your app data from wit or LUIS and feed it into rasa NLU
2. run rasa NLU on your machine and switch the URL of your wit/LUIS api calls to ``localhost:5000/parse``.

rasa NLU is written in Python, but it you can use it from any language through :ref:`section_http`.
If your project *is* written in Python you can simply import the relevant classes.

rasa is a set of tools for building more advanced bots, developed by `LASTMILE <https://golastmile.com>`_ . This is the natural language understanding module, and the first component to be open sourced. 


Read Next:

.. toctree::
   :maxdepth: 1

   tutorial
   backends
   config
   migrating
   http
   visualize
   closeloop
   python
   persist
   troubleshoot
   roadmap
   contribute
   license



