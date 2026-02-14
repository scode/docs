# rstquil: reStructuredText (rst) + sphinx frustration relief

So you\'re considering, or even being asked to, adopt [reStructuredText](http://docutils.sourceforge.net/rst.html) and
[Sphinx](http://www.sphinx-doc.org/) for your documentation needs. You\'ve done a ton of markdown or possibly asciidoc
in the past, but every time you try to use reStructuredText for **real**, something non-trivial, it instantly becomes
painful to get it to do what you want and you spend unreasonable amounts of time googling around. This is for you.

Or\... so I hope. This is what _I_ would have wanted, based on what _I_ consider to be the \"obviously immediately
important\" things I care about when writing documentation. Other people\'s definition of what is \"obviously
immediately important\" may differ, or their points of frustration may differ, but this is my best attempt at easing
adoption for people with similar biases to myself.

My relevant background is writing technical documentation aimed at other software developers in a large organization,
and so my needs are heavily based on this. Further, while I write a lot of documentation for a typical developer, it\'s
not the _only thing that I do_. Part of the frustration of adoption originally was that I would figure something out,
and then just about forget it again before the next time I sat down and did similar things.

Some of the terminology here is not formally correct with respect to the
[reStructuredText spec](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html), but rather intended to
convey meaning for someone with reasonable markup/asciidoc experience (sometimes it may also be because I felt it was
unclear what correct terminology is).

Finally, this is _not_ meant to be a complete replacement for other documentation. Rather, it\'s selectively picking a
few topics that I believe to be extra important and/or extra likely to cause frustration.

Suggestions/feedback? Feel free to [file a github issue](https://github.com/scode/docs/issues), open a pull request
[on github](https://github.com/scode/docs), or just email me at `peter.schuller@infidyne.com`[^1].

## Inline literals

Use _double_ backticks:

```rst
Let me tell you about the ``cool_function`` function!
```

A single backtick, like you\'re used to, may superficially appear to do what you want based on rendered output, but
_actually_ is for
[interpreted text](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#interpreted-text) which is
different.

## Code blocks / multi-line literals

The simplest way is to end your previous paragraph with a double-colon (and don\'t forget empty lines for paragraph
separation):

```rst
Here's an example of foo::

    # example of foo here
    # continued example of foo

And this is the next paragraph of text.
```

The is actually taking advantage of a convenience feature in reStructuredText. The above code-block is equivalent to
_both_ of these:

```rst
Here's an example of foo: ::

    # example of foo here
    # continued example of foo

And this is the next paragraph of text.
```

```rst
Here's an example of foo:

::

    # example of foo here
    # continued example of foo

And this is the next paragraph of text.
```

See the [literal blocks section](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#literal-blocks) of
the spec for more.

The biggest disadvantage of the form is that it does not allow you to specify the language contained in the block of
text - which you may want to do, for example to enable syntax highlighting. You may therefor use this form instead
(which appears to be Sphinx specific):

```rst
Here is an example snippet of Python:

.. code-block:: python

    print('Hello world!')

In the above example, we ...
```

See [showing code examples](http://www.sphinx-doc.org/en/stable/markup/code.html) in the Sphinx docs for more.

## Linking to URLs

NOTE: This is for linking to arbitrary URLs. For linking internally in your documentation (such as between sections),
please see the cross reference section later on.

The short story is to always use the following form unless you specifically know what you\'re doing (note the use of
_two_ underscores at the end, not just one):

```rst
`link text <link-url>`__
```

For example:

```rst
Please make sure you foo the bar (such as
in `this example <https://github.com/scode/docs/blob/master/README.md>`__).
```

Use of a single underscore (instead of two) will create a _named_ hyperlink target. This may appear to work, but you\'ll
find that you start generating warnings over time when you have multiple links with the same link text (even if they
have different target URLs).

The seemingly primary use of the _single_ underscore form seems to be to allow you to specify the link target separately
from the inline text. For example:

```rst
If you want you can look at the `project README`_.

bla bla...

.. _project README: https://github.com/scode/docs/blob/master/README.md
```

See
[the hyperlink targets section](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#hyperlink-targets) of
the spec for more information.

## Bulleted lists

First, a rule of thumb: Always keep an empty line between items in a bulleted or numbered list. I cannot tell you what
the rules are here, but I can tell you it will avoid a ton of frustration trying to understand why something isn\'t
interpreted the way you want. It\'s unfortunate because it is a strain on the eyes when reading the rst source, but I
would advice sticking to this rule until you feel like you want to really figure out and understand restructured text
and are prepared to deal with the problems when they arise.

Second, continuation of an item happens by starting the next line at the same column position as the previous line,
_not_ counting the list markup. The example below illustrates.

```rst
#. Foo, which requires a very long
   explanation. Notice the indentation of these
   lines ensuring that these sentences are all part of the
   same item in the list.

   #. Subfoo 1. Notice the alignment of the hash with the parent item's body.

   #. Subfoo 2.

#. Bar
```

Bulleted lists are exactly the same in terms of indentation and such, but use `*` (and others) instead of hashes:

```rst
* Foo, which requires a very long
  explanation. Notice the indentation of these
  lines ensuring that these sentences are all part of the
  same item in the list.

  * Subfoo 1. Notice the alignment of the hash with the parent item's body.

  * Subfoo 2.

* Bar
```

For more, see [enumerated lists](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#enumerated-lists)
and [bullet lists](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#bullet-lists) in the spec.

## Cross reference best practices {#rst-cross-references}

One of the very enticing benefits of using Sphinx is that of stable cross references that do not break when things move
around or sections are re-named - provided that best practices are followed (there is also support for cross references
across projects through [intersphinx](http://www.sphinx-doc.org/en/master/ext/intersphinx.html) but I have not used it
so am not covering it here).

Let\'s assume we have a document with a section on eating apples, and it has a label defined (`eating-apples`) for the
section:

```rst
.. _eating-apples:

Eating apples
-------------
```

We can now link to it from anywhere in our documentation project like this:

```rst
See :ref:`eating-apples` for more information.

See :ref:`the later section on apples <eating-apples>` for more information.
```

Note how the label is specified with a leading underscore but is referred to without it.

In the former case, the name of the section itself will be used in the rendered text. This is not always appropriate
because the context of the link is different than the context of the section heading itself, so you may want to refer to
the section by a different name - hence the second form.

The key to get the benefit here is to _explicitly_ define all labels that you ever link to. By default, sections will
receive an implicit label based on their name, but the problem with using those include:

- Links break when section names are tweaked, which defeats a big part of the purpose of using cross references.
- A section without an explicit label fails to signal to the person editing the file containing that section, that
  someone may be linking to the label.

For this reason, I strongly recommend always explicitly labeling sections when you decide to link to them. When editing
existing documentation, you should also assume that explicit labels may be linked to and take care to preserve them.
It\'s an indicator that someone cared about it enough to put a label there, and there\'s probably a link to it
somewhere.

(The previous guidance will obviously not work if you don\'t have the ability to modify the documentation you\'re
linking _to_. I don\'t know if there\'s a solution to that problem.)

Though I mentioned sections above, labels can be used anywhere and not just in front of sections. For example:

```rst
Roses are red and violates are blue, here's a code snippet:

.. _hello-world-snippet:

.. code-block:: python

    print('Hello!')
```

## Footnotes

The following example demonstrates the use of a named footnote.

```rst
I love eating fruits [#not-all-fruits]_.

.. [#not-all-fruits] Well, most of them.
```

In particular, note the white space preceding the `[` when referencing the footnote. This is required.

For more information, see [footnotes](http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#footnotes) in
the rst spec, and the [basics](http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html) in the sphinx
docs.

## Semi-automated conversion from markdown to rst

I\'ve found [pandoc](https://pandoc.org/) to be quite useful. It will _not_ be perfect, but it will take care of most of
the simple stuff and after the automated conversion you go through and perform manual fix-ups. Once you\'ve got it
installed:

```bash
pandoc -f markdown -t rst < file.md > file.rst
```

Then edit as appropriate.

[^1]: This would be a link, except I have not been able to figure out how to make a `mailto:` link in which the `@` sign
    is not URL encoded in the output. Know how to fix that? I\'ll add it to this guide :)
