etcet
=====

The Solution
------------

The key is configuration overlays, called "Cet"s. Each one will simply be a
git repo, but they will refine the configuration from:

- The base system, to
  - Your preferred tools (e.g.: Vim, Zsh, Ruby, Pentadactyl) to
     - Your advanced configs (such as some hot-rodded Vim keybindings), to
        - Your personal configs, to
            - Your local, machine-specific configs.

All cet's should mix and match cleanly - with the more specific stuff taking
precedence, but also being able to integrate with upward pieces. A simple
example of this is having more generic tools at the higher level that respect
lower level tools' `$ENV\_VARS` to fill in the blanks.

The Goals
-----------

To solve `\~/.\*` and `\~/bin/` in a once-and-for all way.

That is, the system should be:

- Easily distributed. Logging into an account should tell you if it
  has items that should be push/pulled, and one command should do the
  sync.
- Easily altered. One short command to edit a file in a way that both
  $HOME and the working tree are aware of the changes.
- Easily combined. Some people want pieces that other people won't.
- Easily localized. Each machine will have system-specific tweaks,
  maybe because packages aren't available, for example.
- Easily socialized. Oh? You found some cool area of `vim +h` that I don't
  know about, yet? Awesome. Throw it in your config and I'll check it out.
  The configuration experience is a trail from unawareness → discovery →
  hackish solution → correct solution → clean solution. If we help each other
  out, this process is more fun than when we go alone.

And maybe:
- Extensible to work for system configs in `/etc`. I need to think about this
  one, though. For the most part, this stuff is handled by the distro plus
  your machine-specific config that is not going to lend itself greatly to the
  rest of the optimization of Etcet.

The Use
-------

    # XXX - only an idea. This won't do much, currently:
    git clone https://github.com/sharpsaw/etcet
    etcet/bootstrap

This ↗ will be all it takes to get a half-way decent config, starting with a
Unix-like system (to include Cygwin) that has little beyond `git` and `perl`. 

The first step will be some installation work, grabbing packages that can be
depended on by later Cets. I don't want to have to write shell scripts except
in the full-powered `zsh`, and I don't want to have to write the rest except
in the full-elegance `ruby`. For a system that is more geared toward
generality, being based on `bash` and `perl`, look to [Ingy's ... System](https://github.com/ingydotnet/....git).

The "base system" will mostly be a simple set of management tools to automate
config synchronization, package installation, and definitely: cet addition.

The "preferred tools" configs will maybe someday be very general, but for the
first version of this the goal will be to upgrade past all the defaults,
...TODO
- Color is better than monochrome 

The Input
----------

Many people are working on this idea. I don't know if I'll simply
convert to one of their systems, or subsume it and take it further. The
"once-and-for all" part means that whatever solution I come up with, it
should be good enough that the next guy doesn't have to make this
decision - it will be modular enough that he can start from the solution
and easily overlay his personalizations.

- vcsh - https://github.com/RichiH/vcsh - From my brief scan, this looks like
  a good start.

- dewi - https://github.com/ft/dewi - ft's cool system that is sort of like
  using ExtUtils::MakeMaker in a Makefile.PL
    - ft's configs - https://dev.0x50.de/projects/ftdotfiles666 - based on dewi.

- ... - https://github.com/ingydotnet/....git - ingy's implementation of this
  idea. The final solution will be able to use ... as a Cet.

- briefcase - http://jim.github.com/briefcase - Another one I haven't really
  looked at.

- "scp1" - https://github.com/trapd00r/configs - More.

- rking - https://github.com/ryanjosephking/config - My old attempt. Is not
  much more than a git repo with symlinking.

The Next Level
--------------

A web-based system will be useful. For individual config files, this is along
the right lines: http://www.muttrcbuilder.org/page

...more to come.
