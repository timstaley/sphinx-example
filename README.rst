sphinx-example
==============

A mini-tutorial / working example / cheatsheet / link-collection to get you
started documenting Python code using the Sphinx_ documentation system.

This was hastily put together for an `Oxford Astrophysics`_ code-coffee
session in March 2017, so it's

- brief
- possibly erroneous
- perhaps out-of-date at time of reading

Treat accordingly.

Sphinx and RST - What are they?
-------------------------------
Sphinx_ is a markup formatting engine / ecosystem, originally
developed for documenting the Python programming language.
You likely have already
come across other markup formatters / formats such as LaTeX and MarkDown_.

The format Sphinx uses is called 'reStructuredText', or 'RST' for short.
It sits somewhere in-between MarkDown (simple, good for a single-page document
with hyperlinks, maybe an image or two) and LaTeX (complex, good for a PhD
thesis with huge tables and loads of images and cross-referenced equations
and bibliographies). It's useful to understand the distinction - RST defines
a basic formatting language which can be extended and customised, but isn't
specifically aimed at Python.

Once you get past the basic formatting syntax of RST (e.g. **bold**, *italic*,
``code``, `hyperlink <https://www.youtube.com/watch?v=dQw4w9WgXcQ>`_)
you'll quickly come across the more powerful syntax elements, directives_
and roles_. These are a way of defining a sort of custom formatting 'function';
a role is used for formatting or hyperlinking a short span of text, while a
directive is used for formatting a whole block of text, and may have multiple
`options <directives_>`_.

Sphinx adds a standard framework of useful extra roles and directives
(and many optional extensions) that make it well suited to documenting Python
code (and perhaps C++ if you're adventurous: see Breathe_).
Sphinx is designed primarily for creating HTML
documentation, but can also create static PDFs etc.

We'll talk through the process of setting up Sphinx-docs from scratch in the
coffee-session, but in case you need a reminder or are simply reading this
online, check out the tutorials in the links below.

Super-brief overview
--------------------
A set of Sphinx-docs is just a collection of RST files
('the source') and a Python file typically called *conf.py* which controls
the configuration (HTML theme, Sphinx-extensions, etc etc). You build the
source using the ``sphinx-build`` command, like so::

    $ sphinx-build -b html sourcedir builddir

See ``sphinx-build --help`` for details.

If Sphinx can find your Python code (either because you've packaged it [*]_ and
installed into into your working environment, or added it to ``sys.path``
in your *conf.py* - see tutorials), then you can use the autodoc_ extension
to generate HTML pages from your *in-code* Python docstrings. Which suddenly
become a lot more useful. (NB, make sure ``sphinx.ext.autodoc`` is in your
``extensions`` list in *conf.py*.)

If you're writing docstrings, you should probably be documenting your parameters
and return types. I think the built-in format for this is ugly / hard-to-read,
so I recommend the Sphinx-Napoleon_ extension.

If your code is openly-hosted on GitHub, you can use ReadTheDocs_ to host your
docs with automatic updates (some configuration required).

.. [*] (Something we'll hopefully cover in another code-coffee session)



RST Links and references
------------------------
- An RST 'cheat-sheet': https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst
- The full RST language reference: http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html
- An online RST editor with live-preview (just remember to copy the text when
  done and save locally!): http://rst.ninjs.org/
- (Aside: there's a neat live-editor for MarkDown, too: http://dillinger.io/)

Sphinx links
------------
- Official tutorial: http://www.sphinx-doc.org/en/stable/tutorial.html
- Slightly more friendly unofficial tutorial: https://samnicholls.net/2016/06/15/how-to-sphinx-readthedocs/
- Sphinx-Napoleon, for nicer docstrings: http://sphinxcontrib-napoleon.readthedocs.io/en/latest/index.html
- Sphinx-Argparse, for documenting argparse_ driven command-line interfaces: https://sphinx-argparse.readthedocs.io/
- NBSphinx, for building documentation from Jupyter Notebooks: https://nbsphinx.readthedocs.io/
- ReadTheDocs, for auto-building and online hosting of your docs: https://docs.readthedocs.io/
- Fully-fledged example (of mine) including notebooks and more: http://voevent-parse.readthedocs.io/

.. _argparse: https://docs.python.org/3/library/argparse.html
.. _autodoc: http://www.sphinx-doc.org/en/stable/ext/autodoc.html
.. _Breathe: http://breathe.readthedocs.io/
.. _directives: http://www.sphinx-doc.org/en/1.5.1/glossary.html#term-directive
.. _MarkDown: http://daringfireball.net/projects/markdown/syntax
.. _Oxford Astrophysics: http://www2.physics.ox.ac.uk/research/astrophysics
.. _ReadTheDocs: https://docs.readthedocs.io/
.. _roles: http://www.sphinx-doc.org/en/1.5.1/glossary.html#term-role
.. _Sphinx-Napoleon: http://sphinxcontrib-napoleon.readthedocs.io/en/latest/
.. _Sphinx: http://www.sphinx-doc.org/
