Usage:

    $ ff-hist term

This will search for the term in the URL and title as 'like %..%'.

To limit to just the URL or title, prefix with url: or title:

    $ ff-hist title:term

You can add multiple, which are AND'd together:

    $ ff-hist term title:other

To OR together, add "or:"

      $ ff-hist title:term url:or:reddit.com or:asd

The output is aligned in columns to fit the window; add -full to always
dispaly everything.

Use -show to echo the SQL query before running, or -showonly to just show the
URL and exit.

You can get the full URL by giving the ID (first column in output):

      $ ff-hist 42
      $ ff-hist 42,666
      $ ff-hist 42 666   # Identical

All the parameter can also be passed from stdin if the first argument is `-`;
parameters are separated by newlines.

You can pipe this to `fzf` or `dmenu` or whatever if you wish:

    $ ff-hist hello | dmenu | cut -d' ' -f1 | ff-hist - | xclip -rmlastnl -selection clipboard
