(this is the script for [freex\_screencast\_090308c.mov](http://emacs-freex.googlecode.com/files/freex_screencast_090308c.mov))

Hi. I'm Greg Detre. With Per Sederberg, I'm the co-author of Emacs Freex mode.

Emacs Freex mode helps you organize and edit a massively-hyperlinked database of your notes and ideas. It's a personal wiki on steroids, all within Emacs.

In order to follow along with the screencast, first:

  * Head to http://emacs-freex.googlecode.com.

  * Download and install Freex.

  * Open up ~/path/to/freex/scripts/freex-conf-test.el.

  * Save as freex-conf-demo.el.

  * Search through looking for 'xxx', and change appropriately.

  * Add these lines to your .emacs file:
    * (add-to-list 'load-path "/Users/greg/elisp/freex")
    * (load "freex-conf-demo")

Let's say you want to keep a journal, idea-log or scrapbook of some kind. You want it to be easy to add and edit your notes, but have powerful tagging and searching capabilities.

Let's start by creating a journal.

  * M-x freex-meta-find 'journal'. Type something in ('hello'). Save it.

  * Now type 'journal'. Notice that it automatically becomes a hyperlink.

  * Type a couple of entries, e.g.:

```

----
22 October 2007

toilet paper ran out today.


----
23 October 2007

got awarded Nobel Prize today. Again.


----
24 October 2007

still no toilet paper. Good job I'm constipated.


----
25 October 2007

no longer constipated. one problem down, but still no toilet
paper, so I have other problems now.
```

Enough.

  * Highlight the first entry. Run M-x freex-embed-define-region-as-nugget, and enter "journal - 22 October 2007". Save.

Notice that the region you highlighted now has a grey background. You just created a nugget called 'journal - 22 October 2007" that is embedded within "journal". In other words, you can have nuggets embedded within other nuggets.

  * Run M-x freex-meta-find "journal - 22 October 2007", and you'll see your entry. Try editing it and save.

  * Now, go back to "journal", close it and reopen it. It should have updated to reflect your changes.

  * Let's tag our first entry now. Put the cursor inside the first entry, and run M-x freex-meta-edit-tag-parents-in-minibuffer.

You should see "journal/22 October 2007/". In other words, your first entry is tagged with (i.e. belongs to) "journal" and "22 October 2007".

  * Tag it with "toilet paper".

  * Now, highlight the second entry, define that as a nugget called "journal - 23 October 2007" just as before, and tag it with "Nobel Prize".

Now, Nobel Prize will show up as a link too, though you might have to edit the text nearby to make emacs notice that it's there.

  * Edit the text nearby

  * Highlight the third entry, name it, and tag it with "toilet paper" and "constipated".

  * Close all your buffers.

Let's pretend that you're trying to find that nugget you wrote about toilet paper and being constipated so that you can recount the story at a dinner party.

  * Run M-x freex-meta-find and enter "toi[TAB](TAB.md)". It'll complete to "toilet paper". We want the nuggets that belong to "toilet paper" though, not "toilet paper" itself

  * So put in "toilet paper/[TAB](TAB.md)".

If this was a file system, this would be like saying "which files are in the 'toilet paper' directory?". But we're not in Kansas any more, as you'll begin to see.

Think of anything with a "/" on the end as a kind of subdirectory, i.e. a category that you could use to further whittle down the list of items that belong to "toilet paper". In this case, you could usefully whittle things down with the date, or by "constipated", so let's try that.

  * Enter "toilet paper/constipated/[TAB](TAB.md)".

Sure enough, it should complete to "toilet paper/constipated/journal - 24 October 2007", the only nugget that is tagged with both "toilet paper" and "constipated".

  * Try looking for M-x freex-meta-find toilet paper/"other problems now"/

  * toilet paper//

Hmmmm. My aim was to tell you enough to be dangerous. Not dangerous like a man aiming at a cow with a shoulder-mounted rocket launcher is dangerous, but dangerous enough to be getting on with. Maybe try the more technical, introductory [Tutorial](Tutorial.md) now.