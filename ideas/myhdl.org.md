---
title: myhdl.org 
layout: article
date: 2008-05-29
---

Background
==========

The principal MyHDL website is <http://www.myhdl.org>. It uses a php-based wiki
solution as a light-weight content management system. While this is an
efficient way to create on-line documentation, it cannot be used to provide
other types of online services. Moreover, the MyHDL community would obviously
prefer a Python-based solution.

The goal of this document is to explore whether there is a better solution.

The current MyHDL website
=========================

First, it is meaningful to describe some details about the current MyHDL
website. It is based on [dokuwiki](doku>), a php-based wiki package. A wiki
provides a quick way to create and edit web pages. Moreover, a wiki is
typically associated with the following features:

* the ability to edit content directly in the web browser, using a simple markup
language.
* the fact that anybody can edit content without restrictions.

However, the first feature is not a distinguishing feature of wiki's. For
example, blogs have it too. In fact, any modern content management system
provides it. What's more important is the power of the markup language. A great
number of alternatives is available.

For our purposes, the second feature is undesirable. Leaving the site open
without restrictions on the internet would not provide any benefit, but would
require constant monitoring and clean-up to keep it free from spam. Currently,
we require registration so that as minimum we know that only persons with a
valid e-mail address can make contributions. In the future, it may be necessary
to restrict this even further. In short, without a reasonable access control
mechanism, our present solution would be inadequate and we wouldn't have used
it.

The conclusion is that we are not really using the current tool as a wiki, but
as a (light-weight) content management system (CMS). For a future site, we are
looking for a more powerful CMS.

Technical Requirements for the website
======================================

A CMS
-----

So we are looking for a CMS. This is an important point to stress.

What we mean by this is the following: we don't want to develop the basic
services we need (such as writing documentation) ourselves. We want them to be
readily available, out of the box. Our main goal is to develop MyHDL, not CMS
solutions.

A web development framework, such as Django, Turbogears, or Zope, is not a CMS.
Those are tools that can be used to develop a CMS. CMS examples are Plone
(based on Zope) and Ellington (non-free, based on Django).

Easily extendable
-----------------

We are looking for an open solution.

Our ideal CMS solution follows the Python model. On the one hand, it should
consist of a small, powerful core with an extensive "standard library" that
deliver the basic services we need out of the box. On the other hand, it should
be possible to easily add new services, third-party or self-developed, using
the same mechanisms as for the standard library.

The current solution, or other wiki-specific software, doesn't follow this
model.

Python-based
------------

For obvious reasons, we are looking for a Python-based solution.

Creating great documentation quickly
------------------------------------

MyHDL is an open-source software project. There are a number of online services
that a CMS could potentially provide. However, the most important service that
we require from our CMS is the ability to create great on-line documentation
quickly.

In this it should be as good as our current solution. Let's describe a number
of important features in detail.

* **Easy navigation** Breadcrumbs, a sidebar, highlighting the current page in
the sidebar.

* **Collaboration and revision control** Multiple contributors must be able to
collaborate in a reliable way, and some level of revision control support
should be available for review and recovery.

* **Hierarchical content organization** The current solution uses namespaces
and access control based on them.

* **Powerful markup language** The markup language should be both simple and
powerful. It should support tables and understand source code from various
languages including Python, VHDL, Verilog, C and Java.

* **Easy editing** The current solution makes it possible to edit sections of
a page separately.



A open-source, winning solution
-------------------------------

Clearly we are looking for an open-source solution.

But in addition, we want to have a "winning" solution. To illustrate what this
means, consider revision control tools as an example. For a long time, cvs was
the clear market leader among the open-source solutions. Then suddenly, as a
result of some of its deficiencies coupled to changing usage requirements, a
lot of new tools and innovative ideas emerged, such as bitkeeper, arch,
subversion, git, darcs, mercurial, and several others.  At this point, I
believe there is a concensus that for the type of projects like MyHDL,
subversion is the "winning" solution. Perhaps cvs is still more widely used -
but it wouldn't make a lot of sense to use it for new projects. Also,
subversion is definely not the most interesting or innovative solution. It just
happens to have the right mix of features to get the momentum behind it.

I'd like to qualify the above paragraph. It has become clear that there are
really 2 types of revision control tools: centralized versus distributed. I
maintain that subversion is a winning solution among the centralized systems.
However, I have now become convinced that the distributed type is the wave of
the future. This is mainly because of a very positive experience with the
real-time usage of git. For MyHDL, I am in the process of converting to
mercurial, because it's a Python-based system and some very large projects have
converted to it. Also, it's the only other system tolerated by git's creator
(Linus) :-)  -- *[Jan Decaluwe][jandecaluwe-mail] 2008/05/29*
{: .comment}

It's a question of risk management. Of course we want to contribute to
open-source solutions, but our main focus to work and innovate on is MyHDL.
When we choose a CMS we want to make sure that for the forseeable future
innovation and problem fixing will continue (and will mainly be done by others
:-)).

Website management
==================

In addition to the technical requirements, another issue has to be resolved:
the website management. We have to define how to decide on issues like the
following.

* **Users and access control** Who is allowed access? What type of access?
What's the procedure for registering new users and contributors?
* **Content** What type of content are we looking for? How do we resolve
conflicts about content?
* **Licensing** How is the site content licensed?

The management of the current MyHDL website is simple: MyHDL's author and
maintainer owns the site and has the power to decide on everything. As the new
website should be "owned" by the "community", this would have to change. The
question is how; this is completely open at this point.

Solution status
===============

We have not found an adequate solution yet; it may not yet exist.

It seems that at this point, the main action and innovation in the Python world
is in the development of new web development frameworks - the things that can
be used to develop a CMS. For example, a lot of new template languages are
being developed and proposed. A lot of people just don't seem to be happy with
the traditional Python solution (Zope).

It seems only a matter of time before an open-source CMS solution will
be developed on top of a "winning" web development framework, along
the lines that we have descirbed. But that hasn't happened yet.



