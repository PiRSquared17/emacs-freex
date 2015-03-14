# Introduction #

The purpose of several of the commands accessible within Freex mode via M-x freex-TAB are not immediately obvious. This page provides a few lines of description for each command.


# Details #

**freex-embed-all-tag-children**

This creates a special buffer that embeds all the nuggets tagged with the current nugget, including the current nugget. For instance, let's say you're interested in everything to do with 'elisp'. You open up 'elisp.freex', and then run freex-embed-all-tag-children, to see everything that relates to elisp, including the main elisp nugget itself.

You could think of this as being similar to freex-meta-find:

> elisp//`*`

but it also includes the 'elisp' nugget itself.


---


**freex-fontify-insert-sect-element**

Freex was intended to be heavily xml-based, so to insert headings of different levels, just include the following in a document:

`<sect level="2">`This is a level 2 heading`</sect>`

It will automatically get fontified. To save typing all of that yourself, you could just type 'hello', select it, and run this function. Or, more conveniently, just use one of the wrappers for it, e.g. freex-fontify-insert-sect-element-1.


---


**freex-sqlalchemy-modifier**

`[i` don't remember. And I can't seem to find it with grep. It could be some Pymacs black magic. If this is bugging you, I can look again more closely`]` - Greg D


---


**freex-embed-delete-outside-region**

It looks like this is needed in the innards of the embedding code. We did a **lot** of work to get recursive saving working nicely. Basically, every time you save a nugget with other nuggets embedded, it spawns a load of buffers (reflecting the tree structure of the embeddings), saving the content of each nugget-buffer as it goes.


---



**freex-embed-kill-buffer-no-query**

This should be straightforward. Just like the standard kill-buffer command, but don't ask the user. As above, this is part of spawning buffers to save the embedded nuggets. After we're done with the temporary buffers, we just want to get rid of them, so the user never notices all the work going on behind the scenes when you save. If a save ever gets interrupted halfway through, you may see a vestige of these temporary buffers.


---



**freex-xml-replace-element-at-point**

Per wrote/borrowed this code, but at a glance, it looks like it's replacing one XML element, e.g. `<sect ... blah></sect>` with another one. - Greg