

## Dependencies ##

Installing Freex itself shouldn't be too hard. The tricky bit is getting all the dependencies working first. Here's the list:

### Emacs ###

We've been using version 22, but 21 and higher should work. On OS X we recommend [Carbon Emacs](http://www.emacswiki.org/cgi-bin/wiki/CarbonEmacsPackage) or [Aquamacs](http://aquamacs.org/).

### [Python](http://python.org/) ###

We've used both 2.4 and 2.5 with no problem.

UPDATE: it turns out that the Mac 2.5 Python has issues with very large regular expressions (thousands of nuggets). It's a [known bug](http://bugs.python.org/issue1160), and we're waiting for them to fix it in 2.7.

### [Pymacs](http://pymacs.progiciels-bpi.ca/) ###

Freex requires [Pymacs](http://pymacs.progiciels-bpi.ca/) to interface with python for all of its database functionality.

### [Sqlite](http://www.sqlite.org/) ###

We use Sqlite version 3 to hold the data.

### [Sqlalchemy](http://www.sqlalchemy.org/) ###

Sqlalchemy is the python interface to the database. The stable 0.3 version is working well for us. UPDATE: i think we're using 0.4.8 now (March 2009).

## Platforms ##

### Debian/Ubuntu ###

This is very easy:

```

sudo apt-get install emacs22 python2.5 python-pymacs sqlite3 python-sqlalchemy
```

Gotta love package management.

### Mac OS X ###

The long and the short of it is that you'll likely have to install all the dependencies from source. Follow the links provided above to download the packages. Each should have current instructions for compiling and installing them.

### Microsoft Windows ###

We have successfully tested Freex on Windows XP with Pymacs 0.23. This latest Pymacs version makes things [easier than before](http://groups.google.com/group/pymacs-devel/browse_thread/thread/13e381a7b8993ce7).

Other systems

On any other system, you'll have to see if there's some other package or binary you can use, or follow the [Pymacs installation instructions](http://pymacs.progiciels-bpi.ca/manual/Installation.html#Installation).


## Installing and configuring Freex itself ##

Download and untar the latest stable release Freex tarball from the [downloads page](http://code.google.com/p/emacs-freex/downloads/list) (which should be called something like 'freex-x.x.x.tar.gz'). Inside, you'll see a file called 'freex-conf-test.el.'. This provides an example configuration file. Make a copy and call it something like 'freex-conf.el' - you can store it with your Freex scripts, or put with your other elisp init files as you prefer.

Go through your new freex-conf.el and modify any references to '/Users/greg/elisp/freex' to the location containing your Freex scripts. Also, change the value of the 'freex-mode-dir' variable from '/Users/greg/elisp/freex/testdocs/' to wherever you'd like to store the text files containing your hard-won wisdom. It makes sense to keep this 'data' directory separate from the 'scripts' directory. Create your data directory now.

If you want to make sure that Freex mode loads up every time you start Emacs in future, just add these lines to your .emacs file:

```

(add-to-list 'load-path "/my/freex/scripts/")
(load "freex-conf")
```

Run M-x eval-buffer on freex-conf.el, and now Freex mode should be ready to go, as soon as it sees its first '.freex' file.


## Checking everything works ##

Now, open up a new file called 'test0.freex' in your freex data directory. If you see 'Freex' added to your mode bar at the bottom of your Emacs window, you're in business. If not, head to the Troubleshooting section.

Now, you're ready to try the intro [Tutorial](Tutorial.md).


## Using Freex with Muse ##

As you probably guessed, we are impressed and inspired by the [Muse](http://mwolson.org/projects/EmacsMuse.html) publishing system for Emacs. We are working on making Muse and Freex play well together and we are at least part way there (some percentage of Freex users actually run Freex in Muse mode on a daily basis.)

The following is how to set up Freex for use with one of your Muse projects (such as your personal wiki). As it currently stands, Freex can only be used to monitor a single directory on your system.

Given that Freex is a minor mode, all you really have to do is make sure it gets started whenever you are modifying a Muse file in the directory you want Freex to monitor. One issue is that we have to prevent Emacs from entering into Muse or Freex mode when saving and when we are not editing a file in the monitored directory, so we have to use a custom function to enter into Muse-Freex mode that we add to the auto-mode-alist. All of the necessary changes are outlined in the freex-conf-test.el file that is included with the Freex distribution - just look for:

```

Muse (XXX)
```