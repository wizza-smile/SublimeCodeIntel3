SublimeCodeIntel3
=================

This fork is mainly meant to be a refinement of the wonderful `SublimeCodeIntel <https://github.com/SublimeCodeIntel/SublimeCodeIntel>`_ plugin.
This is for Sublime Text 3 only.
It was developed with a focus on PHP, Python and JavaScript. Bug reports (for all languages), PR and general feedback are welcome!
If you're coming from the original SublimeCodeIntel, take a close look at the ``Configuring`` and ``What's New`` sections below!

---------------------------------------

Code intelligence plugin ported from `Open Komodo Editor <http://www.openkomodo.com/>`_ to `Sublime Text <http://www.sublimetext.com/>`_.

Supports all the languages Komodo Editor supports for Code Intelligence (CIX, CodeIntel2):

    JavaScript, Mason, XBL, XUL, RHTML, SCSS, Python, HTML, Ruby, Python3, XML, Sass, XSLT, Django, HTML5, Perl, CSS, Twig, Less, Smarty, Node.js, Tcl, TemplateToolkit, PHP.

Provides the following features:

* Jump to Symbol Definition - Jump to the file and line of the definition of a symbol.
* Imports autocomplete - Shows autocomplete with the available modules/symbols in real time.
* Function Call tooltips - Displays information in the status bar about the working function.

Plugin should work in all three platforms (MacOS X, Windows and Linux).


Installing
----------

**Without Git:** Download the latest source from `GitHub <http://github.com/wizza-smile/SublimeCodeIntel3>`_ and copy the whole directory into the Packages directory.

**With Git:** Clone the repository in your Sublime Text Packages directory, located somewhere in user's "Home" directory::

    git clone git://github.com/wizza-smile/SublimeCodeIntel3.git


The "Packages" packages directory is located differently in different platforms. To access the directory use:

* OS X::

    Sublime Text -> Preferences -> Browse Packages...

* Linux::

    Preferences -> Browse Packages...

* Windows::

    Preferences -> Browse Packages...


Using
-----

* Start typing code as usual, autocomplete will pop up whenever it's available. SublimeCodeIntel will also allow you to jump around symbol definitions even across files with just a click ..and back.

  For Mac OS X:
    * Jump to definition = ``Control+Click``
    * Jump to definition = ``Control+Command+Alt+Up``
    * Go back = ``Control+Command+Alt+Left``
    * Manual Code Intelligence = ``Control+Shift+space``

  For Linux:
    * Jump to definition = ``Super+Click``
    * Jump to definition = ``Control+Super+Alt+Up``
    * Go back = ``Control+Super+Alt+Left``
    * Manual Code Intelligence = ``Control+Shift+space``

  For Windows:
    * Jump to definition = ``Alt+Click``
    * Jump to definition = ``Control+Windows+Alt+Up``
    * Go back = ``Control+Windows+Alt+Left``
    * Manual Code Intelligence = ``Control+Shift+space``

Don't despair! The first time you use it it needs to build some indexes and it can take more than a few seconds.

It just works!


Configuring
-----------
Basic settings can be configured in the User File Settings.

All settings can be overridden in the *.sublime-project file under the value "codeintel_settings". For Example::

    {
        "codeintel_settings":
        {
          "codeintel_database_dir": "~/.codeintel/databases/myProject",
          "codeintel_language_settings":
          {
              "JavaScript": {
                  "codeintel_scan_files_in_project": true,
                  "codeintel_scan_exclude_dir": ["/min/"]
              },
        }
    }

If you put this in your *.sublime-project file, the codeintel-machine will use the given directory as its database,
scan the project folders for JavaScript source files but exclude paths that somehow match with the regular expression "/min/"


To define settings specifically for a language, use the "codeintel_language_settings" setting. Example::

    {
        "codeintel_settings":
        {
            "codeintel_language_settings":
            {
                "PHP": {
                    "php": '/usr/bin/php',
                    "phpConfigFile": 'php.ini',
                    "codeintel_live": true
                },
                "Perl": {
                    "perl": "/usr/bin/perl",
                    "codeintel_tooltips": "popup"
                },
                "Ruby": {
                    "ruby": "/usr/bin/ruby",
                    "codeintel_word_completions": "buffer"
                },
                "Python": {
                    "python": '/usr/bin/python',
                    "codeintel_scan_extra_dir": ["dir/one", "dir/two"]
                },
                "Python3": {
                    "python3": '/usr/bin/python3',
                    "codeintel_selected_catalogs": ["PyWin32"]
                }
            }
        }
    }

This is an extreme example, but should give you an impression of the flexibility of the language settings.

For adding additional library paths (django and extra libs paths for Python or extra paths to look for .js files for JavaScript for example), either add those paths as folders to your project, use the "codeintel_scan_extra_dir" setting.
It is recommended to configure this setting on a "per-language" basis, as a great number of import dirs will slow down the autocompletion process.



Do NOT edit the default SublimeCodeIntel settings. Your changes will be lost when SublimeCodeIntel is updated. ALWAYS edit the user SublimeCodeIntel settings by selecting "Preferences->Package Settings->SublimeCodeIntel->Settings - User". Note that individual settings you include in your user settings will **completely** replace the corresponding default setting, so you must provide that setting in its entirety.

Available settings:

* Information for all possible settings is available in the ``SublimeCodeIntel.sublime-settings`` file in the package.


Troubleshooting
---------------

To force re-indexation of the code intelligence database you need to follow these steps:

* Close Sublime Text

* Open a terminal or navigate through your directories to find the database directory (default:``~/.codeintel``) that contains ``codeintel.log``, ``VERSION`` and the directory ``db``. In Windows, this should be at ``%userprofile%\.codeintel``.

* Delete the whole directory and all of its content.

* Start Sublime Text and enjoy a clean re-indexing!



What's New
----------
v3.0.2:

+ PHP completions within function brackets

v3.0.1:

+ only working with ST3

+ new settings concept. Settings can now be defined in *.sublime-project file

+ define the directory, where your projects codeintel database should reside (new setting "codeintel_database_dir")

+ sublime style word completions from buffer (new setting "codeintel_word_completions"   possible values: "buffer", "all" or "none")

+ completions are now showing user-defined snippets (the way its supposed to be, isnt it?)

+ PHP local variables support

+ PHP static variables support

+ PHP completions from HTML embedded blocks

- fix the "codeintel_scan_exclude_dir" setting (it was doing nothing at all so far!)

- improved speed for PHP completions dramatically by fixing the number of import libs

- no longer crashes when saving settings file


v2.0.6 (?):

+ Tooltips can use Popups, Output Panel or Status Bar ("popup", "panel", "status" respectively, in the settings)

- Resolved issues with XML and other languages.

- Improved speed by using cache for some things (added zope.cachedescriptors)


v2.0.5 (18-09-2013):

- Resolved issues with ST2 in Mac OS X and Windows

- Fixed a few problems with Ruby and HTML parsers in ST3


v2.0.4 (16-09-2013):

* First non-pre-release for ST3


v2.0.3 (14-09-2013):

* Libraries built for compatibility with more systems.


v2.0.2 (12-09-2013):

* Initial Sublime Text 3 support!

+ OpenKomodo codebase updated to r13636

+ Snippets insertion delayed a bit.

+ Tooltips are removed when line changes.

- Improved autocomplete in HTML.


v2.0.1 (19-07-2013):

- Removed some Linux dependencies to GLIBC_2.4.

- Sublime Text 2 built-in auto complete no longer disabled by default (use `"sublime_auto_complete": false` setting instad).


v2.0 (11-07-2013):

+ SublimeCodeIntel's openkomodo codeintel engine updated. The new codeintel is faster and more reliable.

+ Sources have their own repositories at http://github.com/SublimeCodeIntel

- Disables Sublime Text 2's auto_complete by default (new ``sublime_auto_complete`` setting)

- JavaScript and PHP: Do not include all files and directories from the project base directory while scanning.

- JavaScript: Maximum directory depth is set to 2 (add explicit paths using javascriptExtraPaths).

- PHP: Maximum directory depth is set to 5 (add explicit paths using phpExtraPaths).

+ Snippets for functions inserted during autocomplete.

+ Binary files for Linux, Windows and Mac OS X updated.

+ Shortcuts for jump to definition have changed.

- PHP and UDL languages bugs fixed.

- Stability improved (Should no longer use 100% CPU all the time.)


v1.4 (05-07-2013):

+ Added improved Package Control support and updated old versions.

+ Started transition to v2.0


v1.3 (20-12-2011):

+ This build should fix many of the problems seen in Linux systems.

- Libraries for Linux rebuilt with libpcre statically (libpcre bundled for Linux builds).

- ``calltip()`` is now thread safe (which caused some strange behavior in Linux
  where Sublime Text 2 ended up being unresponsive).


v1.2 (18-12-2011):

+ Added palette commands to disable/enable the plugin in many ways.

+ Added ``codeintel_live_disabled_languages`` and fixed ``codeintel_live`` to disable SublimeCodeIntel live autocomplete mode.

+ Support for new completion settings in Sublime Text 2 Build 2148.

+ JavaScript support improved (it's now much nicer with the CPU).

+ CSS files support much improved (thanks to Jon's new features in autocomplete).

+ Smarter language detection and fallbacks.

+ Improved autocomplete triggering, should now respond better.


License
-------
The plugin is based in code from the Open Komodo Editor and has a MPL license.

Ported from Open Komodo by German M. Bravo (Kronuz).
