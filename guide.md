---
title: Developer's guide
layout: article
author: Jan Decaluwe
date: 2013-12-23
---

====== Guide for developers ======

 --- //[[jan@jandecaluwe.com|Jan Decaluwe]] 2008/07/25 06:21//

===== Introduction =====

The MyHDL [[https://bitbucket.org/jandecaluwe/myhdl|source code repository]] can be used for several 
things, such as browsing through the development history,
and tracking development. In addition, you can use it to contribute your own
changesets. The workflow is such that every contributed change
is reviewed and applied or rejected by me. Therefore, your goal as a contributor should be to
minimize my work :-) What is needed is the following:

  * I need to understand why the change is needed, and why it will be useful to many people
  * I need some confidence that it won't break current and foreseeable things
  * the changes have to be tested
  * you have to use [[http://www.selenic.com/mercurial|mercurial]] to manage the changesets
  * you have to use [[http://www.bitbucket.org|Bitbucket]] to fork the main repo and create Pull Requests.

The implementation of these requirements is described in more detail in the following sections.

===== First things first: communicate =====

Don't send me patches out of the blue.

Your first step is to communicate about the problem or feature with the MyHDL community.
Start a discussion in the [[:mailing_list]] or (if you are certain) add an
entry in the [[http://sourceforge.net/tracker/?group_id=91207&atid=596332|Bug Tracker]].

The result will be a fruitful discussion :-) that hopefully results in a decision about
what should be done. The byproduct will be a specification for the work.

===== Creating changesets =====

To manage your patches, use mercurial. By doing so, I can simply use
my normal development workflow to incorporate your work. Moreover, your name
will be preserved as the author, so you get the credit you deserve.

In mercurial terminology, a set of patches that belong together is called
a //changeset//. Assuming you know how to work with mercurial, creating changesets
is easy. You make changes in your local repository clone, and use:

  $ hg commit

to create a new changeset that contains your patches.

===== First things first: quality =====

At a certain point you will want to publish your changesets, so that everyone can
benefit from them. However, don't publish your work until it is complete. Make
sure there are no loose ends that others will have to address after you.
Most importantly, make sure your changes have been tested.

Run the MyHDL regression tests to make sure nothing breaks.
As a minimum, the tests in ''test/core'' should be run. If your changes
are related to conversion to VHDL/Verilog, the test in the ''test/conversion''
directories should be run also.

Presumably, you have some test for your changes in place. If at all possible,
turn it into a test that can be added to the regression test suites.

You may need a number of changesets to complete your work. That isn't a problem at
all, on the contrary. Finish the job before publishing.
Note that this development flow relies on the decoupling of the creation and the
publication of changesets.
This is a distinguishing feature of distributed revision control systems versus centralized ones.

===== Contributing changesets =====

==== Pull Requests ====

When you are ready with your changes, use mercurial and Bitbucket to
publish them. The advantage of using mercurial instead of traditional
patch files is that it minimizes the overhead to review and apply,
and, more importantly, it keeps the authoring information intact.
The advantage of [http://www.bitbucket.org|Bitbucket] is that has
a great web interface to review and merge the changesets.

Contributing changesets is done by creating Pull Requests. This
process is documented here:

[[https://confluence.atlassian.com/display/BITBUCKET/Fork+a+Repo%2C+Compare+Code%2C+and+Create+a+Pull+Request|Bitbucket]]

I will review the Pull Request, and decide to merge them in or not.

==== Alternative for small changes ====

The Pull Request method is completely general, but it has
some overhead. For small changes, you can also use mercurial to generate
augmented patch files by exporting them. However, you then have to list the
revisions to be exported yourself. Also, you should not use this
method for merge changesets:

  hg export -o <patchfile> REV ...
  
In the simplest case, to create a patch containing your latest
commit, you would to this:

  hg export -o <patchfile> tip

Send the bundle or patch file to [[jan@jandecaluwe.com|Jan Decaluwe]].

==== Discussions ====

Keep any technical discussion leading about the changesets on the mailing list. Only
the final operation of sending the bundle file should not go there. That having
said, I can imagine advanced scenario's in which people exchange bundles on the
mailing list as a means to convince others about new features.
===== Tips =====

==== Commit messages ====

When logging changesets and browsing through the repository, mercurial uses only the first
line of the commit message. Therefore, the first line of your commit message should be a short, descriptive one-liner.
There's nothing against a more verbose message (on the contrary), but start
it on a new line.

