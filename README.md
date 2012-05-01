ineach
======

bash script to perform a command over multiple directories


Examples
========

If you have several git repository clones containing components for your
software (and you're not using submodules), it can be useful to perform the
same git command over all repositories:

    $ ineach * -- git status
    $ ineach a* b* d* -- git fetch
    $ ineach * --p gitk --all

Specify multiple directory wildcards, then a '--' or '--p' then the command to
execute in each directory.

The last example above shows how you can execute multiple GUI apps without
blocking on each one.

Execute in parallel
===================

Normally, the command is executed in sequence for each directory. The
--p option execute the command as a background job for each directory. This
can be useful when executing GUI apps that you don't want to block on. For
example:

    $ ineach * -- 'gitk --all &'

This is a bit cumbersome and tedious to type because you have to remember the
quotes and ampersand - the quotes are important otherwise bash itself
interprets the ampersand. The can be made simpler using the --p option:

    $ ineach * --p gitk --all


Pipes
=====

If you want to execute several commands through pipes, these commands must
still be wrapped in quotes:

    $ ineach * -- 'ls -1 | wc -l'
