==================================
HTML Landing Pages From VOResource
==================================

This is an XSLT stylesheet to turn VOResource_ into an HTML-formatted
landing page accessible to non-VO users (but still useful to people
knowledgeable about the VO_).  It can be, in particular, used to make
`IVOA Identifiers`_ resolve to something usable in non-VO contexts.

A service in which this is live is GAVO's ivo landing page service: If
you have an ivoid like, for instance, ``ivo://cds.vizier/j/apj/852/48``,
you can just replace the schema part with ``http://dc.g-vo.org/LP/`` and
feed the result to a commen web browser.  In the example, this yields
http://dc.g-vo.org/LP/cds.vizier/j/apj/852/48.

.. _IVOA Identifiers: http://ivoa.net/Documents/IVOAIdentifiers/
.. _VOResource: https://ivoa.net/documents/VOResource/
.. _VO: https://ivoa.net


Deployment
----------

The stylesheet should work client-side, so you will probably get away by
prepending a::

  <?xml-stylesheet href='/PATH/TO/XSLT' type='text/xsl'?>

to a VOResource file.  Note that some browsers will only process XSLT
stylesheets when delivered over https, and a same-origin policy is
typically enforced.  This means that when transforming on the client
side, the stylesheet needs to be served from within your web server.

You will also have to make the ``landingpages.css`` file accessible
somewhere in you webserver and adapt the string
``/ADAPT/FOR/YOUR/SITE/`` within ``vor-to-landing.xslt`` accordingly
(though that could be a cross-server link).

An example deployment with server-site rendering is `in the GAVO voidoi
service`_ (this link will only work if your browser does not wantonly
change http to https); see ``res/landingpage.py`` there.

.. _in the GAVO voidoi service: http://svn.ari.uni-heidelberg.de/svn/gavo/hdinputs/voidoi


Public Domain Dedication
------------------------

This material is distributed under CC0_.

.. _CC0: https://spdx.org/licenses/CC0-1.0.html
