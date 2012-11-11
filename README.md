# DM Binder Manager

DM Binder Manager is a set of scripts I use to help me manage my DMing
binder for the RPG campaigns that I run.

My binder contains the resources I need for running encounters in the
current session, planning future sessions, and keeping track of all the
people, places, events, etc. in our campaign world. In general, I prefer
not to have a computer at the gaming table, because it ends up being to
"fiddly" (and I also like the low-tech nature of table-top RPGing).
Having a well-organized binder is, for me, the key to making this work
well.

But... I don't want to have all that data stored only in a bunch of
hadwritten pages in a binder. First, my handwriting is horrible, so
I won't be able to remember what I wrote down in a couple of months.
Second, I have kids, and I've long since learned not to count on
physical objects remaining undamaged. Finally, It's much easier to
organize and reorganize all of this information as needed when I can do
so in a text editor.

At first I started keeping everything on one big WYSIWYG editor
document. This certainly let me format things decently for my binder,
but it was harder to see specific changes in a git repo, and it was
a pain to then print out only the pages that were changed for insertion
into the binder.

After spending a few days poking at different solutions to my problem,
the set of scripts in this repo represents my current workflow.
Currently I am only addressing the "Encyclopedia" for my campaign world,
but I hope this same system will be adaptable for other parts of my
binder.

When I have updates I want to make to the encyclopedia, I simply create
or update the entries under the "Encyclopedia" directory; one entry per
file. The files are plain-text formatted using Markdown and named with
a ".md" extension. For instance, the content of "Encyclopedia/Grue.md"
might be:

    % Grue (monster)

    A **grue** is a fictional predator that dwells in the dark. The word
    was first used in modern times as a fictional predator in Jack
    Vance's *Dying Earth* universe (described as being part "ocular
    bat", part "unusual hoon" and part man).

    Dave Lebling introduced a similar monster, whose name was borrowed
    from Vance's grues, into the interactive fiction computer game Zork,
    published by Infocom. Zork's grues fear light and devour
    adventurers, making it impossible to explore the game's dark areas
    without a light source. The grue subsequently appeared in other
    Infocom games.

    Due to Zork's prominent position in hacker history and lore, its
    grues have served as models for monsters in many subsequent games,
    such as roguelike games and MUDs.

Once I have updated all the encyclopedia entries for that session, I can
simply run `rake print`. This creates (or updates) a PDF for each entry
that was changed, and only those PDFs that are new or updated are then
sent to my printer.

## Requirements ##

The conversion from Markdown to PDF is done by
[pandoc](http://johnmacfarlane.net/pandoc/).

In order for pandoc to create PDF files, you need a working LaTeX
installation (in particular, `pdflatex` must be on your PATH).

The updating and printing is managed by
[Rake](http://rake.rubyforge.org), so both it and
[Ruby](http://ruby-lang.org) are required.

## Installation ##

Assuming you have the above requirements taken care of, just clone this
repository, then start writing your entries.

## Usage ##

1. Create or edit Encyclopedia entries under the `Encyclopedia`
   directory.

2. Run `rake print`
