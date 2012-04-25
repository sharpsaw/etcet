etcet
=====

The last configuration system you'll ever have to learn. There are many
existing solutions, but I am fairly determined to glean the best of each (and,
where possible, allow interoperation with the others).

The key is overlays, called "cet"s. Each one can simply be a git repo, but
they will refine the configuration from:

The base system  
↓  
Your preferred tools (e.g.: Vim, Zsh, Ruby, Pentadactyl)  
↓  
Your advanced configs (such as some hot-rodded Vim keybindings)  
↓  
Your personal configs  
↓  
Your local, machine-specific configs

All cet's should mix and match cleanly - with the more specific stuff taking
precedence, but also being able to integrate with upward pieces. A simple
example of this is having more generic tools at the higher level that respect
lower level tools' `$ENV\_VARS` to fill in the blanks.

The Goals
-----------

To solve `~/.*` and `~/bin/` in a once-and-for all way.

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

This, ↑, will be all it takes to get a half-way decent config, starting with a
Unix-like system (to include Cygwin) equipped with little beyond `git` and
`perl`. 

The first step will be some installation work, grabbing packages that can be
depended on by later cets. I don't want to have to write shell scripts except
in the full-powered `zsh`, and I don't want to have to write general scripts
except in the full-elegance `ruby`. For a system that is more geared toward
generality, being based on `bash` and `perl`, look to [Ingy's ...
System](https://github.com/ingydotnet/....git).

The "base system" will mostly be a simple set of management tools to automate
config synchronization, package installation, and definitely: cet addition.

The "preferred tools" configs will be set up based on the idea that being
elite is worth the investment of learning. It's the Sharpsaw Philosophy
itself. So, though the base system will not force anything on you other than a
few commands in the $PATH, the tools config will do it somewhat. Here are some
examples of how that plays out:

- Automated is better than manual. Of course. -- but there are layers to this.
  We need better tools to make tools (look at
  [kiss](https://github.com/ryanjosephking/config/blob/master/bin/kiss) and
  [conceive](https://github.com/ryanjosephking/config/blob/master/bin/conceive)
  to see the direction I'm going with this).
- Upstream is better than fragmented. Part of this is the DRY principle. As
  the Etcet project develops good ideas, we'll try to push it higher up. For
  example, let's say you come up with a good Vim script. It should pretty
  quickly graduate from a user-specific config to a communtiy cet. From there,
  it could get generalized and promoted to the "preferred tools" config.
  Afterward, it might be worthwhile to release it to www.vim.org/scripts -- so
  that the non-Etcet Vim users can still benefit.
- Networked is better than offline.  This might
  not have played out like the "network is the computer" guys thought it
  would, but I think we're plodding our way in that direction. The goal is an
  uninterrupted workflow regardless of the terminal, to include mobile.
- Vi keys are better than Emacs keys (which are better than "Notepad keys" --
  simply hitting up/right/down/left to move). If you disagree, I can step off
  my bias-horse for long enough to have a conversation, but the general idea
  is that Etcet will put Vi keys everywhere in a hurry.
- Color is better than monochrome. Color is another "dimension", and it
  conveys extra information, quickly.
- UTF-8 is better than junk like ISO-8859-1, but also better than ASCII. It's
  time, folks. Any software that can't hang with it needs to be fixed or
  replaced.
- Default is the tiebreaker. If the differences between two configs are not
  very strong, the default way is a bit better. A great example is Qwerty vs.
  Dvorak. I have used both, but in the end I am happy to take the slight speed
  and comfort hit to be able to work with Qwerty people more seamlessly.
- Still, progress is better than habits. If the community will profit from
  some re-learning, we'll go for it.
- ...

But in all of this, remember that the system will allow you to maintain
control. Your config will still be your config, because you can pick and
choose cets, and because your user cets are always the top priority.

The Input
----------

Many people are working on this idea. I don't know if I'll simply
convert to one of their systems, or subsume it and take it further. The
"once-and-for all" part means that whatever solution I come up with, it
should be good enough that the next guy doesn't have to make this
decision - it will be modular enough that he can start from the solution
and easily overlay his personalizations.

- [vcsh](https://github.com/RichiH/vcsh) - From my brief scan, this looks like
  a good start.

- [movein](http://stew.vireo.org/movein/) - jamessan says this is like vcsh
  but nicer. Cool.

- [vcs-home](http://vcs-home.branchable.com/) - The inspiration for movein,
  and also has some good links/discussion on that page.

- [dewi](https://github.com/ft/dewi) - ft's cool system that is sort of like
  using ExtUtils::MakeMaker in a Makefile.PL
    - [ft's configs](https://dev.0x50.de/projects/ftdotfiles666) - based on dewi.

- [...](https://github.com/ingydotnet/....git) - ingy's implementation of this
  idea. The final solution will be able to use ... as a cet.

- [briefcase](htttp://jim.github.com/briefcase) - Another one I haven't really
  looked at.

- ["scp1"](https://github.com/trapd00r/configs) - More.

- [dotfiles.org](http://dotfiles.org/) - Sprawling collection of config files.

- [rking](https://github.com/ryanjosephking/config) - My old attempt. Is not
  much more than a git repo with symlinking.

The Next Level
--------------

A web-based system will be useful. For individual config files, this is along
the right lines: http://www.muttrcbuilder.org/page

I am also developing some skills in the area of mobile app dev, so if you have
an idea of how to streamline your computing that could involve some mobile
solution, let's talk about it.

...more to come.
