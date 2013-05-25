===========
Publish it!
===========

A tool to generate documents ready to be sent out of your workflow!

This tool specifically aims at extracting documents from your VCS for
them to be sent to people reluctant to use your tools (git, hg,
etc...). If an outdated version of one of your documents comes back on
your desk 6 months after you had sent it by email, with corrections,
modification requests, etc, you might like to know which commit was
the source of that document. An other advantage it that any document
has then a last modification date printed on it with that system.

git-sha
-------

`publish-it` uses the hash of the last commit of the file being
published to generate a string which will be the file release
identifier, refered as `git-sha-tag`.

* If the document has not been modified since its last commit,
  `git-sha-tag` will be the shortened commit hash, extended with the
  date of that commit. Example: `e4r6t20 | 2013-05-25 12:34`

* If the document has been modified since its last commit,
  `git-sha-tag` will be the shortened commit hash with `-dirty`
  appended at its end, extended with the current date and
  time. Example: `e4r6t20-dirty | 2013-05-25 18:34`

For now, this tool supports git only. The other main VCS will be added
on the way.

Behavior
--------

With a plain text file
^^^^^^^^^^^^^^^^^^^^^^

`publish-it` looks for the keyword `git-sha-tag` in the document and
replaces it with its current value (string substitution). The
shortened commit hash is appended to the filename, so the original
file is not replaced. Optionnally, the document is rendered as a PDF
file (available for SVG only for now, inkscape required).


With a binary file
^^^^^^^^^^^^^^^^^^

`publish-it` creates a folder containing the binary and a README file
which contains the `git-sha-tag` value. The name of the folder is the
binary filename appended with the shortened commit hash.

With a folder
^^^^^^^^^^^^^
Many options are possible. I see at least 3 cases. TODO.
