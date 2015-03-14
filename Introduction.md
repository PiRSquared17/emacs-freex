[Emacs Freex mode](http://emacs-freex.googlecode.com) is a minor mode for organizing and editing a massively-hyperlinked database of your notes and ideas. It's a personal wiki on steroids.

If you learn best by doing, then you might want to skip to the [Quickstart](Quickstart.md) or [Tutorial](Tutorial.md) to start with.

Freex mode is a minor mode designed to help you deal with all of your notes and ideas. It has features and ideals in common with [Emacs Muse](http://mwolson.org/projects/EmacsMuse.html), [Howm](http://howm.sourceforge.jp/), [linkd](http://dto.freeshell.org/notebook/Linkd.html), [org](http://www.emacswiki.org/cgi-bin/wiki/OrgMode), and probably a flotilla of other modes that we don't even know about.

Freex mode has 3 major infrastructural features that separate it from other offerings:

  * Stores all of the metadata for your notes in a [sqlite](http://www.sqlite.org/) database, alongside the text content in flat text files. The user can query this database transparently from within Emacs, through Pymacs.
  * Extends Emacs' built-in overlays functionality, allowing you to embed all kinds of information (e.g. files, database queries) within other files, all visible and editable in the same buffer.
  * Makes extensive use of [Pymacs](http://pymacs.progiciels-bpi.ca/) to access python libraries. This is both a boon and a bane. It adds a major dependency, but dramatically extends the scope of what can be achieved within Emacs lisp.

As a result, Freex mode has a variety of handy features for taking notes:

  * Automatically creates hyperlinks as you type to any 'nuggets' (i.e. files) in your database of that name.
  * Any nugget can be 'tagged' as a member of another nugget ([del.icio.us](http://del.icio.us/)-style). This sounds weird, but it becomes intuitive very quickly. Simply put, a nugget can belong to multiple categories. Those categories don't have any special ontological status - they're just other nuggets.
  * Any nugget can embed the content from other nuggets (which can in turn embed other nuggets) right inside the buffer, like Matryoshka dolls. This means that you can have compound documents that incorporate smaller fragments easily. You can edit embedded nuggets, and they will be saved as you'd expect. A nugget can be embedded in multiple places. Also known as [transclusion](http://en.wikipedia.org/wiki/Transclusion).
  * Freex is a minor mode, so you can run it in conjunction with (e.g.) Emacs Muse mode, to benefit from Muse's sophisticated publishing abilities. Unfortunately, Freex doesn't always play as nicely with other modes, so your mileage may vary.
  * Powerful querying syntax, that allows you to easily create queries like 'list all the nuggets that belong to both 'emacs' and 'python', and contain the term "sql"'. The really cool part is that you get instantaneous tab-completion, so Freex will list all the nuggets matching your query so far, as well as suggesting further categories to whittle down your search. Also known as 'faceted' or 'guided search'.
  * Freex actually combines the best of both tagging and hierarchy, by allowing second-level tagging (i.e. tags that are tagged with other tags).