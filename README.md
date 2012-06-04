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

See:
http://github.com/ouicode/rkingy-dots-conf

It's far from perfect, but it's a concrete start to what is described here.

It turns out that we don't actually need a piece of software to do this, it's
merely a set of conventions. Basically,
[...](https://github.com/ingydotnet/....git) is a good installer (can do
hardlinks/symlinks, can overlay many different config dirs, and so forth).
Between upstreaming ideas into `...` or adding new repos, pretty much we have
a realization of the goals.


The Values
----------

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

Virtualization and Pair Programming
-----------------------------------

...is the future.  Let me back up a bit and I'll explain how so.

Ingy döt Net and I have pair programmed for years. Often remotely. We have
some things that work for us, but one thing that always _doesn't_ work is our
initial setup. I'm never happy until I have my full set of vim bindings, shell
aliases, helper tools, etc. Ingy always has 45 Perl modules he wants to get
his stuff going. So the first few sessions we have are sunk in the "yak
shaving" process.

So, Ingy works for ActiveState, which has this Stackato product. It's a cloudy
cloudish thing, but don't let that repulse you. The things you need to know
about it are:

- *It's very sandboxy.* Each "app" runs in an LXC container which is a fresh
  Ubuntu install. You'll get no unexpected behavior as long as you're on the
  same Stackato version as last time. Plus there are security benefits of
  this: ingy doesn't need to give rking access to any of his personal boxes,
  and vice-versa.
- *It's location-independent.* Most cloud things rob you of ownership of the
  processes, but with Stackato you can run on EC2 or your own laptop. In fact
  Ingus made the "on the laptop" a
  [one-liner](http://www.activestate.com/blog/2012/03/install-stackato-micro-cloud-one-command)
  (Note that as of Summer 2012 the script only works on Ubuntu and OSX - but
  it's pretty easy to twack to
  work on other system that support either VirtualBox or vmplayer. I got it
  going on Gentoo in under an hour, and it was my first time to run any of
  that VBoxy type stuff).
- *It's just Linux.* After you log in, you can largely forget that you're on
  some weird system and use it however you'd use any box.

I have to go do other stuff, but here's the punchline:

Using the "Etcet" concept on the Stackato platform VMs allows us to spin up
pair programming environments from zero to done in about 7 minutes.

...more later.

The Next Level
--------------

A web-based system will be useful. For individual config files, this is along
the right lines: http://www.muttrcbuilder.org/page

I am also developing some skills in the area of mobile app dev, so if you have
an idea of how to streamline your computing that could involve some mobile
solution, let's talk about it.

... Alternatives
----------------

You could do the same thing but with a different installer. Here are some other projects:

- [vcsh](https://github.com/RichiH/vcsh) - From my brief scan, this looks like
  a good start.

- [movein](http://stew.vireo.org/movein/) - jamessan says this is like vcsh
  but nicer. Cool.

- [vcs-home](http://vcs-home.branchable.com/) - The inspiration for movein,
  and also has some good links/discussion on that page.

- [dewi](https://github.com/ft/dewi) - ft's cool system that is sort of like
  using ExtUtils::MakeMaker in a Makefile.PL

- [ft's configs](https://dev.0x50.de/projects/ftdotfiles666) - based on dewi.

- [briefcase](htttp://jim.github.com/briefcase) - Another one I haven't really
  looked at.

- [mpapis's smf](https://github.com/sm/sm) - An excitingly abstract system.
