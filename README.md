[![logo](https://i.imgur.com/QAAheRP.png)](https://rubygems.org/gems/rbt)
[![logo](https://i.imgur.com/LiwQlUB.png)](https://rubygems.org/gems/rbt)

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://www.gobolinux.org/)
[![forthebadge](https://forthebadge.com/images/badges/made-with-ruby.svg)](https://www.ruby-lang.org/en/)
[![Gem Version](https://badge.fury.io/rb/rbt.svg)](https://badge.fury.io/rb/rbt)

This gem was <b>last updated</b> on the <span style="color: darkblue; font-weight: bold">19.04.2024</span> (dd.mm.yyyy notation), at <span style="color: steelblue; font-weight: bold">18:03:29</span> o'clock.

## Introduction to the "Ruby Build Tools" Project (RBT)

<img src="https://i.imgur.com/PN2lOHj.png"> Welcome to the 
<span style="color: darkgreen; font-weight: bold">Ruby Build Tools</span>,
also called the <b>RBT suite</b> - <b>getting work done</b>! <b>Making
compiling great again</b>. \o/

This <b>documentation</b> attempts to detail the various objectives for
the RBT project, including its history, as well as how people may benefit
from the project.

## What is the RBT project about?

The <span style="color: darkblue; font-weight:bold ">primary goal</span> for
the <b>RBT project</b> is <b>to support a user whenever the need arises
to install software, on a given computer system</b>.

The primary operating system in this regard is, first and foremost, 
<b>Linux operating systems</b> (henceforthwith simply called <b>linux</b>
in this document.

Additionally, when we refer to allowing a user to install software, 
this typically refers to taking the <b>source code</b> and compiling
this source code - in other words: <b>to simply compile the program</b>
at hand, from a <b>remote URL</b>.

While the <b>primary platform</b> for the <b>RBT project</b> is predominantly
the <b>Linux</b> platform, whenever possible support for <b>other platforms</b>
will be added as well. In fact, it is a secondary goal for the RBT project
to support <b>all</b> platforms ruby is able to run on in the long term. How
realistic it is to reach that goal is another matter, but as a goal RBT
will eventually try to support as many different operating systems as
possible, provided that ruby can run on such a system.

<b>Linux</b> is the <b>main target OS</b> for the rbt project, though,
so things will be tested on <b>Linux</b> first. Most development for
RBT does indeed take place on a Linux system currently.

Ideally, in the future, we could reach a state where we can test the
RBT suite on less commonly used systems as well, such as <b>HaikuOS</b>
or <b>ReactOS</b> to name only a few here. And, of course, the more
popular ones such as OSX or Microsoft's Windows suite as well, naturally.
Windows is the second operating system that RBT will support, by the
way; it is less well-tested than the Linux-specific code of the
RBT project.

## Installing the rbt gem itself

This subsection addresses the possible user question <b>How to install
the rbt gem?</b>.

The <b>canonical</b> way to install the <b>rbt</b> gem, via the
commandline, goes via:

    gem install rbt

However had, I recommend to make use of the <b>--user-install</b> option;
this makes it easier to use the <b>bin/</b> scripts that are part of this
gem, as they will reside in your home directory, at <b>bin/</b> there:

    gem install rbt --user-install

Then you can use them easily if you have the bin/ to your home directory
in your $PATH. (The path may be a bit awkward these days, though,
such as **$HOME_DIR/.gem/ruby/2.7.0/gems/rbt-0.8.11/bin/run_make_then_make_install**.
In older ruby versions the path was simpler; no idea why that changed,
please ask the rubygems maintainers if you are interested in the
why.)

While the <b>/usr/</b> hierarchy as prefix is fine, in principle, some
distributions, in particular debian, have a habit of splitting up
gems <b>a lot</b> (or did so in the past). This makes it harder for users
to know where files reside - see typical questions asked by users on
<b>IRC</b>.

This is also another reason why the <b>--user-install option</b> is better,
in my opinion - you don't have to guess where the executables
will reside; they are just in the home directory, somewhere there.
And you can move them from there to any other location anyway,
or use <b>symlinks</b> and/or **aliases** via your shell to setup
the system how <b>you</b> want it to be. Or, use the ruby code
directly - after all you can create your own executables, since
that is precisely what all gems do anyway in their corresponding
**bin/** subdirectory.

Since gems are also <b>downloaded locally</b>, and then available as
a .gem file, other users can easily install these gems into their
home directory as well, without depending on a global installation.
This may be especially useful in environments where you are
restricted, such as at a **campus/university environment**.

On windows, if you plan to upgrade the rbt gem, I recommend to first
<b>uninstall</b> all old rbt gems. While this is, strictly speaking,
not really necessary, I found that it may work better if old gems
are removed - at the least on windows. There I manually remove the
directory where the old ruby stores gems. Again, this is probably
not strictly necessary, but I found that this works better in the
long run.

## How does RBT handle compiling from source, explained in a simple manner?

Let us now briefly explain how RBT approaches compiling from a source
archive: after all that is <b>the main goal for the</b> 
<span style="color: darkgreen; font-weight: bold">RBT project</span></b>.

Let's take any random remote URL to some tarball archive, 
such as the <b>.tar.xz file</b> for <b>evince</b> that may
be found here →
https://download.gnome.org/sources/evince/42/evince-42.3.tar.xz.

So, to then compile this via the RBT suite, we should be able to
do something as simple as the following, via the commandline:

    rbt evince

That's it! In the above example, <b>rbt</b> refers to the
executable <b>bin/rbt</b>, which is part of the rbt gem itself.

If all goes well then the above tarball, the file name
<b>evince-42.3.tar.xz</b>, will be downloaded (unless it
already exists locally), extracted, and then compiled.
It all goes well the user will then have the specified
version of evince installed, compiled from source.

It should never be more complicated than that, for
<b>well-behaving programs</b>. At the least in theory;
in practice you can imagine that some things may go
awry or not work, but this is where <b>rbt</b> will 
also try to be of help, in order to resolve such
problems.

Note that while the primary focus is on compiling
source code as-is, a secondary focus is to allow 
installation from a binary source, as well as to
support different package managers, similar to the
<b>fpm gem</b> (https://github.com/jordansissel/fpm).

This was the brief introduction to how rbt should work
in theory. Of course there are more details to be
had, which will be mentioned in other subsections of
this document.

## The full scope of the RBT project: extended objectives

The content in this document above delineated the primary
objective for the RBT project.

Of course the <b>full scope</b> of the <b>RBT project</b>
is a significantly wider one:

The <b>RBT project</b> will attempt to be of help to
the user as a <b>general-purpose build toolset</b>.

What does this mean? This means that the RBT project
will try to be of <b>help to people who wish to
manage the software</b> on their respective computer
systems in general. This may even extend towards other
programming languages, be it python, java, C/C++,
shell scripts - you name it.

Although RBT has started via ruby, other programming languages
are permissive as well.

Another "<i>higher</i>" meta-goal that follows this vision is
to integrate tasks that are typicall done via a
<b>package manager</b>. Support for this within RBT itself
is presently (2024) still fairly minimal. Do not expect RBT
to become a fully fledged package manager right now; but,
perhaps this use case may be covered one day in the future.
Until then singular aspects found in different package
managers may be included into the RBT suite as well.

Yet another goal for the <b>RBT project</b> is to provide
all the raw data used for managing <b>all</b> programs
on a <b>Linux Distribution</b> or another Operating
system. As one example: (almost) all programs that are
registered in the RBT suite have a remote URL registered -
see the evince example above.

What the user then does with this data is up to them; I
simply wanted to have this all available within a
<b>single</b> project as-is; and to be able to query
this via the commandline, too.

The data is primarily stored in various individual cookbook
.yml files. These .yml files can be turned into a SQL
dataset. This will at one point in time probably become
the default way for users to interact with the dataset
made available by the RBT project. In the past, since
as of <b>August 2022</b>, it even was recommended to make
use of a SQL database, but I no longer recommend this
for now; many things have to be polished in the RBT
project before we can fully transition into a SQL
database. For now, prefer to make use of the various
.yml files that are distributed. See elsewhere
in this document more information pertaining to this.

This <b>SQL-based approach</b> will eventually be more useful,
as it should be faster to query its content - in
particular on <b>Windows</b>.

For more objectives of the RBT suite, consider reading
the subsection called <b>Is the RBT suite actually useful?</b>.

## What is the policy for program-names stored in .yml files?

Let's consider the program called <b>htop</b>.

This program will be stored in the file called
<b>htop.yml</b>, as far as the RBT project is concerned.

The program called <b>anjuta</b> would be stored
in the file <b>anjuta.yml</b> and so on and so forth.

If the program name contains any '-' character, as part
of their name, then these '-' characters (the hyphen)
are ignored. So, for instance, if the remote URL
to a program is like this:

https://download.gnome.org/sources/gnome-commander/1.14/gnome-commander-1.14.3.tar.xz

then the corresponding .yml file would simply be called
<b>gnomecommander.yml</b>. In other words: the 
'-' character is completely ignored, as far as the name
for the .yml file is concerned.

This is a rather simple convention - the name of the program will become
the name of the yaml file in question.

These .yml files are so-called individual "cookbooks". This name derives
from "<b>to cook/compile a program from source</b>".

Take note that this term is a bit similar to the old linux
distribution called sorcery (see https://sourcemage.org/Sorcery).

Although this approach is very easy to remember and apply, it does
lead to a few issues sometimes. For instance, if two remote
projects have the same name, then only one can be registered in
the RBT project, using that simple naming scheme. The workaround
I use in this case - and let me assure you it happens very,
very rarely only - is to change the name of the .yml file a bit,
such as perlsdl.yml for the perl wrapper over sdl.

## Is the RBT suite actually useful?

This is an interesting question.

I have used RBT specifically to help me in my attempts to
<b>boostrap</b> a LFS/BLFS (Linux from Scratch / Beyond Linux from
Scratch) system, so this is an additional use case (and goal) for
the RBT suite as well.

I think that the RBT suite does have some real value here - or
there. For this I would like to coin the phrase <b>"from zero
to hero"</b> - which means to <b>bootstrap and create a Linux
system</b> that can be burned on a DVD or simply put on
a USB device. This is not yet working flawlessly, but it is
on the TODO list as well: to support LFS/BLFS builds from
scratch (aka <b>from zero</b>). 

Additionally, as yet-another-objective, the <b>RBT</b> project may
aid in the process of <b>autogenerating files and code</b> related
to installing and compiling in general, such as
<b>generating standalone shell scripts</b> or **valid archive formats**:
archive formats such as <b>.rpm</b> or <b>.deb</b>.

For example, one part of <b>RBT</b> can be used to <b>autogenerate completion files
for bash and zsh</b>; I use this to more easily compile programs, such as
by typing "ry autom<TAB>", to become the very same as "ry automake". This
thus saves me a few keystrokes on the keyboard.

Another script, also part of the RBT suite, can modify <b>Makefiles</b> and
change the prefix in that file, without me having to remember the awkward
syntax <b>make</b> uses when trying to override the default prefix in
use. These are examples for such "toolkit" scripts in RBT, so the overall
goal for the RBT suite is to help in regards to such <b>use cases</b>. The
primary use case remains on <b>compiling source code</b> as-is, though.

We could continue this listing here, but I think the basic point was
already pointed out now. If you look at the <b>RBT suite</b> from a wider
perspective, <b>RBT</b> attempts to be a <b>swiss army knife for
compilation/installation</b> of software projects. The focus here
lies on <b>hands-on use</b> - it is a toolset project and has to
offer code/functionality that helps solve certain computer-related
tasks.

## The rewrite of the RBT project in February 2024

In <b>February 2024</b> it was decided to rewrite the RBT project, yet again.

This subsection will briefly explain why.

There were various smaller reasons - a few bugs, a few things that
have to be improved, and so forth. Some of these bugs were very
old, and I haven't gotten around to fixing them, so this provided
an opportunity here.

But, the biggest reason for the rewrite was something else: I wanted
to transition into <b>well-defined actions</b> for the RBT project.
Other subsections of this document will explain the rationale
behind <b>well-defined actions</b> more; suffice to say that I
wanted to have all important, actionable activities tied together
and have them be usable via the commandline as well. This would
allow me to tap into the RBT project without having to rely solely on
classes and methods - instead I can use actions to do individual steps,
such as symlinking files, copying files, performing post-installation
steps and so forth. If I want to apply some patches automatically then
I could do so too, such as:

    rbt sed --apply-the-patch

Or, via actions, from the commandline:

    rbt_action apply_the_patch sed

Yes, there is not much difference between these two variants, but the above
entry-point, via rbt_action, allows us to think in terms of actions first,
<b>rather</b> than the program name first. Plus, I could provide specific
individual actions in a specific order, which I can not easily do via
commandline --flags.

## A theoretical remark from potential users of the RBT suite: „But the RBT suite is so gigantic! I will never need all of it.“

That's right - you may only need a small subset of the RBT suite, and
that's ok. The RBT suite attempts to cover different use cases and
needs, so it is highly likely that not every user needs to use <b>all</b>
of the RBT suite.

However had, even if a user does not intend to install or compile anything
through RBT, many different programs are registered in this project,
which may be of (indirect) help in some other ways. For instance, if a
user desires to <b>determine which particular binary on a given Linux system
belongs to which particular application</b>, or if the user intends to
implement a package manager on his or her own, then the RBT suite may
be useful, as it allows such potential users to query this through the
RBT suite.

The dataset for the standalone programs is available under the namespace
<b>RBT::Cookbooks</b>. For a list of all registered programs, you can
simply query the toplevel-method called <b>RBT.available_programs?</b>.

Related to this question of "<i>How do users benefit from the RBT suite?</i>",
one part of the RBT suite deals with <b>statistics</b>. Support for this is
somewhat minimalistic right now, but will be extended in the future. One script
reports some statistics, such as <b>how many of the registered projects depend
on cmake, or meson, or GNU configure, or a Makefile and so forth</b>. You can
query their percentage value, and thus gain a little insight into how
different projects make use of which particular build tool. That is an example
for statistical information. 

This part about statistics will be slowly extended over the coming years, but
it is not the primary use case for the RBT suite - just something that I found
to be interesting to know, how many different projects out there depend on
which compilation strategy, and how this may change over the years. Presently,
in the year 2024, many projects still depend on GNU autoconfigure/configure.
cmake comes second, meson/ninja comes third. I found that monitoring the rise
of meson/ninja to be quite interesting, and I expect that this trend will
continue. Of course the subset that is registered in RBT is not the 
<b>full</b> picture, so the statistics are only valid <b>in regards to
the RBT suite itself</b>. Globally we may see a completely different picture,
but the statistics shown by RBT are correct when it comes to the programs
registered in the RBT suite.

The <b>primary core functionality</b> of the RBT project, however
had, will remain on <b>compiling programs from source</b>, as this is
what I use RBT for on an almost daily basis. It also was the original
reason why the RBT project was started many years ago.

## How do I use the RBT project personally?

How do I use the <b>rbt project</b> primarily, on my <b>Linux</b> systems,
but also on windows?

This paragraph, added in <b>January of 2023</b> and extended in
<b>February of 2024</b>, will try to give a useful answer to this
question in a unified manner - hence its own subsection here.

Other users of the RBT suite may understand the goals of the RBT
suite better after such an explanation was given to them - a
more thorough overview of the RBT project, from a "<b>my point
of view</b>". That way, hopefully, other users can learn from
how I approach problems that the RBT project tries to solve for
you.

This subsection attempts to helpfully explain <b>how I use the RBT
project most of the time</b>, as that may give some indication how
the RBT project could be used by other people as well. We must
define and declare a few things next.

I use <b>linux</b> as my main operating system, so Linux is the
primary operating system for the code offered by the rbt gem, as
was already pointed out elsewhere in this document. While I try
to support windows as well, windows at this point in time is a
second-class citizen. At a later moment in time this may change,
but as of 2023 and 2024, this is still the case so. Some things
may not work well on windows, whereas they may work well on
Linux.

On Linux, I often found to have a need to quickly compile some software,
such as when a new release of a given project occurs. For example, say
that there is a new <b>php</b> source archive released.

So, what do I do in this case when I want to compile php from
source?

Well, first, I have to update the local version of <b>php.yml</b>,
with the new URL to the latest tarball of PHP. This is also
stored in that <b>.yml</b> file (aka <b>php.yml</b>, under the
<b>url1</b> entry there.

How is the content of said .yml file then updated?

I usually start by navigating to the <b>php/</b> subdirectory first, of
the directory where I keep all source directories, which is <b>/home/x/src/</b>
on my home setup.

Strictly speaking this cd-operation (<b>change directory</b>) is not necessary;
the RBT scripts will work fine from other directories too. But I found it is
easier if I first go to the directory where I keep the corresponding source
archive. In the context of this paragraph, php could then be found in the
subdirectory at <b>/home/x/src/php/</b>. I follow the "one directory
per program" rule - it is a very simple approach.

Now that I have (hopefully) managed to navigate to the source directory at hand
(<b>/home/x/src/php/</b>), I can then run the following command on the commandline:

    incrementversion
    incr # ← or just this alias to the above ^^^ instead

This command will actually invoke class
<b>RBT::Cookbooks::IncrementProgramVersion</b> which will
try to find a new upstream release tarball, using <b>curl</b>
or <b>wget</b> to check if such a remote tarball exists.
 
Note that I use many aliases on my home system; all aliases are kept in
another gem, called <b>rcfiles</b>.

Now, if the remote file specified at <b>url1</b> in the file called
<b>php.yml</b> exists then it will be <b>downloaded</b> the moment I
try to compile the program at hand (in this case php).

So, via the commandline, I can simply type this:

    rbt php

<b>If</b> things go alright from that point forward - which they tend to
do, at the least for php and many other programs that can be compiled - 
then php will have been compiled and installed afterwards into the
<b>/usr/</b> prefix, or the <b>AppDir prefix</b> on my home system,
which would be <b>/home/Programs/Php/8.3.3/</b> in this case,
for instance. That's it for the most part: <b>I just compiled a
program from source</b>, and all I had to do was to type
<b>rbt php</b>. \o/

(Actually, for historic reasons, I use "ry" rather than "rbt", so
the real command is even shorter.)

At any rate, as can be seen, using <b>rbt php</b> is quite simple.
I purposely did not want to make this more complicated than that.

In fact: on my home system I further simplify the above, by using
the alias "<b>trad</b>", which will first update the program
at hand (in this case php), by incrementing the version number
(of php), then try to download the actual source archive, extract
the source archive and then compile php into the <b>/usr/</b>
prefix, which is the "traditional" prefix (hence the abbrevation
"trad" I am using here). Of course you can do something different,
such as using <b>usr</b> as an alias rather than <b>trad</b>;
my brain is just so used to <b>trad</b> as invocation example
that I keep on using that.

A little historic detour comes next ...

From a historic point of view, it was somewhat too tedious for me
to keep on compiling things manually, via the old <b>"./configure; make;
make install"</b> route, so it made sense to me to create some scripts
in ruby that could simplify this for me. Back in 2004 when I was
using Linux, I discovered <b>GoboLinux</b>, which was a great
distribution, with an excellent philosophy. I did not understand the
shell scripts they used, though, so I tried to write (and re-create)
the logic behind it in <b>ruby</b>.

This goal of making RBT compatible with GoboLinux still exists as of
today: the RBT project must work on GoboLinux, out of the box. I have
not tested this in quite some time, though ... need to do so
eventually. Unfortunately GoboLinux is also no longer really developed
actively anymore, so this goal is no longer as important. Nonetheless,
should GoboLinux ever make a comeback, I'll retain this objective,
and try to write code in a flexible manner to help support this
goal.

Having different goals, as part of the RBT suite, reinforces the
statement that RBT tries to <b>remain flexible</b>. This flexibility
should then allow different use cases, subsequently allowing 
users of the RBT suite to repurpose this project to their own
needs.

As already stated elsewhere in this project, I really want to be
able to use the project on linux, on <b>windows</b>, on
<b>mac OS X</b>, on the various BSDs, ideally also on HaikuOS
and so forth one day. <b>One project to rule them all!</b> \o/

This means that <b>RBT</b> has to remain sufficiently flexible, as
much as that is possible. It has to be adaptable to different
operating systems on the fly; or at the least easily.

Additionally, <b>I want to be able to use different prefixes</b>.
Most existing package managers make it hard to install applications
into a particular prefix, and have things work from there. They
tend to assume that the only prefix that is valid is the
<b>/usr/</b> directory.

For instance: <b>debian</b> does not allow you to use a layout similar
to how GoboLinux works, by default. I don't know why they do not allow
for it - probably because nobody wrote the code in dpkg/apt to handle
different prefixes. I dislike that we do not enjoy this flexibility
here.

From that original goal that was historically the <b>bootstrap phase</b>
of the RBT project, I added more and more code over time. I did want
to provide better error messages as well, and hints how to resolve
something whenever a problem happens - way before <b>StackOverflow</b>
existed. The goal here was to try to automatically solve problems,
if the RBT suite has enough information available to do so.

Most <b>compile-related errors</b> are actually quite useless and cryptic
to newcomers, but also to more experienced users; sometimes they are
even bogus and misleading and flat out incorrect. Newcomers often do not
understand the problem domain, so RBT also tries to help users in that
regard. Errors may be collected, and then something useful is displayed
on the commandline - at the least that is one goal for the RBT project.
This may not always be very useful or work in a reliable manner, but at
the least that is one goal for the RBT suite. The code for this is not
ideal; I am slowly rewriting it since as of <b>March 2020</b>. (Actually,
I think I may have to rewrite the whole project past 2021 one day; but
I delay this for now. I want to be better prepared before I rewrite
it. In <b>February 2024</b> I finally hit the bullet and started the rewrite.)

The programs that are part of the RBT project I can usually compile by
just issuing any of the following commands:

    rbt NAME
    rbt php
    rbt python

and so forth, so this is really convenient for me. I don't depend on
another package manager that upstream developers control.

What follows next is, more or less, a description of generic use
cases that I may face on a daily basis.

When I compile a (new) program via <b>RBT</b>, such as by issuing "<b>compile
htop</b>" or "<b>rbt htop</b>" or "<b>ry htop</b>" (I make use of aliases a lot),
then the <b>RBT-scripts</b> will (try to) compile the program **htop** for
me, as specified by the corresponding "htop.yml" file, which is part of
the RBT project - within the **Cookbooks** namespace. Hence, within
<b>RBT::Cookbooks</b>.

If I need to make a change to the compilation process, such as by
using a different default <b>prefix</b>, then I simply edit the
<b>htop.yml</b> file, change, add or remove the corresponding entry,
and things will (should) work past this point - but I can also
override the settings from the commandline, so I have all the
flexibility required available.

## Defined actions in the RBT suite - well-defined, actionable components

A <b>defined action</b>, in regards to the RBT project, refers to an
action that will <b>always</b> "<i>stay the same</i>". Such actions
yield <b>reproducible results</b>. They also should not require of the
user of the RBT project to know the class-name or the file-name (of
the .rb file that handles this task) as such whatsoever - this is a
detail that is not necessary to know. It is thus some kind of 
abstraction.

Some of these action allow for some flexibility.

For instance, the <b>extract-action</b> handles input with a leading
<b>:</b> character as if a full path was desired by the user.

So, take this commandline invocation:

    action_extract :htop
    actionextract :htop

This will be just about identical to, for instance, the following
variant:

    actionextract /home/x/src/htop/htop-3.2.3.tar.xz

If you compare these two invocation examples of the <b>extract-action</b>
then you can see that in the first variant you can omit many characters,
as it is much shorter - and thus more convenient on the commandline.

Of course certain classes, such as class <b>RBT::Action::SoftwareManager</b>,
will extract the source archive for you anyway, but I wanted to have
individual actions, such as the extract-action, also available as a
singular, actionable entry point from the commandline.

Note that this only works if you have already downloaded the source
archive, and moved it to its corresponding location (which class
RBT::Action::SoftwareManager) will also do, by default.

This can be done manually, for instance, via:

    rbt --download=htop

I control most of what I compile via .yml files, first and foremost - a
simple text file. Other package managers do something similar if you look
at them. Arch, for instance, makes use of <b>PKG_BUILD</b> or some file
like that; gentoo uses <b>ebuilds</b>, debian also uses some designated
files, slackware uses its own minimalistic package manager, and so forth.

The "default settings" that I may use for these programs go into 
a specific .yml file, whereas the **commandline switches** allow
me to specifically override or cherry-pick other settings, based
on the machine that I am working with. For example, on **GoboLinux**
the AppDir prefix makes a lot of sense. On **slackware** on the
other hand I may decide to just use **/usr** as option given
to **--prefix=**.

On <b>traditional</b> linux distributions, **/usr** as prefix is
not the only possibility of course. Another popular way is to
compile into the <b>user's home directory</b>. A commandline switch
exists for the latter, for the RBT project, called **--home-directory**.
This is equivalent to whatever the user's home directory ought to
be, such as **/home/debug/** or **/home/joe/**. (I typically have
a user account called **debug** on my systems, which is mostly
concerned with debugging something on the target computer.)

So, --home-directory for the user joe would be equivalent to
<b>--prefix=/home/joe/</b>.

This is useful in the sense that, ideally, I can get away with only
passing the name of the program that is to be compiled, without
needing to change anything. It allows me to be lazy - and
just get things to "work", when they are compiled (if the compilation
process itself will work).

## Code conventions for the RBT suite

The RBT suite contains quite a lot of ruby code. Over time, in particular
when I have not worked on rbt for weeks or even months, I tend to forget
some of the simpler conventions. Thus, this subsection helps me remember
some of these conventions. It may also serve as an additional
documentation for the project.

Without further ado:

    absolute_path: This can be used as a replacement for File.absolute_path().
                   Not only is it a bit shorter, but it will also ensure
                   that there is a trailing '/' character. 

## Time investment into the RBT suite

Time is a finite resource of us humans. Naturally there is a limit
how much code we can maintain - and how much time we can invest
into a given project.

In <b>September 2021</b> I decided to cut back on time investment
for the RBT project. This is mostly because other projects
take away more of my time, including non-computer centric activites.
I won't abandon rbt, but it should be pointed out that most of the
time I am now doing maintenance work, fixing some problems here and
there, polishing this or that - but the RBT suite is still rather
of beta-ish quality, and I can not make any guarantee that the
project will ever leave its beta-ish roots.

In <b>February 2024</b> I invested more time into the project by
rewriting it again - and polishing it while doing so. While I can
not guarantee to invest as much time into the project, every
once in a while I will probably fix lots of small and also
larger things in the project.

## Most recent release series (some kind of "changelog" entry)

I no longer keep detailed changelog entries, as they are too much
effort to maintain. Instead I will use the time to improve the
documentation of existing code.

## The future outlook for the RBT project past June 2023

Some time ago I realised that the RBT project is not "ideally setup".
What does this mean?

Well - there are various big classes, such as class <b>RBT::Action::SoftwareManager</b>.
It works fairly ok-ish, but in May 2023 I noticed that it suddenly
reported errors when there were only warnings shown before. This then
led to failure of installation.

I know how to fix that bug (may take me two hours or so, which I simply
don't always have), but ... that's just one bug. There are several
additional bugs like that, and I often seem to invest time merely to
deal with architectural deficits. Time is a finite resource, so I can
not always invest the time to fix messy code.

Meanwhile I started to use <b>actions</b> - such as stored in RBT.action() -
and I believe this to be the future of the RBT project. I simply want
to capture ALL actionable events through a unified handler - in
this case, as mentioned, via RBT.action().

For instance, sometimes on a new computer system, I want to 
compile sed statically into an appdir prefix such as 
/home/Programs/Sed/4.11. But it may fail and then give a bogus
error. I want to be able to do step-wise actions here, and check
each one in its own right - a bit like the GNU gdb debugger,
so that I can see where the problem is, and work around it.
In classical GNU configure-based projects I may have to sift
through a file called config.log. I don't like that. I want
error messages to be instantly useful, or even be resolved
automatically.

So I decided that I will eventually transition into a fully
actionable-setup of the rbt gem. I will still maintain 
RBT::Action::SoftwareManager and improve it, but at the same time I will
transition towards actionable snippets. I will use them
kind of like individual components/objects, until the
whole rbt suite becomes more reliable. I want it to 
automatically update a computer from zero-to-hero, without
having to care much about the oddities of each individual
component.

In the long run we will move some of the functionality
found within <b>RBT::Action::SoftwareManager</b> into actions, and subsequently
replace the logic stored in class RBT::Action::SoftwareManager with
those actionable callbacks. So, one distant future, 
class RBT::Action::SoftwareManager may just be the general wrapper over
all actions. This will take quite some time, a few years
perhaps, so do not expect anything to work in the nearby
future, for now.

## Conventions and Aliases used for the purpose of this document as well as the RBT project in general

Commands that you can typically use on the commandline, such as
via the <b>bash</b> shell on Linux, are shown with an indent
of four ' ' space character on the left hand side.

Example:

    rbt htop # ← This would try to compile the program called htop.

Here, <b>rbt</b> refers to bin/rbt, as part of the RBT project.

Note that on my home system I have aliased **ry** to **rbt**,
so that is why all the examples below this paragraph will actually
use **ry**; mostly because it is more convenient for me to use 
**ry** rather than **rbt**. Either way, some of the old
documentation may use either <b>ry</b> or <b>rbt</b>, both
of which is equivalent.

By default the programs that are part of RBT will make use of
colours. You can disable this in general via the commandline
flag <b>--disable-colours</b>.

The class name will typically be shown on the commandline;
primarily to let the user know which class is handling a
specific step of the installation/compiling process.

The class name will typically be shown via :: such as
<b>RBT::Action::SoftwareManager</b>.

If an external class is called then the arrow symbol
→ will be used.

The following picture shows this:

<img src="https://i.imgur.com/j54KXl1.png" style="margin:1em">

## Copying the expanded directory

It may be helpful if you simply copy the expanded cookbooks
directory after you installed the gem.

This can be done via:

    rbt --copy-expanded-directory
    # or
    # installer --copy-expanded-directory

You can also generate the expanded dataset anew, or use
the SQLite wrapper, but in general using the above 
option is faster and easier for most (new) users.

Once that has been done you should be able to compile
programs from source.

Keep in mind that currently you have to maintain the
dataset by yourself, or default to the changed dataset
every now and then. The good news is that the .yml
files are rarely changing in format, so you can
easily "plug in" or remove new/old .yml files here.

## Background explanation: FAQ entry "Why a new project rather than extending existing code?"

This is a valid question - why not <b>contribute to an existing project</b>
rather than create a new project from scratch? There are a few
problems with the existing projects out there, though.

The scope of these projects is fairly often limited. For example:
mac **homebrew** is a package manager, but other than that it isn't
doing that much; and it does not work that well on linux or windows -
I tried it in <b>2019</b> on linux and it did not work for me. Perhaps
things improved since then, but since I felt that linux is a
second-class citizen in homebrew, I did not invest more time
into the issues I had faced with homebrew back then.

Another reason is that I do want to have a project that works as
well as ruby does on any given operating system, as long as ruby
is supported. I want to use it on windows, on haiku, on the BSDs,
solaris, for cross-compilation targets and so forth.

But there are **API-differences** as well and the way how these systems
are used. For example, the classical **package managers** on linux <b>do
not allow you to easily use another prefix</b>.

Most of them, at the least on linux, assume that **/usr/** is the
only prefix that is to be used (or /usr/cellar or something like
this). I do not like this restriction - I want more flexibility,
and complete control over the prefix in use <b>at all times</b>. I
want to be able to use a hybrid system too - partially using
/usr/ as prefix, and partially using **versioned AppDirs**
such as into my home directory.

With most package managers I would be forced into using just
/usr/ as the global prefix - no alternatives to this approach.

I absolutely dislike this restriction. Some of them even split
it into /usr/ and /usr/local - for example, debian has python,
perl and ruby packages under <b>/usr/local/</b>. What is this
madness? Why do I need to bother with it? How can I easily
change it? Why is there no consistency in this? The "explanation"
they try to give is a joke. In general the whole FHS is a mess -
and a joke. It makes no sense.

Debian in general is a total mess. Let me show you a single
entry as example demonstrating why, as taken from the
following webpage:

https://wiki.debian.org/PerlFAQ

So they ask the question:

<b>What if you want to install an updated version of perl
in /usr/local for experimental work but keep the
Debian/Release version in usr?</b>

And they answer it via:

"This setup may not work out well with the Debian Perl
package for Sarge since it has its own ideas about
Perl stuff in <b>/usr/local/</b>."

I mean, seriously? Perl is so outdated that they don't
even know how to install packages? So /usr/lib/
becomes an eternal struggle with /usr/local/lib/?
What the actual ... 

As far as I am aware, there is no trivial way to change 
any of that once you are using a distribution. They
expect things to be a certain way.

This above listing of reasons can be extended really, and
you can find numerous more issues - but ultimately it was
less of an issue here to create a new project that has these 
different goals in mind, rather than try to retrofit
existing code bases out there towards my own use cases.

I also preferred to use ruby rather than perl or python,
so the number of available package managers was even
more limited here.

## Package Users

The concept behind <b>package users</b> is fairly simple to
understand:

<b>Every package belongs to a certain user.</b>

So, for instance, the program called <b>evince</b> (a 
.pdf reader) would belong to a user called Evince, or
perhaps with some prefix, such as UserEvince, if we
have to avoid name collision.

This way you can immediately identify which file
on your computer system belongs to which package,
if the underlying operating system supports this -
which linux does.

By default this setting is <b>turned off</b> though. I
am not entirely certain whether RBT should support
this - but it is here mentioned in this document
to demonstrate that some thought has been given
about this feature/functionality. I first read it
when someone wanted to do a BLFS build (Beyond
Linux From Scratch).

## PDF Generation for users of the RBT suite

If you want to generate PDF files which you can print or distribute
anyway you see fit, have a look at the PdfGenerator.rb script.
Note though, right now the output is a bit ugly... I will look into
this again at a later point in time.

The above is fairly old content - generation of pdf-files 
may not work properly anymore. It is not so important, though,
as the RBT suite's primary objective is to support compilation
of programs, from source.

## Determining the version of the RBT suite

You can issue the following from the commandline to determine
the version of the RBT suite:

    rbt --version?

The version is kept in the file <b>rbt/version/version.rb</b>.

You can also query it from within ruby via:

    require 'rbt'
    RBT.version?

## Viewing all packages

To view a list of all packages on your system, do this:

    rbt php packages?
    rbt python packages?

The result would be something like this:

    ["/Depot/Packages/Python-2.5.tar.bz2"]

## Simulate running a program of the RBT suite

This option - also known as <b>no harm</b> Option, allows you
to run the RBT Scripts in a simulation mode.

This works like so:

    rbt php simulate
    rbt php --simulate

## class IncrementProgramVersion

This class can be used to automatically try to find
whether any given program was upgraded.

This assumes that programs are numbered in a
semantic version scheme.
  
## Extended cookbooks

You can require the <b>cookbooks</b> submodule in an
extended variant, such as via the following instruction:

    require 'rbt/module_programs'

The functionality is assumed to <b>extend</b> the
RBT namespace directly. In the past the file was
simply called <b>extended.rb</b>, but the name
<b>module_programs</b> is more logical, so it was
renamed to <b>module_programs.rb</b> some years
ago.

This is also called "modular apps". The idea is that
the dataset can be queried from the toplevel namespace
<b>RBT</b> directly.

After having done the above require statement, you can
then tap into this functionality allowing you to
directly call the dataset via the individual name, such
as by issuing:

    RBT.ruby
    RBT.htop
    RBT.python

Now you can see the data for ruby, htop, python and so forth.

Personally I do not recommend that users of the rbt gem should
use this functionality - it was mostly added to offer that
functionality syntax-wise, so that you can just type the RBT
namespace, and then the program name. Either way, you decide whether
you want to use it or not; I only wanted to make sure that this
functionality is possible for RBT as well.

## The history and philosophy of the RBT Project - philosophic considerations

This subsection in this README-document (autogenerated as **README.md**)
contains some information as to **how the RBT project was initially started**,
and how it has changed over the course of time. Additionally some of the
**philosophy** behind the RBT project will be explained, as well as some
conventions and the terminology used by **RBT**.

The **RBT project** in itself started out initially as means to
<b>re-create the shell scripts' logic</b>, and functionality,
used in <b>GoboLinux</b>, several years ago. I do not recall the
exact starting year, but I believe it must have been in the year
<b>2005</b> or so, give or take; perhaps 2006 at the latest.
    
I was already using **Ruby** at that time and I did not understand the
shell scripts that were used in **GoboLinux**.

Shell scripts can be quite confusing and difficult to read; parameters
do typically <b>not</b> go into a **regular function** via a function/method
signature, but instead are accessed as special **semi-global variables**
such as **$1** or **$2** within the function body. I find this
**extremely unintuitive**, confusing - and quite ugly. I would not mind
it so much if it could be used in addition to regular syntax, but if you
look at most shell scripts out there available on the world wide web, you
will see how unbelievably ugly these are. It's spaghetti code with tons of
syntax noise.

The more code you write that way in this way, the harder it becomes to
untangle that spaghetti mess. To be fair: **GoboLinux** had one of the
prettiest shell script-based code out there, so I have to give the
**GoboLinux** authors credit. It is actually quite readable compared
to a lot of other shell code in the www. But, even then, I still think
that well-written ruby code is so much prettier and easier to read. (Of
course you can write horrible ruby code too, but I am not referring
to such cases. By and large, I found it to be true that well-written
ruby code tends to be a lot better to read/maintain/change than
well-written shell code, for the **equivalent functionality**.)

So, the seemingly logical thing to do here for me was to <b>re-create the
functionality that GoboLinux offered</b>, in **Ruby**, as I find well-written
ruby code **much** simpler and easier to read and understand than shell
scripts - at the least the functionality that these shell scripts try to
offer.

At the least for me personally, I have a hard time trying to understand
what shell scripts do in general, even though the shell scripts used in
GoboLinux are one of the easiest and nicest to read, in my opinion.
The GNU Sorcery distribution also had some good shell scripts, but the
GoboLinux scripts were better written, in my opinion. Anyways.

Still, shell scripts are difficult to understand, and not very elegant,
and elegance/beauty, which is a subjective metric, was one important
reason as to why I did want to use ruby rather than shell scripts. I
prefer using elegant systems. Both GoboLinux, from a conceptual point
of view, and Ruby, are elegant systems/technologies, so it made sense
to want to combine different ideas.

Elegance/beauty/symmetry in style helps ease the **flow of mind** in
some ways. Why make something complicated if you can keep it simple?

People who may have been using other languages, such as PHP or perl,
may agree with this e. g. when comparing these languages to, say, 
ruby or python. I do not think python could have been so dominating
among the 'scripting' programming languages if it would have had a
syntax like perl.

Anyway. This was sort of **the initial impetus** for creating the
**RBT project**. Lots of years have gone by since then ... well over a
decade, really. I can not even pinpoint to a single year when the RBT
project was started, since it started out as a set of semi-random .rb
files/scripts, but I think the rbt project was created, through
the old cookbooks project, in the year **2005**, give or take. The
file called **cookbook_statistics.md** keeps some old entries. For
example, in late October in the year **2005**, the old Cookbooks project,
which was eventually changed into RBT, already had **274 programs registered**,
so it had to have been started prior to October 2005. For comparison -
in the ~middle of **May 2019**, **3593 programs** were already integrated
into the **RBT project**. In **January 2021** **3724 programs** are
now registered - it keeps on growing, slowly, but steadily. (And yes,
sometimes old programs that were not updated in decades, are removed
as well. I try to keep the registered programs count for projects
that, with some patches, could be adapted to the modern era.)

Naturally if you have a project that is that old, a lot of things
change. This was also the case for the **RBT project**, in particular
the scope of the project has expanded since then.

The **primary focus** for the **RBT project** still focuses on compile-related
activities. I use the RBT project almost daily in order to get something to
compile/install. At a later point, **RBT** became more of a toolset project.

In some ways, this implies that one secondary goal of the RBT project is
to be able to build a **LFS** ("Linux from Scratch") system from scratch, 
but not every functionality within the RBT project is equally well
polished or battle-tested, so manual intervention is still necessary
for the time being. The long-term goal is to be able to build a fully
automated LFS, though. For example, the option **rbt --intelligent-bootstrap**
taps into this, even though it does not work perfectly well yet; the
idea is to simply perform a "bootstrap" operation, de novo, and
let ruby figure out what is all necessary. This is akin to the
ALFS project, aka **automated LFS**.

Without buzzword talk, RBT itself is in many ways just a large, happy
hackish project, rather than something that has a great, perfect design.
While a good design is immensely useful, it is not quite how I approached 
the problem domain originally, nor was it possible for me to do so, since 
*RBT** is ultimately a hobby project; I more try to solve a given problem
at hand, and then move on to do other things. Of course I do try to keep
the code clean and well documented, but you know how it goes for any
hobby project. Sometimes you have more time (and motivation) and
sometimes you lack both. I try to remain motivated; otherwise projects
may be abandoned suddenly, which isn't great.

As **a rule of thumb**, though - **the simpler the task** that you may
want to achieve through RBT, in an automatic, scripted way, the easier
it should be for RBT to be of help here.

As it was already mentioned, in the past there used to be a separate
project called **Cookbooks**, the predecessor to **RBT::Cookbooks**.
That project specifically handled the recipes for the programs, that
is, **how to install or compile something specifically**. In the year
**2018** the Cookbooks project has been fully merged into the RBT
project, primarily to make syncing the code easier. The **RBT::Cookbooks**
namespace handles the source files' logic, whereas RBT itself handles
how to interprete this information, in particular through the main
class to use for compiling something, which is the class
<b>RBT::Action::SoftwareManager</b>. (The old class RBT::Compile has been
deprecated in <b>2022</b>.)

When you have a look at the RBT project, including the documentation
on the homepage of the RBT gem, you may notice that the documentation
is quite detailed and will explain quite a bit of the **internals**,
that is, of the internal code used in RBT. This code base is
predominantly written in ruby. As such, the whole RBT project caters
**heavily** towards people who already use ruby as their main language
of choice.

Why did I decide to also document and explain some internals? After all
this will lead to a lengthier documentation. Now, there are two main
reasons for this:

• The **first reason** is that it actually helps me remember when I made a
specific decision, and why. When looking back at it, perhaps even years
lateron, I need to understand why I did choose to go to a particular
route.

• The **second reason**, and more important one, is that I want to treat
users as intelligent people, so I will try to explain to them how 
some of the RBT internals work. Naturally not all of RBT will be
explained that way, but more important parts, such as e. g. <b>RBT::Action::SoftwareManager</b>
in particular, will have several entries that will explain what is
done, and why. My ideal aim would be to actually write a specification
as a text, and then let ruby simply parse and evaluate that text -
that would be the best. For now, though, the logic simply is hardcoded
in the various .rb files, as-is.

I am aware that not everyone using RBT may use ruby. For example, you
may use python as your primary language rather than ruby, but would 
still like to make use of the **yaml files** in the RBT project.

I will try to keep the yaml files and format well-documented and
well-written; this is an ongoing effort, though. Keep in mind that some
entries are literally very very old by now. (You can also compare this
to the old GoboLinux recipes, which you can find on Github. Several
of these projects no longer exist.)

You can generate a sanitized variant of these yaml files from ruby, and
then just keep on using these .yml files in other projects - after
all that is **one advantage of yaml**, that we are freed from any 
single programming language (such as e. g. hardcoding information
into a **.rb file** or a **.py file**). If you wish to generate these
**expanded yaml files**, you can use **rbt --expand-cookbooks**, but
you may wish to **set to another temporary directory** before doing
this - see other parts of this document for how to do so. Note
that the expanded .yml files are also distributed with the rbt
gem; this was done to allow for faster bootstrap-like operations.
People can just take the dataset from the .yml file and work on
it, even without using ruby. See the subdirectory at
**rbt/cookbooks/expanded_cookbook/** for this.

That still leaves some room to explain some of **the philosophy of
the RBT project**.

There are different philosophies, but to name a few key ones:

- Try best to solve the use cases that the user at hand has, without
getting into the way or preventing specific actions if a user really
wants to do so.

- Try to be "apolitical", "agnostic" and as flexible as possible. For
example, while I  personally do not use systemd, the RBT project in
itself has to be as flexible to allow those who use/depend on systemd
the use of RBT.

- Try to provide the most common functionality through RBT, as much
as that is useful, including acting as a (surrogate) package manager
or as a set of tools to auto-generate files. For instance, RBT 
includes one class that can modify the PREFIX variable in a Makefile.
That way people can easily change the target prefix of a Makefile
without having to use any other commandline options.

- Focus on Linux as a first-class citizen but do not exclude any
other operating system, if possible. Primary testing will happen
on Linux but other operating systems should be supported whenever
we can (if ruby works on these systems that is; but I will also
keep in mind resource-constrained systems, e. g. small/embedded
systems; for example, the RBT project can also autogenerate
shell scripts, so this could in theory be extended to work on
systems that only have shell scripts rather than ruby installed.
Do note, though, that for small systems, it is often better
to compile on a larger desktop machine than on such a small
constrained device; compiling on a raspberry may take even
days.)

Do note that in early **2020** I decided to partially abandon
the GoboLinux scheme. The RBT project will retain the focus on
GoboLinux, if only for compatibility - but other than that,
the project attempts to be standalone and general-purpose,
not coupled to any single distribution as such. This also 
means that alternative approaches will be explored.

## Current status of the RBT project

The following subsection was added in **March 2020**, in particular
because new users may be overwhelmed about the level of detail
and options available in the **RBT project**. In **January 2021**
this section was updated, as well as in **September 2021**, to
explain that the project is in maintenance mode mostly.

I understand that the complexity of the RBT project can be a problem
for newcomers. Furthermore, the RBT project differs in quality - some
parts of it work really well, whereas other parts have bugs. I am 
aware of many smaller bugs, and a few larger bugs, and while I do
happen to eventually fix one or the other, RBT is ultimately only a
hobby project; time is limited so I can not necessarily fix all bugs
in a short amount of time. Sometimes later code changes lead to
regressions, or other parts of the project no longer working correctly.

The complexity of the RBT project can be an obstacle for **newcomers**
in general.

Historically the RBT project has been growing a LOT in the last some
years. While some functionality could be removed, I believe that at
the end of the day, the project will always be somewhat complex and
allow for a lot of flexibility to exist - thus, it will always be
a somewhat complex project.

Different people have different use cases as well, so this is quite
difficult to want to change, without losing benefits from having the
code in the first place, such as for supporting specific functionality
that may be useful to some users, depending on the circumstances.

**If** the goal is to allow for easy compilation and installation,
then code has to exist that achieves precisely this outcome -
and this will unavoidadbly lead to some **necessary
complexity**.

Still, I understand that new users may struggle with the amount
of information, which could lead to confusion and frustration, 
so this subsection tries to explain at the least a few things
in addition to other subsections here that do so as well, as-is.

In January 2023 this subsection was changed; the "How I use
the RBT project" was added as a separate subsection closer
to the top of this page. That way new users can quickly
read and learn how I use the RBT project.

## New users and how to "onboard" them, as far as the RBT project is concerned: policy and strategy

This subsection was added in <b>March 2023</b>, as one tiny step
towards trying to teach newcomers how to use the RBT project.

This subsection only explains a few policies, though - the background
context, so to say.

The subsection before pointed out that the <b>rbt gem</b> is quite complex,
and to some extent complicated. In the past the rbt gem was even
more complicated - and this was one primary reason as to why this
subsection was added. I want to keep things simple, at the least
for new users; to some extent also at a later time.

At any rate, before <b>March 2023</b> the rbt gem made use of various
add-ons, such as <b>ccache</b> or <b>porg</b>. In the event that you
do not know projects like these: ccache is useful when you have to
compile many different programs from source. It will use a cache,
which can really help speed up subsequent recompilation efforts -
very useful really. <b>porg</b> on the other hand can be used to
trace as to which files are installed onto the target computer.
This functionality is especially useful when you wish to be able
to provide a package manager, e. g. by providing an <b>uninstall</b>
functionality.

So, before <b>March 2023</b>, the configuration I would use for the
rbt gem, typically mandated that porg and ccache are to be used -
and the assumption here was that both projects are installed on
the target computer, and that they will work, too. These assumptions
may turn out to be incorrect. I noticed this problem in particular
when I set up a new computer with a semi-broken toolchain. I can
typically "uncripple" this eventually, by recompiling what I need,
but how should a new user know any of this? That takes experience
and at the least a bit of knowledge.

Thus, as I realised that mandating ccache and porg "out of the
box" isn't that useful for new users, on a freshly installed
(random) computer system, I decided that a new policy had to be
added for RBT. This policy states that the rbt gem will try to
be <b>minimal</b>, whenever possible, in regards to depending
on external projects such as ccache or porg. That way the rbt
gem no longer distributes configuration settings that are not
so useful for new users.

What is the long term benefit of this approach?

It is hoped that this new policy in place will make it easier
for genuinely new users to give the project a try. As it is,
the project is catering too much to my own use cases - while
that is acceptable for a project that has not yet reached
a stable release, I believe we should slowly begin to help
new users more, should they wish to make use of the rbt
gem. Less frustration, more happiness. \o/

## @source_base_directory

The very important instance variable **@source_base_directory**, defined
at the toplevel **module RBT**, can be used to **denote the directory
where archives of different programs are to be kept** (or are
already kept).

For **example**, on my home system I store the source code to many
different programs in the directory **/home/x/src/**. That name 
emerged mostly due to historic reasons, as the user "x" was just
a generic name I would use for various different tasks, including
making regular backups. (I did not want to type too much when
doing a backup, hence why just one letter was used there.)

As other users of the **RBT** project may wish to use another
directory rather than the one listed above, such as
a directory like <b>/Files/Archives/</b> or **/Depot/Archive/**
or anything like that, there are essentially **three different
ways** how to define your own target directory for keeping
such <b>source archives</b>:

(**1**) Simply set a new target altogether, via the **toplevel-method**
called **RBT.set_source_base_directory()**. A shorter API exists
as well, an alias to this method, called **RBT.set_source_directory()**.

You can also use **RBT.source_directory = path**, if you would like to.

As **argument** to this method, simply pass in **the path to the
directory** that you wish to use, such as **/opt/** or **/home/src/** or
any other location that you may wish to use.

Explicit examples for the API that was mentioned above, will be shown
next:

    RBT.set_source_directory('/opt')
    RBT.set_source_base_directory('/opt')
    RBT.source_directory = '/opt'
    
    # Or for the target /Depot/Archive/

    RBT.set_source_directory '/Depot/Archive/'

Note that this method will **ensure** that a trailing '/' token will be
the last character here. (Directories should end with a trailing **/** -
it makes the subsequent code easier to handle when we can assume that
this is always the case. I am not entirely sure why Linux/UNIX does
not seem to share the same notion, but this may be due to a POSIX
requirement perhaps, and a way how the filesystem is addressed in
general, such as via **./**.)

The method call to **RBT.set_source_directory()** will **not** make
the above directory persistent, mind you, so you may want to read
on for option (**2**).

(2) Another option is to use a setting in the main **configuration file**,
typically a yaml file called **source_base_directory.yml**, the path to
the source directory can be set as well. This is the method that I use
primarily, since I keep the same base directory all the time.

In the directory of the RBT project where the configuration files are
stored, you can simply use the target directory, by putting the path 
to the source archives into that file.

You can also use **environment variables** in this file - simply 
use ALL_CAPS to make use of such environment variables. (This
won't work in all settings, e. g. for **.cgi files** it may not
work since .cgi files may use fewer environment variables. But
for regular commandline-work, this works fine. I may use an
ALL CAPS constant such as MY_SRC_DIR there in this file.)

(3) Not everyone will be able to modify the directory where the
configuration of RBT is kept, so a third way has to exist, using
the **environment variable** called **RBT_SOURCE_DIRECTORY**.

In general, RBT may use environment variables that have a leading
**RBT_** as prefix. Simply define the variable called
**RBT_SOURCE_DIRECTORY** for your shell, pointing to the
directory that you wish to use, and it should work just
fine:

    export RBT_SOURCE_DIRECTORY=/Files/Archives

The last option may work for you if **option (2)** is not available
or not possible.

## Return an Array of programs from a remote URL

In the **RBT project** there is code that allows us to query the
remote programs listed on an URL.

This was a necessary addition because there are some websites that
have made available several programs on the same URL - think of
the **GNOME project** here, or the **KDE project**, or the
LFS/BLFS project page. Their remote websites, typically as a
FTP-listing, all list several programs there.

The basic API for obtaining an **array of programs** from a remote
URL is the following:

    RBT.return_programs_from_this_url
    RBT.return_program_from_this_url('https://download.kde.org/stable/plasma/5.10.5/')
    array = RBT.return_program_from_this_url('https://download.kde.org/stable/plasma/5.17.5/'); pp array.size # => 46

This will, if all goes well, return an Array of programs available
at that site, if it can be found.

## psych or syck

You can determine **which yaml-engine to use**, as far as the
**RBT project** is concerned.

In the past, the **RBT project** would try to make use of the syck
engine, but since psych has become the default since some years,
RBT will try to make use of psych by default. This can be changed
via the configuration file **use_psych_or_syck.yml** that
resides at **rbt/yaml/configuration/use_psych_or_syck.yml**.

A top-level API also exists to query which yaml-engine is
currently used:

    RBT.yaml_engine?

If, for some reason, you have to or want to modify this, you can
use the following API to toggle any other yaml engine:

    RBT.yaml_engine=
    RBT.set_yaml_engine

I am using psych these days, though, so this is only kept as
a legacy option. It will probably be retained for the full
"lifetime" of the RBT project, but I myself no longer need
this really - psych has replaced all my yaml needs.

## Configuration of the RBT project

Most of the configuration for the **RBT project** is done through
yaml files (**.yml**). These individual yaml files are normally
kept under the subdirectory **rbt/yaml/configuration/** of
this gem.
         
For example, a file called **be_verbose.yml** can be found in
that subdirectory. This file determines as to whether the scripts 
are verbose by default or as to whether they are not. You can use 
shortcuts here, such as "t" which stands for true, or "f" which 
stands for false. Of course you can also use true and false, 
as content of said file. Additionally you can use "yes" or "no"
if you prefer these instead.

So, if you put the string **no**, without quotes, into the file called
**be_verbose.yml** then the RBT scripts will not be verbose by
default. This means less output on the commandline, for example.

Similar possibilities exist for the other files that accept a **Boolean
value** (true/false aka yes/no). Obviously this would not work when you
are expected to input a **file path**, such as the path to a certain
directory. In this case you simply have to provide a string to the
path in question - but you can also use environment variables if you
have defined them. For example, I keep an environment variable called
$MY_PROGRAMS, so I can input that String (**$MY_PROGRAMS**) into the
file called **programs_directory.yml** and all RBT scripts will refer
to that as the main /Programs/ directory (it is indeed usually 
**/Programs/** but it could also point to my home directory or
any other target; since as of January 2020 I actually use
**/home/Programs/** as I sometimes do not have access to the
**/** directory, or may have to relocate this into my user
directory anyway.).

## How does the format of a cookbook recipe, the respective .yml file, look like?

Each **cookbook entry** is just an **individual yaml file**, with the extension
name being **.yml**. For example, information about the programming language
**ruby** will be stored in the file called **ruby.yml**; information about the
programming language **python** will be stored in the file **python.yml**;
information about the **mate-desktop** will be stored in the file
**matedesktop.yml**. If there are any "-" tokens as part of the name, then
these will be removed when rbt tries to determine the filename. 

This **yaml file** should contain all the required information to get that
particular program to install on a given system.

Additional information can be added as well, such as **maintainer**(s),
**extra information** of the program at hand, tips and hints in how to install
or use the program, sed-modifications, pkgconfig files (aka .pc files) that are
installed alongside with, patchsets that are to be applied, binaries, headers
and libraries and so on and so forth.

It can be a quite detailed file, mostly due to being able to allow some flexibility
during installation.

Many programs "out in the wild" are **well-behaving** and will honour a 
**--prefix** variable given (or **-DCMAKE_INSTALL_PREFIX=**, such as in
use by programs that depend on **cmake**, for compilation). Such programs
usually require **little to no modification**.

Unfortunately, some other programs come with **flawed installation scripts**,
hardcoded paths or workarounds that have to be employed to get these to work -
very often sed-operations, such as done in the LFS project. Some programs
may also have already become obsoleted, due to changes e. g. in glibc/gcc
and other programs. If there is no maintainer of the downstream package
then this normally means that other people have to either maintain that
package; or provide patches to get this projects to work again.

As **a reference project**, the **LFS project** provides a **lot** of useful
information in how to get many programs to work. I consider the **LFS
project** to be hugely important for the whole Linux ecosystem, much more
important than the various different distributions.

At any rate, let's now have a look at the **fish.yml** recipe, to give
a specific example and explain that.

This **fish.yml** file will look like this, as of **August 2018**:

    fish:
     binaries:
     - fish
     - fish_indent
     - fish_key_reader
     short_description: |
      FISH is an interactive (commandline) shell.
     description: |
      FISH is the Friendly Interactive Shell, a smart and user-friendly
      command line shell for macOS, Linux, and the rest of the family.
     url1: https://github.com/fish-shell/fish-shell/releases/download/2.7.1/fish-2.7.1.tar.gz
     url2: http://fishshell.com/files/2.1.0
     url3: http://sourceforge.net/projects/fish/
     homepage: http://fishshell.com/
     tags:
     - shell
     prefix: f
     keep_extracted: t
     last_update: 08 Jan 2018

The very first entry, on top, is the name of the program itself, in this
case, **fish**.

While this part could in theory be omitted (since the name of the program
is already stored as the first part of the very filename), I found that it
is useful to have this entry within the file, primarily as a visual identifier
if you work with it in an editor. It helps me a lot, for instance.

Note that no **-** or **_**characters are allowed there in this entry - it is
really a stripped down name of the program at hand only.

If the name would be e. g. "gtk-doc", with an URL such as
**http://ftp.gnome.org/pub/gnome/sources/gtk-doc/1.26/gtk-doc-1.26.tar.xz**,
then the name there for the gtkdoc.yml file would have
to be **gtkdoc:** - thus, all '-' were removed. The name that appears there
is also the name of the .yml file at hand. The .yml files may also not 
include any '-' or '_' characters. Do also note that while I am following
this convention since many years, it may one day be changed to allow for
'-' and '_'. But for the time being, the strict requirement is that we may
not have '-' or '_' characters there.

Next, let's look at the entry **binaries:**. This entry tells us which
binaries/executables this particular program will install. This also
allows us to remove binaries in the /usr/bin/ hierarchy, if you compiled
into an AppDir prefix - for more information here, see class
**RBT::PurgeBinariesOfThisProgram**.

The next entry is **short_description**, which is e. g. equivalent
to slackware's pkg-format, as introduction to the specific program
at hand, in a short notation.

Then we have the entry **main description**, followed by several **url**
entries. The first url entry, aptly named **url1**, is the most important
entry. It tells us where to find the archive to the program at hand.
This is ideal the URL to an existing archive, but it could also be
a github repository, in principle.

Then we also have the **homepage** entry, which denotes the homepage of
the program (or any other webpage that has relevant information, in the
event that there no homepage entry exists for that particular program).

Then we have **tags**: which just groups the program into popular
**tag-classifiers**, such as "shell" in this case. Then the prefix in
use, which is f for false, meaning "non-traditional" aka "appdir" prefix
such as GoboLinux makes use of. Then there is the keep_extracted 
setting, which tells us whether to keep the archive extracted or not
after extracting/compiling it. Last but not least, the last_update
tag tells us when this program was last updated. The default format
here is dd.mm.yyy, but shortcuts are allowed. For example, Oct, for
October, can be used rather than 10, and so on. 

The next entry is <b>prefix</b>. This one is mostly synonymous for
the --prefix= option given to GNU autoconfigure based projects.
A prefix value of t means true, which stands for /usr/. A prefix
value of f means false, which stands for the particular AppDir-like
prefix. In the case here, for fish, this would expand to
<b>/Programs/Fish/2.7.1</b>. GoboLinux uses a very similar AppDir
layout by default, although with slightly different program names
that can also be upcased, e. g. "KDE-Libs" and so forth. (RBT will
offer both variants here; the GoboLinux naming scheme, and the
simpler scheme where only the first character is upcased, and
the other characters are all downcased.)

There are many more entries, most of which should be documented
under the doc/ subdirectory of this gem. What follows next are
some more mentions of important (and less important) entries.

The entry **configure_base_dir: unix** determines which base
directory is to be used. In the above example, RBT would
cd into the directory called unix/. This is important for some
programs such as **tk** or **xvid** - have a look at their
directory structure to understand this setting.

Since as of December 2018 it is possible to use github URL that
are truncated. Take the program **conky** as an example. It
has an url like the following:

    https://github.com/brndnmtthws/conky/archive/v1.11.0.tar.gz

This will now be automatically expanded into the correct 
naming scheme, aka **conky-1.11.0**. No idea why GitHub is not
doing so on their own automatically; the tarball is even 
wrongly built, since it extracts to precisely that name 
after download. But anyway, ask GitHub about this, not me.

The content of these individual .yml files is essentially just
a Hash that describes the various attributes of the given
project at hand (and some additional information when it is
required for installing/compiling this program).

Note that since as of January 2020, you can also just provide
a new URL and register a program this way anew.

Commandline Example for this:

    rbt http://ftp.gnu.org/pub/gnu/kawa/kawa-3.1.tar.gz

## /home/Programs/ versus /Programs/

On GoboLinux, the main application directory is at **/Programs/**.

For RBT, the default since a few years is **/home/Programs/**.
Now - the user can set any other application directory anyway,
so this subsection explains mostly my own use case.

I was following the **/Programs/** hierarchy for some years,
but eventually changed to **/home/Programs/**.

There are two reasons as to why:

(1) It makes backups a bit simpler, since I just copy all
that may be in the /home/ directory, so I don't forget.
And then I copy it onto the target system - job done.

(2) In particular on Fedora, /home/Programs/ seems to 
work better than just /Programs/, e. g. due to the default
splitting of the filesystem. Since I did not want to 
bother researching sanitizing the filesystem, I simply
decided to go with /home/Programs/ rather than /Programs/.

So, my two major reasons are convenience and laziness.

Of course I think /Programs/ is more elegant, but I get
around this by just using a symlink anyway, pointing
from /Programs/ -> /home/Programs/.

## Cookbooks - Recipes to install programs from source

The **Cookbooks module**, part of **module RBT** and thus residing
under the **RBT::Cookbooks** namespace, attempts to collect recipes
and instructions that allow you to **install programs** from source
(primarily).

This project has well over 3350 programs registered so far - and that
number continues to grow slowly.

If you are interested in seeing the specific programs and the associated
programs versions and URLs, have a look at the side pane on the right
hand side, at __**Available program versions**__.

**What is the use case for this project? How could this project help you?**

The use case for the Cookbooks component, part of the RBT project, is
to **provide the necessary instructions for compilation/installation of
programs**. These instructions will be primarily stored in <b>yaml</b>
files.

For example, the text-editor called <b>nano</b> will have some information
that details how it should be compiled, in the file called <b>nano.yml</b>.

This is valid for all programs that are registered, by the way - for each
program, there will be a single .yml file that describes that program
in question.

Now, how could this be of help to you or anyone else?

This of course depends on your use case at hand, but say that you may want
to compile a <b>linux from scratch</b> system and then a <b>beyond linux
from scratch</b> system on top of it. You can - and should - follow the
official instructions of course, but once you understand the basic concepts,
perhaps you may want to have more control over the programs at hand or
wish to compile/install more programs, including their dependencies.
That's exactly one use case for the **RBT project**, through its
Cookbooks subcomponent.

There are more use cases of course, such as updating your programs
from source quickly. Keep in mind that a lot of information is stored
in all the yaml files together - describing the program at hand, where
to find the source, how to install it, and so forth. This information
may always be helpful to some people. Many yaml files include the
homepage link, so rather than having to use google, one can quickly
jump to the registered homepage at hand (the entry in the .yml file
will be called <b>homepage:</b>).

The **Cookbooks project** is a component of the **RBT** (Ruby Build Tools)
project. The latter project, aka <b>rbt</b>, is the one that formally
integrates the dataset provided by the module Cookbooks part, into
general compile/install related activities. I use rbt to compile
programs from source or otherwise install them. 

If the cookbooks project and the RBT project are used in <b>combination</b>,
then they are in **some** ways similar to the **MacOSX homebrew project**
or the **fpm project** - sort of.

There may be some philosophical differences between these projects, but
the cookbooks project and the RBT project will attempt very hard to provide
similar functionality as fpm and mac homebrew do, too, in the long run.
Please do keep in mind that this is a hobby project here, and as a consequence,
it may not move as fast as <b>homebrew</b> does.

The similarity towards **fpm** is that the cookbooks project will also attempt
to allow you to **interconvert** the registered dataset into .deb or .rpm files
or gobolinux files or snapcraft files - or even homebrew formulas. But that
functionality is very limited (as of in 2018). It will definitely become better
over time. The slackware support is a bit better since I myself mostly use
slackware and GoboLinux, but the slackware support in cookbooks/rbt still
requires quite some more polish and clean-up before it can be easily used.

The <b>RBT project</b> is in some ways similar to the LFS/BLFS project
in that it attempts to put together information that would be useful for
when a user wishes to compile some program from source, in particular
when these programs are requiring modifications to their build system,
such as when "sed" is used - but the RBT project could also be used
when installing a binary program. In doing so, the RBT project can
also be used as a basic **building block** for creating package managers
or other compile-tools in Ruby. If you have a project like this and may
want to make use RBT, and require some modification, let me know - I will
try to adapt the project to make them useful for these cases as well.

Now - let us have a look as to **how information is stored** in the
**RBT project**.

The information for the respective programs is stored in yaml files by
default, largely due to convenience and "historic reasons". Taken together,
we could call the collection of yaml files a "yaml database" - even though
it is not a real database, per se.

These individual .yml files, by default, reside in the subdirectory called
**yaml/individual_cookbooks/** of this gem. The .yml files usually also
make use of shortcuts and abbreviations, which will be sanitized when
the specific yaml file is loaded by the Cookbooks project.

For example, a common entry point may be like so:

    "keep_extracted: t"

The "t" at the end is a shortcut for "true". The entry **keep_extracted** 
means that, after an archive is extracted, it will be kept rather than
removed, after compilation has finished.

The Cookbooks project operates under the assumption that all archives that
the user will use, are put into a certain base directory, which, for the
purpose of this file here, will be called the **archive directory**.

This is the directory where your archives should reside. You can ultimately
decide which directory that shall be.

On my home system, this archive directory is at **/home/x/src/**, mostly
due to historic reasons how I kept making backups. On GoboLinux, you may
want to use perhaps /Files/Archives/ or /Depot/Backup/ or something 
similar. You can query the current archive directory in use by issuing
this command:

    cookbooks --archive-directory?

There, source files can be stored, such as **htop-2.0.2.tar.xz**
or <b>ruby-2.4.1.tar.gz</b> and so forth.

Since many other users may wish to use another base directory for
their archives, you can define another archive directory on the
commandline like so:

    cookbooks --permanently-set-base-directory-to=/opt

The above would assume that all source archives will be stored
within the **/opt/** hierarchy.

Or use the more prevalent rbt name:

    rbt --permanently-set-base-directory-to=/Mount/USB1/last_backup/src/
    rbt --permanently-set-source-archive=/Mount/USB1/last_backup/src/
    rbt --set-source-dir=/Mount/USB1/last_backup/src/
    rbt --set-source-dir==/Files/Archive/

The above would assume that all source archives will be stored
within the <b>/Mount/USB1/last_backup/src/</b> hierarchy.

Since as of April 2019, the following shorter variant can also be used
instead:

    rbt --source-dir=/SRC

I added this primarily because typing the longer variants above, on a
freshly set-up computer, is somewhat cumbersome. So the shorter variant
should do fine in these cases.

Within that archive directory, subdirectories have to be created
for the respective program at hand.

Actually, ruby may already do this for you, via the **rbt project**;
but I recommend that you first start slowly and manually create
directories for now.

So, pick just some program, anyone will do fine as long as it is
registered in the RBT project. Create that archive directory if
it does not yet exist, cd into it, create the directory of the
program which is the program name (downcased, and without any
'-' or '_' tokens).

Let's break this down and use specific examples, to illustrate
what is meant - we wil pick the program "htop" as example.

First, create a subdirectory called "htop/", within the source
archive directory that you picked.

On any linux/unix system, "mkdir" should be able to allow you to do
that - but you could also use Ruby's fileutils class to do so, via
**FileUtils.mkdir_p()**.

Next, download the remote source for this program locally (you can
also use the rbt project to do so for you: **"rbt htop --download-source"**
but for the first steps, again, I recommend to do these steps manually
instead).

    wget http://hisham.hm/htop/releases/2.0.2/htop-2.0.2.tar.gz

More specifically, on my home system, I'd do the following things manually
(but keep in mind that ruby does this for me automatically):

    mkdir /home/x/src/htop
    cd /home/x/src/htop
    wget http://hisham.hm/htop/releases/2.0.2/htop-2.0.2.tar.gz

If you, for instance, want to store multiple versions of GLib, then
a downcased directory called glib/ has to exist within that 
source archive directory - just as the example above shows for
htop.

Different versions of **GLib** can then be stored in that directory.

The path would, in my case, be:

    /home/x/src/glib/

That's it, essentially!

Past this point, the cookbooks project - or rather, the Cookbooks
submodule of the RBT namespace - can feedback some information
about htop via the executable called "scookie".

For example, to use scookie (<b>bin/scookie</b>) and thus display
information about a program in a colourized manner, on the
commandline, do:

    scookie glib
    scookie htop

By default this will truncate too many entries (e. g. more than 5
entries for libraries, headers, and binaries). If you would rather
not want scookie to truncate, you can pass the commandline flag
**--do-not-truncate**, like so:

     scookie glibc --do-not-truncate
     scookie htop --do-not-truncate

Take note that you can enable this functionality also through **bin/rbt**
(aka **rbt** on the commandline) as well, such as in the **following
examples**:

    rbt --scookie=glib
    rbt --scookie=htop

The associated .yml file is always available anyway, with or without the
archive being available locally as well. So you can always query the
information stored in these .yml files the moment you install the
**rbt project**; it can thus function as a weak "database". (I will
at some point add **SQL instructions** in how to create a SQL database
and use it with the RBT project. But note that the .yml way will
most likely remain the default way; primary reason being out of
convenience, since it is so trivial to edit a single text file such
as .yml files.)

If you are wondering why the name "scookie" was picked - it originated
from the **sanitize_cookbook_dataset** functionality, which ensures
that the dataset is correct. I was using the abbreviation "scook" to
refer to sanitize_cookbook_dataset, but I found that "scookie" is
easier to remember. Everyone likes cookies, right?

The **cookbooks project** should now be usable to display information
about this project - provided that it has been registered of
course. If it is not yet registered, then someone has to register
it; there are some helper scripts that can aid you there, but as
a rule of thumb, I'll add new program entries when needed. They
are essentially just a single .yml file.

Currently, there are more than 3000 programs that are registered
in the Cookbooks project; almost 3200 already and this number is
very slowly continuing to grow.

Cookbooks may also keep track of information such as whether
a given progam at hand will install a .pc file (pkgconfig file).
This may help if you are on a non-GoboLinux system and wish to
find out which particular program installed which specific
.pc file, too. (On GoboLinux this is trivial to find out since
it keeps AppDir-related and versioned programs, whereas on
the traditional FHS preferring /usr prefix, the individual 
.pc files would usually reside under /usr/lib/pkgconfig/, 
without always giving you a simple way to ind out as to where
they came from.)

You can query this by using "scookie", which will show this, and
more, in a colourized manner.

An example follows:

    scookie libvorbis

If you wish to support this project, for now please just test it and
report any bugs or report inadequate or confusing documentation.

The project is still in a beta stage and it will take quite a long
while before it can leave that beta stage.

## Obtaining the number of registered programs

You can obtain the **number of registered programs** from the
commandline by issuing any of the following:

    cookbooks --registered_programs?
    cookbooks --n_programs?
    cookbooks registered_programs?

The number of registered programs can be queried via the
commandline as well, like in this way:

    rbt --n_programs?

Although the output may be a little bit different.

This would then output something such as this:

    → 3330 programs registered as of 30 January 2018.
    → 3414 programs registered as of 18 September 2018.
    → 3635 programs registered as of 01 December 2019.
    → 3656 programs registered as of 12 January 2020.

(The format may be a bit different to the above, but the
information content is the same.)

## Optional dependencies for the RBT gem

The **wget gem** is recommended as an optional dependency for the
RBT gem, but you can also use the RBT project without the wget
gem just fine. In that case, if the wget gem is not available, the
RBT project will attempt to use the wget binary via a
**system()**-call, hence an "external" program, to ruby.

This requires the installation of **wget** e. g. from this URL (or
from your package manager's repository), unless wget is already
available on your local computer system:

http://ftp.gnu.org/pub/gnu/wget/?C=M;O=D

Of course, most Linux systems will have "wget" available by default,
so the above more applies towards operating systems such as windows
(although more recent windows versions also include a linux-subsystem
including bash, the **WSL**, so this should also not be a problem).

## Increment Program Version

class **RBT::Cookbooks::IncrementProgramVersion**, stored in the
file **rbt/utility_scripts/increment_program_version.rb**, can be
used to **automatically update a local program version** to a
newer version, provided that the new version can be "guessed"
by the script.

Let's use a specific example, because it wil be easier to explain
this when we can be specific.

Take the program called **wget**. Let's say that we wish to
increment the program version of wget to a more recent one.

An **older version**, as a tarball release, may exist at
a remote location such as this one here:

    ftp://ftp.gnu.org/gnu/wget/wget-1.19.1.tar.gz

The (more recent) version in use may be for version
<b>1.19.2</b>.

**class IncrementProgramVersion** will first test whether a
remote URL such as:

    ftp://ftp.gnu.org/gnu/wget/wget-1.19.2.tar.gz

**exists**. If it does exist, it will be downloaded and the
new program version will be changed towards **wget 1.19.2**.

This can be done for all programs, and it allows a simple
update-mechanism for individual programs.

If you have to or want to batch-update several programs,
this is also possible for some of the *nix stack. For example,
there are some classes that can download the whole KDE5 stack;
have a look at the KDE entry or the mate-desktop entry, in
this (autogenerated) README.md file here.

Since as of **November 2020**, this also works for github-based
URLs. I needed this functionality because there are more and more
packages that are published only on github these days.

## Commandline ways to manipulate the dataset

There are some classes that can be used to manipulate the dataset
stored in the individual cookbooks files (the corresponding .yml
file). This is presently quite limited, though.

The only commandline-manipulation that is currently available,
is done by **class RBT::Cookbooks::ToggleKeepExtractedValue**.

This acts as a **toggle-switch**. If you invoke the class, and pass
the name of the program at hand, then the keep_extracted: value
will be toggled, from false to true and from true to false.
    
## Additional information

Consider having a look at the **doc/ subdirectory** of this project's
gem, for some more information. Another useful subdirectory may be the
**lib/yaml/** subdirectory, which also contains some specifications
such as **specification_of_registered_cookbook_entries.yml**.

## Stable software versus Unstable software

This subsection here explains how the RBT project currently (in
January 2019) views stable and unstable software releases
**upstream** - that is, by other developers, companies and so forth.

From my own experience, unstable releases may bring in new features,
but this often comes at a cost. Compilation errors may happen; bugs
may happen while running the software. What is even worse is that
other software may depend on functionality that may be changed 
during an unstable release. (While it may also be changed in a 
stable release eventually, stable releases in general often have
problems fixed whereas unstable releases often do not.)

In particular the latter is one reason why I focus on stable 
releases - there will be fewer issues in the long run, thus 
easening the maintenance burden. That also means that the Cookbook
projects tries to be **moderately conservative** - stable releases
are favoured, unstable releases are often skipped. For example, 
I skip odd-versioned releases of the GNOME project and also of
the KDE project. Waiting for stable releases just a little bit
longer is worth the time, IMO.

This is a loose philosophy, not a strict policy, so expect some
deviations - but in general, as a rule of thumb, there will be
stable releases preferentially in the RBT project. (In
the future we may have to change the cookbook entries to denote
whether a release is stable or unstable, but for now, in the
beginning of the year 2019, this is how the RBT project will
handle updates of any its registered programs.) 

## The difference between "build tools" and a "package manager"

A **package manager** allows you to handle packages in one way or 
another; installing, removing, tweaking, changing, activating,
selecting software. Things like that. As such, a package manager
is very useful in itself - it can help keep your system up-to-date
with new, or patched, **packages**.

**Build tools** in this context, though, are much more general. The
above description of a package manager can easily fit into a set of
build tools as well, but the scope of "build tools" is overall 
simply larger and more inclusive.

**Build tools** may also include helper code that can fix build-related
problems, problems in Makefiles, act as sed-wrapper, and so on and
so forth. A **package manager** on the other hand rarely needs to
tamper with sed instructions, since that should have already been
handled by the developers who maintain the packages for a particular
distribution.

So the scope of the build tools is larger and not as narrowly defined as
just a "mere package manager" alone. Another good comparison here is the
**ublock origin** extension or the **adblock plus** extension - the
latter wants to block only or primarily ads. The former allows you to act
as a "general content blocker" under your control, which CAN include 
ads but can also block generic content, which makes it a lot more powerful
and flexible in its approach.

I consider the approach taking up by **ublock origin** option to be far more
useful to users in general, so this is in some ways how one could look at
the difference between a "package manager" per se, and "build tools" on
the other hand, too.

**Build tools** could easily include a package manager but a package manager
will probably never include build-tools related helper scripts as its primary
means to go about handling anything. The RBT project is going the "build
tools" route - it attempts to collect code that can help with building,
installing, compiling packages in general, but also automatic patching
and automatic generation of files, and so forth.

If you wish to install the **rbt** project, via RubyGems, you can issue
the following command:

    gem install rbt

Do note that some functionality can work outside of the RBT::Cookbooks
namespace, such as <b>RBT::Libtool</b> related actions.

Now, when the above installation method has worked - and if it has not,
please do consider reporting this - you should be able to compile
something via the RBT scripts.

Let's start with "htop" as example, a useful program written by
one of the original creators of the **GoboLinux** project:

    rbt htop

This should, if everything works fine, download htop, extract
and compile it.

If you wish to use another prefix, such as:

    /Programs/Htop/2.0.1

you can do this:

    rbt htop --appdir
    rbt htop non-traditional
    rbt htop ntrad

ntrad stands for "non-traditional". Note that the entry is **NOT**
hardcoded towards **/Programs/** - you can define your own app-dir
prefix and even make use of $SHELL variables. For example, I point
to this directory via a custom variable called $MY_PROGRAMS, which
is stored in the file programs_dir.yml that is part of the RBT
project. More about this elsewhere though - for now just keep in
mind that this will install into a versioned AppDir directory, but
you can of course use any other variant such as "/pkg" or "/Programme"
or "/opt" - whatever. Note that you can omit the trailing '/'
there, so "/Programs/" is the very same as "/Programs" -
the RBT scripts will internally make sure that this will be
a directory anyway, and thus have a trailing **/** character.

**AppDirs**, for the purpose of this document, means that what belongs
to one program, goes into the same, versioned directory.

You can also use another prefix, in particular **/usr**. This
is called the "traditional" prefix. In the respective yaml file,
the cookbook file at hand, this entry is called "prefix: ".

If you see a "t" there then this is short for "traditional",
and it will be expanded towards "/usr" when used. Whereas
the character "f" will be expanded to mean "non-traditional",
thus AppDir prefix. Do note that you can also use other
shortcuts there and absolute targets as well - the reason why
single characters are used is largely to save me, but also
others, some typing work. If you want to use the longer
variants, you can do so just fine, but I assume that after
some typing work, you may be bored of having to make use of 
long words and consider using abbreviations instead. :)

Anyway, here is the example to use **/usr** as prefix:

    rbt htop --traditional
    rbt htop --trad
    rbt htop trad

Use any variant there. I prefer the last one, "trad", because
it is shorter to type.

If you wish to look at the available help options that are
available for rbt, do:

    rbt --help

Note that this will showcase mostly just the more common
ones. There are many more options that can be used.

There is a fairly large tutorial available as well. I 
have to publish it in .pdf format eventually.

## (Auto)Registering problems

The RBT suite attempts to identify errors, register them and
sometimes report these problems. The main idea behind this is
twofold:

    (a) To be able to auto-correct reported (and registered)
        problems.

    (b) To notify the user and optionally provide information
        as to why the error happens and how it could be fixed.

Ideally, autocorrecting would work to the extent that all
problems that occur, could be automatically solved. But
this is not trivial; while some problems can be quite easily
autocorrect, others can not. And sometimes there is ambiguity
so only the user can decide which variant is the correct one.

This is why the **notification part** is more important than the
**auto-correct part**. See the next subsection for some
autocorrection that can be done.

## Finding all programs that start with a specific letter

If you wish to find all registered programs that start with
a specific letter, such as k, do this:

    rbt k*

This will output all programs that start with k and also
tell you how many programs with that letter exist.

## Base subclass

The **RBT project** has a **base subclass**, residing at **rbt/base/base.rb**.

Most classes in the RBT namespace will inherit from this base class.

There is another class, called prototype.rb, which is pulled in by
base.rb. The reason why prototype.rb was needed is to avoid circular
dependency warnings - prototype.rb is much smaller than base.rb and
provides mostly just the core functionality that is sufficiently
useful for several classes.

## Show the last configure option

Since as of January 2018, a way exists to show the last configure
option used for a given program. This depends on the file
<b>configure_command_database.yml</b>.

If this file exists, and if the sought program has been compiled
before (meaning that RBT has stored the configure command used
in that .yml ile) - say, the program <b>attica</b> was compiled,
then you can query this information from the commandline, via:

    rbt attica --show-last-configure-option

This could then be used to copy/paste, or modify if you experience
some problems related to compiling a program from source, for
instance.

Of course you can also always peek into that .yml file on your
own. Thankfully yaml is sufficiently readable, more so than
big, clunky XML files.

## Timing of the compilation (duration)

Since as of January 2018, code exists to tell us how long it
took to compile a given program at hand.

This requires the configuration option time_compilation set to
true it the corresponding yaml file (within the <b>configuration/</b>
subdirectory).

If this setting is set to <b>true</b>, then RBT::Action::SoftwareManager will show, on the
commandline, how long it took to compile a program, in seconds (and also
in minutes). The default for this setting is <b>true</b> as of <b>January
2018</b>.

Note that the time it took to compile the given program at hand will
only be shown if there was no proble/error during the compilation
process. This may be fine-tuned at a later time, but for now, the
functionality at the least exists as part of <b>RBT::Action::SoftwareManager</b>.

The time it took, in seconds, will also be stored in the file
called <b>database_storing_compile_times.yml</b>, in a simple key-value
hash. (This file will be generated into the <b>rbt_logs/</b>
subdirectory.
On my home system this file will thus be at 
**/home/Temp/rbt/database_storing_compile_times.yml**)

If you compiled several programs via rbt, you can also show how 
long it took to compile these programs.

The commandline option for this is:

    rbt --show-compile-time-statistics

## Packaging the RBT scripts

You can package all the latest RBT Scripts by using a commandline
flag such as this:

    rbt package_cookbooks
    rbt --package_cookbooks

This will create a directory in <b>/Depot/Archives/</b> and package
the RBT Scripts into that directory.

Of course you can do so manually as well, but I wanted to have
this functionality at the least available for when a user is
on windows and may need to transfer the files, for whatever
the reason(s).

## systemd

I personally do not like systemd in the slightest nor can I align
with the, in my opinion, absolutely unnecessary and constantly
changing goals of the ever-expanding systemd project or the attitude
of the main systemd developers. It seems as if systemd's primary job
is not to solve any user-related problems, but instead to be of the
main benefit to those who wrote, created and maintain it, primarily.

This subsection here is, however had, not about projecting my personal
opinions about systemd onto others - this subsection is **how systemd
relates to RBT**, if it does so at all.

The RBT project is "apolitical", that is - it is for the people who
use it, the **users**. If users want to use systemd then this is
fine. And if users do not want to use systemd then this is fine as
well.

Note that the <b>LFS</b> (linux from scratch) project follows a similar
philosophy. It has a non-systemd and a systemd variant, so you can pick
either variant **at your own discretion**.

Compiling and installing programs should work at every moment
in time, as far as the **RBT project** itself is concerned. At
the least RBT will attempt to **make things work** and aid a
user in precisely that way.

However had, the **RBT scripts** are predominantly tested on
non-systemd linux systems, so it may be that parts of RBT
have to be changed/adjusted if you are using the RBT project
on a systemd-dependent setup.

I will accept bug fixes and behaviour changes in regards to
compliance with systemd systems **IF** non-systemd systems
can continue to work just fine as-is. That is, **changes may
not happen in an exclusive manner** - changes that do will be
rejected. They will of course be accepted if it does not 
break this assumption and if they are in the spirit of the
RBT project itself.

The primary reason for this here does not relate to my 
personal opinion either, but the simple question of the
amount of time that is available to me, which I invest
into various projects already. (RBT is only one project
among many more; and that's just computer-related
projects. I have many non-computer related projects,
hobbies and things that require time investment.)

## Subversion

You can try to download from SVN sources, by issuing the
following command:

    rbt dosbox svn # This would download dosbox using svn

Note that this depends on the setting <b class="color: royalblue">svn_url</b>
in the respective cookbook file (in this case dosbox.yml).

The <b>svn_url</b> setting must be specified, as otherwise RBT
can not download the code via svn.

It is quite rare that source archives depend on svn nowadays, though.

## Creating a .yml yaml file for a specific program

If you modify a .yml file, from the rbt project,
and then wish to autogenerate a new expanded cookbook
dataset, then you can use this commandline switch from
within rbt to do so, too:

    rbt --create-yaml-file-for=subversion

This requires the cookbooks gem to be installed.

You can do so from the rbt project already as-is, so
why was this functionality added to rbt?

Mostly out of convenience. I feel that it may be simpler 
to make available functionality that is somewhat common
between the two projects (cookbooks and rbt) from rbt
itself too. After all, rbt is the project that sort of
builds upon - and thus extends - the cookbooks project.

## Issues and Problems with Compiling in general

This subsection is **not extensive**; it only provides some
information for somewhat advanced users. In other words, for
those people who already have compiled some programs more
or less successfully.

Some programs may fail due to various reasons, some of
which may be hard to debug.

For example, perhaps you may run into a "bad file descriptor"
problem one day. I did so in March 2018. The fix for me
here was to change the $PATH setting.

You can modify the $PATH setting for rbt too at runtime.

For example, to prioritize on <b>/usr/bin/</b>, you can use
this commandline switch:

    rbt --traditional-path

Of course you can also change the $PATH variable on your own
permanently - environment variables are in general available
in ENV, in ruby files.

## RBT_SOURCE_DIRECTORY

Since as of <b>April 2018</b>, there is a way to specify
another target for the <b>SRC_DIRECTORY</b>, that is - the
directory under which all other local source-archives reside.

On my home system, the source directory resides under
<b>/home/x/src/</b>.

If there is an environment variable called <b>RBT_SOURCE_DIRECTORY</b>
defined on your system, then this is the variable that we will
use across RBT for the source directory.

If there is no such variable then, by default, we will use
the setting specified by the <b>Cookbooks</b> project, if it
is available.

Do note that the variable <b>RBT_SOURCE_DIRECTORY</b> will
<b>overrule every other setting</b>, except for values
set from the commandline to RBT::Action::SoftwareManager, such as via
<b>--use-this-source-directory=</b> - so use this variable
with care. If you do not need it, I recommend to simply not
set it at all; it really only exists in the event that
there are no better alternative ways, or because the 
alternative ways may be too cumbersome to use.

If you wish to find out the current **source directory** used by
**RBT** then you can use either one of the following commandline
flags:

    rbt --source-dir?
    rbt --source-archive?

## Prefixes to use

The most common (default) prefix on most linux systems will be **/usr/**
or **/usr/local/**.

That is, if a program is compiled from source, and no explicit --prefix
is used, then most programs will default towards **/usr/local/** as
prefix. 

Sometimes **/opt/** is also used as prefix; and sometimes we can use
versioned AppDirs (Application Directories) or compile into the home
directory. The latter two ways were what the GoboLinux creators used
on university clusters.

Some convenient shortcuts exist here, in order to make working with
prefixes simpler:

    rbt m4 ULOCAL

This will use the **--prefix=/usr/local/** setting, so it is
<b>exactly</b> the same as if you would have been issuing this
instruction:

    rbt m4 --prefix=/usr/local/

So the only real benefit of using upcased ULOCAL is that you save
a few keystrokes - which is a real benefit for people who like
to type as little as possible. :-)

Do note that if the user provides a specific **--prefix=** setting
on the commandline then this setting will overrule **every**
other means of setting the target prefix at hand. The reason for
this is that RBT assumes of the user to know what he or she wants
to do - thus, the commandline must be useful for overruling 
other settings. User decisions have a higher priority than
other settings.

Let's look at another example:

    rbt m4 --opt_prefix

This will use **--prefix=/opt/**.

If you want to, you can also compile into your $HOME directory
and build up an AppDir layout; this is how **GoboLinux** has
been created actually, a long time ago:

    rbt htop --appdir-into-home-dir

If you only wish to compile into the home directory, without
using the AppDir approach, then you can use the following
invocation:

    rbt htop --compile-into-home-dir

Do note that since as of the 26.01.2019 (26th January 2019) you
can also use **RBT::CompileIntoHomeDir.new** if you wish to
compile into your home directory. There is also a bin/ executable
available, called **home_dir**, so if you wish to compile htop
into your home dir, via proper prefix, you could use:

    home_dir htop

This is functionally equivalent to:

   rbt htop --prefix=/root/

if you are the **superuser**; and if you are a regular user then of
course it will use your default **HOME_DIR** setting (usually
somewhere under **/home/**).

You can also use numbers instead of the target program, for
**home_dir**. This will use the file **installation_procedure.yml**,
and the entries in 'default'. Example:

    home_dir 1 # compiles ccache
    home_dir 3 # compiles libgpgerror

Note that **the last prefix** that was **used** for any given compilation,
is always stored on the module RBT "namespace", that is, the toplevel RBT.

You can query its value through the following ruby code:

    RBT.last_prefix_used?

This will either return nil, if no prefix was used yet (which
is the case on startup of the RBT project, for example), or
it will be a String that points to the last prefix that was
in use. That way, if other projects want to find out what
prefix was used in the RBT project, they can do so through
using the above method invocation.

Do note that using a --prefix setting is **not** mandatory,
and it can be disabled, for the current run, via **--no-prefix**
or **--noprefix**.

Example:

    rbt htop --noprefix

## Determine how many core/processors the computer has

If you wish to find out how many processors/core a target
machine has, you can use any of the following two invocation
examples:

    rbt --n-processors?
    rbt --n-cores?

The code for this resides in the method
**try_to_output_how_many_processors_this_computer_has**, which
is part of **class RBT::Action::SoftwareManager**. (This statement is correct at
the least for **October 2018**).

## Compile/Installation shell

Since as of <b>January 2018</b>, code exists that allows us to
**batch-compile programs**, via a shell-input. It also allows
us to query installation options and scan for what is
installed, where these programs are installed exactly as
well, and so forth.

This is <b>experimental</b> - do not expect for this to
work very well as of yet.

The future goal is that we can use this <b>special shell</b>
to easily install/remove any given software on any given
computer system at hand.

The <b>namespace</b> for this code currently resides
under <b>RBT::Compile::Shell</b>.

For **the available options of the compile-shell**, input
"help" for help (or just "h").

The general idea behind the compile-shell is that we can not
only batch-compile, or easily compile one program after the
other - but that we can also modify and control the compilation
process via a shell-like interface, sort of like an interface
to customize the target computer system at hand.

If you wish to change the prefix for compilation, this can
also be done, e. g. via:

    gmp trad

This would compile GMP with the traditional prefix
aka <b>/usr/</b> prefix.

If you want to find out which were the last n programs
that were updated, say n = 35, then you can do this in
the <b>compile-shell</b> interface:

    last_update? 35

The idea is to also have the compile-shell as some kind
of guide or tutor that can properly explain some cave-eats
or problems and make some "semi-seducated guesses", in
order to fix this. But this is a long-term goal - for
now, the primary purpose of the compile-shell is to aid
in <b>batch-compiling programs</b>.

Since as of March 2018, an autocompile-option exists in
the shell. This is currently unfinished but in the future
the idea is to allow us to automatically compile to the
most recent program versions, without necessiting user
input. This would then allow us to update a linux-system
to the most current program versions - stay tuned for
more improvements here in the future.

You can also edit the cookbooks, if you have the cookbooks
gem installed, from within the compile-shell, via:

    edit bluefish
    edit vim
    edit ruby

And so forth. This is only useful if you have the cookbooks
gem, since all modifications will take place on the <b>Cookbooks</b>
namespace there, rather than <b>RBT</b>.

You can query the main prefix in use via:

    prefix?

To set a new **global prefix**, do something like this:

    set_prefix=/usr/local

## Auto-resolve compile-related problems

Note that since as of September 2017, the **RBT scripts** can also
give some advice how to resolve some compile-related problems.

This is currently fairly minimal, but it will be extended 
subsequently in the future. It was also a reason why the namespace
Libtool has been integrated into RBT, as **RBT::Libtool**. This allows
us to auto-correct some libtool-related problems and keep all
libtool-related code within that namespace.

## Available programs and the corresponding program version

Every time the cookbooks gem is updated, a .html file is created
and uploaded at this location:

    http://shevegen.square7.ch/programs_version.html

This remote .html file will show which programs are registered, part of
the RBT project, and what the corresponding program versions are.

Note that you can also generate a .html page for some select programs,
via the commandline. For instance, if you wish to show ruby, python
and php, then you can use this commandline invocation:

    rbt --create-html-page-for-these-programs=ruby,python,php

The input program names should be separated via **,** and not 
include any '-' or '_' character. There are also some ways to
display the full, e. g. **KDE stack**. More on this in another
section of this README file.

To query all available programs, do:

    rbt --all_available_programs?
    installer --all_available_programs? # or use RBT::Action::SoftwareManager.

## Checking for binary duplicates

If you ever want to find out whether you have **binary duplicates**
at two different locations, such as at **/System/Index/bin/**
and at the more traditional **/usr/bin/** location, then you can
use the following method:

    RBT.check_for_binary_duplicates()

The code to this method resides in the file
**rbt/toplevel_methods/check_for_binary_duplicates.rb**.

You can also invoke this from the commandline, of course.

Usage examples for the commandline invocation:

    rbt --check-for-binary-duplicates
    rbt --binary-duplicates
    rbt --report-binary-duplicates
    rbt --report-duplicates

## Compile hooks

**Compile hooks** are defined in the **rbt gem**, in the file
**compile_hooks.yml**

Via that file you can *hook* the compilation of some programs to
the compilation of other programs.

This is somewhat similar to the chained programs feature - 
a chained program means that several programs will be
compiled one after the other, sort of like a <b>dependency
chain</b>.

For example, if you compile <b>ffmpeg</b>, and have <b>mpv</b>
installed, then a new compilation of ffmpeg will trigger the
re-compilation of mpv. This will only be done if you have
mpv installed at $PROGRAMS/Mpv though.

<b>Be careful with this functionality</b> - it can lead to problems,
in particular when compilation may fail. I do not know whether
I will keep this functionality (as of the year 2018); the
future will tell. It does add some complexity after all, and
I am not sure if it is a good idea to have this.

For now I recommend to use this feature only sparingly, if at all.
Manual control over the process may be simpler in the long run
since you are sitting in the driver seat and can decide what 
you need and what you don't need.
    
## Advanced usage of the RBT project - helpful information

This **subsection** here will explain **how to use rbt on a linux
system** - at the least how I use it.

The subsection will also give some advice and it is intended largely
for somewhat more advanced users that may already know a thing or
two about ruby and linux systems.

The whole RBT project is somewhat inspired by the **Linux from scratch**
project.

That is, people who may want to maintain their own system, the way they
want to. This is also one focus that the RBT project has - to be able
to compile any program and <b>have things work</b> as-is. The fpm
project, for example, also follows that general philosophy to some
extent as well, by the way; you can use **fpm** to create packages
specific for a particular distribution.

So what can - or should - be done on a Linux system?

Well - this of course depends on what YOU want to have and need, and what
kind of base system you may want to use. Perhaps you have full superuser
access - but perhaps you may be in a more restricted cluster-environment
where you only have full access to your home directory; the latter may be
the case if you work on an university campus site. Either way, the RBT
project attempts to be useful in both cases.

Let's first start with a **linux desktop system**, since that is the one
that I am using most of the time.

I would recommend that you first compile your own version of a **core linux
software stack**. This will help in bootstrapping immensely.

The following command should suffice - but **review this list on your own
before you use it**; as a first step, it may be simpler to compile
step-by-step, rather than all in one giant step.

    rbt make sed awk coreutils utillinux gawk m4

(Note that the above may no longer work; you may have to be more
explicit like so:)

    rbt --compile-these-programs=make,sed,awk,coreutils,utillinux,gawk,m4

I recommend that, if possible, compile as many of these programs
as a static binary. That way, if you somehow break a dependent
shared library the tools will still continue to work.

Having the application called **busybox** installed, in a static manner,
helps too - more on this on a separate section.

At any rate - once you have that set going, you should try to compile
your own version of **GCC**, ideally a recent GCC if that is possible.

This probably takes longer than the steps above and may require a few
more programs on top of that. Make sure to have enabled C and C++ as
languages for GCC, and perhaps a few more languages, should you need
them (the programming language R requires fortran, I believe, as
example).

Invocation examples:

    rbt mpfr
    rbt gmp
    rbt mpcr
    rbt gcc

Keep in mind that you can also use the LFS/BLFS instructions. They
are available via the "blfs" entry in the respective .yml cookbook
file.

<b>Glibc</b> is obviously also a target candidate that could/should
be upgraded eventually, but this is a rather delicate step - many
programs have to be recompiled if your glibc version changed.

My best advice here is to compile glibc into a versioned AppDir
(directory, such as **/Programs/Glibc/2.30/**) but to NOT symlink
it yet.

An invocation example follows here:

    rbt glibc ntrad --do-not-symlink

Or use another --prefix, such as /opt/glibc/2.30 or just
/opt/glibc or your home directory.

Since different people may want to tell RBT to compile a 
subsystem for linux, a commandline option exists to allow
us to compile the core programs here.

Invoke it like so:

    rbt --compile-base-system
    rbt --compile-basic-system

The exact programs that will be compiled may change from time to
time. If you need a commandline result of the programs that will
be compiled that way, simply append a '?' character to the above
way to compile the base system, such as:

    rbt --compile-base-system?
    rbt --compile-basic-system?

If everything works here then you should have several 
"linux" programs under the **/Programs/** hierarchy installed.

Of course **/Programs/** can be changed to any other prefix
that you may want to use. I myself make use of **/home/Programs/**
since a few years - primary reason being that I have more
control over /home/ typically. An even better prefix may be
your user's personal /home/ account. It all depends on your
use case evidently.

Do note that RBT tries to sanitize the given input a little.

For example, the following would work:

    rbt libcryptsetup

even though there is no program called **libcryptsetup** registered.
The real name is actually **cryptsetup**, but the philosophy
of RBT is to try to guess that the user just wanted to 
compile/install libcryptsetup, so rather than stopping and
notifying the user about this, the current RBT philosophy
is to try to find something that makes sense, and continue.

This may not always be wanted, but I believe the advantages
(convenience) outweigh the disadvantage (less stringent
usage policy). If both cases are equally valid then I will
add a configuration setting and a commandline flag to allow
the user to decide which behaviour is to be used - but for
the time being (February 2020) the described behaviour is
the only valid way.

## RBT project will install these executables

The RBT project will install the following executables in the **bin/**
directory:

    all_urls
    appdir
    appdir_prefix
    autosymlink
    autoupdate_this_program
    batch_validate_the_cookbook_recipes
    beautify_configure_help_output
    binary_of
    blfs
    build_detector
    chainer
    chroot_compile
    colour_make
    colour_make_install
    compile_in_traditional_manner
    compile_strategies
    compile_the_python_addons
    compile_these_programs
    compile_via_appdir_prefix_without_symlinking
    cookbooks
    copy_these_archives
    create_app_dir_skeleton
    create_html_page_for_these_programs
    create_new_cookbook
    create_pkgconfig_file
    create_registered_tags
    create_snapcraft_file
    custom_toolchain
    dual_compile
    expand_cookbooks
    extra_information
    feedback_all_available_formats
    feedback_description_of
    feedback_program_description
    find_all_archive_types
    find_alternative_archive
    find_url_for
    force
    generate_all_slack_desc_files
    gitty
    highest
    home_dir
    home_dir_without_symlinking
    homepage
    infer_build_system
    make_app_prefix
    manual_steps
    meson_appdir_prefix
    mirror
    multi_url_displayer
    ntrad
    parse_help
    paste_blfs
    query_file_association
    rbt
    rbt_action
    rbt_config
    rbt_download
    rbt_make
    rbt_test_alias
    remove_symlinks
    report_host_cpu
    report_mate_desktop_version
    report_total_size_of_all_archives
    root_prefix
    ruby_libtool
    run_make_then_make_install
    scookie
    search_for_tags
    show_all_about
    show_compile_chain
    show_configuration_options
    show_versions_of_these_programs
    simple_appdir_configure
    software_manager
    store_abbreviations
    suggest_cookbook_for
    symlink_from_to_current
    to_current
    toolchain
    uchroot
    update_all_ruby_gems
    update_entry
    update_kde_applications
    url_action

## Mate-desktop

You can try to update some of the **mate-desktop components**.

In order to do this, call either of the following variants.

    rbt --update-mate
    rbt --update-mate-desktop
    rbt --check-for-mate-updates
    rbt --check-for-mate-desktop-updates
    rbt --check-for-mate-desktop
    rbt --check-for-matedesktop

The first variant is the **shortest**, whereas the second one is
the main entry point in the **case/when** setup.

This instruction will check for new updates to the mate-desktop
releases and download them when found. Note that presently, any
more recent version is preferred, so unstable versions will often
be downloaded (since e. g. 1.19.1 is a higher version than e. g.
1.18.0).

Similar to the various KDE components (look at the KDE entry in this
file), if you wish to compile the **mate-desktop components** then
you can also use a simplified scheme, using "mate1", "mate2" and
so forth, in linear order. This will be replaced with the
registered name of the mate-desktop component.

Invocation example:

    rbt mate1
    rbt mate2
    rbt mate3
    rbt mate4

This is the very same as doing e. g.:

    rbt mate-desktop
    rbt libmatemixer

and so on. Using **numbers** may be simpler, though, as you do not
have to remember the names as-is, while still being able to use
the correct compilation order.

If you want to compile all mate-components into their own standalone
prefix via an environment value, you can use the following list:

    env_compile_via_prefix matedesktop MATE_DESKTOP
    env_compile_via_prefix libmatemixer MATE_DESKTOP
    env_compile_via_prefix libmateweather MATE_DESKTOP
    env_compile_via_prefix matemenus MATE_DESKTOP
    env_compile_via_prefix matepanel MATE_DESKTOP
    env_compile_via_prefix matenetbook MATE_DESKTOP
    env_compile_via_prefix matemedia MATE_DESKTOP
    env_compile_via_prefix marco MATE_DESKTOP
    env_compile_via_prefix matesettingsdaemon MATE_DESKTOP
    env_compile_via_prefix libmatekbd MATE_DESKTOP
    env_compile_via_prefix matecontrolcenter MATE_DESKTOP
    env_compile_via_prefix matesensorsapplet MATE_DESKTOP
    env_compile_via_prefix caja MATE_DESKTOP
    env_compile_via_prefix cajaextensions MATE_DESKTOP
    env_compile_via_prefix engrampa MATE_DESKTOP
    env_compile_via_prefix eom MATE_DESKTOP
    env_compile_via_prefix mateutils MATE_DESKTOP
    env_compile_via_prefix pluma MATE_DESKTOP
    env_compile_via_prefix mateterminal MATE_DESKTOP

## Module programs (the extended cookbook dataset)

**Module programs** refers to the ability to access all registered programs at
the **toplevel** "RBT." namespace. In other words, we can "copy" the program
names onto the RBT top-level module "namespace".

For instance, **htop** would be available at

    RBT.htop

if it is called as a "module program".

Note that this is **NOT** the default. By default the above way to call the
method .htop() on RBT would not work.

The program **binutils** would, as module program, be available at:

    RBT.binutils

And so on, and so forth. No "-" characters are allowed there, as these
are not allowed in methods written in ruby.

Note that this will return a sanitized Hash that holds all the information
required to compile the given program from source - this dataset thus
describes these programs. That information may still have to be interpreted
by a program, of course.

Simply require the necessary file for this:

    require 'rbt/module_programs'

After that, the above methods will work. Let's see a few more examples
for this:

    RBT.wayland
    RBT.ruby
    RBT.php
    RBT.gnomemimedata
    RBT.evince
    
Note that **reader methods** via '?' character are available too,
although this could be toggled. The '?' will access the datastructure
as a **Hash** rather than a specialized object.

Invoke it like so:

    RBT.htop? # => {"archive_size"=>323560, "short_description"=>"ncurses-based interactive process viewer.", "github"=>nil, "set_env_variables"=>{"LDFLAGS"=>"-ltinfow"}, "homepage"=>"http://hisham.hm/htop/", "binaries"=>["htop"], "headers"=>[], "libraries"=>[], "postinstall"=>[], "pre_make_commands"=>[], "required_deps_on"=>["glibc => 2.3.2", "ncurses => 5.6"], "tags"=>[], "pkgconfig_files"=>[], "program_path"=>"/home/x/SRC/htop/htop-2.0.2.tar.xz", "program_full_name"=>"htop-2.0.2.tar.xz" ... and so forth }

This functionality exists primarily because it may be easier for you
to use the above API calls. Internally though, the RBT project
will prefer API calls such as **RBT::Cookbooks::Cookbook.new :htop**
instead.

Note that the above works without any '-' as part of the name, so
there will not be **RBT.gnome-mime-data()** - it would be
**RBT.gnomemimedata()**.

When may you want to use this? Well, it could be used if you do want
to use a simpler API. It is very easy to remember, too: just use
"RBT." followed by the name of the program, without any '-' or
'_' characters there.

## Showing the last 750 updated programs

You can show the last updated programs, currently, by default, being
750 programs, like this:

    rbt --show-last-updated-programs
    rbt --slu

## RBT::Cookbooks::ShowConfigurationOptions

If you want to show the default configure options for a program
on the commandline, then consider making use of class
<b>RBT::Cookbooks::ShowConfigurationOptions</b>.

I have it aliased to <b>sco</b>, for convenience.

Then I can do the following, in a GCC extracted directory for instance:

    sco gcc --ntrad

This will show the following String on the commandline:

    ./configure --prefix=/home/Programs/Gcc/10.3.0 --enable-languages=c,c++,d,fortran,objc,obj-c++ --disable-bootstrap --disable-libstdcxx-pch --disable-multilib 

I can then use this string to compile GCC 10.3.0 from scratch.

I needed this so that I can more easily ad-hoc compile
programs from source as well.

Since as of February 2024 a standalone .sh file will also be
created. That way you can invoke it without having to type
anything manually. I needed this in the event that I could
not start the xorg-server but had to <b>compile LLVM</b> 
specifically.

## Auto-removing .la files

If you do not like **.la files** (libtool files), you can set the configure
option called **delete_libtool_files** to **true**. Then, if a program
has been successfully compiled into an **AppDir prefix**, such as 
**/Programs/Libcanberra/0.30/** and at the least one .la file has been
found under the **lib/** subdirectory, then these .la files will be removed.
That is, **deleted**.

That way .la files do not taint the given host system any longer (or at the
least will be removed after having been created).

If, for some reason, you rather want to **NOT** remove .la files for the
current compilation run, you can always use the following commandline
flag: 

    --keep-la-files

You can also **purge all .la files** manually, via the commandline.

**class RBT::Libtool::RemoveLibtoolFiles** is able to do. Simply pass
to it the **path** of the directory that contains these .la files, and
that class will eliminate all these .la files. (Be sure to know 
exactly what you are doing before doing so on a directory such as
**/usr/lib/** - if in doubt, always keep full backups of directories 
like this.)

During normal compilation, class RBT::Libtool::RemoveLibtoolFiles
is invoked if you compile a program with an AppDir prefix into something
such as the **/Programs/** hierarchy, as value to **--prefix**.

Informally I myself call this class a **standalone libtool killer**.

If you want to use a top-level API instead, consider the following
variant:

    RBT.remove_libtool_files_from(this_directory = '')
    RBT.remove_libtool_files_from()

Again, pass in the path to the local directory that contains these
.la files.

Since as of September 2018, the last faulty .la file will also be
registered in a local .md file. You can then let the RBT::Libtool
namespace fix the last faulty .la file via:

     rubylibtool --remove-from-file
     rubylibtool --remove-from-stored-file

The reason why this exists is because I sometimes found myself
without a running xorg-server. Copy/pasting then was difficult
with the mouse (and I dislike **gpm**). So I wanted a way how
to fix these faulty .la files without requiring the mouse -
thus the idea was to store the last faulty .la file into a local
file). The usual location for this would be at
**/Depot/Temp/rbt/libtool/** but this of course depends on
where your **temp-directory** is set at.

You can also use **rbt** directly to remove a faulty .la
file, by passing in the path, such as:

    rbt /usr/lib/libpango-1.0.la

## Working with (debian) .deb files

This subsection has been added mostly because one goal of the RBT project
is to handle .deb files in one way or another - so I wanted to collect
useful information in one place.

If you wish to create **.deb** files on your own, you may need the **dpkg-dev
package**. The following syntax should allow for this:

    apt-get install dpkg-dev

apt will handle the necessary dependencies.

## Sed operations

The binary called <b>sed</b> is well known - and often used -
on *nix operating systems. The primary reason for this is, most
likely, that <b>sed</b> is so useful and versatile. You can 
replace text very efficiently via sed.

If you look at the <b>LFS/BLFS homepage</b> (the "Linux from
Scratch" or the "Beyond Linux from Scratch" homepage), **sed**
is often used to change settings in various programs, before
compilation begins.

The **RBT project** also supports sed-related changes to programs.
The sed-operations have to be defined in the individual yaml file
that stores the instructions in how to compile a program from
source, which is part of the Cookbooks gem.

So for example, the <b>yaml file</b> for a given program simply
has a tag called <b>sed:</b>, which specifies an <b>Array</b>, and
also it specifies which sed operations are to be run, in a linear
order. The first entry is processed, then the second entry, and
so forth (if there are several entries that is).

<b>RBT</b> will then apply these sed-modifications by default.

(Internally there is even a SedWrapper class that can be used
as replacement for GNU sed - but it has a few bugs and is
mildly deprecated. Perhaps one day I may fix it, but for
the time being it will stay as it is. We will default
to GNU sed as far as RBT itself is concerned.)

If you do not need this for a given program then you can
<b>disable</b> this behaviour on the <b>commandline</b>,
you can disable it via the following commandline flag:

    rbt htop --disable-sed
    rbt htop --disable-sed-modifications

Note that there are essentially **two** ways as to how to use 
sed-operations, as far as <b>RBT</b> is concerned. One is by
simply using the binary called "sed"; and the other is to use
<b>class SedWrapper</b>. That class is unfortunately a little
buggy as of February 2018 (and beyond) for some sed-operations.

So for the time being, RBT will <b>default</b> to the system
binary called "sed". If this is not available, then RBT may
default to <b>class SedWrapper</b>, which is a pure-ruby
variant.

Most Linux systems will have a <b>sed</b> binary, so this should
work fine on these systems; should also work fine on Windows
under the WSL subsystem these days. 

If you want to query whether the internal sed wrapper is used
in general, as-is, then use the following commandline option:

    rbt --use-the-internal-sed-wrapper?

The sed-operations are run by class RBT::ApplySedOperations.
This class can also be used standalone, that is, from the
commandline. Or you can invoke them from within rbt itself.

Example:

    rbt htop --only-sed # only apply the sed-operations, then exit.

If you wish to simply run the sed-operations registered in
a cookbook .yml file, then you can invoke:

    RBT::ApplySedOperations.new
    RBT::ApplySedOperations.new :glibc
    RBT::ApplySedOperations.new :htop
    RBT::ApplySedOperations.new 'coreutils'
    
## Compiling a random program

If, for whatever the reason, you want to compile a random
program, then you can use a commandline switch such
as the following:

    rbt --random-program
    # or if you aliased "compile" onto "rbt"
    
    compile RANDOM
    compile random

## Upgrading programs through a file

You can read in input from a file, aka programs that have to be
compiled, stored in a file.

The default name for this file will be
**these_programs_can_be_upgraded.yml**, but you can also use
another name. The file has to exist, obviously.

Invocation examples:

    rbt --upgrade-from-this-file=these_programs_can_be_upgraded.yml
    rbt --upgrade-from-this-file=:default
    rbt --upgrade-from-this-file=:def

:default or :def will refer to the file **these_programs_can_be_upgraded.yml**.

The reason why a default filename exists is so that other projects
can auto-generate such a file, which we can then use for **RBT**.

## Compiling the dependencies of a program as well - handling dependencies via the RBT gem

You can <b>compile the dependencies</b> of a program if you want to,
via a commandline instruction such as:

    rbt kbreakout --compile-dependencies-as-well # verbose, but good to read, in my opinion
    rbt kbreakout --with-deps                    # shorter and easier to type
    rbt php with-deps                            # this should work as well, but using -- is recommended
    rbt gcc3 wdeps                               # similar as above
    rbt feh wdeps                                # and yet another example

Note that this will try to compile <b>all</b> the dependencies AND the
program as well, with the dependencies first, and the program that
was given as argument coming last.

This presently (as of <b>October 2018</b>) works in a brute-force manner,
meaning that it will compile the dependencies even if they are already
installed.

In the future, this behaviour may change, and code may be added to
check which dependencies are met and which ones are not met, but for
the time being, that has to suffice (the feature is thus somewhat
<b>experimental</b> right now; it has to be tested further). It may
be simpler to not use this feature for now, and instead compile
programs on an individual basis instead.

Do note that since as of March 2020 you can display all programs
that depend on another program whose name is known.

For example, if you wish to find out which programs all depend
on <b>cmake</b> then you can use the following commandline
flag:

    rbt --show-programs-with-this-as-dependency=cmake

You can use a slightly shorter variant since as of the year **2022** 
as well:

    rbt --dependencies-on=cmake
    rbt --dependencies-on=kio

Just make sure that you pass in **a registered program** as name;
otherwise rbt can not show the dependencies.

Likewise, to display all programs that depend on ruby, do this:

    rbt --show-programs-with-this-as-dependency=ruby

Since as of <b>July 2022</b> you can also calculate a 
dependency chain, via the toplevel API <b>RBT.dependency_chain()</b>.

This currently does not work that well (it will only traverse
two layers, for instance), but if you just want to get an
estimate then this may suffice.

Usage example:

    dependencies = RBT.dependency_chain(%w( php ruby python )) # => ["httpd", "libxml2 >= 2.6.31", "mysql", "sqlite3", and more ...

So you get an Array back, telling you which programs are the
dependencies of these three programs (the Array that contains
php, ruby and python).

Dependencies can be specified as <b>ranged</b>, which means that
they will be valid only under some conditions.

For example, consider the following entry which you can
find in some entries of the individual cookbooks (the corresponding
.yml files):

    glib2 >= 2.17.6

This entry means that the program requires glib2 of at least
version 2.17.6 or higher.'

The <b>Ruby Build</b> Tools will notify the user if the dependency
does not match. The default compilation mode will be to interrupt
compilation when a dependency is not met. 

## Games support

Similar as to how it has been done for KDE and mate-desktop, you
can use numbers to compile a particular game too.

For example:

    rbt game3
    rbt game5
    rbt game6

And so forth.

You can also compile all games, e. g. by doing this:

    rbt --compile-this-tag=games

Or, even simpler:

    rbt --compile-all-games

(And I also did set an alias at home, to invoke
this via **compile_all_games**).

## All binaries of every registered program

If you wish to determine the binaries of every registered program
then you can use the following **top-level API**:

    RBT.all_binaries?

This will return a **Hash**, where the keys constitute all binaries
that belong to a particular program at hand.

For example, the two binaries **xzcmp** and **xzcat** both point
to the main program **xz** (such as is available on an URL like
https://tukaani.org/xz/xz-5.2.4.tar.xz). The Hash will store
this association. Another example is the binary **xtrapproto*,
which will point towards the program called **xtra** (
"xtrapproto"=>"xtrap")

How may this functionality be useful?

This depends; if you ever want to find out to which particular
program a given binary belongs too, you could try to use this
API (or ask your package manager instead, of course).

You can also use the following **top-level API** to find out
whether a binary is registered within the RBT project or
whether it is not:

    RBT.has_this_binary? 'xzcmp' # => true

This will return a boolean value - **true** if it is registered
and **false** otherwise.

You can also gather some "statistical" information, such as
through how many binaries are registered in the RBT project,
via this method:

    RBT.report_how_many_binaries_are_registered

If you only want to see which binaries are registered in
all the registered programs of the RBT project, then you
can use this commandline:

    rbt --all-binaries?

## The mate-desktop

If you wish to compile the components of the mate-desktop,
you can try:

    rbt --compile-mate-desktop

Note that this presently (July 2018) does not handle the dependencies
correctly, so there is a very high chance of failure, unless you
already have the dependencies installed on your system.

You can also compile all of the mate-desktop into a standalone
directory, such as **/Programs/Mate/1.12/**.

Issue the following command for this:

    rbt --mate-desktop-into-standalone-dir

## Purging traditional FHS binaries and FHS libraries

The <b>RBT scripts</b> support hybrid systems, that is, systems that both
use the legacy/traditional prefix at <b>/usr</b>, and also GoboLinux-style
AppDirs such as /Programs/PROGRAM_NAME/PROGRAM_VERSION or similar layouts.
For example, php-7.2.1 would reside at <b>/Programs/PHP/7.2.1/</b> (or
<b>/Programs/Php/7.2.1/</b> - all depending on which naming scheme is
used precisely).

This may lead to having e. g. binaries duplicated, first at /usr/bin/,
and then also in the respective AppDir bin/ directory.

If you then wish to get rid of the old /usr/bin/ binary of a specific
program, you can issue the following commands:

    rbt --purge-traditional-binaries-from=xscreensaver
    rbt --purge-traditional-binaries-of=gnupg

The last entry is the program at hand, in these two examples
**xscreensaver** or **gnugp**.

Be sure to **really want to do so** before invoking this functionality.
It is mostly a convenience functionality, avoiding some manual 
removal of these binaries from the commandline.

A similar functionality exists for **libraries**. So if you want to
purge libaries at **/usr/lib/**, you can do this:

    rbt --purge-traditional-libraries-from=libva
    rbt --purge-traditional-libraries-of=libva

The relevant entries for binaries and libraries can be found in
the individual .yml cookbook - have a look at the **binaries:**
and **libraries:** entries of the particular .yml file at hand.

Since as of November 2018, an additional way exists to remove
binaries:

    rbt poppler --purge-its-binaries

This will currently (November 2018) only remove binaries found
under the **/usr/bin/** hierarchy. In the future **/usr/sbin/**
may be scanned as well, but for the time being only
**/usr/bin/** is targeted.

**Remember to do so only if you are sure that you want to do this.**

## Autoswitching python version

There is a configuration setting, stored in the file autoswitch_python.yml.

This can hold true or false (or yes or no). If set to true, then it
means that RBT will attempt to autoswitch the python version, e. g.
version 2 to version 3, if a program at compile-time depends on
the other python version.

This allows us to try to recompile the program at hand.

This will be tried only once, though, in order to avoid infinite
loops.

Do note that this functionality currently will only be used if
the RBT scripts run on "roebe", which is my home system. This may
also be enabled for all users one day in the future, but for now
it is mostly experimental on my home system. (You can of course
also enable "is on roebe"; I use an environment setting for
this.)

## The directory /System/Tags/ and registered tags in the RBT project

The directory at **/System/Tags/** can be used to store **tag-related
binaries**. Other entries, such as in a **lib/** subdirectory, will
be ignored.

For example, take the game called **wesnoth**, which may, as a
binary, reside at a path such as **/Programs/Wesnoth/Current/bin/wesnoth**.

This binary may then be **symlinked** into a path such as
**/System/Tags/Games/wesnoth**. Note that this resides under the 
**/System/Tags/** hierarchy. This functionality thus effectively allows
you to quickly look at which application types you may have installed
on your computer system. All compiled/installed games that have been
registered with the tag "game" will then reside in the subdirectory
called **Games/**. It provides an overview over the system and I think
that this is of some use, since different tags are used to describe
the various programs at hands.

If you need an overview over all registered tags, from the commandline,
try to issue this command:          

    rbt --available-tags?

This **only** works for programs that are installed into the **/Programs/**
hierarchy for the time being. (Remember that /Programs/ is not hardcoded
as such but can be changed by the user; it just happens to be /Programs/
on my system, but you could take any other name too, such as /pkg/ or
/home/programs/ and so forth.)

<b>class RBT::CleanupSystemTags</b> can eliminate stray (non-existing)
symlinks, and it is invoked from <b>class RBT::Action::SoftwareManager</b>, so the
directory at **/System/Tags/** will be guaranteed to <b>not</b> have
any stray symlinks whenever RBT::Action::SoftwareManager is run. (This
is checked in the <b>post-installation</b> part of class
RBT::Action::SoftwareManager.)

The class **RegisteredTags** can be used to register all available
tags in a .yml "database".

Simply run this file to register every available tag into a yaml file,
which we can then load if we are to search for registered tags, rather
than relying on "grep" itself. Thus, searching for tags will now be
available as well without grep - you have to run it once to register 
the available programs before you can use it.

## Guessing the build-type of a source package

You can try to guess the build type of a source directory.

First, extract the source tarball, such as for **zsh** (the
URL may be: http://www.zsh.org/pub/zsh-5.6.2.tar.xz).

Next, cd into that extracted directory and do:

  rbt --guess-build-type

This will return a String (or Symbol), such as "configure" or
"cmake" and so forth.

The functionality was needed so that RBT can **make a guess**
when information is otherwise unavailable about a given 
program at hand (e. g. not yet registered in a .yml file).
      
## Everything about symlinking

This subsection contains some information about how symlinking is
handled by the RBT project.

In general, the main functionality resides in the file
**rbt/toplevel_methods/symlink.rb**. When it comes to class
**RBT::Action::SoftwareManager then the file is rbt/compile/symlink.rb**.

Certain settings in the cookbook .yml files can be used to do
some trivial symlinking jobs, such as symlinking **lib64/** to
<b>lib/</b>. The boolean setting **autosymlink_lib64** handles this.
If you need such a symlink-job during post-installation, then
set this entry to true in the respective .yml file, such as for
the program called **poppler** and the associated **poppler.yml**
file:

    autosymlink_lib64: t

Note that presently (November 2018) this is only honoured if
we compile in an **AppDir-like manner**.

If you wish to remove all symlinks under the **/Programs/** hierarchy,
or wherever you have your own particular equivalent of this main
**Application directory** set to, then you can use the following
**commandline switch**:

    rbt --remove-all-symlinks
    rbt --remove-all-symlinks

(ry is an alias on my system towards rbt)

Why was this commandline flag added?

I needed to **test the re-creation of symlinks**, so I had to add
the functionality to also remove all symlinks prior to testing this
functionality.

## Exiting at the "make" or "make install" stage

If you wish to instantly exit when reaching the "make install" stage,
you can use the following commandline for this:

    rbt htop --stop-at-make-install-stage

Something similar exists for the "make" stage:

    rbt htop --stop-at-make-stage

## class RBT::SymlinkIntoUsrLibDirectory

class **RBT::SymlinkIntoUsrLibDirectory** can be used to symlink content
into the /usr/lib/ directory. The name for this class is fairly unwieldy,
but I needed the functionality in a specific .rb file that I could
call from the commandline.

By default, RBT::Action::SoftwareManager does **not** make use of this class, but you
can enable it via any of the following commandline flags:

    rbt gtk+ --symlink-into-usr-lib-dir
    rbt gtk+ --symlink-into-lib-dir
    rbt gtk+ --symlink-lib-dir
    rbt gtk+ --symlink-libs

Why may this functionality be useful to have?

For practical purposes it may be better to use a hybrid linux system,
e. g. one that has versioned AppDirs under /Programs/, but also keeps
symlinks at /usr/lib/. A similar approach is used by the program
**stow**, for example. Once you understand how stow works, it is 
quite easy to realize that this functionality is useful to be had,
so RBT also has the same or at the least a similar functionality.

Furthermore you can also call this class from the commandline, by
simply calling the .rb file at hand.

## Batch compiling all locally existing archives of a given program at hand

Since as of **23.11.2018** (23rd November 2018) it is possible to
batch-compile programs that reside locally, if they differ in their
versions, into an AppDir-like prefix.

This sounds difficult, so let's show an example to make this easier
to understand.

Say that you have a directory called **/home/x/SRC/libsigc++/**.
In this directory you store source archives such as the following
ones:

    libsigc++-2.10.1.tar.xz
    libsigc++-2.6.2.tar.xz
    libsigc++-2.8.0.tar.xz
    libsigc++-2.9.3.tar.xz
    libsigc++-2.99.11.tar.xz

Now you may wish to compile all these, into their proper prefix,
such as that <b>libsigc++-2.10.1</b> will end up in **/Programs/Libsigc++/2.10.1/**
and so forth. In fact, this is precisely why I added this functionality.
I needed to be able to compile different versions, including old versions,
into the corresponding hierarchy under **/Programs/**.

The commandline for this is something like:

    rbt libsigc++ --compile-all-available-local-versions
    rbt libsigc++ --all-available-local-versions

This is a convenience feature.

## Check for duplicate binaries

class RBT::CheckForDuplicateBinaries can check for binaries that
are a duplicate. By default, this class will scan for the /usr/bin/
hierarchy, but you can specify other target directories. If a 
duplicate was found, the user is notified.

That way you, as the end user, can decide how to proceed - for
example, I needed this class so I can find out which files
I can remove on a **hybrid system**.

If you have aliased this class to <b>check_for_duplicate_binaries</b>
then you can invoke it like so, with another target directory:

    check_for_duplicate_binaries --dir=/usr/local/bin/
    check_for_duplicate_binaries --pwd
    check_for_duplicate_binaries PWD # Is the same as the above ^^^ variant.

If you only want to check for the current working directory, you
can use the bin/rbt executable as well, via:

    rbt --check-for-binary-duplicates
    rbt --check-for-duplicates
    rbt --duplicates-in-pwd?

## Determine to which particular program a specific binary name belongs to

If you wish to find out to which program, e. g., the binary called
"shar" belongs to, then you can query this from the commandline
via:

    rbt --this-binary?=shar

Alternatively you can use this:
    
    rbt --binary=env

The output of these would be:

    RBT::BinaryNameBelongsToWhichProgram: The binary called `shar` belongs to the program `sharutils`.
    RBT::BinaryNameBelongsToWhichProgram: The binary called `env` belongs to the program `coreutils`.

That is the main purpose of **class RBT::BinaryNameBelongsToWhichProgram**.

Since as of June 2019, an executable exists under **bin/** that can be used for
this task, the name being **binary_of** - mostly for convenience.

Example equivalent to the two above commands:

    binary_of shar
    binary_of env

## Binaries installed by a given program

Several programs (cookbooks) that are registered in this gem
will install binaries/executables under a bin/ subdirectory.
This will usually be at the prefix /usr/bin/ or at the prefix
/usr/local/bin/, for most programs on a Linux system. How does
the RBT project handle these executables?

In the **rbt project**, in the respective .yml files, there
will be an (optional) entry called "binaries:", followed by an
Array of binaries that this program will install.

So, for example, take the file called **binutils.yml**.

Binutils will, by default, install the following **binaries/executables**
when you compile it from source (actually a few more, but we will
only show the following listing for the purpose of this document
here):

    addr2line
    ar
    as
    c++filt
    gprof
    ld
    nm
    objcopy
    objdump
    ranlib
    readelf
    size
    strings
    strip
    libiberty
    libbfd
    libopcodes

If you want to find out how many binaries are registered in the
cookbooks project so far, in total, then you can **invoke the 
bin/rbt executable** like in the following manner:

    rbt --n-binaries?

The result will then be something like this:

    RBT: There are 4102 registered binaries in all cookbook files.
    RBT: There are 5745 registered binaries in all cookbook files. # This one in April 2023, so RBT
                                                                   # tracks more and more binaries

## Suggest the content of a cookbook .yml file

If you compile a program from source successfully, say **glib**,
into an AppDir prefix such as **/Programs/Glib/2.58.1/**, then
you may use class **RBT::SuggestCookbookFor** to display the
content of a .yml file for glib. This is obviously not perfectly
accurate, but may help to get things started when you wish to
create your own .yml files.

Invocation examples from the commandline:

    rbt --suggest-cookbook-for=glib
    rbt --suggest-cookbook-for=htop
    rbt --suggest-cookbook-for=pango

**Note** that this depends on these programs being installed
in the **programs_directory?**, which on my system is equal
to **/Programs/**. See elsewhere in this document how to set
this value to some other target location.

Do note that class **RBT::SuggestCookbookFor** is also used
to indicate (to me) if a specific .yml file needs to be 
updated, in regards to libraries. As of 28th December 2018
this is experimental; but I may need to extend this eventually,
and also include headers and binaries in this. The win-win
situation here would be that the .yml files that are part
of the RBT project, may become better and more complete
in the long run.

## Querying the host system

The host system can be queried from within RBT via:

    rbt --host-system

## Inferring the build system that a particular program uses

If you look at different programs, they may use GNU configure,
meson, python setup.rb files, scons, cmake, waf and so forth -
in short, a vast array of different build systems.

The toplevel method called **RBT.infer_build_system()** can be
used to determine which build system is assumed, by RBT, to
be used. It will return a one-word **String** such as **meson**
or **configure**. Do note that this is NOT perfect - you should
not absolutely rely on this method, but for most programs this
should work fine.

The code for this resides in the file
<b>rbt/toplevel_methods/infer_build_system.rb</b>.

Some projects may use more than one build system, e. g. harfbuzz
would allow you to use either **configure** or **meson**. In
this case, what should the method **RBT.infer_build_system()**
return? It could return an Array of both build systems, or that
method could just "pick" one variant and return it. The latter
is presently (January 2019) the current default. A yaml file
keeps track of which build system is prioritized by default.

(Note that in February 2024 this is currently broken; I'll
rewrite it eventually and probably split up the functionality
into two separate methods.)

## The RBT project supports colours on the commandline.

By default, the scripts available within <b>module RBT</b> support
colours on the commandline. Colours may help put proper focus
on what is important and what is not.

If, for any reason, you do <b>not</b> want to use colours, you can
disable them either via the **configuration** (in the .yml file), or use
this toplevel API to disable colours:

    RBT.disable_colours
    RBT.disable_colors # ← This works as well, of course.

The above method-call will completely disable colours for the whole
RBT namespace.

The <b>configuration file</b> that is used to determine whether to use
colours is called <b>use_colours.yml</b>. Since not everyone may
be able to modify the .yml file, depending on the host setup (such
as in a restricted environment like at a university campus site), a
**commandline flag** is also available:

    rbt htop --disable-colours

## Disabling colours

If you dont want to display or use colours, either disable
them globally in the config.yml file (the entry is called 
`use_colours_output` there) or pass --nocolor (or --nocol or
--nocolour) on the commandline, like this:

    rbt libmemcached --nocolor
    rbt libmemcached --nocolor
    rbt libmemcached --nocolour
    rbt libmemcached --nocolours
    rbt libmemcached nocolours

Note that you can also change the colours. For this, edit the
file <b>colours.yml</b>

The above will, however had, only disable the colours for the
<b>current</b> run.

You can find out whether you use colours specifically or
not, by issuing this command:

    rbt --use-colours?

You can also <b>permanently disable the colours</b> by issuing
the following command:

    rbt --permanently-disable-colours

## Auto-updating libraries installed under a versioned AppDir

You can auto-update the "libraries:" entry in a given .yml file,
but this is usually only useful when I do so. I update the
libraries entry; and eventually I will upload a new version of
RBT.

If you, for any reason, wish to try to do so too, you can do
so via any of the following invokation ways:

    rbt --update-libraries-of=poppler
    rbt --update-libraries-for=poppler

This would then update the file called **poppler.yml**, 
after making a backup of the old **poppler.yml** file first.
(Make sure to have set the environment variable called
**IS_ROEBE** to a value of 1).

## RBT::Cookbooks::CheckForInvalidEntriesInThisCookbook

**class RBT::Cookbooks::CheckForInvalidEntriesInThisCookbook** can be
used to check that only valid entries are registered in a cookbook
file.

It can be found under the subdirectory **rbt/validation/**.

You can also batch-invoke all validations via.

    rbt --validate-entries

However had, this is mostly for me, to assure quality control;
regular users don't really need this (and it is a bit buggy
as well).
    
## The log directory

The **log directory** for RBT is the directory into which RBT can
store various files. This directory will also be used for storing
extract archives, so the name **log directory** is a bit of a
misnomer - it simply is the main directory that RBT will use to
keep stuff stored that may be useful for compilation, or created
during a compilation/installation process.

On my home system this defaults to the directory
**/home/Temp/rbt/** but for other Linux systems this
may typically be **/tmp/** or **/tmp/rbt/**.

You can also generate this log directory from the commandline via
either of the following commandline invocation ways:

    rbt --create-log-dir
    rbt --create-log-directory

## Usefulness of this project

If you may wonder how this project may be **useful** to you, well -
I think the **main target audience** will be fairly small, mostly
only more experienced users at best, in particular linux users.
These people often already know a lot about, not only linux, but
also programming - and may, ironically enough, not even have a
real need for the RBT project.

While I will continually **improve the documentation** so that novice
users can understand what the **RBT project** is doing as well,
to the point of everyone being easily able to use the project, I think
that there will not be many novice users who are even interested in
such a project in the first place these days. People just tend to
install a linux distribution and let the distribution handle everything
e. g. automatic updates and what not.

So, the RBT project should perhaps be seen as a "complementary" project
to the LFS/BLFS project (Linux from Scratch etc..) - or for smaller
linux distributions as an additional set of scripts that aid in
managing a distribution, to some extent. After all you do not have
to use all the scripts that are part of the RBT project - only pick
those that may be of benefit to your use case(s). The RBT project is
purposely not focused on only one particular mind set or strategy;
it attempts to remain flexible and useful for many different use
cases.

At the very least, the programs found in rbt project have a
**description**, so this alone can be of help to
**distribution-creators**. And there are some classes that 
focus on validation the dataset, so that people who use the
project can be reasonable sure that everything is in proper
order. For example, I can use the RBT project to autogenerate
slackware packages or GoboLinux recipes (although this may
require the removal of a few bugs here and there still).

## Obtaining the main URL for a given program 

The method **RBT.return_url1_of_this_program()** can be used
to return, as String, the remote URL to a program, also called
"url1". This entry usually denotes the path to a tarball/archive
that can be downloaded from the commandline.

If you need to determine the URL from the commandline, you can
try this:

    rbt --show-url=readline
    rbt --show-url=php
    rbt --show-url=ruby
    rbt --show-url=python

Note that you can also query whether a remote URL exists, if
you have wget available.

Example:

    i = 'https://github.com/linuxwacom/libwacom/releases/download/libwacom-1.6/libwacom-1.6.tar.bz2'
    RBT.does_this_remote_url_exist? i

## Report the status of the project

You can report the status of the project via:

    rbt --report-status

This actually means which target directories will be used by the
RBT project mostly.

## ColourMake and ColourMakeInstall

If you wish to use some colours when doing "make" or "make install"
then you can use **bin/colour_make** and **bin/colour_make_install**,
like in this way:

    colour_make
    colour_make_install

You can also tap into this code from the commandline, through the
**bin/rbt** interface, such as in this way:

    rbt --colour_make
    rbt --colour_make_install

Of course the slightly shorter variants work too:

    rbt --colourmake
    rbt --colourmakeinstall

And this as well:

    rbt --colour-make
    rbt --colour-make-install

## RBT::ShowAllAbout

You can quickly show all about a given program at hand, via the
class **RBT::ShowAllAbout**. I have aliased this class to
**show_all_about**, so then I can do:

    show_all_about ruby
    show_all_about make

This will show the content of the .yml file at hand. In order for
this to work, the Cookbooks project has to be available - and that
particular program has to exist, too. Thus meaning, that a .yml file
must exist, such as ruby.yml and so forth.

You can also invoke the above from the commandline, by issuing:

    rbt --show-all-about=ruby
    rbt --show-all-about=php

In these two cases, we would query the content of the two yaml files
called <b>ruby.yml</b> and <b>php.yml</b>.

You can also use the current working directory as "input", via:

    rbt --show-all-about-this-dir

For example, if the directory name is **/Depot/Temp/xcb-util-xrm-1.0/**,
then calling rbt via the **--show-all-about-this-dir** flag will
assume to be the same as if you would have done:

    rbt --show-all-about=xcb-util-xrm

This allows you to type a little less (and not have to think about
the name of the program at hand, since you are just using the working
directory as the "input" / argument).

## Running strip on binaries

You can use <b>strip</b> to reduce the size of the binaries in
general. This is often done on programs written in the C programming
language.

You can also invoke the command called "strip" on binaries
(**executables**), from within **rbt** too.

A simple way to do so is to first navigate to a bin/ directory,
and then invoke the following command:

    rbt --strip-binaries

But be careful **before** running the above - this will really
run "strip" on every file found in the current working directory.

Only do so when you are sure you want to invoke **strip** there.

You can also specifically strip only the binaries that belong
to a certain program, such as through:

    rbt --strip-binaries-of=htop

The **configuration option** called **use_strip** will determine
whether the RBT-project does so automatically.

If this configuration option is set to **true**, then we will
run "strip --strip-unneeded" by default.

On my home system this defaults to **true**.

## Available utility scripts of the RBT project

There is a large collection of small scripts available in the 
subdirectory called **rbt/utility_scripts/** - you can either
go into that directory to have a look, or show a summary by
calling:
  
    RBT.show_utility_scripts

Each .rb file there should have a small header that explains
what the respective .rb file will do. You may want to check
these out.

## Commandline examples for rbt

This subsection here has a few examples how I use rbt every now
and then. I will try to expand this subsection with useful
snippets in the long run, but they will not be explained in
this subsection - see for other parts of the README.me file
here for explanations, or use "rbt --help".

    rbt gdkpixbuf --home-dir --use-meson

## Show everything about a given program (show all)

There is a class called ShowAllAbout, which will simply show
the whole .yml entry of a given program.

I aliased this on my system to "show_all", so then I can type:

    show_all htop

And the content of the .yml file is shown. This is convenient
because you can quickly view the content of the yaml file
at hand.

Note that there exists another way as well, via scookie, but
scookie does not necessarily show all information, whereas
class ShowAllAbout will do so.

A commandline variant also exists via **cookbooks** itself:

    cookbooks --show-all-about=htop
    cookbooks --show-all=htop
    cookbooks --show-file=htop

Of course this works through **rbt** as well:

    rbt --show-all-about=htop
    rbt --show-all=htop
    rbt --show-file=htop

## Postinstallation steps

First, we have to define the "postinstallation phase".

The <b>Postinstall-Phase</b> will begin after compilation has 
finished. This also means that the postinstall step can only happen
if the compilation procedure was successful - at the least from
a technical point of view. We could assume that a post-install
step must always happen, but then we should not call it
post-installation step.

If you **compile a program from source**, sometimes there may be post-installation
steps that may have to occur after the program has been compiled. For example,
if you wish to **symlink** **cc** to point to **gcc**, then we need to have
this specified in the corresponding file called **gcc.yml**. The class that
handles these **postinstallation tasks** is called **class RBT::PostInstall**.

You can invoke this class manually too, if you want to - I aliased the name
"<b>post_install</b>" to point to the file in question. This I needed because
I sometimes need to perform post-installation steps through the commandline,
so it was simpler to have this a standalone, separate class.

Note that **postinstallation steps** can become quite complex, which is why
RBT tries to simplify some of the steps by using shortcuts.

For example, say that you wish to **copy several files** to another location
automatically after compilation has finished.

You can do so via the **copy_files** instruction. Let's show a specific
example for doing so:

    - copy_files { VERSION,assembly,common,eclipse,epub,epub3,extensions,fo,highlighting,html,htmlhelp,images,javahelp,lib,manpages,params,profiling,roundtrip,slides,template,tests,tools,webhelp,website,xhtml,xhtml-1_1,xhtml5 } /usr/share/xml/docbook/xsl-stylesheets-PROGRAM_VERSION

The leading ' - ' in the line above is for **YAML** and it denotes an entry that
is to be kept as an Array. The rest of this Array is quite easy to understand.
The instruction <b>copy_files</b> will simply copy several files; and these files
are denoted within the **square brackets { }**. These entries can b a file or a
directory and **RBT::Action::SoftwareManager** will correctly handle these.

The very **LAST entry** is the target location that you wish to copy these
files to, which in the above case is at
**/usr/share/xml/docbook/xsl-stylesheets-PROGRAM_VERSION**.

Note that the upcased word PROGRAM_VERSION is considered a MACRO and will
automatically be expanded to the current program version at hand, e. g.
the one that is inferred or specified within the specific cookbook .yml
file.

You can have as many postinstallation steps as you want to, in the
specific .yml file. The entry that is important here is called
**postinstall**.

Of course you can use more commands than "just" copy_files; another
example would be the command **create_pkgconfig_file**, such as
in this way.

    postinstall:
    - create_pkgconfig_file

This would automatically try to create a pkgconfig .pc file under
the **pkgconfig/** directory. The file **libmad.yml** needs this.

Some programs may require a post-install symlink step, such as
**vte**. **vte** will install a file called **bin/vte-2.91**.
It is easier to approach this file as **bin/vte** so a symlink
option is used in the file **vte.yml**.

The corresponding entry in the postinstall section of that .yml
file is any of the following two:

    symlink_binary
    symlink_this_binary

Have a look at the file called **vte.yml** for a complete example.

Various additional macros exist that can be used in this regard.

For instance, to create a directory in the app-dir prefixed
target, one can use this:

    postinstall:
    - mkdir APPDIR_INSTALLATION_PREFIX/logs/

This requires that the program is to be compiled via an
appdir prefix (such as via --ntrad or --apdir on the
commandline, to <b>RBT::Action::SoftwareManager</b>).

Since as of June 2022 you can also invoke the postinstall
action from the commandline.

Example for this:

    rbt --postinstall-for=docbookxsl
    rbt --postinstall-for=littleutils

This was added in particular because docbook is quite painful
to install.

Usually, via <b>postinstall actions</b>, you can do something like
remove certain directories or files, create new files or new
directories, handle symlinks and similar actions. It is quite
rarely needed, but at least this functionality exists
whenever you need it.

You can of course disable this behaviour if you want to, 
at run-time.

Use something like this:

    rbt htop --no-postinstall

## The $PATH variable

You can put <b>/usr/bin/</b> at the beginning of $PATH, via:

    rbt --traditional-path

This may be useful if you ever run into some PATH-related
problems, such as when you mix different paths. I have had
an issue with bash once, which is why I added the
above flag to resolve this issue.

Of course other ways may be to simply change <b>PATH</b> in
your shell, such as in <b>bash</b>:

    export PATH="/usr/bin:$PATH"

This is probably the best, as in most reliable way. Remember
that within **ruby**, PATH is available under:

    ENV['PATH']

## Autogen

Some programs require a (very old) program called "autogen".
This refers to <b>GNU autogen</b>; if you wish to read up more about
<b>autogen</b> then you could do so here:

https://www.gnu.org/software/autogen/

In the respective cookbook file, as far as the RBT gem is concerned,
support for autogen will be handled via the corresponding entry
called <b>use_autogen</b>.

If this entry is set to **true** (or **yes**), then **RBT::Action::SoftwareManager**
will <b>invoke autogen</b> for that particular program, before
trying to run <b>./configure</b>.

If you want to find out whether a program, such as "<b>pacman</b>",
requires the use of autogen, you can use this query to find
out on the commandline:

    rbt pacman --use-autogen?

The result may be output like this:

    RBT::Action::SoftwareManager: No, autogen will NOT be used for the program pacman.

To specifically enable autogen for the current invocation
run you can use:

    rbt htop --enable-autogen

Conversely, you can also specifically disable autogen, via
--disable autogen. This is only necessary in rare cases
when you do not wish to have autogen to be run. Only a
few programs will require autogen normally.

Example to disable autogen for the current invocation
run:

    rbt htop --disable-autogen

## hebang Fixing

You can fix all Shebangs of the RBT scripts by issuing:

    rbt --shebang

Use with care, though. Most users will never need to
use this functionality.
    
## Picking a specific program version

You can e. g. select a local version via:

    rbt python --2

This will only work if you have a python version available locally
in the right directory, starting with the version number **2**. 

You can also use specific versions, such as in this way:

    rbt caja 1.21.4 --trad

This latter example would require a tarball archive, a file, such
as **caja-1.21.4.tar.xz**, to exist in the main directory
for **caja/**. I tend to have multiple versions for many programs
stored locally, for added flexibility.

## Snapcraft files

Since as of **June 2018**, the **RBT project** can also autogenerate
the necessary information for an (_ubuntu_) **snapcraft file**.

The class that handles this file-creation is called
<b>RBT::Cookbooks::CreateSnapcraftFile</b>. It can be found
at the path **rbt/utility_scripts/create_snapcraft_file.rb**
within the RBT gem.

Note that the functionality is currently **very limited**; not every
aspect of a _snapcraft_ file is presently supported. But if you only
need a very simple snapcraft file, or want to auto-generate one and
then improve on it manually, then this may be useful for you to
make use of.

The **argument** to class <b>RBT::Cookbooks::CreateSnapcraftFile</b>
should be **the name of the program** that you wish to generate a
**snapcraft.yml** file for, such as "m4" or "php" or "ruby" and so
forth.

There are essentially **two different ways** how to go about creating
this snapcraft file:

(**a**) Either from within ruby code, you can do this:

    require 'rbt/utility_scripts/create_snapcraft_file.rb'

    RBT::Cookbooks::CreateSnapcraftFile.new('m4')

or, via a **toplevel API**:

    RBT.create_snapcraft_file('m4')
    RBT.snapcraft_file('m4')

or

(**b**)

from the <b>commandline</b>, do:

    cookbooks --create-snapcraft-for=NAME_OF_THE_PROGRAM_HERE
    cookbooks --create-snapcraft-for=ruby
    cookbooks --create-snapcraft-for=m4
    cookbooks --create-snapcraft-for=php
    cookbooks --create_snapcraft_for=php,ruby,m4

The last variant allows you to use a ',' separated list for
several programs.

The toplevel API exists mostly **due to convenience**; the commandline
variant may be the simplest to do so, though.

If you wish to look at the official documentation for a
**snapcraft.yaml** file, look here:

    https://docs.snapcraft.io/snapcraft-yaml-reference/4276

## Colours used by the RBT project

By default, the **rbt project** will use lots of different colours
on the commandline.

These colours are usually used on a **KDE Konsole** or a mate-terminal,
on my home system - and they work best with a **black background** in
these terminals.

If the default colours are to your dislike or do not work with your
given setup, you can always disable them via an option such as
"--disable-colours" or "--disable-colors", if you prefer the US
spelling.

Examples:

    rbt htop --disable-colours
    rbt htop --disable-colors

This would try to compile htop while disabling colour support for
the current compilation-run.

More shortcuts exist as well, such as "nocolours" and so forth.

If you want to **permanently disable the colours**, use a commandline
variant such as the following:

    rbt --permanently-disable-colours

This will modify the file '<b>use_colours.yml</b>' in the 
**yaml/** subdirectory of the RBT project, which is the file
that determines whether RBT will use any colours or not. By
default, colours will be used.

In the future I may provide colour support for users who prefer
a white or light background, but I would need a specific suggestion
and a name for this colour "scheme". Then I can add more colours
and even colour schemes for use here.

Note that you can customize the colours a little bit, via the
.yml file called <b>colours.yml</b>. The content of that .yml
file may look like this:

    information: lightblue  # 
    warn:        red        # For warnings to the user. 
    error:       red        # 
    file:        magenta    # 
    normal:      green      # The default colour to use.
    important:   brown      # cyan
    directory:   cyan       # brown
    fancy:       teal       # bold green

Not all output by the RBT project is currently handled via that
file, but most output could be customized; and eventually it
is planned to allow a user to modify <b>all</b> colours that
way. If you want to change the colours in use then you have
to modify that .yml file. That file can be found at 
<b<rbt/yaml/colours/colours.yml</b> - you may have to look 
at your local ruby installation to find out where that .yml
file will reside. For instance, on my home system that
file, once the rbt gem is installed, can be found here:

    /home/Programs/Ruby/Current/lib/ruby/site_ruby/3.2.0/rbt/yaml/colours/colours.yml

For most other users it may be in /root/.gem/gems/ or
in another directory.

## Specifying which build system to use

By default, most **.yml** files that are part of the RBT project will
make use of the **GNU configure** build system - e. g. **configure**,
**make** and **make install**. You can, on the commandline, determine
which build system is to be used; and you can also instruct
**RBT::Action::SoftwareManager** to **use another build system**.

For example, if you wish to specifically use **configure**, then
you can do this:

    rbt htop --use-this-build-system=configure

Or, if you want to use an even shorter variant, the following example
is equivalent to the one issued above:

    rbt htop --use-configure

Similarly, for **cmake** or **meson**, you could use any of the
following variants:

    rbt htop --use-this-build-system=cmake
    rbt htop --use-this-build-system=meson

## LXQt

**LXQt** is a lightweight desktop environment based on **Qt**. It may
be an alternative if **KDE5 plasma** is too heavy for a given
computer system.

You can compile individual **LXQt components**, such as in this 
convenient way, through **rbt**:

    rbt --lxqt1 # ← This refers to "libqtxdg"
    rbt --lxqt2 # ← This refers to "lxqtbuildtools"
    rbt --lxqt3 # ← This refers to "libsysstat"
    rbt --lxqt4 # ← This refers to "liblxqt"
    rbt --lxqt5 # ← This refers to "lxqtabout"
    rbt --lxqt6 # ← This refers to "lxqtadmin"
    rbt --lxqt7 # ← This refers to "lxqtconfig"
    rbt --lxqt8 # ← This refers to "lxqtglobalkeys"
    rbt --lxqt9 # ← This refers to "lxqtl10n"

and so forth.

Of course passing in the **name**, rather than these numbers,
will also work just fine. The number-based input exists
purely due to convenience.

Examples for the long names corresponding to **--lxqt1**, **--lxqt2**,
**--lxqt3**, **--lxqt4**, would be:

    rbt libqtxdg        # lxqt1
    rbt lxqtbuildtools  # lxqt2
    rbt libsysstat      # lxqt3
    rbt liblxqt         # lxqt4

(See the content of the file called **chained_programs.yml** for
the complete listing of all LXQt components.)

If you wish to compile all LXQt components, in the order specified
by the file **chained_programs.yml**, then you can use this
commandline instruction:

    rbt --compile-lxqt

You can also **manually update lxqt** via the following **top-level API**
from within ruby:

    RBT.update_lxqt

(But normally this should not be needed, as long as I maintain the
**cookbooks-dataset**, as I will already do so when a new lxqt
release is published.)

## Generate a .html file for several programs

A **.html file** can be generated via the
method **RBT.create_html_page_for_these_programs()**.

The input to this method should be an Array listing the
programs that you want to view in that .html file. Alternatively,
a String that contains these programs separated via a ',' token
can also be used.

Example:

    "php,ruby,elixir,enchant,m4"

The code that is part of the above method will generate a .html file
that shows some information about these programs, in the given
input-output order.

Commandline invocation example:

    cookbooks --create_html_page_for_these_programs="php,ruby,elixir,enchant,m4"

Why was this functionality added?

Mostly because I needed a way to autogenerate a .html file that contains
information about several programs, such as the whole kde5-set of archives.
This then generates a .html file with about ~170 kde5-related programs, and
can then be uploaded somewhere for other people to have a look at, not
unlike the LFS/BLFS project is doing already so.

In fact, if you also want to generate a .html file for the **whole
KDE toolchain**, try this:

    cookbooks --create_html_page_for_these_programs=:kde5_toolchain

You can also autogenerate a set of "homepages" for all programs,
via class <b>Cookbooks::GenerateHomepage</b>.

Either invoke the file directly (cookbooks/utility_scripts/generate_homepage/generate_homepage.rb)
or simply use this commandline instruction:

    cookbooks --generate-homepage

This will generate .html files that are somewhat similar to the LFS/BLFS
files.

## RBT::Make

RBT::Make is the main class that may be invoked for make-related actions.

It also supports some toplevel methods such as:

    RBT::Make.run

Additionally it can also be used to run "make install" or even "ninja",
the alternative build system.

This class exists primarily to make it easier to deal with the "make"
and "make install" step. Some instructions can be given to make,
such as the -j option, and it is simpler to abstract this away through
RBT directly, so that we can use it when compiling any program from
source.

## The IS_ROEBE environment variable

The **IS_ROEBE environment variable** is set to **1**, aka true, on my home
systems. When this variable exists and is set, then RBT will behave
slightly different from the default. For example, on my home system
I tend to use a hybrid system between the **/usr/** hierarchy and
AppDirs under **/Programs/**. Sometimes it is useful to symlink from
/Programs/Foobar/1.0.0/lib/* into **/usr/lib/**. If the IS_ROEBE
environment variable is set to 1, then the RBT scripts will, after
compilation has completed successfully, symlink into the
**/usr/lib/** hierarchy.

**IS_ROEBE** to a value of 1).

## Some options for the individual cookbook files explained

This section will explain some entries in a .yml file.

**run_configure**:

The option option **run_configure** is set to true by default.
If it is set to **false**, then RBT will **NOT** attempt to
invoke GNU ./configure.

This may be useful for programs that you are certain to not
have and use any **configure script**. The **man-pages** archive
at **https://www.kernel.org/pub/linux/docs/man-pages/man-pages-4.16.tar.xz**
is one such an example. It does not use any configure file, so
a configure step would fail. (Note that there may be other
ways to do the same, but for the time being, <b>run_configure</b>
seems simple and effective.)

## Xorg

The Xorg-Server is the main implementation for the graphical Linux
system. It is a display server for the X Window System. 

Some helper-code exists in the **RBT** project to make compiling
xorg-related components somewhat easier. One aspect here is that 
the RBT project has code that will easily allow you to compile
all of the **xorg-proto** programs.

To invoke that functionality, do:

    rbt --compile-all-protos

Do note that since some time, at about the year 2018 or so, the
individual protos have been bundled into the project called
**xorg-protos**.

If you want to display all <b>xorg-related entries on the
commandline</b>, do:

    rbt --tags=xorg

You can also **compile** the xorg components in an **ordered fashion**,
by making use of numbers.

Examples:

    rbt xorg1
    rbt xorg2
    rbt xorg3
    rbt xorg4

And so forth.

To batch compile most of these components, try:

    rbt xorg1..200

If you wish to compile post-xorg-server components, that is
components that ought to be installed after **xorg-server*
has been compiled/installed, then the following commandline
may be used:

    rbt --compile-xorg-server-post
    rbt --post-xorg-server

If you wish to only compile some of the addons, in particular
input-addons related to mouse, keyboard, and a few more
entries, then you can issue the following command:

    rbt --compile-mouse-and-keyboard

If you wish to compile all xorg-libraries, also called as
the **xorg-base**, you can issue any of the following commands:

    rbt --compile-xorg-libraries
    rbt --compile-xorg-base
      
## Gentoo and ebuilds

Gentoo's portage software makes use of **ebuilds**.

In theory, **RBT** can (auto)generate ebuild files but this has not been
tested sufficiently - mostly because I myself do not use Gentoo, so
someone else has to do the testing.

You can give the current implementation a try though, via:

    rbt ruby --create_ebuild_recipe
    rbt php --create_ebuild_recipe
    rbt perl --create_ebuild_recipe
    rbt python --create_ebuild_recipe

And see which parts aren't working well yet.

## YAML Engine

Ruby itself defaults to **psych** as its **main yaml engine**.

When the cookbooks project was started (before it was merged
into the RBT project), **syck** was the main yaml engine.

Since as of **January 2018**, the RBT project will default to
**psych**. If for some reason you prefer syck, then you can use a
commandline switch to denote which yaml engine is to be used.

To **enable syck**, do:

    cookbooks --use-syck

To **enable psych**, do:

    cookbooks --use-psych

This will modify the yaml file called **use_psych_or_syck.yml**.

Note that in order to use **syck**, you may have to install
the **syck gem** first, via:

    gem install syck

If you want to find out which yaml engine is in use, you can do:

    RBT.yaml_engine?

Both engines should work fine. The reason why I kept on using syck for
such a long time was mostly because I used to have some german comments
in the various yaml files, which had umlauts in non-UTF encoding. I
lateron switched to pure english instead, since it is easier for other
people, and since that time, psych works just fine for the **RBT 
project**.

Otherwise I recommend to default to psych as well, as this may make other
things simpler to work with (such as working with **UTF-8 / Unicode**).

## Permanently set to another programs directory

The default programs directory is at **/Programs/**. Programs will be
installed into that directory.

If you wish to permanently set to another directory you can use this
commandline flag:

    rbt --permanently_set_programs_dir=/pkg
    rbt --use-this-as-programs-dir=/pkg

## pre_configure_steps

The entry called **pre_configure_steps** can be used in a cookbook
.yml file. It should be an Array.

The entries listed there will be run one after the other.

A typical example for this may be like this:

    - autoreconf -vfi

A few GNU configure programs require this step, such as **hunspell**.
Have a look at the **hunspell.yml** file to find out how this is
used.

## Using the DESTDIR variable

This subsection is just an explanation of a feature of a **Makefile**.

If you wish to use a specific --prefix value for a Makefile as well
then you can use DESTDIR such as in this way:

    make DESTDIR=/Programs/Bzip2/1.0.7 install

## class RBT::Cookbooks::ReportTheseProgramsCouldBeUpdated

**class RBT::Cookbooks::ReportTheseProgramsCouldBeUpdated** has been added
in August (06.08.2019). It is assumed to report, on the commandline, all
programs that could be updated.

In order for this to work, the class will have to check several different
remote websites.

Currently (August 2019) the class will only check distrowatch.org,
but in the future this will most likely be extended, so that we can
use this to update programs from the commandline alone.

## class RBT::SimplifyRootEntries

This very specialized class will replace all root:root entries in a
file, such as a Makefile, with 0:0 entries.

The reason why this small class was added was primarily because sometimes
the host system may be partially broken, and only display 0:0 rather
than root. This may happen more frequently in a chrooted environment.

Since I was tired of makefiles then failing due to this reason, I 
created that class in August 2019.

## configure_command_to_use

This short subsection is to briefly explain the option called
**configure_command_to_use** that is available for individual
cookbook .yml files.

By default, this command can be omitted, and will then default
to **./configure** - aka **GNU configure**. This should cover
most programs.

There are some programs that do not use GNU configure, though,
in particular cmake-based projects, scons, waf, meson/ninja
and so forth. These are handled separately for the most part.

There are, however had, **also** programs that use their
own custom and unique build system, often defaulting to some
shell script. The RBT project thus has to be flexible here
and allow for custom shell scripts to be used as well.

An example for this can be seen in the file **discount.yml**
for the program **discount**. If you look at that file
you can see the following line:

    configure_command_to_use: ./configure.sh

It thus specifies that RBT::Action::SoftwareManager will make use of that
**configure.sh** shell scripts rather than the more generic
**configure** invocation run.

Some other programs use other configure_command_to_use settings;
a recursive grep can find these, should you be interested in
that.

## Some commandline options explained

If you do not want to pick up the **configure options** from
a specific .yml file, you can pass in the option
**--dont-use-configure-options** to avoid doing so.

Examples:

    rbt htop --dont-use-configure-options
    rbt glib --user-home-prefix --use-meson --no-configure-options
    rbt ruby --do-not-use-any-configure-options

This allows you to just use the "barebones" compilation mode;
may be helpful if you encounter some errors due to the 
configure options used.

## Show the last compiled programs

If you want to, for example, show the last 8 compiled programs,
then the following commandline may be useful:

    rbt --last-compiled=8

Note that you first have to have compiled some programs, as
otherwise nothing, or less than 8 programs, would be shown.

As of October 2019, another way can also be used, if you wish
to show all last compiled programs:

    rbt --last-compilations?

To show only the last compiled program, try this:

    rbt --last-compiled-program?

If you want to find out which were the last 20 programs that were
compiled, then you can use this commandline option as shown
above:

    rbt --last-compiled=20

## Speeding up the compilation

This subsection deals with <b>speeding up the compilation</b>.

<b>make</b> itself accepts a commandline option, through
-jN, where N is the number of parallel builds to use.

For example:

    make -j4

would make use of <b>four parallel builds</b>. This should
speed up compilation significantly. Do not put any
incorrect number there, such as **0** or some crazy huge
number. The **maximum number** should be the maximum amount
of processors that you have, which you can find out via
this way, on <b>Linux</b>:

    grep -c '^processor' /proc/cpuinfo

You can also obtain this from RBT itself, on the commandline,
via:

    rbt --n-processors?

Passing the option **-j4** to make means to "**spawn off 4 parallel
compiling processes**". There is actually not a limit for the
number of job slots that can be used, but as **a rule of thumb**,
one should not exceed more than twice the number of CPU cores
that the local computer system has. So if we have 4 processors,
we should never use a number higher than 8 to "make -j".

Whether this is really true or not, I have absolutely no idea.
I think the main message here is to not use any arbitrary high
number.

If you wish to append the default value to make -j, which is the
number of processors that the local computer has, then do
this, for example:

    rbt flac ntrad --speed-up-the-compilation
    rbt ruby --ntrad --speed-up-the-compilation

The important option here is <b>--speed-up-the-compilation</b>.

Note that you can also directly pass this -j option to rbt,
such as exemplified through the following **usage example**:

    rbt lame -j5

This is the same as doing "**make -j5**", by the way, during
the <b>make step</b>.

You may also define this in a cookbook file, by adding a parameter
called <b>parameters_to_make</b>. Be careful though, since this
may not always be what you may want, in particular if you use
different computers. An alternative to this may be to use a
yaml file, part of rbt, called 
<b>use_maximum_speed_for_compilation.yml</b>.

(On a sidenote, if you do not wish to use parameters_to_make
then you can use **--no-parameters-to-make** on the commandline
to disable them for the current run.)

This can also be disabled for the individual run, via:

     --do-not-use-maximum-speed
     --no-auto-speedup

More complete example how to disable this from the commandline:

    rbt lame --do-not-use-maximum-speed
    rbt xvidcore --ntrad --donot-use-maximum-speed

It seemed important to provide this option on the commandline because
the end user may **not** want to use maximum speed for compilation,
or because some other problem exists on the given computer system
that requires the end user to avoid this particular setting.

## Installing libstdc++

If you wish to install libstdc++, according to
http://www.linuxfromscratch.org/lfs/view/development/chapter05/gcc-libstdc++.html,
then the method called **RBT.install_libstdc_plus_plus()** may be of
help.

Usage example in ruby:

    require 'rbt/toplevel_methods/install_libstdc_plus_plus.rb'

    RBT.install_libstdc_plus_plus

Note that you may have to download gcc prior to invoking this method.

In November 2019, this functionality has been extended. It is now
possible to actually compile a fake-libstdc++ program into the
**/Programs/** hierarchy (or wherever you designated your programs
directory to reside on your machine).

A compile-profile has been created for libstdc++, which resides in
the file called **libstdc++.md**, as part of the **RBT project**.

Libstdc++ can be compiled into the programs directory, such as:

    /home/Programs/Libstdc++/9.2.0

It can be kept separate from e. g. **/home/Programs/Gcc/9.2.0**.

Presently the path for libstdc++ is mostly hardcoded; reason
being that it is simpler here, and my use case is only to get
it up and running quickly, anyway. 

Invocation examples:

    rbt --compile-libstdc
    rbt --compile-libstdc++
    rbt --install-libstdc
    rbt --install-libstdc++

# class RBT::ShowDescriptionAndExtraInformation

**class RBT::ShowDescriptionAndExtraInformation** is just a little
helper class for commandline-use. It can be used to quickly show
the description, and the extra_information entry from a cookbooks
.yml file.

It also uses colours, which was one major reason why I wrote it -
sometimes you need to quickly get some helpful information when
you compile something; and this class achieves precisely that.
(Keep in mind that the extra_information entry has been added
for precisely that goal: to show useful additional information
about a program, or how to get that program to compile.)

## Comments about GCC, the GNU Compiler Suite

This subsection is mostly just for commenting on random parts of
GCC. Evidently GCC is quite critical on a Linux system, together
with glibc (or musl), and the binutils.

One question that people may have is: which configure settings 
should I use for GCC? The following subsection will explain some
of these; and serve as a mnemonic.

For GCC 8.1.0 I would typically use this configure line:

    ../configure --prefix=/Programs/Gcc/8.1.0 --enable-languages=c,c++,lto,objc,fortran --enable-shared --disable-static --disable-multilib --target=x86_64-slackware-linux --build=x86_64-slackware-linux --host=x86_64-slackware-linux --disable-libunwind-exceptions --enable-bootstrap --enable-linker-build-id

Not all of these seem to be required, but evidently --enable-languages=
is very important.

## Flexbox

Until November 2019, the RBT project had <b>class RBT::Infobox</b>. This
was moved into the <b>AsciiParadise project</b> in November 2019, and
renamed to <b>Flexbox</b>.

Let's next have a look how the new Flexbox looks, on the
<b>commandline</b>:

<img src="https://i.imgur.com/NwC33Gu.png" style="margin: 1em">

(Ignore the colour bug in the middle; this may be fixed at a later
time. It's just a cosmetic issue, not a functional regression.)

The **Flexbox** can show some information about the program that is to
be compiled/installed next - or a program that you may wish to install.
It is thus only a **visual aid**, through colours, and <b>Unicode
symbols</b>, on the commandline.

For this to work, the program has to be **registered** prior, as
part of the <b>RBT project</b>.

You can specifically tell RBT to only show the Flebox, by making use of
the commandline flag called **--show-flexbox-only**.

Usage examples for this:

    rbt ruby --show-flexbox-only
    rbt python --show-flexbox-only
    rbt php --show-flexbox-only

If you do not wish to see this flexbox (as infobox) during compilation,
you can also **disable** it for the current compilation/installation
run, via a commandline flag such as **--no-flexbox**:

    rbt ruby --no-flexbox
    rbt python --no-flexbox
    rbt php --no-flexbox
    rbt sed --no-flexbox

You can also use the flexbox directly, through **bin/flexbox**
if you have the AsciiParadise installed, such as in:

    flexbox ruby
    flexbox php
    flexbox sed

Note that this may show slightly different results, as the variant
that makes use of **rbt** will also honour specific configuration
settings, whereas the **flexbox** variant will only try to make
use of the dataset stored in the respective .yml file. So if you
would like the information displayed to be more accurate, you should
use the longer variant with **rbt**; if you just need some general
information then **flexbox <name>** should do just fine. 

Since as of **May 2019** the flexbox will also show **which compiler**
will be used. Normally this will be **GCC**, but clang may also be
an option here; this information serves to be indicative of that.

Since as of **June 2019** the Flexbox will try to use Unicode symbols
on the commandline, for the outside box. This should look better than
using === and | (ASCII characters). Do note that this is work-in-progress
and may be subject change until it is consolidated.

## Status of the RBT project

The RBT project is currently (**November 2019**) in a slighty advanced
testing stage, somewhat "semi-complete". Or at the least, "sufficiently
useful" for my use cases. Presently (in November 2019) I am working
through the existing dataset and clean it up mostly, improving on it.

**Nonetheless I do not recommend anyone to use this project as of yet,
but fearless testers could test it and it may even work to some
extent**.

Please **be wary** when using the RBT project for the time being,
as there may be some bugs, but also behaviour that may be
surprising to you. The project is not yet on the same level as
e. g. **homebrew** - things will be "cleaned up" more rigorously
at a later stage.

The RBT project makes **certain assumptions**, a certain layout
of the filesystem, and so forth. While this can be tweaked by
the user, for the time being, it is best to just follow these
assumptions for now. 

## Currently compiling programs

You can query which program(s) are currently compiled by issuing:

    rbt currently_compiled?

## Show all statically compiled programs on the given computer system

If you need to show all statically compiled programs on the given
computer system then the following may be of help:

    rbt --static-overview?

Note that the checks used here are not perfect, so expect some
false positives. But for a quick overview this should do fine.
The class was added in November 2019 to the rbt project.

## Registering errors during compilation/installation

Some problems and errors may happen during compilation or
installation of programs.

These are handled internally by RBT::Action::SoftwareManager, but they will
also be registered in a module-method onto the RBT Namespace.

It is available via the following code:

    RBT.error_message?

Note that this will be reset to nil, its **default value**,
whenever a new program is compiled.

Sometimes it is not wanted to stop on errors, in particular
if the error reported is not a real error. Thus, the user
needs to have a way to overrule this behaviour, which can
be done by the following commandline flag:

    rbt --dont-stop-on-errors
    rbt --ignore-errors

This would instruct **RBT::Action::SoftwareManager** to **not** stop on
errors and instead (try to) continue.

## Pre-install actions

<b>Pre-install actions</b> are actions taken before **RBT::Action::SoftwareManager**
will invoke the configure script, or cmake invokation.

Typically the pre-install action(s) may involve calling a shell
script, such as **bootstrap**, but certain sed-operations may
also have to occur.

You can pass in which particular pre-install action should be
done, via:

    rbt htop --preinstall="sh bootstrap"
    rbt htop --prerun="sh bootstrap"

    rbt htop --preinstall="sh bootstrap, clear"
    rbt htop --prerun="sh bootstrap; clear"

As can be seen above, you can separate multiple arguments via
either ',' or ';'.

Additionally, you can use ruby classes in the preinstall setting,
such as:

    preinstall:
    - ChangeLib64ToLib.new

In the cookbook file **gcc.yml**. This will call the respective
class and invoke it (the class has to exist of course).

The reason why the support for .new was added here was because
I was tired of the shell scripts used in the LFS/BLFS scripts.

The classes-approach leads to somewhat more lines of code, but
they are easier to read and understand, in my opinion, and they
will properly inform the user as to what is done.

## class RBT::MapThisInputToThatRegisteredProgram

class **RBT::MapThisInputToThatRegisteredProgram** was added
shortly after class **RBT::QueryFileAssociation** was written.

The core idea for class **RBT::MapThisInputToThatRegisteredProgram**
is to translate (user) input into a registered program.

So for example:

    x11 → libx11
    hto → htop
    udev.h → eudev

Thus, the idea is to get any input, partial or complete, and find
the corresponding program. In the above example, the header
file **udev.h** is part of the program called **eudev**.

The idea here is to remain flexible when it comes to user
input. The user would like to compile and install something?
Then a partial input should work just fine.

Do note that this is NOT perfect. If in doubt, always input
the **full program name**, as-is, because the class will
have to make certain decisions. For example, some .h header
files have the same name across different programs, yet
class **RBT::MapThisInputToThatRegisteredProgram** will only
pick one of them (always the .first one found in the Array).

That behaviour may also be subject to change in the future,
so if in doubt, again - rely mostly on the real name. But
if you forgot the name and don't want to look up or can
not look up, you can try to leverage class 
**RBT::MapThisInputToThatRegisteredProgram**.

class **RBT::Action::SoftwareManager** also makes use of that class if the
input is not a registered program.

## Configure profiles / decorators

This subsection is about **configure profiles**, also called **decorators**
within the context of the **RBT project**.

These **profiles** (or decorators) allow you to use different configure
"profiles", depending on the given context. For example, if you wish to
build a LFS system from scratch then the configure option that you may
want to use will be different for regular compilation of **GCC**.

Thus, a profile exists called **gcc_lfs_pass1.md**. This file contains
the configure options that are normally used for the LFS build,
excluding the **--prefix** switch (because you will still be able to
decide which prefix is to be used here, on your own).

This functionality has been added to the RBT project in **June 2019** and
is still experimental - use it with care, if you decide to use it at all.

Specific examples follow next.

First, to display an overview of the available profiles, you can issue
any of the following commands:

    rbt --available-profiles
    rbt --profiles?
    
In order to use the profile for **GCC first pass**, as described in the
**LFS project**, use a commandline switch as the following:

    rbt gcc --profile=gcc_lfs_pass1

If you want to compile a minimal GCC, into its versioned AppDir prefix,
then you can use the following call:

    rbt gcc --profile=gcc-minimal --ntrad

You can also use a slightly more explicit variant:

    rbt qt --use-profile=qt
    rbt qt --use-profile=qt --trad

For some profiles you can also use a shorter variant, such as 
**--basic-gcc** for --profile=gcc-minimal:

    rbt gcc trad --basic-gcc

In order to see individual profiles based on the program name
at hand, such as **gcc**, you can use this sub-query search:

    rbt --show-this-profile=gcc
    rbt --show-these-profiles=gcc
    rbt --profiles-of?=gcc

Note that in order to display such a profile, it has to exist. If
it does not exist for the given program at hand then **RBT** will
notify the user about this fact.

## Validating the cookbook recipes and validation within the RBT project as a whole

You can invoke, from the commandline, the following:

    rbt --validate-entries

This will validate the dataset stored in the various .yml files.

It will run the test-code in the **validation/** subdirectory.

This is not so useful for casual users of the RBT project, though, but
more interesting for people who may want to contribute recipes and
such. That way they can ensure that the recipe that they have created
is valid.

If you wish to **validate all cookbook entries** then you use the
following class:

    RBT::Cookbooks::ValidateAllCookbookEntries.new
    
This class can validate all cookbook-entries. It will analyse them
in detail and report the findings on the commandline.

Again - this is not so useful for the average user, but it helps
me respectively anyone else maintaining the code and cookbook
recipes if we seek to maintain a correct, and consistent,
dataset.

## CreateAppDirSkeleton (RBT::CreateAppDirSkeleton)

The class <b>RBT::CreateAppDirSkeleton</b>, residing at 
<b>rbt/create_app_dir_skeleton/create_app_dir_skeleton.rb</b>, prepares
a program for installation under the <b>/Programs/</b> hierarchy.

Keep in mind that the target at <b>/Programs/</b> can be changed by
the user - so the rest of this paragraph should be kept in this
context. The main programs directory could be **/opt/** or 
**/pkg/** or any other target too.

The behaviour by class <b>RBT::CreateAppDirSkeleton</b> is loosely
modelled after the GoboLinux <b>PrepareProgram</b> script.
Differences exist mostly in regards to the usage pattern and
scope between these two programs; and what is reported to the
user.

Here is a link to the **GoboLinux program** called PrepareProgram:

    https://github.com/gobolinux/Documentation/wiki/PrepareProgram

In order to remain somewhat compatible to the **GoboLinux PrepareProgram**
script, options such as the following will work just fine:

    create_program --tree Foo 1.0

(Here we assume that <b>create_program</b> is an alias to the file 
<b>rbt/bin/create_app_dir_skeleton</b>).

The much simpler variant would be to do either one of the following
instead, as far as the <b>RBT project</b> is concerned:

    create_program Foo 1.0
    create_program Foo-1.0
    create_program foo-1.0

I personally prefer the <b>last variant</b>, since it is the simplest
one for me to remember - but use whichever variant you prefer. The
last one is simple for me because I can sort of copy/paste the 
directory structure through just one argument, to that class.

You can also use this from the commandline, if you would like to
do so, via <b>rbt</b> like in the following examples:

    rbt --create-program=foo-1.0
    rbt --create-program=php-7.4.3
    rbt --create-program=python-3.3.3

Do take note that CreateAppDirSkeleton may be called from some RBT scripts,
in particular **RBT::Action::SoftwareManager**. Some directories will not see that
their default symlink (called **Current**) is removed, such as gcc or
binutils, as otherwise subsequent compilation runs would not work
to the **Current** not being set properly.

You can also use the current working directory as input.

For example, say that you are in a directory called **yelp-3.30.2/**.

If you wish to make use of that directory, as the input, as if you
would have passed the above as String into RBT::CreateAppDirSkeleton.new(),
you can use either of the following two variants:

    rbt --create-program
    rbt --rcp

## Compile statistics

This subsection shows just a few random programs that were compiled in
December 2019, to show how long it took my main computer to compile
them. This machine is a fairly cheap one (x86_64, AMD A8-7600 Radeon R7,
10 Compute Cores 4C+6G, 4 CPU cores, RAM (max):  14954 MB) but it is
quite fast considering its low cost. For faster machines you will
obviously see better results.

    --------------------------------------------------------------------------------
    Name of the program         Compile time in seconds Compile time in minutes File size of the archive
    --------------------------------------------------------------------------------
     python:                          316.62 seconds  (5.28 minutes)   17836412 Kb
     rhythmbox:                       248.61 seconds  (4.14 minutes)    6410600 Kb
     ruby:                            203.06 seconds  (3.38 minutes)   11553580 Kb
     mesa:                            128.94 seconds  (2.15 minutes)   11460812 Kb
     postgresql:                       72.63 seconds  (1.21 minutes)   16050068 Kb
     php:                              60.81 seconds  (1.01 minutes)   10232208 Kb
     libogg:                           22.09 seconds  (0.37 minutes)     428696 Kb
     esound:                           20.51 seconds  (0.34 minutes)     327352 Kb
     geoclue:                          19.62 seconds  (0.33 minutes)      86376 Kb
     ncftp:                            18.14 seconds  (0.30 minutes)     420760 Kb
     audiofile:                        16.15 seconds  (0.27 minutes)     530760 Kb
     madplay:                          14.76 seconds  (0.25 minutes)     364040 Kb

## class RBT::SystemCompilePossibilities

**class RBT::SystemCompilePossibilities** is on my todo list. It 
essentially attempts to inform the user of the compile-possibilities
of the given system at hand; and will also compile "missing"
or outdated programs, optionally. So it works as some sort of
information and auto-compile tool.

It is presently (middle of **May 2018**) in a very early beta stage.

Do not consider it to be complete as of yet - I will have to test
it extensively yet. The idea is to use this as a basis for
an "automatic linux from scratch" system - or to complement
the latter.



## class RBT::PurgeIncorrectYamlDirectoriesInTheProgramsHierarchy

class **RBT::PurgeIncorrectYamlDirectoriesInTheProgramsHierarchy** can
be used to purge incorrect yaml/ directories on the system, under the
Programs hierarchy (**/home/Programs/** on my system).

To invoke this from the commandline, try either of the following:

    rbt --purge-incorrect-yaml-directories-in-the-programs-hierarchy
    rbt --purge-flawed-yaml-directories-in-the-programs-hierarchy

Do note that this class is largely unnecessary these days - it was
created as a quick ad-hoc solution, to work around the buggy
behaviour of another class, until that class was fixed.

## class RBT::CreatePkgconfigFile

class RBT::CreatePkgconfigFile was added in December 2019.

The idea is to be able to generate, on an ad-hoc basis, .pc
files (pkgconfig-files).

We can tap into the already available existing dataset of the
**RBT project**, so autogenerating the .pc files is trivial -
and sometimes necessary, for programs that do not come with
their own .pc files.

On my home system, from the commandline, I tend to invoke this
like so:

    create_pkgconfig :htop

This means that RBT::Action::SoftwareManager will be used internally, and then
generate the file **htop.pc**. (In this case create_pkgconfig
is an alias to **bin/create_pkgconfig_file**).

## More commandline examples including a brief tutorial

This subsection includes different commandline examples, to
see how the RBT project can be used. A short explanation will
be given for each invocation.

You can compile a program based on a .pc (pkg-config file)
as an input.

Example:

    rbt xau.pc # ← This is equivalent to "ry libxau"
    rbt xscrnsaver.pc --ntrad # ← This will substitute for "libxscrnsaver". You can use .pc files as input arguments.

You can also compile through registered .h header files such 
as shown in the following example:

    rbt  SMlib.h --ntrad

If you wish to see a **brief introduction on the commandline**,
issue the following command:

    cookbooks --tutorial

This tutorial is really just very short though, and not
always up-to-date - the other, more verbose, and lengthy
documentation that can be found in this file (README.md)
may be sufficiently more useful to users of the **RBT
project**.

## Using a different set of configure-options

Sometimes you may want to overrule, on the commandline, the configure
options that are to be used by a program.

You can do so via the switch **--use-these-configure-options=**.

Usage examples:

    --use-these-configure-options="--enable-shared --enable-bootstrap --enable-languages=c,c++,lto,objc,fortran --enable-threads=posix --enable-checking=release --enable-objc-gc --with-system-zlib --enable-libstdcxx-dual-abi --with-default-libstdcxx-abi=gcc4-compatible --disable-libunwind-exceptions --enable-__cxa_atexit --enable-libssp --enable-lto --disable-install-libiberty --with-gnu-ld --verbose --with-arch-directory=amd64 --disable-gtktest --disable-multilib --target=x86_64-slackware-linux --build=x86_64-slackware-linux --host=x86_64-slackware-linux"

Complete usage example:

    rbt gcc --use-these-configure-options="--enable-shared --enable-bootstrap --enable-languages=c,c++,lto,objc,fortran --enable-threads=posix --enable-checking=release --enable-objc-gc --with-system-zlib --enable-libstdcxx-dual-abi --with-default-libstdcxx-abi=gcc4-compatible --disable-libunwind-exceptions --enable-__cxa_atexit --enable-libssp --enable-lto --disable-install-libiberty --with-gnu-ld --verbose --with-arch-directory=amd64 --disable-gtktest --disable-multilib --target=x86_64-slackware-linux --build=x86_64-slackware-linux --host=x86_64-slackware-linux"

    rbt poppler --use-these-configure-options="--enable-xpdf-headers"

## File simple_appdir_configure.rb

File **simple_appdir_configure.rb** can be invoked to create an AppDir
layout program, for compilation.

I aliased this file to **appconf**. Then I can navigate to a directory,
and simply invoke **appconf** - the program will be compiled with
the default prefix as-is.

Since as of December 2019, support for cmake is possible as well, via:

    appconf --cmake

Do note that this is just a method right now; in the future this may
be changed to become a class, though.

The full path to the file is at:

    rbt/toplevel_methods/simple_appdir_configure.rb

If you need to use a build directory for this method, you can
use this:

    appconf --down

## Keeping empty directories in the /Programs/ hierarchy

By default, class **RBT::ToCurrent** and class **RBT::SymlinkThisProgram** will
remove empty subdirectories of programs that are installed in an
**AppDir-like** fashion.

This is not always wanted, though, so a commandline flag exists to disable
the auto-removal of empty directories:

    rbt feh --ntrad --do-not-remove-empty-directories

## Ensuring that all relevant directories exist

To ensure that all important directories exist you can invoke
the following method to do so:

    rbt --ensure-all-directories-exist

## class RBT::SymlinkThisProgram

**class RBT::SymlinkThisProgram** can be used to symlink an AppDir 
program into the **/usr/** prefix (or another target main prefix
in use).

You can also decide to only symlink certain subdirectories, such
as **bin/**.

Example:

    cd /home/Programs/Geany/Current # first we cd to this directory
    rnsymc --bin
    # rnsymc --bin/ ← This variant works as well.

Do note that on my computer system **rnsymc** is an alias
to the executable called **symlink_this_program**.

In January 2020 the --force commandline argument was added. This
allows us to remove the target files at /usr/bin/, before the
symlink-operation is done. Only use this when you are absolutely
certain that you wish to remove the target file(s) from there.

## class RBT::BuildDetector

**class RBT::BuildDetector** is used to determine the build type
of a given directory. This should be the extracted archive,
such as for htop-1.2.0.tar.xz, the class will expect of the
user to have changed the directory into **htop-1.2.0/**. Then
it will try to determine the build type, e. g. configure or
cmake or meson/ninja. Note that this may fail, so do not rely
too much on it. For most regular software projects out there,
this class should work fine, though.

## Installing (compiling) the dependencies of a given program at hand

The required dependencies of a given program at hand can be compiled
or installed, respectively, via the following means:

    rbt rails --install-its-dependencies

This will NOT install the program itself, though - in this case
**rails**. It is just a quick-and-dirty way to compile 
dependencies, without any further checking. All entries specified
in **required_deps_on:** will be processed.

## Compiling all programs that belong to a particular tag

**Tags** are registered in the individual .yml file of a program,
such as **htop.yml** or **poppler.yml**.

You can also batch-compile these programs, such as the instruction
of "compile all programs that belong to the tag called game":

    rbt --compile-this-tag=game
    rbt --compile-this-tag=gnome
    rbt --compile-tags=pdf

The tag that you wish to compile has to exist of course, as otherwise
no program would be compiled. It has to be registered as part of
the **.yml** file.

The functionality exists mostly as a convenience feature, say if
you wish to compile all registered games. Presently it does not
do any dependency-checking, so it is not sophisticated at all -
it was added mostly because I sometimes don't even care about
what is done, so I just want to keep on moving forward and
compile/install all programs belonging to a particular tag.

## Querying the program versions available

The commandline script **bin/show_versions_of_these_programs** can be
used to show the versions of the available programs, if the expanded
cookbook dataset is available. (If it is not then you first have
to expand it; see other parts of the document here in how to do so.)

Invocation examples:

    show_versions_of_these_programs ruby python # show the version for ruby and python 
    show_versions_of_these_programs atril caja caja-dropbox caja-extensions engrampa eom libmatekbd libmatemixer libmateweather marco mate-applets mate-backgrounds mate-calc mate-common mate-control-center mate-desktop mate-icon-theme mate-indicator-applet mate-media mate-menus mate-netbook mate-notification-daemon mate-panel mate-polkit mate-polkit mate-power-manager mate-screensaver mate-sensors-applet mate-session-manager mate-settings-daemon mate-system-monitor mate-terminal mate-user-guide mate-user-share mate-utils mozo pluma python-caja 

## .gir files

Several gtk/glib/gnome applications come with .gir files.

These files can then typically be found in this directory - at the least
in the year **2020**:

    /usr/share/gir-1.0/

As of **21.02.2020** the RBT project tracks .gir files too. In the long
run this will allow us to automatically symlink the .gir files into
the proper target, if they are installed via an AppDir prefix. But
this functionality will be added at a later time - for now we will just
gather information about these files.

As of **22.02.2020** the RBT project now allows us to symlink .gir
files into the corresponding target directory at **/usr/share/gir-1.0/**,
if the proper configuration setting is true, and if the program at
hand has at the least one .gir file and is compiled via an AppDir
prefix.

If you specifically do not want this, then use the commandline
flag called **--do-not-symlink-gir-file**. Example for this:

    rbt upower --ntrad --do-not-symlink-gir-file
    rbt gnomedesktop --ntrad --do-not-symlink-gir-files

## build_systems_priorities.yml

The file **build_systems_priorities.yml**, distributed within the
rbt gem, simply determines which build systems are to be prioritized
over others. The entry on top of that .yml file is the main one that
will be used **preferentially**; then comes the entry at second
position, then the entry at third position and so forth.

Some programs may come with more than one build system (such as
harfbuzz, in February of 2020). This allows the user to pick 
one way or the other in order to compile the program at hand.

Some of the gnome-related software was using both GNU autoconfigure
and meson, but since as of 2020, most of the new releases offer
support solely for **meson**.

The reason why the file **build_systems_priorities.yml** hadto
be created was so that we can favour one build tool over the 
other, without necessarily having to specify this up-front.
Some configure-flags are not valid in every build tool or
may have to be changed, which is why this yaml file had to
be added.

For example, GNU configure typically uses --foo=bla settings
whereas cmake will use ALL_UPCASED entries and meson will
prefer variants such as -Ddoc=false. So the rbt project
had to be flexible.

To query, on the commandline, which build system will be
prioritized you can use any of the following configure
switches:

    rbt --priorities?
    rbt --build-system-priorities?

Internally the method **RBT.infer_build_system()** can be used
to try to guess the build system, while also honouring the
priorities listed from the file **build_systems_priorities.yml**,
since as of February 2020.

This code has not been tested very thoroughly yet, though, so
expect some improvements in the coming weeks, until it works
very fine.

## Flatpak

Support for flatpak in RBT is very minimal as of right now (**July
2020**). This may be improved upon in the future - but for now, it
is just minimal.

You can typically install flatpaks in this way on the commandline:

    flatpak install --user https://flathub.org/beta-repo/appstream/org.mozilla.firefox.flatpakref

This would install firefox.

Because the above is a bit inconvenient to type, the entry **flatpak_url:**
has been added to the cookbooks part of RBT, which allows you to do
the above, through **rbt*+, in this way:

    rbt --install-the-flatpak-for=firefox
    rbt --flatpak-for=firefox
    rbt --flaty=firefox

Either variant will essentially just do the above "flatpak install --user URL"
part.

## Checking the validity of the yaml files

Within the **rbt project** code exists to ensure that the yaml files are
(mostly) **valid** and **correct**.

Code for this functionality can in general be found under the **validation/**
subdirectory. Most users will not need to use the files in that directory,
though - these scripts are mostly for developers or maintainers of the
**rbt gem**.

The code in the **validation/** subdirectory can be thought as some kind of
test-code, with the primary focus on ensuring that the cookbook yaml files
adhere to the given specification at hand - and are, in general, correct.

If you do happen to want to check the validity of the cookbook files,
then the following command can be run:

    cookbooks --validate

Cookbook entries that are invalid, will eventually be fixed - please 
be patient (or report the erroneous entry to the lead maintainer(s)).

Class **Cookbooks::ScanForIncompleteLastUpdateEntries** can be used
to ensure that the <b>last_update:</b> entries have a valid date
entry. The currently used scheme is for "DD MM YYYY" where DD and
YYYY are numbers and MM is the three-letter abbreviation for the
month at hand. For example, "22 Mar 2018" means the 22nd of
March in the year 2018. In the future I may allow for other 
formats, but for the time being this is the variant that is
to be used (I am open to add automatic display-conversion to
any other date format).

Since as of **May 2020** some code exists to check whether a .yml file
has two **url1:** entries. This is evidently incorrect; usually the
second entry should be **url2:** instead. As I ran into this problem
every now and then I decided to fix it. Now this problem has to
be corrected before compilation of that program can continue.

## class RBT::SaveTheAvailableProgramsVersions

The class **SaveTheAvailableProgramsVersions** can be used to quickly store
all available programs version into a text file (a .md file). This is only
useful on my home system though. I use it to quickly store it into the
home directory of the RBT project, before I then publish a new gem release.

The class was added in May 2020, mostly because the older class was way
too slow (a fully fledged object was instantiated upon creation of 
every new cookbook .yml file; during the rewrite, I switched to using
a hash instead, since that is evidently much faster than a large
object with lots of methods. That large object still exists, and is
used in many other places - but not for this task anymore.)


## File errors.yml

Since 2019/2020 a file called **errors.yml** has been added to the
RBT project.

The general idea is to use that file to register and describe 
**every possible problem** that may occur when someone tries to
install or compile software from source.

The file was created specifically because in the past, the
logic for handling errors was hardcoded directly into different
.rb files. This made changes a bit difficult. After a while I
also tend to forget what is all done, so I had to refresh my
old knowledge, but that was tedious too.

By having creating this file **errors.yml**, I expect to describe
all possible problems in a neutral format, which can then be
used to write specific code that implements the solution.

Another reason why the file was created was so that we can
describe in more detail which particular error happens -
and this is resolved in general. This way the RBT project
will also attempt to teach and educate people about 
compile-related problems.

## Copying archives to the current working directory

I sometimes need to be able to copy source archives to the current
working directory. One reason as to when this was necessary was
when I was about to compile a linux-from-scratch system. There I
needed to have all archives available. Another use case I have
had was to compile musl in a chrooted environment, and I wanted
to only (automatically) copy source archives that I needed, rather
than all of them.

Anyway, say that you wish to copy <b>binutils</b>, <b>gcc</b> and
ruby, so three different source archives.

You can do so via the following class:

    require 'rbt/utility_scripts/copy_these_archives.rb'
    RBT::CopyTheseArchives.new(%w( binutils gcc ruby ))
    RBT.copy_these_archives(%w( binutils gcc ruby )) # Or use this method instead; it does the same as ^^^ above.

Or invoke it from the commandline, via bin/copy_these_archives:

    copy_these_archives binutils gcc ruby

Since as of March 2024 this is also available via RBT.actions().

The entry-point would be either :copy_these_archives or just
:copy. The latter may change (or not); the former, aka :copy_these_archives,
will remain as-is. But I don't expect :copy to change either, so
you are probably well-off using the shorter :copy.

## Simple AppDir confugre

The following API:

    RBT.simple_appdir_configure()

can be used to quickly compile a program via its default AppDir
prefix.

For example, for the program htop-2.2.0, the AppDir prefix amy
be **/Programs/Htop/2.2.0/**, or a similar variant.

You can invoke this from the commandline via:

    simple_appdir_configure

This would be equivalent to these lines in a shell:

    ./configure --prefix=/Programs/Htop/2.2.0/
    make
    make install

In other words, it allows us to type less, and still compile
a program (from source) into its designated "default" 
prefix. This was the primary use case why that functionality
was added to the toplevel "namespace" of RBT - I was tired
of typing the longer prefix on the commandline. Nowadays
I just invoke an alias to that **bin/simple_appdir_configure**
instead.

You can also append -- options to it.

Example:

    cd ncurses-6.2
    appconf --enable-widec

This would pass --enable-widec to the configure or cmake script,
just as you would do normally via **./configure --options-here**
anyway.

## RBT.configure_appdir_prefix

If you wish to quickly determine which appdir prefix would
be used for **./configure**, without actually running it,
use this file:

$RBT/toplevel_methods/configure_appdir_prefix.rb

The API would be:

    RBT.configure_appdir_prefix 'htop-1.2.3'

## Showing the dependencies of a given program

class **RBT::Cookbooks::ShowDependenciesOf** can be used to show
the dependencies of a given program. The code for this functionality
resides in the file **show_dependencies_of.rb**.

API usage from within Ruby:

    RBT.show_dependencies_of(ARGV)
    RBT.show_dependencies_of('gtk+')

Invocation example from the commandline:

    show_dependencies_of gtk+

This is currently (**February 2020**) fairly slow and not very
sophisticated. I merely wanted to show that this functionality
exists. It can be improved at a later time anyway, but for
now I'll just keep it the way it currently is.

Note that this class is a bit similar to **debfoster** on
debian. The general idea here is to quickly show the
dependencies of a given program, including *derived*
dependencies.

## RBT::Linux::RenameSystemMap

class <b>RBT::Linux::RenameSystemMap</b> can be used to quickly
rename the /boot/System.map file. It is probably not very
useful to most folks, but I needed this as part of the effort
to do an automated build for LFS/BLFS.

## Slackware-specific code in the RBT project

The RBT project contains some .rb files that specifically deal
with packages on slackware.

One such class is **class RBT::Linux::Slackware::InstallThisSlackwarePackage**.

**class RBT::Linux::Slackware::InstallThisSlackwarePackage** can
be used to **quickly install a slackware package**.

**installpkg** works on slackware by default, so why was this
class created?

It was created specifically because I wanted to install a
slackware-package via an **AppDir prefix**, rather than use
the default **/usr/** prefix.

The AppDir installation can be invoked in this way:

    islackware binutils-2.26-x86_64-3.txz --appdir

Note that this was added on **18.12.2019** and has not been
tested extensively yet. I need to test it more thoroughly
before declaring this a stable feature. Also note that
**islackware** is simply an alias for the file at
**rbt/linux/slackware/install_this_slackware_package.rb** -
perhaps this should be turned into **bin/install_this_slackware_package**
eventually.

Another useful class that may be of help on a slackware system is 
**class RBT::Linux::SlackwareGenerateSlackDescFile**.

This class can be required as follows:

    require 'rbt/linux/slackware/generate_slack_desc_file.rb'

As argument to that class, provide the name of the program that
you wish to generate a slack-desc file for.

For example, for the program ruby, I do this on the commandline:

    slackdescfor ruby

where slackdescfor is an alias to that .rb file.

(Note that this only works for registered programs; the RBT project
currently does not allow for unregistered programs to generate a
slack-description. This may be extended in the future, but for now
we are limited to the some ~3600 programs that are registered in
the RBT project.)

If you ever need to parse a slackware FILELIST.TXT then you can
use code like this:

    require 'rbt/linux/slackware/filelist_parser.rb'
    RBT::Linux::Slackware::FilelistParser.new('https://slackware.nl/alien-kde/current/latest/x86_64/FILELIST.TXT')

This was written primarily so that I can compare which programs
are missing in the RBT project, but contained in slackware as-is.

If you want to create a slackware-package then you could use
this:

    require 'rbt/linux/slackware/create_slackware_package.rb'
    RBT::Linux::Slackware::CreateSlackwarePackage.new(ARGV)

Unfortunately that class has to be cleaned up, as it is a bit
buggy right now.

## GoboLinux specific code in the RBT project

The RBT project was originally created because I did not understand
the shell scripts used in GoboLinux. I still don't understand
them, by the way. :)

GoboLinux uses its own unique naming scheme. For example, 
"lib" will become "Lib", "bin" will become "Bin", 
"info" will become "INFO", "mate-desktop" will become
"Mate-Desktop" and so forth.

Additionally, all three character parts, such as "abc-", will also
be upcased.

To infer the proper gobolinux name of a program, you can use
the following code in RBT:

    require 'rbt/linux/gobolinux/gobolinux_naming_convention.rb'
    RBT::GobolinuxNamingConvention.new(ARGV)

Note that this is not quite perfect; some use cases may be
missing, but if notified, code will be aded to support
this.

If you wish to generate a new gobo-recipe, try:

    require 'rbt/linux/gobolinux/create_recipe.rb'
    RBT::Gobolinux::CreateRecipe.new('htop') # <- Name of the program should go in here.

## Copy only the headers

If you want to copy only the headers of a program, do this:

    rbt gmp only_headers
    rbt gmp --only_headers

Of course you can do so manually, but in particular on windows
I tend to be lazy, so support for this was added. Most users
rarely, if ever, will need to do so, though.

## Finding headers (.h files) of registered programs

If you need a toplevel API to determine which .h files belong
to a particular program, then you could use this:

    RBT.find_headers 'ruby'

This will show which .h files belong to that program.

## class RBT::AggregateInformationFromTheExpandedCookbooks

**class RBT::AggregateInformationFromTheExpandedCookbooks** can
be used to merge all individual cookbook .yml files into one
file that represents the whole dataset as a big hash. This
can then be used to e. g. generate SQL instructions.

## class RBT::FindAlternativeArchive

This class can be used to find a likely alternative to a given
(locally existing) archive.

On my home system I have aliased it to faa and can then do
this:

    faa $MY_SRC/gdkpixbuf/gdk-pixbuf

This functionality is useful if you wish to gather different
versions of programs locally, and still be able to compile
them via RBT.

You can also use this via a toplevel-method from within the
**RBT namespace**:

    RBT.find_alternative_archive
    RBT.find_alternative_archive('/home/x/src/gdkpixbuf/gdk-pixbuf')

## The mac-homebrew project

The rbt gem has a few code snippets that may be useful for homebrew.

For example, if you wish to find out which programs are
exclusively registered in homebrew, but not in rbt, then
you can use this toplevel-API:

    x = RBT.return_programs_that_are_exlusively_registered_in_the_homebrew_programs

## Updating all registered rubygems

You can batch-update all <b>registered rubygems</b> via:

    rbt --update-all-gems

Note that this presently will only work if you use the Cookbooks
project. I am open to extend this functionality to allow other
projects to use another dataset, though.

The boolean constant **ALSO_AUTOMATICALLY_INSTALL_THE_UPDATED_GEM**,
defined in class RBT::Action::SoftwareManager, controls whether the updated gems
will automatically be installed by the RBT project. If set to
true then RBT will not only download the respective gem, but
also install it. Since not everyone may want this, the constant
handles this case for the time being - I personally like this
constant set to true, since it saves me some keystrokes in the
long run.

If you do not want to, or can not, update all registered .gem 
entries, yet you still want to install the .gem files that are
registered, then you can use this commandline:

    rbt --install-all-rubygems

This will install all registered .gem files, in an alphabetical
manner. Dependencies will not be checked that way, but in
principle if all .gem have been properly registered in the
Cookbooks project, then this batch-gem installation should
work just fine.

## Return the file size of a program

You can quickly determine the file size of a local program
via:

    RBT.fast_return_file_size_of_this_program "htop" # => 212840

In order for this to work, the program at hand has to exist
locally, e. g. as a file like **htop-2.2.0.tar.xz**.

## Colourizing configure --help related output

If you wish to use colours for whenever you do:

    ./configure --help

then this is available via the executable at **bin/parse_help**.

The class that is doing this is called **RBT::ParseConfigureHelp**.

Simply invoke it in a directory that can respond to a
"./configure --help" output and you'll get some colourization.

This was added in January 2019, so expect this to not be quite
perfect as of yet.

You can also give, as input, an archive, such as foobar.tar.xz;
the class will extract this archive before doing a
**./configure --help** run.

## Expanding the cookbook dataset within the RBT project

By default, the individual yaml files, such as **ruby.yml**,
**python.yml**, **php.yml** and so forth, are kept in a **minimal
state**, primarily because it is easier to modify the dataset
then, via an editor.

A minimal state also means that the format is not terribly useful
by default.

For example, the setting **keep_extracted: t** is an abbreviated
form of the setting **keep_extracted: true**. (Note that this entry
means that **the archive will remain extracted after compilation has
finished**.)

The setting **use_build_directory:** can use a value of **yes**
or **y** rather than **t** or **true** for true. The RBT project
deliberately tries to remain flexible here, so multiple ways
are supported for the end user's convenience.

When such a "minimal" yaml file is loaded up, the RBT project
(submodule Cookbooks there) normally has to sanitize that yaml
file, which takes a little time. For individual files this is
not a huge deal, but sanitizing all ~3600 something .yml
files can take quite a long time, so code had to be added
to expand this dataset into its "final" variant. This final
variant is the variant that has all the information in a ready-to-use
format.

If you do not want to wait, you can speed up this process by running
the **expand** functionality early on, such as after installation
of RBT. The **expand** functionality **will expand all yaml files**
and store them in the **expanded** (correct) format. Then, when
such a yaml file is loaded up lateron, no change has to be made at
all, thus no further time has to be spent sanitizing the information
since it is already sanitized. This makes things a bit faster in
the long run.

In order to do so, you can invoke the rbt project via any of the
following **commandline flag**:

    rbt --expand
    rbt --expand-dataset 

You normally only have to do this **once**, but it is a purely
optional step. It is recommended to do so, though.

**If** the expanded dataset is not available then the **rbt 
project** may (have to) sanitize the dataset.

(Also note that the expanded dataset could be converted into
**SQL instructions**. I'll still have to add that step at
a later time, though.)

Since as of June 2019, on my home system, rbt will expand
individual entries when no expanded cookbook exists for
that given program at hand as of yet.

Since as of May 2020 the expanded cookbook dataset is
also distributed with this gem; this should allow others
to make use of the expanded and correct .yml files that
fully describe an individual recipe (cookbook). Just
look the .yml file and you should have all the data
necessary to compile the program at hand - of course
you may still need wrapper code that actually makes
use of that dataset, such as **RBT::Action::SoftwareManager** does
normally.

## KDE

Many <b>KDE components</b> (== <b>programs</b>) are registered in the
**rbt project**.

These programs usually have the registered tag **kde** or **kde5**,
in the respective .yml file. You can also search for these via
**class Cookbooks::SearchForTags**; just pass in kde or kde5 as
argument to that file/class. (I have the file aliased to "stag",
so I can just do "stag kde5" quickly.) 

You can also **batch-download** KDE components - that is, to download
them all to the local filesystem (aka to your local **harddisc**).

There are several ways how to achieve this. Either call the respective
class directly. These .rb files will reside in the subdirectory
**check_for_updates/**.

Alternatively, you can invoke them directly from the commandline
like so:

    rbt --update-kde-plasma

This will download all of the KDE5 plasma components (unless they
are already available locally).

If you wish to download the **KDE5 applications**, then you can
try this command:

    rbt --update-kde-applications

**Aliases** exist to the above:

    rbt --kde-apps
    rbt --compile-kde-apps

In general, the **rbt project** attempts to allow aliases, for
sake of convenience. The "official" entry points are usually the
longer ones though, as they are less likely to conflict with
other instructions given on the commandline. ("update kde 
applications" is more explicit than "kde apps", but the latter
is shorter, and thus may be more convenient when used on the
commandline).

To update the **KDE5 Frameworks**, do:

    rbt --update-kde-framework

To update the **KDE5 porting aids**, do:

    rbt --update-kde-porting-aids

And to then compile them, do:

    rbt --compile-porting-aids

Note that you could also use '_' **tokens** in the above invocation
examples, or omit these, so the following would work just as well:

    rbt --update_kde_porting_aids
    rbt --updatekdeportingaids
    rbt --compile_porting_aids
    rbt --compile-porting-aids

You can also query the KDE "status", that is, which variant is
currently the most recent one. Use something like this:

    rbt --kde-status

The output of the above command, on the commandline, would be something
like this:

    KDE Frameworks version:      5.50
    KDE Applications version: 18.08.1
    KDE Plasma version:        5.13.5

Or, in December 2019 on my computer system:

    KDE Frameworks version:      5.65
    KDE Applications version: 19.12.0
    KDE Plasma version:        5.17.4

This information may be useful if you go to the official KDE homepage
and want to find out whether there have been any updates recently.
Then you can compare your local version to the remote one and see
whether you may want to update the KDE components that you are
presently using.

Since as of the year **2018**, I am able to compile just about all of
the KDE components, through the **rbt project** (excluding a few 
troublemakers, in particular of the qt-chromium web-stack)).

My primary target among these KDE components is usually the
<b>KDE konsole</b> ( e. g. at 
https://download.kde.org/stable/release-service/19.12.0/src/konsole-19.12.0.tar.xz ).

If I am able to compile the **KDE konsole** then I can usually compile
the rest of KDE as well. It is a fine konsole; give it a try if you
haven't yet.

You can also use a **number** to **compile a particular KDE component**.

For example:

    rbt --kde1
    rbt --kde2
    rbt --kde3

Will compile these registered kde components. The reason as to why
this functionality exists is that it makes batch-compiling the KDE
components easier. I simply have to increment a number and compile
the KDE suite en suite, without having to remember the name (my memory
is quite bad, so using numbers is so much easier).

You can drop the **--** too, of course:

    rbt kde1
    rbt kde2
    rbt kde3
    rbt --kde4 # Using leading -- also works.

You can chain these via a range-like syntax:

    rbt kde1..100

This would compile the first 100 KDE components (if all goes well
and no errors have occurred).

You can also be more verbose, if you'd like to. The following
demonstrates this:

    rbt --kde1..kde250

The linear order of these numbers can be seen in the file
**rbt/yaml/chained_programs.yml**, under the respective KDE component
(kde-plasma, kde-applications and so forth).

If you wish to compile all of the KDE5 plasma components, you can
use either one of the following variants:

    rbt --compile-all-kde5-plasma-components
    rbt --compile-plasma
    rbt --compile-all-of-plasma

This is a convenience-shortcut. Of course the option with --batch=
also works.

To update all kde-applications you could do the following:

    rbt --update-kde-apps

To compile all of KDE, try this:

    rbt --compile-all-of-kde

If you wish to compile only the components up to (and including)
the KDE konsole, which I often do, then the following invocation
should achieve this:

    rbt --compile-all-up-until-konsole
    rbt --compile-towards-konsole # ← This is equivalent to the above ^^^.

## Aliases for program names

The **rbt project** makes use of several **aliases** to
program names. This is mostly a convenience feature, to avoid
having to type too much or remember the full real name of a
program.

Sometimes this may lead to unexpected or unwanted results,
though, such as when you want to compile program **a**, but
the <b>rbt project</b> renames the program to <b>b</b> instead.

In order to avoid this, a commandline-option exists for
the RBT project that specifically disallows this from
happening.

Invoke it like so:

    rbt sdlttf --do-not-use-cookbook-aliases
    rbt sdlttf --do-not-use-cookbook-alias  

This will specifically **disable** making use of <b>cookbook
aliases</b>. (That functionality only works if the Cookbooks
gem is used. It resides within the source of the Cookbooks
project rather than the RBT project.)

## Downloading in general and downloading a remote URL into a specific local directory

The **rbt project** has some code support for downloading a remote archive or any
other remote file into the local filesystem/directory. This functionality was added
primarily in order to aid the user in setting up the RBT project properly, in
particular when the user is before a freshly setup computer system. In other words,
to help and support "boostrapping". This is not the only use case, of course; other
use cases exist as well as to why this functionality was added to the RBT project.

If you would like to download an archive from a **remote URL** into a specific
(local) directory, you can use an **API** such as this here, from the
commandline:

    rbt htop --download-into-this-directory=/opt/bla/

The **first argument** is the registered program that ought to be used; in
this case the program called **htop**. The second argument specifies the local
directory to be used, in this case **/opt/bla/**. Obviously you could also
download first, and then **mv** the file anyway, but sometimes you may want
to do it in one go.

Note that you can simplify the above if you wish to download into the
current working directory. If this is the case, you can use
this variant instead:

    rbt htop --downloadhere
    rbt htop --dhere # This works too, if you are really laze.

This command invocation will download the htop archive into the current
working directory. Note that this almost exactly identical to <b>wget 
https://github.com/htop-dev/htop/releases/download/3.1.2/htop-3.1.2.tar.xz</b>.

If you wish to quickly download e. g. htop or another program, and wish
to do so from within ruby itself, you can use the following simpler
**toplevel API**:

    RBT.download :htop

This is treated as the very same way as if you would have used
the following API with the full URL instead:

    RBT.download 'http://hisham.hm/htop/releases/2.2.0/htop-2.2.0.tar.gz'

Thus, it is simply **a convenience feature** and works really well
in **irb*. Obviously "wget http://hisham.hm/htop/releases/2.2.0/htop-2.2.0.tar.gz"
may be even simpler on Linux-based systems, but since RBT makes
use of ruby, functionality such as this has to be included. We
want to remain flexible and succint whenever that is meaningfully
possible in regards to supporting different use cases for the
project.

You can also use the current directory as input, e. g. if you
would first create the directory htop, then cd into it, and
then invoke that method:

    RBT.download :pwd # the symbol :pwd will be treated as referring to the current working directory

This may save a little bit of typing.

The functionality can also be used from the **commandline**, through
the **bin/rbt** script, such as in the following examples:

    rbt --download htop
    rbt --download ruby
    rbt --download python
    rbt --download php
    rbt --download m4
    rbt --download=m4 # This variant works too, if you prefer to use =

This would download **htop**, or **ruby**, or **python**, respectively,
into the **current working directory**. The latter variant, with 
<b>=</b>, actually downloads into the designated source directory
so you do not even have to cd into that directory manually before.

Note that the following syntax works as well:

    rbt --download=htop
    rbt --download=ruby
    rbt --download=python

Use whichever syntax you prefer here; both ' ' or '=' work just fine.
I recommend to use the '=' all the time since the code checking this is
a bit simpler. As **argument** you can use any registered program
in the RBT project - so **over 3600 programs**.

This commandline option thus allows you to quickly **download remote
source archives**.

If you do not want to type "rbt --download" then you could
also use **bin/rbt_download** instead, aka:

    rbt_download
    rbt_download htop
    rbt_download python

Or put an alias to this to make this even shorter - which is
exactly why this oddly named executable was added.

If you wish to find out which programs can be downloaded that
way, you could try to issue this command:

    rbt --show-downloadable-programs

This will display all the names of the registered programs,
more than 3600 (so it is quite a long output; you may want
to pipe the output into **more** or **less** on Linux).

You can also download remote programs into the **proper local
directory**. The "<b>proper</b>" directory is the one where
RBT expects source archives to reside at.

Examples:

    rbt --download-into-proper-directory htop
    rbt --download-proper ruby # ← This variant is significantly shorter

On my home system, this would download
http://hisham.hm/htop/releases/2.2.0/htop-2.2.0.tar.gz into
the local directory **/home/x/src/htop/**. The exact local
position depends on your <b>SRC_DIR</b> (source directory).
See elsewhere in this documentation how the source
directory can be set for the RBT project.

Do note that since as of April 2019 we can also attempt to
download different versions of a given program. As an example, let's
say that we wish to download **glibc version 2.28**. You could
use this commandline way in order to achieve this:

    rbt --download glibc-2.28
    rbt --download glibc-2.27
    rbt --download glibc-2.26
    # and so forth

This has a few constraints, though. Firstly, the remote file
must exist at the assumed position. Second, not all file
extensions may be checked. The functionality can be improved
in the long run but for now, it is like that. (The above
should work reliably well, though).

Certain github-based URLs may also not work.

Note that different version may be supported as well,
such as:

    rbt kernel --version=2.6.30.1 download

This would then attempt to download the linux kernel version
2.6.30.1. However had, this was last tested a long time ago,
so it may be easier to stick to the other mentioned
use cases.

This has an additional chance for failure, such as wehn
the remote FTP/website changes - so it is no foolproof
mechanism.

Also note that there is a configuration option which allows
you to automatically attempt to download a missing file.

## The method try_to_find_an_alias_to_this_input_unless_the_program_exists()

The method <b>try_to_find_an_alias_to_this_input_unless_the_program_exists()</b>
can be used to find an alias name to a given input.

For example, the input **xorgser** will be converted to **xorgserver**. This
will help us compile programs, since abbreviations are available for all
the registered programs in the **RBT project**.

If you need to determine whether something is a registered abbreviation,
as far as the RBT project is concerned, you can use the following
toplevel method:

    RBT.is_this_a_registered_abbreviation?(i)

## The constant called FILE_ABBREVIATIONS and abbreviations for the RBT project

**FILE_ABBREVIATIONS** is a constant pointing to a file that
keeps the abbreviations to the registered programs. Abbreviations
in this context are words such as "**ph**", which may stand for
"**php**". So in short: **an alias** to a longer name.

The above example may be useful if you wish to compile PHP
on the commandline: rather than typing "php", you can type
"ph" and it should still work.

The net gain in this specific example is little, but consider a
longer name, such as **xorg-server**.

You could compile it via:

    rbt xorgser

That is more convenient, isn't it?

Do note that **tab-completion support** for bash and zsh also exists
to enable a functionality like this, but I wanted to be able to find
shorter aliases **within** the ruby code itself too, so that a
toplevel-method API such as the following one may also work:

    RBT.compile 'php'     # For php.
    RBT.compile 'ph'      # For php, too.
    RBT.compile 'xorgser' # For xorg-server.

All variants should work fine. The longer variant, while it is more
typing work, is **the recommended way**, though. This is primarily
because that way you can **avoid ambiguity**, since you fully
specify the name as-is; the RBT project will not have to guess
in these cases.

(Note that since as of 2020, the main abbreviation for 'ph'
is 'physfs'. So do not rely too much on these abbreviations -
they are determined automatically, so the shorter the input,
the less likely it may be that you find a particular 
program, **IF** many other programs are already defined.
The more choices you have, the more possibilities exist
for these abbreviations too. Compare the number of
abbreviations by 100 different words, as opposed to
10000 different words - the latter will have many more
abbreviations.)

The usual residency of the file pointed at via the constant
FILE_ABBREVIATIONS resides at:

    rbt/yaml/abbrevations_to_the_programs.yml

In short: the reason why this file exists is so that we can
**use abbreviations**, if we wish to compile programs from
source.

Do note that additionally the configuration flag **use_abbreviations**
must be set to true; otherwise the RBT project will not make
use of abbreviations.

## Repackaging archives and Packaging archives

You can quickly repackage archives, such as **foobar-1.0.tar.gz**
into **foobar-1.0.tar.xz**, by issuing this command:

    rbt --repackage=foobar-1.0.tar.gz

To quickly create an archive from a compiled and installed
AppDir, try something like this:

    rbt --package-this-app-dir=htop
    rbt --package-this-appdir=htop
    rbt --package-appdir=htop

## Optimizations for compilation

This subsection will be expanded in the future.

If you wish to compile via -O3 optimization, you can
pass it in:

    rbt gnomedesktop --O3
    rbt gnomedesktop --speedy

This may lead to faster program execution, at the expense of 
slightly larger program size - say +20% or so increase in
size, depending on the program at hand.

In principle this can be combined with --static (to enable
static compilation), but not every program can be compiled
statically.

## Installing/Compiling the various xcb components

If you, like me, get tired of installing the various xorg-related
**xcb components** then the following command should be of help
here:

    rbt --compile-xcb-components

This will install the xcb-components in the correct order
(actually it will compile the xcb-components).

Aliases exist for this:

   ry --compile-the-xcb-components
   ry --compile-all-the-xcb
   ry --compile-xcb

## Perl

In order to **compile perl**, you could simply issue the following command:

    rbt perl

If you wish to install the various registered perl-addons, you can
try to use the following command:

    rbt --compile-perl-addons

(Unfortunately there is some bug, where the installation stops after
the first installed perl program. I will have to investigate this at
a later time; this notice has been written in 20.04.2019).

Keep in mind that if the above --flag does not work for you, you
can always try to install these programs individually.

## class RBT::QueryFileAssociation

Sometimes you may wish to find out to which particular program
any file belongs to - for example, the header called
**stdio.h**.

class **RBT::QueryFileAssociation** does answer this.

Usage example:

    require 'rbt/utility_scripts/query_file_association.rb'

    RBT::QueryFileAssociation.new(of: 'libc.so')
    RBT::QueryFileAssociation.new(of_this_file: 'vlc')
    RBT::QueryFileAssociation.new(of_this_file: 'stdio.h')

Any registered input will do fine, be it a binary, a library
or a .h header file. The file must be registered as part of
the RBT project, though. If that condition is met then this
class will report, on the commandline, more information as
to which program this input-file belongs to.

Do note that before January 2020, multiple associations were
not reported properly. Since as of January 2020, if for
example a .h header file belongs to several programs then
this information will be properly displayed on the
commandline. That way if a header file, such as stdio.h,
belongs to different programs, all of them will be
reported as well.

Do note that since as of February 2020, querying .gir files
is also possible.

Example:

    query_file_association Gdk-3.0.gir

Currently (**23.02.2020**) not all .gir files are registered,
but expect more .gir files to be added to the RBT project
in the near future.

Support for .m4 files was added in June 2020.

Usage example:

    what ltoptions.m4

(**what** is my alias towards **query_file_association**.)

## Using /usr/lib64/ as the libdir target for configure

If you wish to use /usr/lib64/ as the libdir target for
the current invocation run, you can use **--libdir64**
as in:

    rbt libgpgerror --libdir64

This is essentially equal to:

    rbt libgpgerror --libdir=/usr/lib64

So we just save a bit of typing work. Note that --dir64
also works, as slightly shorter variant.

Example:

  ry libgpgerror --dir64

## Disable adding the shell script error line

By default, the configure scripts will try to make use of
**2>&1**. That is, this is normally appended.

Not every user may want this by default, though, so it
can be disabled for the current invocation run, via
**--do-not-append-no-error**, like in this way:

    rbt coreutils --static --do-not-append-no-error

## Generating shell scripts / shell recipes

You can generate standalone .sh (shell scripts).

Examples:

    rbt sed        --generate_shellscript
    rbt python     --standalone
    rbt gnunetgtk  --create_shellscript
    rbt wxwidget   --shellscript

This will generate .sh files that are, in theory,
usable to just compile a source archive via a
shell script.

That way you don't even need ruby (in principle)
on the target machine.

Unfortunately the code is not perfect; the extract
function for the shell code currently (June 2020)
does not work properly, so you may have to write
your own function in shell/bash that works here.
But eventually I may fix this, and then also
add support for cmake, meson and so forth.

I rarely use shell scripts these days, though -
ruby is so much more powerful, so this option
is mostly a legacy option really.      

## Use a local file for configure-options

Usually when I compile a program from source, I am
using a graphical interface - typically the xorg-server.

This is convenient as I can then make use of the KDE
Konsole in particular.

However had, sometimes I do not have a running
xorg-server available - and this makes compiling
more difficult than normal. In particular when
I break xorg, then I may end up without a
working xorg-server, and thus without a working
graphical user interface. This is really annoying.

As a tiny "workaround", I made it possible to 
read instructions to GNU configure based
scripts via a local file.

Consider these two invocation examples:

    rbt gcc --use-instructions-from-this-file=/Depot/foobar.md
    rbt php --trad --use-this-file=/Depot/j/foo.md

These instructions would read in the dataset from these
two files, and treat them as the main configure-options.

That way you can quickly edit/modify local files if you
wish to use different configure options, rather than
have to rely on the hardcoded values that are part of
the default yaml files for a given program. This was
the primary use case, because sometimes you may wish
to, for example, compile another GCC with different
options, so this option can then be useful in such
a case. 

## Extract to and the Temp directory

Archives such as **foobar-1.0.tar.xz** or **barfoo-2.0.zip** will first have
to be extracted before they can be compiled. The **RBT** project thus
needs to have this functionality; and you, as a prospective user, also
need to have (some) control over this behaviour, in particular if you
wish to **extract to a specific directory**.

The file <b>temp_directory.yml</b>, which is part of RBT's configuration,
designates the main directory to which RBT will extract an archive.

For example, if the content of this yaml-file is **/tmp/** then RBT
would extract archives into that directory. (Actually, RBT will
extract into the **rbt/** subdirectory, in order to not make a mess
of the target temp-directory; so a value of **/tmp/** would really
mean **/tmp/rbt/** instead.)

It is permissible and possible to use $FOO variables inside of that
yaml-file, to designate and make use of shell variables. For example,
I may use the variable called $TEMP as the content of the file
<b>temp_directory.yml</b>, which in turn points towards
<b>/Depot/Temp/</b> on my home system. This is the very same as if
you would have used **/Depot/Temp/** as the content of this yaml-file,
so the only net-gain is that you may not have to hardcode the same
path several times; instead, you can re-use shell variables that
way.

If you want to extract into the **home directory** instead, then
you can use any of the following commands to do so permanently:

    rbt --permanently-extract-to-home
    rbt --permanently-extract-to-home-dir
    rbt --extract-to-home

You can also specify a specific target directory that is used
for the extraction step of a compilation that you are about
to start.

Consider the following example:

    rbt htop ntrad --use-this-temp-dir=/opt/foobar_create_it 

This would use the directory **/opt/foobar_create_it** for
extracting the source archive.

I needed this functionality in particular because I sometimes
have to do two compilation runs at the same time, e. g. for
different target prefixes - so it made sense to also use a
**different* **temp dir** for extraction.

If you want to, or have to, you can also designate another
temp-directory, permanently, via the following **toplevel
API**:

    RBT.permanently_set_temp_dir
    RBT.permanently_set_temp_dir '/tmp/rbt/'

You can also quickly extract any local archive via this
**toplevel method**:

    RBT.extract()

The latter method can also be used on the commandline, through
**bin/rbt** via:

    rbt --extract htop

This will first **download htop** and then extract it, in the
**current working directory** (**cwd**).

You can also quickly extract a locally existing archive,
such as **bison-3.2.4.tar.xz**.

    rbt --extract-this=bison-3.2.4.tar.xz
    rbt --extract=zenity-3.42.1.zip

(This should also work on windows, since as of <b>June 2022</b>
if <b>7z</b> has been installed.)

Another functionality is that you can change the directory as to
where source archives will be extracted to, **permanently**, from
the commandline. Normally a good directory for this may be
**/tmp/** but you can of course choose another directory, too. I
tend to use /home/Temp/ as my temp-directory - to me it feels
cleaner than /tmp/ but your mileage may vary.

Examples:

    rbt --permanently-set-temp-dir-to=/user/bioinf4/Temp/
    rbt --permanently-set-temp-dir=/user/bioinf4/Temp/
    rbt --permanently_extract_to=pwd
    rbt --permanently_extract_to=/Depot
    rbt --permanently_extract_to=/tmp
    rbt --permanently-set-temp-dir=/user/bioinf4/Temp/
    rbt --permanently-set-temp-dir-to=/user/bioinf4/Temp/
    rbt --use-this-temp-dir=/Depot/
    rbt --use-temp=/Depot

These are all equivalent.

If you wish to extract to, for example, the target location
**/opt/test** just for the current run, then the following
command should suffice:

    rbt htop --extract-to=/opt/test

Sometimes you may not want to even think about a specific
name and just wish to use any random name for a directory.

In order to do so, you can use any of the following 
ways to invoke rbt:

    rbt php --random-temp-dir
    rbt php --random-dir
    rbt php --random-temp
    rbt php --rdir

This will use a temp-directory such as **/home/temp/rbt/foeghe/**.

Do note that you can also quickly extract the tarball of a
registered program into the current working directory.

For example, say you cd to /tmp:

    cd /tmp

Next, you want to extract **htop**:

    rbt --extract htop

This should work fine if you have htop downloaded (**ry htop --download**
should work for this as well).

The reason as to why the ry --extract functionality was added
is mostly due to convenience alone.

To quickly extract into the current working directory, use
**--extract-here** such as in:

    rbt gimp --extract-here

This would extract into the current working directory, if the
archive has been downloaded into the default working directory
before. I use this option to quickly work with the source 
archive as-is, without having to manually extract it.

## Busybox

Having the application called **busybox** installed, in a static manner,
is quite useful.

I recommend to have a **working version of busybox** available on the
local computer system, as that may help in recovering in the event
that something has gone awry.

To compile busybox, try this:

    rbt busybox

Make sure to compile busybox **statically**. That way you become less
dependent on .so files being available, in the event that you somehow
manage to break your system (which I typically used to do).

In **November 2019**, a **default configuration** was added for
busybox, **allowing static linking**. The name of that file is 
**static_busybox_config.md** and it can be found under the
**profiles/** directory of the rbt gem:

    rbt/misc/profiles/static_busybox_config.md

This should allow you to quickly install a static version of busybox.

I needed this because I did not want to manually run "make menuconfig"
or "make config", since I only needed the static version; and the
rest is fine either way for me.

For a static compilation of busybox, this should work fine by
default:

    rbt busybox ntrad

At a later time more flexibility may be added here, but for the
time being (November 2019) this has to suffice.

## Different package managers

The **RBT project** is a toolset project. This means that:

(a) it should be able to seamlessly integrate in a given system
and making native use of the package manager in use by that
system.

(b) it should also provide package-manager functionality.

Both parts are quite a lot of work to implement, so don't
expect this to happen soon. Some baby steps have been done.

For example, for (b), the dataset for all the ~almost 4000
registered projects in RBT are distributed with the RBT
gem as well, in the **rbt/yaml/expanded_cookbooks/** 
directory. Furthermore, this information is also stored
in some .yml files, which means that you can easily
query the file association of a registered program.

At any rate - let's proceed to (a) now. The following
subsection will continue as time passes by (that is,
when I have more time to add new content).

Let's begin with the package manager for debia, **dpkg**.

**dpkg** requires header files such as **md5.h**.

I am not quite sure where this .h file typically resides.

Archlinux uses **pacman** as package manager. Installing pacman
is quite simple:

    rbt pacman trad

You may need **libtar** too:

    rbt libtar trad

What to do next afterwards?

Create a **pacman.conf file** or copy it from somewhere. Add
repositories that you may want to have.

Then do:

    pacman -Syyu

**Void** uses another package manager, called **xbps** (the
**X Binary Package System**).

It has not yet been added into rbt, but once it is, this part
will be modified, to allow simple compilation/installation of
**xbps**.

## Dual Compile

In the file rbt/toplevel_methods/dual_compile.rb there is
code that will first compile a program into the /usr/ prefix,
before it will then compile that program into its AppDir
prefix as well, such as **/Programs/Htop/2.2.0/**.

I needed this functionality because sometimes I use a hybrid
layout, so it makes sense to keep a "backup" at the
appdir place.

## Colourizing output

In general, **--disable-colours** or **--disable-colours** or
**--nocol** will **disable colour output**. The rest of this
subsection here explains some of the colour-settings used by
RBT.

By default, RBT will attempt to colourize output from some
external programs, in particular "make" and "make install".

The class **RBT::ColourizeParser** will handle most of this.
It can also be used in standalone scripts such as ColourMake
or ColourMakeInstall, which will run a coloured variant of
"make" and "make install", respectively.

The idea behind the colours is to mostly make it easier to detect
what is going on; and in particular where errors may occur. I
personally found the colours to be helpful, but it is indeed VERY
colourful, which is why a commandline option exists to disable
the colours.

The colours are presently hardcoded, but in the future we could use
different profiles and then let the user decide which (other) profile
to use. But I'll extend this part only when other people may want
to have this - for now, the default colour "profile" has to suffice.

If you wish to **permanently disable the colours** for the RBT
project, then you may use the following command:

    rbt --permanently-disable-colours

And to permanently enable the colours again, issue:

    rbt --permanently-enable-colours

Note that there are also a few classes that can handle colours
or colourizing. In particular, class **ColourizeParser** will
take any external output (e. g. output that has been taken
via system()-like calls by ruby) and colourizes it.

The general idea here is to make it visually easier to see
which problem may have been encountered while compiling
a program.

Users of RBT should be able to fully disable coloured output
at any moment in time. See the section <b>controlling the
output of class RBT::Action::SoftwareManager</b>.

## Controlling the output of class RBT::Action::SoftwareManager

By default, IO.popen() is used to parse the result of
system-calls, and colourize some of them.

But the user may not always want this, so a commandline
flag exists to overrule this.

Invocation example:

    rbt glade --trad --use-simple-system

This would just use system() instead, which is not as 
advanced, but simpler. (Won't use as many colours
for example; and there will be fewer automatic error
tracking as well. But if you prefer the simpler
variant, or need to use it, this option exists for
precisely that situation.)

## Minimal chroot environment

On my home system I tend to have a working backup system
at **/Depot/Chroot/**. In this directory I tend to have
all important programs "duplicated", so that I can
safely re-compile when necessary.

Which compile-chain may be used to build up a minimal
chroot?

I will try to list the options here, as I use this on
my system (or a new system):

    rbt make --static --chroot
    rbt bash --static --chroot # <- This may already suffice.
    rbt mpfr --chroot
    rbt gmp --chroot
    rbt mpc --chroot
    rbt sed --static --chroot
    rbt grep --static --chroot
    rbt coreutils --static --chroot
    rbt ruby --dontuseconfigureoptions --chroot
    rbt python --chroot
    rbt gawk --chroot --static
    rbt nano --static --chroot
    # Generate my custom rc-files next:
    rcfiles --populate-this-dir=/Depot/Chroot/AUTOGENERATED/
    rcfiles
    rcfiles --populate-this-dir=/AUTOGENERATED/
    rbt gcc --chroot --dont-symlink
    rbt ncurses --dontuseconfigureoptions --chroot
    rbt zlib --chroot
    rbt bison --static --chroot
    rbt m4 --chroot
    rbt curl --chroot
    rbt isl --chroot
    rbt flex --chroot
    rbt nasm --chroot
    rbt gc --chroot
    rbt tar --chroot
    rbt texinfo --chroot
    rbt openssl --chroot
    rbt libelf --chroot
    rbt elfutils --chroot
    rbt ccache --chroot
    rbt lzma  --chroot
    rbt cmake --chroot
    rbt file --chroot
    rbt pkgconfig --chroot
    rbt gperf --chroot
    rbt popt --chroot
    rbt git --chroot
    rbt pcre1 --chroot
    rbt pcre2 --chroot
    rbt libunistring --chroot
    rbt gettext --chroot
    rbt check --chroot
    rbt libxml2 --chroot
    rbt mtools --chroot
    rbt gzip --chroot
    rbt doxygen --chroot
    rbt strace --chroot
    rbt valgrind --chroot
    rbt graphite2 --chroot
    rbt tcl --chroot
    rbt expect --chroot
    rbt dejagnu --chroot
    rbt patch --chroot
    rbt libogg --chroot
    rbt sqlite --chroot
    rbt libpciaccess --chroot
    rbt libdrm --chroot
    rbt pixman --chroot
    rbt llvm --chroot
    rbt enchant --chroot
    # Compiling glibc should come last:
    rbt glibc --chroot --do-not-symlink --do-not-run-ldconfig

Do not forget to also copy a statically compiled
version of busybox.

## Json support in the RBT project

The package manager called **homebrew** has support for json files.

Example for using this:

    brew info --json

In August 2020, the possibility to dump (display) the json
dataset for a given program was added to the RBT project as well.
Additionally, if this is used, a file is generated in the 
**current working directory**.

Usage example for this:

    rbt htop --json
    rbt gcc --json

Give it a try! (For this to work, the expanded cookbook
dataset has to exist locally.)

## class RBT::Cookbooks::ExpandedCookbook

<b>class RBT::Cookbooks::ExpandedCookbook</b> has been created in <b>August 2020</b>.

The main idea behind this class is that, in the long run, we will use different
"backends" for the cookbook dataset (the individual cookbook recipes),
including SQL datasets.

That way we the user can decide which variant to use, with different advantages.
For example, class RBT::Cookbooks::ExpandedCookbook is quite a bit <b>faster</b>
than class <b>RBT::Cookbooks::Cookbook</b>, but not as versatile.

## Cmake

**cmake** is a build system that is becoming increasingly
popular these days. For example, the KDE project has
transitioned into cmake completely, away from **GNU autoconfigure**.
The GNOME project has transitioned into meson/ninja, though.

Anyway - **cmake support** is available within the RBT project too,
to some extent.

If you want to compile specifically via cmake, making use of
**class RBT::Action::SoftwareManager**, then you can use the following instruction
on the commandline:

    --use-cmake

Or more specifically have a look at these two examples:

    rbt harfbuzz --use-cmake
    rbt zlib --trad --use-cmake

Note that the **target build system** has to support cmake, in order
for this to work. You can often find out whether cmake-support
exists by simply looking as to whether a file called
**CMakeLists.txt** exists.

Auto-generating cmake files does not yet work for the **RBT gem**
alone, but it is on the todo-list, to easily transition between
GNU configure and cmake one day.

cmake can be a bit annoying to use from the commandline, since
the user has to use ALL_CAPS. For instance, to create a release
build with optimizations, one has to use the flag
**-DCMAKE_BUILD_TYPE=Release**.

As that is not very convenient to type, --release has been
added to the **RBT project**.

Use it like so:

    rbt initng --release

More options may be added in the future like this. For now, only
this shortcut to **-DCMAKE_BUILD_TYPE=Release** exists.

## Copying archives to the current working directory

If you ever need to copy some archives into the **current working
directory** (pwd), such as if you wish to **copy them onto a
USB stick**, or for any other similar use case, then the following
API may be of help to you, accessible via this commandline
variant:

    rbt --copy-these-archives=ruby,php,python
    rbt --copy-archives=kde5_plasma

The latter in particular will copy all the different KDE5-plasma
components onto a USB stick. This was the original use case as
to why I have added this functionality - I needed to copy the
plasma components to another computer located elsewhere (but
accessible via USB stick only), in order to compile these
programs on that machine.

Note that you could also, in principle, **use abbreviations**
here:

    rbt --copy-these-archives=xorgser

This would copy the local directory containing the xorg-server
tarball, rather than the user being required to input "xorg-server".

In order for this functionality to work, the directory has to
exist prior to invoking the above command(s).

Take note that in order for this functionality to work, you
must have already downloaded these programs into local 
directories. Currently the **RBT** project does not automate
these downloads for you (although it would be simple to add
- we will see when this functionality is actually required).

If you only wish to copy a single source archive to the
current working directory then you can use an API such
as the following:

    rbt --copy-source=php

A few aliases exist to the above, such as:

    rbt --copy-this-archive=bison

I am not yet sure whether I should unify this distinction
(**archive** versus **archives**) or not, but for the time 
being, do not be too confused that the code makes an internal 
distinction between a single archive, and multiple archives 
(**August 2020**).

## class RBT::Action::Cookbooks::MultiUrlDisplayer

<b>class RBT::Action::Cookbooks::MultiUrlDisplayer</b> can be used to quickly 
show several programs and their associated remote URLs to their
respective source archive on the commandline. In order for
this to work, naturally, these have to be part of a component,
and registered in the cookbooks.

Since as of April 2024 this class is now part of the Action
submodule, and thus <b>an actionable component of the RBT suite</b>.

Let's look at a specific usage example to demonstrate this
functionality:

   require 'rbt/actions/individual_actions/cookbooks/multi_url_displayer/multi_url_displayer.rb'

    RBT::Action::Cookbooks::MultiUrlDisplayer.new(ARGV)
    RBT::Action::Cookbooks::MultiUrlDisplayer.new('kde-plasma5')
    RBT::Action::Cookbooks::MultiUrlDisplayer.new('plasma5')
    RBT::Action::Cookbooks::MultiUrlDisplayer.new('audio_suite')

Or, simpler, since as of <b>April 2024</b>:

    RBT.action(:MultiUrlDisplayer, :audio_suite)

Or from the commandline, via <b>multi_url_displayer</b>:

    multi_url_displayer plasma5

The output will show all remote URLs of, for example,
the KDE5 plasma components.

Example listing:

    plasmabrowserintegration:    https://download.kde.org/stable/plasma/5.19.4/plasma-browser-integration-5.19.4.tar.xz
    plasmanano:                  https://download.kde.org/stable/plasma/5.19.4/plasma-nano-5.19.4.tar.xz
    plasmaphonecomponents:       https://download.kde.org/stable/plasma/5.19.4/plasma-phone-components-5.19.4.tar.xz
    kwaylandserver:              https://download.kde.org/stable/plasma/5.19.4/kwayland-server-5.19.4.tar.xz

On my computer system the output this will generate is as follows (as an image):

<img src="https://i.imgur.com/vC3Zfyt.png" style="margin: 1em">

If you are only interested in the raw URL entries, on the
right side, without the leading name, such as when you wish
to use wget to batch-download this easily, try any of the
following variants from the commandline:

    multi_url_displayer plasma5 --show-only-URLs
    multi_url_displayer plasma5 --only-URLs
    multi_url_displayer plasma5 --show-only-urls
    multi_url_displayer plasma5 --raw

## Support for Windows

One goal for the RBT project is to work on Windows, even in a restricted
environment such as **cmd.exe**.

However had, for now this is ... not working. But you can try RBT in
WSL1 or WSL2 (Windows Subsystem for Linux). There, RBT works just
fine. I am currently (September 2020) testing how well it works and
making adjustments to the RBT code base as a consequence. Stay tuned
for more updates here - eventually I think I may get RBT to work 
even with msys2, thus adding another option (more flexibility) for
the RBT suite of programs. 

## Changelog for the RBT scripts

Years ago I decided to no longer maintain a changelog for the RBT scripts,
since there is some maintenance time associated with it.

However had, in September 2020 I changed this opinion a bit - the RBT 
project may sometimes include some changes, in particular some bug
fixes here and there. This way users may occasionally check here and
see whether they may want to upgrade.

On 02.09.2020 (2nd of september 2020) an annoying bug was fixed where 
symlinks in the post-install section were linked to the name "m", 
rather than there real name. So for example, the vte-2.91 binary 
was linked to "m", rather than "vte". I kept on having symlinks to
"m" all the time, which made no sense, until I finally tracked this
annoying bug down and squished it.

## Compiling several programs in one go (Chain-Compiling)

Compiling several programs one-after-the-other is what the RBT
tools will refer to as <i>chain-compiling</i>.

It is handled by the ruby script called chain_compile.rb,
<b class="crimson">class RBT::ChainCompile</b>. The code
can be found within the file called
$RBT/utility_scripts/chain_compile.rb

This script allows you to compile several programs in one go, thus
making your life easier if you need to compile several programs
quickly.

There are basically <b>two ways</b> to trigger this.

lem 'The first one uses Installer.rb, i.e. the file we aliased to
`compile` earlier on.

The syntax for this is:

    rbt sdl wrap # This is no longer working. I removed this feature 
                 # for now. If you need this feature, use "chained sdl"
                 # instead.

    rbt sdl chained

Because the above idiom may be commonly used, you may omit the 
last argument if you prepend a <b class="yel">@</b> to the name.'

For example:

    rbt @sdl

In this regard, @ acts as a shortcut for wrap/chained mode.

However, there were a few design problems, and for now this is
disabled - use "chained sdl" instead. One day I may reenable
this feature.

The other way uses chained directly. Example:

    chained sdl

Personally I prefer the latter version <b>"chained sdl"</b>, 
mostly because I feel it is cleaner to use another command 
for compiling multiple programs in one go.

In this example <b>chained</b> is aliased to 
<b>ChainedCompiling.rb</b>.

In later versions I switched to "chained" command instead
of chained.

Examples with some modular xorg chains follow:

    chained xorg_protos
    chained xorg_apps

The above commands would compile several xorg related
 programs.

This is also doable from within rbt itself, as of
June 2017. Issue this command:

    rbt protos

To find out which chain is used, simply look 
at the <b>cookbook_chained_programs.yml</b> file.

If you only want to compile a single program from within
that chain for some reason, you can use specific positions.'

For example:

    chained xorg_apps 3

would compile the third program of xorg_apps. 
(At the time of this writing, this program would be 
<b>beforelight</b>)

The default is also to report the size of the tarballs used in
this chained compilation process - this can be altered via the
config file. (At March 2009 this was not a very sophisticated
solution - it needs to be heavily improved.)

The info for compiling several programs at once is written 
(and can thus be changed) inside 
<span class="lightblue marl2em">chained_programs.yml</span>'

    cat $RBT_COOKBOOK_DIRECTORY/cookbook_chained_programs.yml

## Showing the components of a chained compile setup via the commandline

If you wish to quickly see all components that belong to, e. g. the
compile chain forming xfce, then you can use this variant:

    rbt --show-components=xfce

Similarly to do so for ruby, try:

    rbt --show-components=ruby_addons

## Chained compilation

The term **chained compilation** simply refers to programs
that are compiled one-after-the-other, in a compile chain.

For example, if you wish to install (compile, that is) the
mate-desktop then you need the necessary libraries.

The yaml file chained_programs.yml keeps track of such compile
chains. That file is edited manually; in the future it may
be useful to automatically analyse all dependencies of a
given program, but code support for this has not (yet) been
added to RBT.

To compile the mate-desktop, for example, try:

    rbt --chained=mate

To compile xfce, try:

    rbt --chained=xfce

Take note that this is not very sophisticated right now. A
proper dependency manager requires more error checking
and error handling, whereas the current variant in RBT
is simple - and stupid.

Some aliases to the above exist, such as the following:

    rbt --chained=kde5_porting_aids # if you wish to compile the KDE5 porting aids

## Compile chain

Several programs require the <b>compilation of prior, other programs</b>.
For example, KDE or KDE Plasma or mate-desktop.

If you want to find out which programs are part of a particular
chain, you can try any of the following:

    rbt --show-chain=plasma
    rbt --show-compile-chain-of=mate

The first variant would show the proper compile chain that ought to be
usable for KDE plasma; the second variant would show the proper 
compile-chain for the **mate-desktop*.

Simply pass in the argument of the compile-chain that you seek. Note that
the main class that handles this on the commandline, class
**RBT::ShowCompileChain**, will do a little bit sanitizing in order to
find proper and plausible compile-chains.

Note that you can also batch-compile various components that are listed
that way, as they are registered in the file **chained_programs.yml**.

For example, to try to batch-compile the KDE5 applications framework,
you can try the following command:

    rbt --batch-compile=kde_apps
    rbt --batch-compile=kde-plasma

Or, simpler:

    rbt --kde-framework
    rbt --compile-kde-framework

Keep in mind that the **prior dependencies** ought to have been installed
already for this to work (that is, <b>to have compiled successfully</b>
before).

Since **as of July 2018**, a few simpler shortcuts exist as well.

For example, to compile all programs of the **KDE5 foundation**,
you can simply use the following command:

    rbt --compile-kde-foundation

You can also manually specify which programs you may wish to
**batch-compile** (that is, to compile them one after the
other). The following **example** shows how this can be done:

    rbt --compile-these-programs=make,sed,awk,coreutils,utillinux,gawk

This would specifically compile these programs in the given order,
e. g. starting with **make**, over to **sed**, **awk**,
**coreutils**, **utillinux** and finally **gawk**.

Since as of **25.12.2019** it is also possible to compile the first
n programs of, for example, KDE.

For example:

    rbt --kde1-first=10
    rbt --kde1-first=20

This would compile the first 10 or first 20 programs of the 
**KDE5 foundation** stack. Why has this functionality been
added?

I did not want to have to remember the names; instead, I just wanted
to tell to RBT that I want to compile the first 10 or 20 etc.. 
programs of said stack.

The first part here, "kde1", is an alias to "KDE5 foundation".

More such aliases may be added in the future, but for now this
has to suffice.

## class RBT::Chainer - the chainer

This is the **chainer**!

The class was added some day in October 2020. The idea for
RBT::Chainer is simple:

Pass a name of a program to it, and if said program is part
of a "compile chain", the whole compile chain is compiled.
That way, you can use any member of the compile chain
in order to compile it. I needed this because I do not want
to have to remember to which compile chain a particular
member belongs to, when working on the commandline.

So, for example:

    chainer libxmu

This would compile the compile chain where libxmu is a member 
of; in this context, this would be **xorg_libraries**.

Or another example:

    chainer khotkeys

This would compile **kde5_plasma**.

I believe this class may be somewhat useful in some cases,
so a **bin/chainer** file was also added.

## Specifically run autoconf before compilation begins

Sometimes you may have to trigger "autoconf", as some programs
do not come with a **configure** script. The **--use-autoconf**
commandline flag can be used for this.

Example:

    rbt tiff --ntrad --use-autoconf

## Bootstrapping on a new system

Since as of November 2020, the following option attempts to
compile the missing and outdated programs, if the gem called
environment_information is available.

So:

    gem install environment_information

And then:

    rbt --intelligent-bootstrap

The name "intelligent" is a misnomer. Right now it is not
intelligent; it simply grabs all missing entries, then
will attempt to compile them one after the other, starting
with the smallest program first (otherwise these will be
appended to the array, and be handled last).

## Checking a remote git repository

If you wish to quickly download the git-source of a program,
say **binutils**, you could use any of the following options:

    rbt binutils --check-source
    rbt binutils --git
    rbt mpv --git-download

This would, in principle, work for all programs that are
hosted via git. A requirement is that the .yml file at hand
has the corresponding **git_url**: setting set to a valid
value - a remote URL. See the file **binutils.yml** for
an example of this. Without such an entry, the git checkout
can, quite logically, never work.

Do note that the method in use here will also automatically
rename the downloaded directory and create a .tar.xz file
from that as well. This is mostly a convenience feature,
since I tend to store those .tar.xz files anyway. If you
don't need it, just disregard that feature and delete
the file, or re-package as you want it to.

Since as of <b>November 2020</b> another way exist as well,
a bit shorter than the above:

    rbt --git-clone=htop

The difference there is that you simply specify the program
last, e. g. via the **--git-clone=** commandline switch.

## Copying all headers to the current working directory

If you want to copy all .h files from, say, glibc, to the current
working directory, then you could do it via this commandline 
flag:

    rbt glibc --copy-headers-from=/usr/include

I needed this functionality so that I could copy a glibc version
installed into the **/usr** or **/** prefix, into
**/Programs/Glibc/VERSION_NUMBER/include/**.

There also exists a slightly simply API:

    rbt glibc --copy-headers
    rbt glibc --copy-headers-into-pwd
    rbt glibc --copy-headers-to-pwd

The two variants are not completely the same, though. The second
variant will only copy .h files that reside in an AppDir-like
prefix, so it is more likely to fail. It will, however had,
never pick up any possibly incorrect .h files from **/usr/include/**.

## Glib-schemata

Some programs, such as <b>evince</b>, require a .xml file that is
installed into a certain directory.

You can enable symlink-action of that .xml file by issuing the
following command:

    rbt ntrad --use-glib-scheme

Note that this has not been tested extensively though.

## Determine to which program a particular .h file in /usr/include/ or an executable in /usr/bin/ may belong to

If you ever do want to find out to which program a particular .h
file (header file) belongs to, you can make use of the class
**RBT::QueryHeaderToPackage** for this task.

A specific usage example in ruby follows:

    RBT::QueryHeaderToPackage.new('/usr/include/')

You can also do so from the commandline, if your target is the
**/usr/include/** hierarchy.

Example:

    rbt --query-headers

You can designate another target directory to be checked for
.h files, via a commandline flag such as:

    rbt --query-headers=/usr/local/include/

This functionality also works for binaries found under **/usr/bin/**,
by issuing something like:

    rbt --query-programs
    rbt --query-programs?
    rbt --attribute?

This is equivalent to the following ruby code:

    RBT::QueryBinaryToPackage.new('/usr/bin/')

If you want to determine all headers of, say, the program called
**ruby** then you can issue the following command:

    rbt --headers-of=ruby

## Using header files such as ao.h or udev.h as input for compilation

**class RBT::Headers** is a helper class that can map the
given input at hand, if it is a header file such as **ao.h**,
to the corresponding program at hand - which is **libao**
in this case.

This also works if you wish to use a .h header file as compile
input and don't care about the program name; or do not remember
the name of the program.

Consider the following:

    rbt udev.h ntrad

This would replace **udev.h** with **eudev**, and compile it in
a non-traditional (== **AppDir**) way.

This functionality has been added in **November 2019**, but it is
quite experimental at this time. My personal recommendation is
to use the real name of the program, because using the .h as name
can lead to errors (such as when different programs use the
same .h file, for example).

On the other hand, the functionality was specifically added because
sometimes you just don't care about to which program a particular
.h file belongs, yet still wish to compile/install it, so that
is the rationale as to why that functionality has been added.

## The clang compiler and LLVM support

**LLVM** offers the **clang compiler**. Compiling most programs should
be possible via **clang**. The content of the configuration file
**use_this_compiler.yml** tells RBT::Action::SoftwareManager which compiler to
favour. If clang is available, and the content of the file
use_this_compiler.yml is clang, then clang will be used - 
otherwise RBT::Action::SoftwareManager will default to **gcc**, as the latter is
more commonly used than clang (in 2020 at the least).

The environment variable **RBT_USE_THIS_COMPILER** can overrule 
the content of this yaml file **if it is set**, so you will
always have a way to toggle the behaviour when you desire to
do so, even without tampering with yaml files. (From within
ruby code, you can modify it via
**ENV['RBT_USE_THIS_COMPILER'] = compiler_to_use_goes_in_here**.)

To find out which compiler will be used you can use the following
from the commandline:

    rbt --compiler?

If you wish to compile not only LLVM from source, but also the
**clang-compiler** and the **compiler-rt add-ons**, then you
can use the following commandline to do so:

    rbt llvm --include-clang-for-compilation
    rbt llvm --compile-clang

Make sure that you have the necessary archive tarballs in the
corresponding directories for this to work, though. (This
last step is a bit hackish so don't expect this to work
flawlessly.)

Take note that you do not necessarily have to compile llvm
first **with** clang support; you can first compile llvm, and
then at a later time also compile clang.

You can also permanently enable **clang** on the commandline.

Example for this:

    rbt --permanently-use-clang

(This will modify the .yml file, so you can do the very same on your 
own; the feature exists merely as a convenience tool, to avoid users 
having to modify a .yml file's content as such.)

You can use <b>clang</b> rather than <b>gcc</b> to compile something.

To enable this functionality for the current compilation run, do use
any of the following variants:

    rbt htop --use-clang
    rbt htop --clang
    rbt htop --do-use-clang
    ry php --ntrad --do-use-clang

## Traditional compiling

Traditional compiling, in the context of the RBT project, means
**compilation** with the implied prefix being **/usr/**. This is
typically done via **--prefix=/usr/**, for projects that make
use of **GNU configure**.

As I use this variant quite frequently, and have a use case to
download newer packages from source, code was added to the
RBT project that allows me to automatically update a program
if a remote URL was given. This has been combined via the
alias I use called **trad** (for "traditional").

A specific usage example for this follows:

    trad https://mesa.freedesktop.org/archive/mesa-20.2.3.tar.xz

This will download this remote tarball (if it exists there),
register it as the new up-to-date version locally, and then
proceed to compile it into the **/usr/** hierarchy. Quite
nifty and convenient! **\o/**

Of course this is no guarantee that it will compile, but many
programs are well-written and compile fairly decently and
easily.

## The shortcut option called --backup

Sometimes you want to combine --ntrad and --dontsymlink. For
that particular use case, the following **aggregate entry point**
exists as a commandline option to **rbt**.

Example for this:

    rbt libx11 --backup

This will compile the program called **libx11** into
a prefix such as **/home/Programs/Libx11/1.7.0/** or wherever else
your programs-directory is set to, and it will **NOT** symlink
by default. This option was added merely due to convenience,
as I had to use the above quite a lot over the years.

The functionality was added in **November 2020**.

Note that the name --backup is not a great name, so this **may**
be subject to change one day. However had, when and if this
happens, the section here will also be updated; I just wanted
the functionality, to avoid having to pass both
**--ntrad --dontsymlink**.

## The XFCE desktop environment

If you wish to compile all of **XFCE** into a single directory, such
as <b>/Programs/Xfce/4.12.0/</b>, then you can issue the following
command:

    rbt --xfce-into-standalone-dir

Some aliases exist to the above commandline flag, such as:

    rbt --compile-xfce-components-into-one-standalone-directory
    rbt --compile-xfce-components-into-a-standalone-directory
    rbt --compile-xfce-components-into-standalone-directory
    rbt --use-xfce-prefix

This functionality is experimental as of **October 2018**, and
relies on a hardcoded path; but in the future, this functionality
may be extended to more components than just XFCE, and not depend
on a hardcoded path. When it is changed, this section will also
be changed (hopefully :) ).

If you wish to compile all of XFCE into a **standalone directory**,
but wish to do so in a step-like fashion e. g. in order to
reduce errors, have a look at the subsection here in this
page called **Environment settings**.

You can also batch-compile the XFCE components via:

    rbt --compile-xfce

If you already have XFCE installed/compiled, then you can use
the following code to report the versions of the XFCE
components:

    require 'rbt/utility_scripts/report_xfce_version.rb'

    RBT::ReportXfceVersion.new

Commandline invocation:

    rbt --report-xfce-version

Note that this will depend on a few .pc files, and a few
binaries, so it may not work for all systems as-is.

**class RBT::ReportXfceVersion** has been added on **23.02.2020**,
so it is fairly new and not yet complete. Keep this in mind.
In the long run, this notice will be removed or changed, once
everything works very well in this regard (that is reporting
the XFCE version).

## Using meson

You can use the build-system meson but keep in mind that this
requires python version 3.x and the build tool called "ninja".

You can then add a dependency on meson in the individual cookbook
file, at **required_deps_on:**, or you can use meson via the
commandline switch **--use-meson**.

Usage example:

    rbt glib --use-meson

Note that presently (2018) this does not work perfectly well,
which may be understandable since meson/ninja is fairly new,
compared to GNU autoconfigure-based systems.

If you want to prevent automatic download of source code,
such as via git, through meson, then this option could
be given to meson:

    --wrap-mode=nodownload


## highest.rb - showing the highest n programs

You can use the file highest.rb to show the largest local
programs, a Top 50 for instance, by doing:

    rbt --highest

You can specify an argument to it to denote how many
programs to find. It defaults to 20 programs right now
if no such argument is supplied.

    rbt --highest=50

## find_alternative_archive.rb

^^^ Use this when you could not find an existing
    archive first. After this has failed, we can try
    to check if we have to download a new archive.

## new_cookbook.rb

^^^ Use this when you wish to create a new yaml
    file.

## scan_source_archive.rb

^^^ Use this when you wish to scan through the
    local Source archive. This class will report which
    entries are missing.

## merge_cookbooks.rb

^^^ Use this when you wish to create one big
    new cookbookfile containing all other entries.

## generate_machomebrew_formula.rb

^^^ Use this to generate a machomebrew formula.

## GNOME

The gnome-project tarball archives can be found here,
as I last verified this in **April 2021**:

    https://download.gnome.org/sources/?C=M&O=D

The releases usually have even numbers for **stable releases**; and
odd numbers for **unstable releases**.

I myself used to stay on the "bleeding edge", thus using unstable
releases, to try to see what is new - but after some time, running
into problems here and there, I am now convinced that the stable
releases are MUCH much better, since you will have less problems
or errors in the long run. Every time I encountered a problem related
to an unstable release, I ended up investing via my time trying to
fix the problem at hand, which often was not possible, and quite
frustrating anyway. In the end I did waste way too much time for
too little gain, so I decided to stop making use of unstable
gnome releases. Past that point I am using only the stable 
tarball releases, unless there is some specific reason why
not - but, 99% of the time I settle for stable releases.

I added some code to the class that automatically download 
gnome-packages, to only consider **even numbers** when doing
such a download. But this behaviour can be toggled via a
**commandline switch** on the commandline, anyway - so 
the subsection here just explains as to why I personally 
**favour stable gnome releases** really.

You can also compile the gnome components in an ordered fashion
if you wish to compile them, by making use of **numbers**.
(This also works for kde, xfce, xorg, mate-desktop, games
and the like.)

Specific examples:

    rbt gnome1
    rbt gnome2
    rbt gnome3
    rbt gnome4

And so forth.

To **batch compile** most of these components, try:

    rbt gnome1..200

If you want to see what entries are available on the
gnome FTP site, try this API:

    RBT.show_the_gnome_ftp_listing

## class RBT::ShowVersionsOfThesePrograms

class **RBT::ShowVersionsOfThesePrograms** can be used to
quickly compare the versions of different programs.

You can use it from the commandline via bin/show_versions_of_these_programs:

    show_versions_of_these_programs ruby python php

Or from within ruby itself via:

    require 'rbt/utility_scripts/show_versions_of_these_programs.rb'
    RBT::ShowVersionsOfThesePrograms.new(%w( ruby python php ))

The output would then be something like:

    ruby:                          3.0.0
    python:                        3.9.3
    php:                           8.0.3

This is really just a quick way to show the versions of programs
you may be interested in. If typing **show_versions_of_these_programs**
is too cumbersome simply alias it to a shorter name.

## Removing outdated (local) archives

I tend to batch-update the RBT project quite frequently. As a result
of this, I end up having lots of local archives, usually in the
**.tar.xz** format. Since removing these manually is annoying
and time-consuming, a class has been added on **07.01.2020**,
called **RBT::RemoveOutdatedArchives**.

This class is presently not very flexible, since I only used it
to remove a specific set of programs - mostly KDE-related
packages.

For example, one specific invocation may go like so:

    require 'rbt/utility_scripts/remove_outdated_archives.rb'

    RBT::RemoveOutdatedArchives.new(:kde_plasma)

This would **remove all outdated archives** belonging to the
**KDE Plasma stack**.

More examples:

    RBT::RemoveOutdatedArchives.new(:kde_applications)
    RBT::RemoveOutdatedArchives.new(:kde_foundation)

The above would remove all outdated KDE5 applications (if all
goes well), respectively all of KDE5 foundation.

I run this from the commandline actually, so I tend to use:

    remove_outdated_archives :kde_applications

In the future this class may be extended, to allow more groups
of programs to be batch-removed, but for now this has to suffice.

Also note that whenever this paragraph refers to KDE, it refers
to **KDE5**. This may change in the future (e. g. KDE6 release
and similar), but for now (January 2020) it is up-to-date and
thus correct.

**Recommendation**: do not invoke this class unless you are
<b>absolutely certain</b> that you want to get rid of local, outdated
archives. I recommend to do a backup onto an external storage
device first in general. As said, this class was not very
thoroughly tested, so be cautious.

In <b>May 2022</b> a toplevel action was added for this
functionality. It is available via:

    RBT.actions(:remove_outdated_archives, :kde_apps)

## ccache

There is a configuration setting available as part of the **RBT
project**, called <b>use_ccache</b>. If this is set to yes, aka 
**enabled*, then the RBT project, in particular **RBT::Action::SoftwareManager**,
will attempt to **make use of ccache for compilation**.

This **may speed up repeated compilation cycles** of the same
program quite efficiently, so if you compile many different
programs again and again, it is recommended to use ccache.

If you do not need ccache or do not have it on the given computer
system, you can disable the use of ccache **permanently**, as far
as RBT is concerned, via the following commandline invocation:

    rbt --permanently-disable-ccache

Alternatively you can also modify the file at
<b>rbt/yaml/configuration/use_ccache.yml</b>, which is
where the configuration setting as to whether to use
ccache or not, resides. The allowed values are
<b>true</b> or <b>false</b>, <b>yes</b> and <b>no</b> (for
all configuration values, by the way. I tend to use yes and
no in yaml files quite a lot; these get sanitized to true
or false internally, anyway).

If you only want to **disable ccache for the current run**, then you
can use any of the following variants (here we assume that the
target program you wish to compile is <b>fluxbox</b>):

    rbt fluxbox --disable-ccache 
    rbt fluxbox --do-not-use-ccache
    rbt fluxbox --no-ccache
    rbt fluxbox --ccache-

A manual use of ccache would go like this:

    ccache gcc # files to be compiled go in here

In **November 2021** I noticed a few compile-related issues
with ccache. Although it may be possible to solve these
issues, having spent a few hours on these indirect problems
led me to change the default for **RBT**. So ccache is
now **disabled** by default. You can easily enable it 
as-is with the information displayed above; if you build
a LFS/BLFS, or want a clean system from scratch then 
you should perhaps consider avoiding ccache, until that
system is **sane**. I had no issues on slackware, for
instance, but on **devuan** and **debian** I had issues,
most likely because the base system is somewhat set up
incorrectly - says a lot about the debian maintainers
too ...

Learn from the oldschool folks, people - learn from
**slackware**.

## Installing the registered python addons

The RBT project has some python add-ons registered. These can
be installed via either of the following:

    rbt --enable-python-addons
    rbt --compile-python-addons
    rbt --python-addons

You will most likely not need this, since this is catered to my
own use case (since I have to batch-install things on a new
computer, for example). But the option exists nonetheless
since as of **March 2019**. I use it typically after I have
compiled a new python version. Once that python version has
been installed, I compile (or just install) the python
addons.

## Show which files will be installed by a given program

To show which files are installed by, say, the program
called **htop**, try this:

    rbt htop --show_which_files_will_be_installed

## Forgetful API design

Over the years, tons of code has been added or removed; some
of the existing code is not called.

Since I tend to forget what exists and what does not, I
added this subsection in 2021 as a brief memo for (future)
me.

    return_possible_abbreviation_to_this_input(i)
    # ^^^ This can be used to return all possible
    # abbreviations to the given input at hand.

## Changing the prefix in any given Makefile

Since as of **03.05.2019** (3rd May of 2019) it is now possible to change
the prefix in a given **Makefile**, via class **RBT::ChangePrefix**.

This class can modify the PREFIX variable in that Makefile. It was added
so that we can change the PREFIX target of any Makefile on the fly.

Currently it does not have a lot of configurable options but this may
change in the future. For the time being, the first argument should
be **the path to the Makefile** that should be modified.

## Configure options saved

The **configure options** that were used in order to compile a particular
program at hand, will be stored in the file called
<b>configure_command_database.yml</b>, which can typically be found
at a location such as:

    /Depot/Temp/rbt/configure_command_database.yml

The entries in this yaml file may look like this:

  minuet: cmake -DCMAKE_INSTALL_PREFIX=/usr/ /Depot/Temp/rbt/minuet-18.12.3/ 2>&1

So the format is - first comes **the name of the program**; followed by the
particular command that was invoked.

Note that this will **only** be stored in that .yml file if no problem was
encountered during compilation - thus, assumingly, would mean that the
compilation was successful or at the least continued without major
problems/errors encountered.

The primary reason as to why this functionality was added was so that the
user can quickly look at that .yml file and see which configure option was
used to compile a program. This may be useful at some later time when you
wish to find out what went wrong (if something went wrong) or perhaps
if you can not access the xorg-server but need to re-compile something.

## Configure options and passing additional configure options

The content of the various .yml files distributed as part of the **rbt**
gem may have an entry called **configure_options**. For example,
the **htop.yml** entry may look like this:

    disable-unicode

Which will be expanded into **--disable-unicode** if that .yml file
is **expanded**.

The entries that are listed under **configure_options** are usually
those that will keep track of the arguments that a user may normally
pass as arguments towards GNU **./configure**, such as
**--enable-static** or **--disable-shared**.

For example:

    ./configure --prefix=/usr --enable-static

Over the years, new and different build systems, such as meson/cmake or
cmake, emerged. They often would use different syntax as well, 
such as **-Dlibpsl=false** for meson or **-DDONT_USE_INTERNAL_LUA=Off**
for cmake.

Largely because of these reasons, the rbt project had to allow for
configure options sent to meson or cmake specifically, due to the
difference in syntax.

In **December 2018**, a new syntax was added for the .yml files,
for meson specifically, called **meson_configure_options**. A
similar option exists for cmake, called **cmake_configure_options**.

An example for this in regards to meson can be found in the 
file **networkmanager.yml**.

Some of these configure options can be directly passed to an
instance of class **RBT::Action::SoftwareManager** as well.

For example, if you wish to use **--enable-shared** then you can
simply pass it, like so:

    rbt htop --enable-shared

This will simply pass in the configure option **--enable-shared**.

In the future, more options will probably be added and allowed.

Some options may be translated into the equivalent cmake-option, if
cmake is used, but for the time being, this is presently (November
2018) not well supported. Stay tuned for later changes in this regard.

Since as of **November 2019**, the configure options that were used
to compile a program, will also be stored into the target
file at **Resources/configure_options.md** if it was installed
via an AppDir prefix (e. g. **/Programs/Ruby/2.6.5/** and
similar), if the compilation was a success **and** if there
was **at the least one** configure options - thus, empty Strings
will not be stored.

Note that this file will **only** store the actual configure_options
that were used; for the **full** configure-like command, see the
corresponding file in the same directory, whose name is
**full_configure_command.md**.

In the older rbt releases, it was possible to re-purpose the
entry called **configure_options** for cmake and meson. In
**April 2021** this was deprecated. It is cleaner, simpler
and more logical to use separate entries for GNU configure,
meson/ninja and cmake instead.

## md5sum

The expanded cookbook dataset includes the **md5sum** entry
for a given archive, such as **foobar-1.0.tar.xz**.

This md5sum entry is calculated locally on my home system, where
the "md5sum" binary is run on a .tar.xz archive. So if you get
another value, have a look whether you get the same value
when the package is also in the **.tar.xz format**.

## Sinatra-interface

The RBT project comes with a small **sinatra-wrapper**, for use
on the **www**.

Not a lot of functionality is available as of yet (**November 2020**),
but more functionality will be added over the coming months and
years. Stay tuned. Some more functionality was added in
**April 2021**. In **July 2021** the sinatra part now depends
on the **cyberweb gem** - it is easier for me to maintain
the www-related code via another project in general,

Right now you can **view** the content of a registered 
program. In the future you may also be able to install/
or remove/ an installed program. Be careful when doing
so, as things may not work properly - if possible use 
the commandline variant instead, as that one has been
tested more thoroughly.

Note that you can start the sinatra-interface from
the commandline via:

    rbt --sinatra
    rbt --sinatra & # if you want to start it as a background service

To view a program, either use the input-field, or
simply use an URL such as this:

    http://localhost:5580/view/php

Replace the URL port with whatever port you want to use; this
is currently hardcoded and defined in the constant
**USE_THIS_PORT**.

In order for this to work, the program must have been
registered as part of the RBT project.

You can also display the **available programs**, via
the sinatra interface, by using:

    http://localhost:5580/available_programs

Note that since as of June 2021, this now depends on the cyberweb
project. The reason is that I want to simplify maintaining
sinatra-related code, and the cyberweb project handles this
for me as-is.

For more documentation, have a look at
**doc/sinatra/README.md**.

## Tab-Completion support for various shells

<b>Tab completion</b> support exists for some of the commands, for **bash**,
**zsh** and **fish**. These are completions that can be invoked when
the user hits the <b>tab-key</b> on the keyboard.

In order for this to work, the corresponding file has to be sourced
(loaded).

For <b>RBT</b>, making use of tab-completion can simplify compilation.
Simply type "rbt", followed by a space, and then the first character
of the program that you wish to install, followed by hitting the
**TAB** key. (Do not forget to source the generated file in your
shell.)

Let us contemplate which syntax is to be used to
**generate** these (**tab**) **completions** for
the RBT project:

    rbt --generate-completions
    rbt --generatecompletions
    rbt --completion
    rbt --complete

The code for this functionality resides in these two files primarily:

    rbt/compile/shell.rb
    rbt/utility_scripts/generate_shell_completion.rb

Now - after you have sourced in this file into your shell, e. g.
via **source /path/to/the/file.sh**, you should be able to
use the tab-completions, like so:

    rbt gnomede**TAB**
    rbt k**PRESS TAB KEY HERE**

**TAB** in the context above means **to press the tab key** on
the keyboard.

The **tab-completion shell script** can be **generated anew** via
the above .rb file, but since as of 27th March 2019 the shell code
for bash and zsh is also distributed with rbt itself directly.
This may simplify making use of it, in the event that ruby may
not be installed on the host system or some other constraints
exist. I source that **.sh** file in my .bashrc file since that
same day.

If you want to find out where that .sh file exists on your system,
try this commandline invocation:

    rbt --shell-completion?

In **September 2021** the dependency on the gem called
**generate_shell_completion** was removed, though. The functionality
is retained, but users are no longer required to install that gem
in order to make use of **rbt**. If you need shell completion 
support then you are encouraged to install that gem via:

    gem install generate_shell_completion

## Showing the last updated programs:

Use:

    rbt --oldest-programs

This will show a "table" overview on the commandline
starting with the oldest program first (based on the
**last_update:** entry).

## Use random directory names for the extracted archive

The default compilation cycle may begin with a local archive,
such as /home/x/src/htop/htop-3.0.5.tar.xz.

This file may then be extracted into, for instance on my
home system, /home/Temp/rbt/htop-3.0.5/. Then htop will
be compiled from source, if all goes well.

Sometimes you may want to compile different variants at
the same time. If we then use a hardcoded path, such as
for the target directory at **/home/Temp/rbt/htop-3.0.5/**,
then only one program can be compiled.

This is why the commandline option **--gibberish** has been
added in **October 2021**. You can use other names, which
may make more sense for you, so for example: 

    rbt htop --random-extracted-dir

This would use a randomly named, extracted directory.

For instance:

    /home/Temp/rbt/HAoW4jJas1_htop-3.0.5/BUILD_DIRECTORY

This is used mostly to avoid using the same directory name.

That way you can now compile "concurrently" with different
options. I use this option sometimes when I want to compile
into the /usr/ prefix as well as an AppDir prefix.

Note that this does not yet work 100% perfectly, because
RBT uses a different variant to compile such programs,
based on "logic snapshots" - these are individual steps
that are taken. Right now class RBT::Action::SoftwareManager can not
handle them perfectly well. In the future this may all
be re-organized and work better at one point in time,
but for now this has to suffice. The whole compile-logic
behind RBT::Action::SoftwareManager became too complex. I will split
this up eventually into smaller, logical chunks - perhaps
even store them into a yaml file.

## The **manual_steps** entry in an individual cookbook .yml file

Since as of November 2021 a new entry exists that is optional,
called **manual_steps**.

In order to understand it, let's look at a specific program first.
We look at the program called **bzip2**.

First, have a look at the LFS/BLFS description for **bzip2**.

https://www.linuxfromscratch.org/lfs/view/9.1-systemd/chapter06/bzip2.html

If you look at the raw instructions, these go like something like
this:

    sed -i 's@\(ln -s -f \)$(PREFIX)/bin/@\1@' Makefile
    sed -i "s@(PREFIX)/man@(PREFIX)/share/man@g" Makefile
    make -f Makefile-libbz2_so
    make clean
    make
    make PREFIX=/usr install
    cp -v bzip2-shared /bin/bzip2
    cp -av libbz2.so* /lib
    ln -sv ../../lib/libbz2.so.1.0 /usr/lib/libbz2.so
    rm -v /usr/bin/{bunzip2,bzcat,bzip2}
    ln -sv bzip2 /bin/bunzip2
    ln -sv bzip2 /bin/bzcat

So, one use case for this entry is that we can quickly copy/paste 
this from the .yml file onto the commandline. But aside from
this convenience feature, we can also store additional (or
different) compile instructions there, which are available
if you invoke **rbt**.

The syntax for this is as follows:

    rbt bzip2 --manual-steps # easy to remember!

An alias exists:

    rbt bzip2 --ad-hoc # I liked the name --ad-hoc; easy to remember too

As to how useful that option is remains to be seen. In my experience
not many programs need such an entry, but bzip2 in particular is
quite annoying to handle, so that feature was added precisely due to
**bzip2**. **bzip2** is not the only misbehaving program in this
regard, though - there are a few more troublemakers.

Note that this will extract into the current working directory, so
the behaviour is a bit different to how rbt normally handles
programs. The rationale for extracting into the current working
directory is that if the user is going to want to use the
manual_steps instructions, then this is usually done in a manual
manner anyway; thus, it makes sense to continue to work in the
same directory. Make sure to be in a directory that could
constitute your own working directory.

Note that in May <b>2023</b> I also got tired of bzip2's horrible
Makefile-based installation method. The rbt gem is not yet
able to dynamically rewrite Makefiles (stay tuned for the
future), but since I need bzip2, I simply added the following
ad-hoc method to install it easily:

    ry --simple-bzip-installation

## Compiling via the --rootprefix option

Using the --rootprefix is exactly identical to passing this flag:

    --prefix=/

Nothing more than that.

The option was added in **November 2021** because I needed to
compile all coreutils binaries into the /bin/ subdirectory
on my home setup, and I needed these to be compiled statically,
to avoid any problems during reboot when some shared libraries
can not be found.

The exact command I used was:

    rbt coreutils --static --rootprefix

## Download the remote documentation from the commandline

If you want to quickly download the RBT documentation for local
display, do this:

    rbt --download-documentation

This was added in **November 2021**. The reason this commandline
flag has been added was because the xorg-server may sometimes
not work but you may want to look at the documentation locally,
such as via the browser called **lynx**.

## Future Goals for the RBT suite

The **RBT project** may not necessarily have truly grand goals,
such as "changing the world of package managers" - the scope of
the project is way too limited for that.

The primary project's goal is to:

(1) gather information about source code in general
(2) be able to present that information to the user, in a transparent
manner
(3) make use of that data to other programs or software suites,
be it on the commandline or via a GUI or via the WWW
(4) allow the user to compile/install these programs

Thus, the project has to be a practical project rather than a
visionnairy one.

But there are some **future goals** for the RBT project nonetheless.

- One distinct goal is to translate the instructions stored in the
various yaml files, into **specific SQL instructions** which can be
used to populate a SQL table - this is currently (July 2020) not
working, but stay tuned; it will eventually work and be properly
detailed and documented. The idea behind this is to be able to
store all the data stored in the various .yml files, into a
single database instead.

- Another goal is to use the project in order to create a full,
reproducible LFS/BLFS build, in combination with the RBT
project.

- And yet another goal is, similar to the point above, to turn
an existing Linux-system into a Linux-system based on an **AppDir
approach**. Note that this is also covered by the RBT project
primarily, and ... it does not work yet (**July 2020**). That means
that rather than having files spread all over the place on a system,
they will be contained in the respective directory of the given
program at hand.

So these are future goals.

Will these be achieved?

This is hard to say - and it has to be explained **why** this is
hard to say.

The RBT project was always a hobby project. On top of that, I wanted
to understand package managers, and how to compile/install
different programs from source. I have learned a lot over the years
in this regard, but I am not sure how much time I really want to
invest into the project in the future. Don't worry: this is not
a "I will abandon this project.". It is simply a question to
see how much time spent is worth it.

I never wanted to have to work professionally on this particular
project, that is to work on it, and get paid for it. That would
remove the old hobby-aspect. It may be feasible, but even with
adequate pay, my vision for life was never about a compile-related
software tool to be too overly important. I just wanted to get
things to work.

My personal interests are really much closer to
**synthetic biology**, so after considering this for a few
years, I have decided to **limit** the time I spend on other
projects. Again - this does not mean that I will abandon
this project at all, but in regards to the future goals, the
only honest statement to make is that the above would be
nice ideas, but they may never be implemented, simply due
to lack of time and lack of focused effort. Users of the RBT
project should be aware of that.

I will continue to improve the rbt project of course, including
the documentation, and may add some features here and there.
But the grand goals may never be achieved, simply due to lack
of time and dedicated effort.

In <b>December 2021</b> I thought about adding "actions" and
"actionable events" to the RBT project. Please look at the
subsection **Defined actions in the RBT project** for more
information about this.

The future is hard to predict, but I do have some ideas 
on my mind. Not everything seems to be possible in pure 
Ruby, but who knows - maybe we will include some C.
Perhaps integrate crystal.

I will also include other fancy ideas. Here goes:

- Ability to compile a project without being 
dependent on hardcoded Makefiles, cmake, or whatever.

- Ability to snapshot these compilations at any time,
and being able to resume the compile process lateron.

- Ability to generate Makefiles etc... for projects.

- We should realize a generic plugin architecture,
so that build types like cmake or scons work easily.

## Installing the Linux Kernel Header files and/or extracting the Linux Kernel archive

The **LFS project** has a step where the kernel headers are
copied to the **/usr/include/** target. I wanted this on a
versioned AppDir layout as well, so the following commands
were added: 

    rbt --install-kernel-headers
    rbt --install-linux-headers

This will essentially copy the important .h files from the linux
kernel to the correct target AppDir location, under the corresponding
PROGRAMS_DIR (wherever the user has set this; on my system this is
**/home/Programs/** usually).

If you merely wish to extract the Linux Kernel archive into the
corresponding target directory specified in the file **linux.yml**
then you can do the following:

    rbt --extract-linux

This is simply a convenience feature, not an important one; I wanted
to alias **extract_linux** in bash to simply extract the current
linux kernel, and then continue from there.

You can also install the kernel headers into your home directory,
e. g. at **/home/name/**.

To do this, use:

    rbt --install-kernel-headers-into-the-home-dir

## Determining the log directory for the RBT project

The RBT project needs a base directory for log files, that
is when it attempts to create log files and store these
in a directory.

If you want to know where the log directory is on your
given system, then you can ask rbt, using this
commandline flag:

    rbt rbt_log_dir?
    rbt --log_dir?
    
## Statistics used by the RBT project in general (and class RBT::CompileStrategies in particular)

The RBT project includes code that is related to **statistics**.
Furthermore, raw data points are also added, typically into 
.md files (markdown files).

To look at a specific example for **code** pertaining to statistics, have a 
look at class <b>RBT::CompileStrategies</b>. This class can be used
to query how many programs use meson, python, ruby or cmake, in
order to be compiled or installed. class <b>RBT::ShowHowManyFilesAreTracked</b>
on the other hand can show how many .h header files, binaries, and library
files (.so and .a) files are tracked by the RBT project.

Since the latter may be interesting from a <b>historic perspective</b>,
this is the result I got after running the latter class on the
15.09.2019 (<b>15th september 2019</b>):

    There are 4512 programs registered in total in the RBT project.
    There are 3616 binaries registered in the RBT project.
    There are 17221 .so / .a library files registered in the RBT project.
    There are 7278 .h header files registered in the RBT project.

I repeated this on the 12.05.2022 (<b>12th may 2022</b>) and got even
more results in this regard:

    There are  3756 programs registered in total in the RBT project.
    There are  5531 binaries registered in the RBT project.
    There are 24165 .h header files registered in the RBT project.
    There are 11995 .so / .a library files registered in the RBT project.
    There are   124 .gir files registered in the RBT project.
    There are    11 .m4 files registered in the RBT project.

(The first result from 2019 appears to be wrong, not sure why. The
second result in 2022, though, appears to be correct. So consider
the first result to be incorrect and just look at the result from
2022 and past that point.)

A module-method allows you to query for the **compile strategies**
used in the registered cookbook files of the RBT project,
via:

    RBT.compile_strategies?

And from the commandline, you can invoke it via the following
invocation:

    rbt --compile_strategies?

If you would like to see a more comprehensive overview over
the whole RBT project, and associated statistics, you can
do so via either of the following variants:

    rbt --stats?
    rbt --stats?

This will essentially invoke class **RBT::ShowStatistics**,
which in turn calls the other classes. (Take note that this
may take a while, since lots of .yml files may be
processed.)

The cookbook-submodule of the RBT project also includes some
statistics, which can be next seen **here**, displayed (and
stored) in the file called **rbt/doc/statistics/cookbook_statistics.md**:

In **April 2021**, the output of class RBT::ShowHowManyFilesAreTracked was
as follows:

    There are  3725 programs registered in total in the RBT project.
    There are  5500 binaries registered in the RBT project.
    There are 24031 .h header files registered in the RBT project.
    There are 11620 .so / .a library files registered in the RBT project.
    There are   120 .gir files registered in the RBT project.
    There are    11 .m4 files registered in the RBT project.

This should give you some overview as to how many files are 
tracked so far, within the RBT project as-is.


<pre>
# =========================================================================== #
# === Statistics for the Cookbooks found in the RBT project
#
# This file here (cookbook_statistics.md) was probably created in September
# 2005.
#
# It was later renamed from source_files.yml to cookbook.yml (on the
# 04.05.2006), before it was then eventually renamed to
# cookbook_statistics.md years lateron. This name will probably
# stick, as long as the RBT project is continued.
#
# The main purpose of this file is to mostly outline the history of the
# RBT project, how many programs were registered when.
# =========================================================================== #
# - How many programs do we have registered in the RBT project?
#
#   →  274 programs registered as of 25.10.2005.
#   →  340 programs registered as of 31.12.2005.
#
#   →  851 programs registered as of 28.04.2006.
#   → 1114 programs registered as of 11.07.2006.
#   → 1168 programs registered as of 01.08.2006.
#   → 1195 programs registered as of 07.08.2006.
#   → 1230 programs registered as of 24.08.2006.
#   → 1245 programs registered as of 31.08.2006.
#   → 1270 programs registered as of 16.09.2006.
#   → 1315 programs registered as of 15.10.2006.
#   → 1352 programs registered as of 13.11.2006.
#   → 1402 programs registered as of 27.12.2006.
#
#   → 1432 programs registered as of 28.01.2007.
#   → 1452 programs registered as of 07.02.2007.
#   → 1506 programs registered as of 17.03.2007.
#   → 1547 programs registered as of 19.04.2007.
#   → 1584 programs registered as of 24.05.2007.
#   → 1598 programs registered as of 04.06.2007.
#   → 1649 programs registered as of 01.07.2007.
#   → 1704 programs registered as of 05.08.2007.
#   → 1736 programs registered as of 01.09.2007.
#   → 1822 programs registered as of 27.09.2007.
#   → 1835 programs registered as of 03.10.2007.
#   → 1887 programs registered as of 27.10.2007.
#   → 1931 programs registered as of 30.11.2007.
#   → 1994 programs registered as of 30.01.2007.
#
#   → 2107 programs registered as of 05.04.2008.
#   → 2172 programs registered as of 02.06.2008.
#   → 2202 programs registered as of 29.07.2008.
#   → 2256 programs registered as of 12.12.2008.
#
#   → 2269 programs registered as of 31.01.2009.
#   → 2288 programs registered as of 03.05.2009.
#   → 2318 programs registered as of 01.09.2009.
#   → 2325 programs registered as of 24.11.2009.
#   → 2328 programs registered as of 08.12.2009.
#
#   → 2347 programs registered as of 31.03.2010.
#
#   → 2373 programs registered as of 28.02.2011.
#   → 2380 programs registered as of 19.03.2011.
#   → 2393 programs registered as of 25.04.2011.
#   → 2482 programs registered as of 29.08.2011.
#   → 2491 programs registered as of 13.10.2011.
#
#   → 2516 programs registered as of 04.01.2012.
#   → 2270 programs registered as of 28.07.2012.
#
#   → 2518 programs registered as of 25.09.2013.
#   → 2524 programs registered as of 25.10.2013.
#   → 2540 programs registered as of 20.11.2013.
#
#   → 2600 programs registered as of 26.01.2014.
#   → 2609 programs registered as of 26.02.2014.
#   → 2628 programs registered as of 22.06.2014.
#   → 2642 programs registered as of 12.07.2014.
#   → 2644 programs registered as of 14.09.2014.
#
#   → 2652 programs registered as of 10.01.2015.
#   → 2742 programs registered as of 04.06.2015.
#   → 2780 programs registered as of 26.07.2015.
#   → 2781 programs registered as of 02.08.2015.
#   → 2795 programs registered as of 06.09.2015.
#   → 2800 programs registered as of 24.09.2015.
#   → 2803 programs registered as of 28.09.2015.
#   → 2817 programs registered as of 26.11.2015.
#
#   → 2903 programs registered as of 01.04.2017.
#   → 2976 programs registered as of 09.08.2017.
#   → 3231 programs registered as of 23.10.2017.
#   → 3264 programs registered as of 01.12.2017.
#
#   → 3314 programs registered as of 04.01.2018.
#   → 3405 programs registered as of 25.08.2018.
#   → 3444 programs registered as of 14.10.2018.
#
#   → 3582 programs registered as of 14.04.2019.
#   → 3594 programs registered as of 12.05.2019.
#   → 3616 programs registered as of 17.09.2019.
#   → 3635 programs registered as of 30.11.2019.
#
#   → 3666 programs registered as of 21.05.2020.
#
#   → 3730 programs registered as of 08.04.2021.
#   → 3727 programs registered as of 30.04.2021.
#
#   → 3762 programs registered as of 26.07.2022.
#   → 3766 programs registered as of 05.02.2023.
#   → 3781 programs registered as of 02.04.2023.
#
# =========================================================================== #
</pre>


The number of registered binaries are also kept in a file - 
specifically look at the file at <b>doc/statistics/n_binaries.md</b>.
To show only three entries:

    On the 30.04.2021 there were 5497 registered binaries.
    On the 12.05.2022 there were 5531 registered binaries.
    On the 05.02.2023 there were 5651 registered binaries.

These are executables that reside under the **bin/** hierarchy
of a given program. As you can see, the number of registered
(and thus tracked) programs increases steadily, as more and
more programs are added.

## Different datasets

The first, raw material for the dataset is a fairly short .yml
file that may contain information specific to the program at
hand. For example, files such as <b>ruby.yml</b> or <b>php.yml</b>.

This variant has to be expanded and sanitized, though.

If the end user wishes to skip this step then this short .yml
file can be converted into a so-called <b>expanded</b> .yml file
(via the commandline **rbt --expand-dataset**, for instance;
you can test this on your computer system. I recommend a Linux
system though).

Since as of <b>September 2019</b> an additional, SQL-based way
exists. This variant is currently (re)written and requires
more testing before it can be added completely. Consider this
as work-in-progress for now. In the long run, RBT will
optionally allow for the use of a SQLite database in 
order to allow for faster queries. A positive side aspect
of this will be that RBT will work better on windows, since
all queries can then be done from a single sqlite database.

In <b>July 2022</b> a new SQL-specific class was added and the
SQL database definition improved.

The code for this new class can be found here:

    require 'rbt/sql/compile_via_sql.rb'
    RBT::CompileViaSQL.new(ARGV)

You first have to generate a new SQL database.

You can use the following API for this:

    RBT.generate_sql_table

Or from the commandline via:

    rbt --sql

This will create a new SQL database which is then
used by class RBT::CompileViaSQL for compiling 
a program from source.

This currently does not work that well, tons of
things are missing - but the overall idea is to
be able to use a single SQL database, in 
particular on windows, and compile or install
things from source on windows. At a later time
we may also turn the windows-specific cookbook,
a .yml file, into a SQL database. This may
speed up compiling from source on windows, 
and we could also skip having to install all
.yml files - simply use a single SQL database
instead. But right now this is limited, so
stay tuned for more updates in this regard
at a later time.

You can also query the raw dataset from that sqlite
database quickly. I made sure that we can use
simple select statemets, such as <b>WHERE
PROGRAM_VERSION =</b> to quickly query sub-components
as-is.

The sqlite dataset is currently (August 2022) distributed
within the rbt gem, to help you bootstrap the project.
However had, it is quite large (almost 1MB already)
and since it is generated from the expanded cookbook
dataset it is not necessary to distribute it. So this
may change in the future. For now it is the way it
is, though. If it is changed then the section here
will be updated as well.

## Databases and the RBT project

This subsection was created in <b>August 2022</b>. In the
long run it will contain information about how RBT works
with different databases. For now, though, the existing
information is spread out among different subsections here;
this may be remedied at a later point in time.

The primary database used by RBT project, if possible,
is sqlite3.

On windows you should download both the .dll file as
well as the .exe files - in particular sqlite3.exe
will be used to create the initial database for
sqlite. This may eventually become the new default
one day, so if you use ruby, RBT and windows then
you may have to setup your windows machine properly.
On Linux this is a little bit easier usually.

On <b>August 2022</b> I could confirm that the generated
SQL-file works. This means that in the future we may
be able to read in the dataset solely from a single
sqlite database. Stay tuned for more updates in this
regard in the coming weeks and months.

## RBT.make_app_prefix

This method can be used to create a make command such
as the following:

    make PREFIX=/home/Programs/Xfce4-panel/4.14.3/ install

In other words: we will automatically use the specified
PROGRAMS_DIRECTORY entry, and then run the actual
Makefile, via that "make" command. I was too lazy to
remember the specific syntax, so this method was added
to the rbt suite.

## Registering errors during compilation/installation

Some problems and errors may happen during compilation or
installation of programs.

These are currently handled internally by <b>RBT::Action::SoftwareManager</b>,
but they will also be registered in a toplevel-method
onto the RBT Namespace.

It is available via the following code:

    RBT.error_message?

Note that this will be reset to nil, its default value,
whenever a new program is compiled.

The whole error-handling part doesn't work that well
in RBT. At some point in the future it will be
rewritten - but first we will collect more errors
that can occur during compilation.

## Last updated programs

The following programs were updated with this release,
compared to the previous release:

gnometerminal was updated to program version 3.52.0 (on: 16.04.2024-16:34:26)<br>
eog was updated to program version 45.3 (on: 16.04.2024-16:36:07)<br>
simplescan was updated to program version 46.0 (on: 16.04.2024-16:37:23)<br>
linux was updated to program version 6.8.7 (on: 17.04.2024-13:34:59)<br>
xfsprogs was updated to program version 6.7.0 (on: 17.04.2024-16:49:02)<br>
cifsutils was updated to program version 7.0 (on: 17.04.2024-17:40:09)<br>
clamav was updated to program version 1.3.1 (on: 18.04.2024-13:57:00)<br>
nasm was updated to program version 2.16.03 (on: 18.04.2024-13:57:09)<br>
utilmacros was updated to program version 1.20.1 (on: 18.04.2024-14:01:01)<br>
libxmu was updated to program version 1.2.1 (on: 18.04.2024-14:01:22)<br>
bluez was updated to program version 5.0 (on: 18.04.2024-14:05:18)<br>
bluez was updated to program version 5.75 (on: 18.04.2024-14:05:36)<br>
waylandprotocols was updated to program version 1.35 (on: 18.04.2024-14:06:14)<br>
flatpak was updated to program version 1.14.6 (on: 18.04.2024-22:47:02)<br>
calibre was updated to program version 7.9.0 (on: 19.04.2024-08:03:45)<br>
gtk was updated to program version 4.14.3 (on: 19.04.2024-08:03:59)<br>
bind was updated to program version 9.18.26 (on: 19.04.2024-08:22:37)<br>
bind was updated to program version 9.18.26 (on: 19.04.2024-08:22:59)<br>
bind was updated to program version 9.18.26 (on: 19.04.2024-08:25:08)<br>
bind was updated to program version 9.16.50 (on: 19.04.2024-08:25:31)<br>
bind was updated to program version 9.16.50 (on: 19.04.2024-08:29:46)<br>
evolution was updated to program version 3.52.1 (on: 19.04.2024-12:59:24)<br>
evolution was updated to program version 3.52.1 (on: 19.04.2024-13:00:21)<br>
hatchling was updated to program version 1.24.1 (on: 19.04.2024-16:25:04)<br>
glibmm was updated to program version 2.80.0 (on: 19.04.2024-16:34:52)<br>


## Available program versions

The following list, as html-pre tag, shows which versions are currently
tracked, including the URL to these programs.

The **four entries** are:

(**1**) **program name**

(**2**) **program version**

(**3**) **last update of this program** (in regards to the cookbooks project)

(**4**) **remote URL**

The most useful entry of this list for users of the RBT project is probably
the **remote URL** entry there - the **most right** entry.

Note that some old programs are no longer available, which explains
why they have not been updated in many years. Can't update what is
no longer there now, can you. :)

(Very outdated program entries will eventually be removed from the
Cookbooks listing, in particular if the program is no longer
available.)

The file is also distributed with the RBT project at:

**rbt/yaml/programs_version/available_programs_versions.md**

That way you can use it on your local system easily, if you would
like to, e. g. to quickly scan for any entry there and
determine the URL or something like that.

## Makefiles and support for Makefiles in the RBT suite

Most open source projects on Linux that require you to compile
C or C++ code, come with a file called a <b>Makefile</b>.

The command "make" can then be used to interpret the rules
stored in said file.

Sometimes no such file is provided, though, and instead,
some other variant is used, that typically generates such
a <b>Makefile</b>. For instance, a generic file called
<b>Makefile.linux</b> can be found, or some other 
generator.

This file is a <b>template</b> file that can be used to
generate such a <b>Makefile</b> file.

The common syntax for how to invoke this this would
be like this:

    make -f Makefile.linux

So you pass the <b>-f</b> flag to <b>make</b>.

However had, the RBT scripts will automatically check
whether such a file exists, in the event that no Makefile
exists. If this is indeed the case, then the make command
will be modified to first create this Makefile. Note
that this behaviour may be subject to change at some
point in the future, but for the time being I wanted
to document this, in case a modification may be 
necessary.

## How to find out how many programs are registered in the RBT suite

To find out how many programs are registered in the RBT suite,
do one of the following:

    rbt --n_programs?
    rbt n_registered?
    rbt registered?
    
It will then feedback something such as:

RBT::ReportTheRegisteredPrograms: 2619 programs are registered
in our cookbooks as of 30.03.2014.

RBT::ReportTheRegisteredPrograms: 2832 programs are registered
in our cookbooks as of 18.02.2016.

RBT::ReportTheRegisteredPrograms: 2862 programs are registered
in our cookbooks as of 18.08.2016.

RBT::ReportTheRegisteredPrograms: 3185 programs are registered
in the cookbooks as of 06.10.2017.

As can be seen, more and more programs are (slowly) added
and registered over time. We are now (2022) past over
3500 programs already. \o/

## View the remote URLs of certain programs

To view the URLs of certain programs, you can do this:

    rinfo
    rinfo video
    rbt libxrandr url
    url libxrandr

Also note that you can set the program name by using 
USE_URL - we will then use the URL from <b>url1</b>.

The USE_URL is automatically assumed if you only provide
a remote URL.

## class RBT::Cookbooks::SearchForTags

This class can be used to <b>search for specific
tags.</b>

## Graphical User Interface (GUI) for the RBT suite

A GUI simplifies interacting with the computer for most
(regular) users. The RBT suite makes use of some GUIs
as well.

For the purpose of this subsection we will count the
www (world wide web) as part of a GUI too, as it is
quite similar to traditional desktop applications.

In <b>August 2022</b> support for ruby-gtk2 was removed
from the rbt gem. Only ruby-gtk3 is supported now.

While in theory it would have been possible to maintain
the ruby-gtk2 bindings, in practice I found that it was
not worth the extra time spent to do so. ruby-gtk3 is
simply significantly better than ruby-gtk2 at this point,
for the most part, in particular the CSS support it brings
made the GUIs look so much more pleasant. Some of the
functionality in gtk2 no longer works, which is unfortunate,
but it is simply a trade-off. We have to "go with the flow"
and move onto ruby-gtk3.

A few libui widgets exist as well. To start the main one
you can simply pass --libui such as via:

    rbt --libui

Keep in mind that this could, in theory, change one day.

## How many classes are available in the RBT suite?

This is kept track via the .md file
called <b>n_classes_in_total_in_this_project.md</b>.

## Displaying the AppDir prefix of a given program via the commandline

Use the following code if you want to know the AppDir
prefix of a given program:

    require 'rbt/toplevel_methods/configure_appdir_prefix.rb'

    puts RBT.return_appdir_prefix(ARGV)
    puts RBT.return_appdir_prefix('libssh-0.9.6')

The latter would yield this as a result:

    /home/Programs/Libssh/0.9.6/

## General information about the RBT project via a generated HTML file

The RBT project allows you to also generate some HTML pages,
similar to how the LFS (<b>Linux from scratch</b>) project.

The central ruby script that does that is called
<b>central_information_agency.rb</b>.

In order to generate a bunch of HTML pages, do this:

    cia lfs

or

    cia html_pages

## Using / Reusing old configure options

If you wish to re-use very long configure options, such
as from gcc, then you can use this command:

    rbt gcc --use-this-version=7.1.0 --use-old-configure-options

This will use the configure options from the currently
installed gcc compile.

## class RBT::ScanSourceArchive

class <b>RBT::ScanSourceArchive</b> will scan through the
(local) main archive repository and check if a tarball archive
was encountered that is not registered within the RBT suite.

I use it to make sure that the local copy I keep is "sane"
and correct. The class could need a rewrite, though - it
is a fairly old class at this point in time.

## Environment settings and the external gem called environment_information

Sometimes environment settings, stored in ENV as far as ruby itself
is concerned, may interfere with compilation. For example, assigning
to the env variable called TZ may cause a build to fail (TZ stands
for TIMEZONE).

I consider this pretty awful for shells such as bash or zsh, but
I did not design any of them.

What this means as far as the RBT project is concerned is that we
may need a way to easily **AVOID** using any ENV variable that may
be faulty.

The simplest way how to do this may be by not using any ENV variable,
save for PATH (which has to work, as otherwise the compiler can not
find anything).

Usage examples:

    rbt nss  --clear-envs ntrad
    rbt nspr --clear-envs ntrad

This would attempt to compile both nss and nspr without any environment
variables (save for PATH).

Since as of **December 2018**, a new class called 
**RBT::CompileViaEnvironmentVariableAsPrefix** can be used to 
specifically compile into a prefix that is specified via an
**environment variable**.

This allows me to then use something like this on the commandline:

    env_prefix xfconf

And it will compile the XFCE xfconf component into the prefix 
specified by the environment variable called XFCE_PREFIX,
which I happen to have set to a value such as
**/Programs/Xfce/4.12.0/**.

As we discussed the situation concerning environment-variables,
at the least to some extent, it should be mentioned that there
is an external gem called <b>environment_information</b>,
written by the same (original) author of the RBT project.
That project is not depending on the rbt gem, but if you have
both gems installed then you can use the <b>environment_information</b>
gem to indicate which programs you could install still. I use this
actually to see whether I have to update some programs on the
given computer system (on Linux typically). See the commandline
option <b>--really-everything</b> to obtain that information.

## Batch Compiling and Chain compiling

You can batch-compile several programs in one go.

The syntax is:

    rbt --batch-compile=mate
    rbt --batch-compile=ruby_addons
    rbt --batch-compile=xorg_protos

The first example will compile all of mate; the last example will
compile all xorg-protos.

Note that for this to work, you first must have defined a compile-chain
in the file chained_programs.yml, which is part of the RBT project.

Alternatively, you can just specify the programs that you wish to
compile, separated by a "," character, such as shown by the
following commandline example:

    rbt --batch-compile=python,php,perl,ruby
    
## Batch-downloading all source archives

You can download all registered **source archives** by calling
**class RBT Cookbooks::DownloadAllSourceArchives**. Warning:
before you do so, consider that this will really download
a <b>LOT</b> of source archives - several GB. On my home 
setup, where I keep all archives in the directory
<b>/home/x/src/</b>, in <b>September 2022</b>, this reached
a size of <b>31GB</b>. That's quite a LOT.

I use an alias to call that **.rb** file, if I ever have a use
case to invoke this functionality. Then I can do, for example,
on the commandline:

    download_all_source_archives

Alternatively, you can also **invoke the file from the commandline 
directly, by issuing either one of the following** to 
<b>bin/rbt</b>:

    rbt --download-all-source-archives
    rbt --downloadallsourcearchives
    rbt --grab-source-archives
    rbt --grabsourcearchives
    rbt --batch-download-all-source-archives

From within Ruby code, you can use the following **toplevel-API**
to download all source archives, if you have a use case to 
support this in any of your ruby files:

    RBT.download_all_source_archives

You can also download only those files that have a certain **tag**
registered. For example, if you want to download all programs that
have the tag "plasma" attached (for KDE5), you can issue the
following command (and argument) for this functionality:

    download_all_source_archives --tags=plasma

In order for this to work, the <b>tag</b> (in this case
<b>plasma</b> has had to be **registered** (and thus,
logically, exist). This registration typically happens on
the individual .yml file, which can then be expanded into
a SQL database. However had, I primarily work with the yaml
files, so this is where I make modifications first - see
the corresponding entry called <b>tags</b> in these
yaml files.

If you need an <b>overview</b> over the existing tags, issue
this command:

    rbt --available-tags

## Deprecations within the RBT project

Over the years, quite a lot of old code was removed or rewritten. As I can
not keep track of everything mentally, I will use this subsection to note
down when something was removed.

- In the past, cmake configure options were stored as <b>configure_options:</b>
in the corresponding .yml file. However had, since some time the new
option <b>cmake_configure_options:</b> exists. For about two years,
if no such cmake_configure_options was existing, yet cmake was used as
the build system, then the RBT scripts would assume that the user
wanted to make use of **configure_options** anyway, so this was used.

In April 2021, though, I decided that it is cleaner to only use
**cmake_configure_options** and thus deprecate that old behaviour where
**configure_options** could be substituted.

The constant FILE_SOURCE_DIRECTORY was finally removed in August 2022;
it was deprecated in May 2020 and commented out. Use the method
RBT.file_source_directory if you need to find out the file that
specifies the source directory.    

In <b>September 2022</b> I decided to slowly deprecate class
<b>RBT::SymlinkFromToCurrent</b>. There is currently a bug in
this class where it does not symlink into the /usr/bin/
hierarchy. As that class is a huge mess, rather than spending
time to fix it, I decided to slowly rewrite its logic step
by step. First step is to no longer allow it to handle
<b>bin/</b> and <b>sbin/</b> entries. At a later time it
may be removed completely.

class RBT::Action::SoftwareManager was taken as base to create RBT::Install
in <b>September 2022</b>. Several old code parts were
removed. For instance, @internal_hash[:original_input] was
removed, as well as the two method names input? 
and original_input?. Both were not really in use. If I ever
need these again I may look at this deprecation notice here.
But I am fairly certain that the rewritten code won't need
this.

## Querying the licence for a program

The file <b>feedback_licenses.rb</b> can help you if
you want to determine the licence for a program from
the commandline. It will feedback the known
(aka registered) licenses.

Usage example where <b>flic</b> is an alias to the
.rb file:

    flic gpl
    flic bsd

## Mandating a specific licence on the commandline

<b>Gentoo</b> has an interesting feature through Portage, since
as of version 2.1.7.

The user can designate a specific mandatory licence to
be used, on the commandline. If the program at hand does
NOT fulfil this licence then the program will not be
installed/compiled.

In other words, <b>the user can accept or reject software installation
based on its license</b>. The RBT suite added support for
this in <b>September 2022</b>.

Note that presently many licences are missing in the rbt
suite - this information has to be added over time. But
in the long run it is expected that this feature will be
supported fully, so stay tuned in this regard.

The goal here is to <b>have a pure system in regards to
licences</b> - or at the least the possibility.

How does this work syntax-wise?

Use any of the alternatives shown below - simply pick
the one that makes most sense to you:

    rbt php --honour-this-licence=GPLv3
    rbt php --check-for-licence=GPLv3
    rbt php --check-licence=GPLv3
    rbt php --only-this-licence=GPLv3
    rbt php --only-this-licence=gplv3
    rbt xfce4panelprofiles --licence=gplv2
    rbt exo --licence=gplv2
    rbt exo --licence=gplv3
    rbt plasmapa --licence=gplv2

Internally this is sanitized and checked by the method
<b>RBT.sanitize_licence()</b>.

What will happen when you pass the "incorrect" licence?

Consider the following two uses cases:

    rbt exo --licence=gplv2
    rbt exo --licence=gplv3

Only one of these two would compile. The other one would
show this error:

    RBT::Action::SoftwareManager: The licences do not match. Expected licence
    RBT::Action::SoftwareManager: was: GPLv3, specified licence was: unknown
 
## The method RBT.filter_for_valid_program_names()

The method <b>RBT.filter_for_valid_program_names()</b> can be
used to turn short input into a valid program name.

It is best to demonstrate this via an example.

Consider the following code tapping into RBT:

    require 'rbt/toplevel_methods/filter_for_valid_program_names.rb'
    RBT.filter_for_valid_program_names('libarch')

This would return the string <b>libarchive</b>, which is
a registered program in RBT.

The remote URL for this program is
<b>
https://github.com/libarchive/libarchive/releases/download/v3.6.1/libarchive-3.6.1.tar.xz
</b>.

Thus, this method can be used by a user to find programs that
he or she wants to download and subsequently compile.

On the commandline I can then do this:

    rbt libarch

And it will compile libarchive for me. Saves some keystrokes
thus - mostly it is a convenience feature. (You can also use
tab-completion, so you could then type <b>rbt libarch</b>
and hit the TAB key, if you loaded the completions in your
shell. But this happens before input is sent to RBT itself;
I wanted to be able to support both the case of tab completion
as well as the case where the user did not use tab completion,
for whatever the reason.)

Note that <b>RBT.sanitize_this_program_name</b> is an alias
to this method.

The method was added because different .rb files in the
RBT suite may require such abbreviations, so it was
easier to just bundle all these use cases into a single
methods.

I am making slow but steady progress with class RBT::Action::SoftwareManager.
For instance, we can now install any different program version
via the <b>@ special syntax</b>.

Let's explain this with a specific example.

Say that you have two archives locally,
glib-2.74.0.tar.xz and glib-2.72.3.tar.xz.

Normally the RBT suite will cater to the most recent
program version by default, such as glib-2.74.0 in the 
above situation - but this is not always wanted. Sometimes
a program does not compile, and you may want to look at
another program instead.

So we need a way to specify another program version
on the commandline.

In the past the following syntax was used, with 
the old class called <b>RBT::Compile</b>:

    rbt glib --use-this-version=2.72.3

But this was quite verbose and not very convention to
type.

For <b>RBT::Action::SoftwareManager</b>, the above syntax will work
(eventually), but the user can also use the <b>@ syntax</b> (which
already does work, and was one reason why RBT::Action::SoftwareManager
has been written, to begin with) like this:

    installer glib@2.72.3
    installer glib@2.80.0

So this will infer the version after the @ part, rather
than requiring of you to pass it explicitely on the
commandline.

This is quite convenient and shorter to type than the
old variant - just compare it. It is so much shorter
and more succint. Laziness for the win! \o/

## Installing only the headers of a program

You can use this:

    ry gmp --only-headers

This will just copy the .h files into <b>/usr/include/</b>.
      
## Build directories

Some progams insist on using a <b>build directory</b> that
is separate from the directory where the source code is
kept.

For example, the KDE program called **kirigami2** requires
an "out-of-source" build directory. I typically use the
generic name <b>BUILD_DIRECTORY/</b> for such a build directory.

There is a relevant entry in the cookbooks .yml files that
can be used, called **use_build_directory**. If this entry
is set to **true** or to **yes** (both are equivalent to 
one another) then the RBT project will make use of a
build directory for compiling a particular program. Conversely
if set to **false** or to **no** - or omitted - then this
will default to "no, we will not use a build directory 
for installing/compiling this program.".

You can get an overview over the programs that make
use of a build directory, by using any of the following
APIs on the commandline:

    rbt --show-all-programs-that-make-use-of-a-build-directory
    rbt --all-build-directory
    rbt --all-build-directories
    rbt --build-directories?
    rbt --build-directories
    Installer --build-directories?

In order for this to work on your system you may have to
create the expanded cookbook directory (or copy the existing
expanded directories via <b>rbt --copy-expanded-directories</b>).
We could use the internally distributed directory since as of
2021, but for the time being the above approach will still be
valid as-is. I recommend to simply copy the expanded directories
after installing the gem, for now.

That still leaves a question of design consideration: if some
build systems mandate a separate build directory, such as
meson, how to handle this situation?

Well - there are two basic ways how to go about it here:

(1) One could cd into a separate build directory in
general, and then require that build systems, such as
meson, cd back into the original "configure base directory".

(2) Or one could not cd into a separate build directory
in general, and instead require a separate cd-action
to change into a build directory.

While (1) is probably the more elegant solution, as it
leads to less duplication of code, in September 2022
I decided to pick option (2). Perhaps at a later time
in the future this may be changed, and then this subsection
will have to be updated, but for now I wanted to specify
this behaviour and rationale here, when I was creating
class RBT::Action::SoftwareManager.

## class RBT::CreateLogFile

<b>class RBT::CreateLogFile</b> is going to be used for all
log-related functionality of the RBT suite eventually.

Right now in <b>September 2022</b> it is only used by class
<b>RBT::Action::SoftwareManager</b>, but in the long run it is expected to
handle all log-related aspects. The idea is that this
class can be so flexible as to create all log files,
including via .yml, that a user may want to look at
or inspect at some later point in time.

## Java-related code in the RBT project

More Java-related code will be added to the RBT project in
the coming months and years. These Java-related parts are
currently not quite complete, not even an early beta. It is
most likely that one has to handle these parts with more
care, such as manually downloading source archives before
invoking the java-related parts. Having said that, though,
some parts work somewhat: for instance, I can do:

    java BuildTools expat

And on my home system this would mean to work on:

    /home/x/src/expat/expat-2.4.9.tar.xz

At some later point in time I may then turn this 
into an executable via GraalVM and just do:

    buildtools expat

In the long run, perhaps years from now on, I intend
to have RBT also work via Java. There should be a 
noticable speed-up when one combines this with
GraalVM.

## Binary and Library Checking

You can also compile a program if you only know the name of a
binary. For example, to compile the package "xine-ui", you could
supply the name of one of its <span class="yel">binaries</span>, 
like so:

    rbt xine-check

xine-check is a binary of xine-ui. The above will actually 
compile <b>xine-ui</b>.

Another example:

    rbt basename

<b class="yel">basename</b> belongs to the package 
<b>coreutils</b>, and thus we will attempt to compile 
coreutils.

Note that you can change this in the config file, look
for the option `check_for_binary_names`.

One last example - say, you know the binary name which is
called `startx`. You attempt to compile it, and we will set
it to the proper package name:

    rbt startx

<b>startx</b> belongs to xinit and the above is the same as:

    rbt xinit

And the same mechanism works for library names just as well
(if they were registered in RegisteredLibaries.yml that is).'

So for instance:

    rbt libqui.so

The above would actually try to compile QT4 and would thus be 
the same as if you would have entered:

    rbt qt4

In the end, this is just a slight convenience to make your 
life easier.

The default behaviour for the scripts is to treat the given
input as alias to a real program name, and if this alias is
not found we check for binary names, then for library names.

Sometimes, this is not desired.
 
Consider that you input "ld". Now let us also assume that you 
already have an entry called "ldmud" in your scripts. But "ld" 
is also the name of the binary "ld" in the binutils package.

To force that we seek for the binary "ld" and not for 
"ldmud" you could do this:

    rbt ld treat_as_binary_name

Same works for library names as well:

    rbt ld treat_as_library_name

## Gstreamer

If you want to compile all gstreamer components, use:

    rbt --all-of-gstreamer

I added this functionality because I can not offhand
remember the proper compile order, e. g. gst-plugins-bad,
gst-plugins-ugly and so forth.

## Porg: the package organizer

<b>Porg</b> is a small utility that allows a user to track which files
are installed by a given program that is compiled from source. RBT
supports the use of porg through a configuration file, called
<b>use_porg.yml</b>. You can set its content to either true/false,
or yes/no - these are synonymous to one another. I prefer the
yes/no nomenclature.

To query from the commandline whether porg is available on the
given computer system, try:

    rbt --is-porg-available?

If it is not available then you can compile porg of course,
via:

    rbt porg --trad


To query from the commandline whether porg will be used, use:

    rbt --use_porg?

The raw command for porg to run the make install step is like this:

    porg -lp htop-2.2.0 "make install"

So, to give you a more specific example, say you compile zlib
via the rbt gem, like this:

    rbt zlib --ntrad

And you also have porg enabled.

Then you can run the following on the commandline to let porg tell you
which files were installed:

    porg -f zlib

The output will then be something like this:

    zlib-1.2.13:
    /home/Programs/Zlib/1.2.13/include/zconf.h
    /home/Programs/Zlib/1.2.13/include/zlib.h
    /home/Programs/Zlib/1.2.13/lib/libz.a
    /home/Programs/Zlib/1.2.13/lib/libz.so
    /home/Programs/Zlib/1.2.13/lib/libz.so.1
    /home/Programs/Zlib/1.2.13/lib/libz.so.1.2.13
    /home/Programs/Zlib/1.2.13/lib/pkgconfig/zlib.pc
    /home/Programs/Zlib/1.2.13/share/man/man3/zlib.3

Quite convenient to have! \o/

You can read up more about porg here:

https://porg.sourceforge.net/

# Handling errors and problems in regards to the RBT project

## Autocorrecting some errors

The RBT scripts can attempt to auto-correct some errors. This
is presently in testing. The few errors that RBT can try to
auto-correct are mostly related to libtool.

If the file use_autofixing.yml contains a String called t or
true, meaning "enable autofixing", then auto-correcting will
be used. There is another option that has to be set to true
though, which is the "is_on_roebe?" settings, which indicates
my home directory use. Presently (Sep 2017) this option does
not work too reliably, so I am still testing it. You can 
test it too though if you enable "is_on_roebe".

## Helpful hints when a .h header file is missing

Since as of December 2022 the RBT suite will give information
to the user as to when a .h header file is missing, and if that
missing .h header file is (in turn) registered as part of the
RBT project.

Let's explain this statement via a specific example.

The software called <b>usbutils</b> depends on a header file called
<b>libusb.h</b>.

This header file (libusb.h) is part of <b>libusb</b>.

So, if the user tries to compile usbutils, but the error reported
refers to a missing libusb.h file, then the RBT::Action::SoftwareManager class will
inform the user about this situation.

This message may look like this:

    RBT::Action::SoftwareManager: You could consider compiling it via:

      rbt libusb

That way the user can then consider compiling this program if
he would like to.

Before that code was added, if the user got some error about
a missing .h file, there was no indicator as to what
was missing. Now, since as of December 2022, the user
will get this notification <b>if</b> the program is 
registered in the RBT project.

## class RBT::SimpleAppdirConfigure

class <b>RBT::SimpleAppdirConfigure</b> can be used to quickly
use the appdir-prefix at hand.

Note that you can also use the following toplevel-method for
this functionality:

    RBT.simple_appdir_configure # ← simply pass arguments to this method.

## class RBT::WhatCouldBecomeAnAppDir

class <b>RBT::WhatCouldBecomeAnAppDir</b> was added in March 2023. The idea
behind this class is that RBT should tell us which programs could be
turned into an AppDir program, based on the binaries. This class will
thus scan through all of /usr/bin/ and notify the user whether this is
a registered binary or whethre it is not; and, if it is, whether it
can be compiled into an AppDir.

This may be a bit confusing for newcomers, so this is clearly something
for advanced users only.

## Show the manual installation steps

If you want to see the manual installation steps, use the file
show_manual_steps.rb.

This will not invoke these steps, contrary to another class which
will invoke the manual steps.


## Static compilation

Some programs can be <b>compiled statically</b>, but this may also lead
to problems sometimes - such as when the program can <b>NOT</b> be
compiled statically.

The optional entry **build_static** in a cookbook file allows us to
determine whether compilation should be statically or
whether it should not be static.

If you wish to overrule this on the commandline and specifically
**disable** static compilation, you can use a commandline 
instructions such as:

    rbt htop --do-not-build-statically

Note that as of **December 2018** you can also combine
--enable-shared --disable-static in one variant via
<b>--shared-no-static</b>:

    rbt libxmu --shared-no-static ntrad

To determine whether a program can be compiled statically, you can
issue a command such as the following:

    rbt tar --can-be-compiled-statically?

Do note that this requires a manual registration in the corresponding
yaml file; by default this will return false (aka no).

Since as of July 2020 you can also determine which programs can
be compiled statically in general, via:

    rbt --which-programs-can-be-compiled-statically?

Next, a few words about statically compiled binaries on Linux. I added
this subsection in 2023 because I sometimes need to remember how to
do so without the rbt project.

I found that often setting CFLAGS to include -static works.

In ruby this would look like this:

    ENV['CFLAGS'] = ENV['CFLAGS']+' -static -g'

I tested this on the program called <b>sed</b> in June 2023, and,
indeed, the resulting binary was statically compiled. \o/

## The entry status_of_the_project in a cookbooks .yml file

In June 2023 the entry <b>status_of_the_project</b> was added.

Possible values include:

    - outdated
    - possibly outdated
    - low maintenance
    - actively maintained

This is somewhat experimental for now. The key idea is to
indicate the maintenance health of a project. Most will
default to the value <b>actively maintained</b>, so this
entry is primarily useful when a project was abandoned.

## Defined actions in the RBT project and actions (actions tag)

So, rather than think in terms of classes and .rb files, we think
of every important part of RBT to be "actionable". That is, we can
call its "action", which will lead to its specified, designated
effect, such as compiling a program from a remote URL.

Thus, we should also provide a <b>unified topdown way</b>
how to call <b>all</b> these actions. Furthermore we
can <b>chain</b> these actions, to achieve a combined,
new effect. For instance, in order to compile a program
from source, we have to do certain actions one after the
other. Thus we can specify all of them via these
actions. 

The general syntax suggestion for such an <b>action</b>
is as follows:

    RBT.action(:create_program_skeleton, 'htop-1.2')

This would be the very same as issuing:

    rcp htop-1.2

From the commandline.

The reason why I think adding support for this is useful is because once
you have many individual tasks in the project, it gets messy to remember
their names and remember where that action resides (in which particular
.rb file and class). Whereas, if we use a Symbol such as the above, we can
call this from any other .rb file as-is, and have that work, without having
to think about which specific .rb file to call, and so forth. Extra
actions can be passed via {} blocks in a generic way, so this should
be quite flexible if the user requires fine-tuning of this.

I will keep on exploring this - in the long run, the goal would be to
make all **actions** available via the above generic API call.
Furthermore we can also alias this, to simplify calling it from
within ruby code.

The following actions are registered as of **May 2022**, sorted
alphabetically:

    :all_urls                                # Feedback/Show all remote URLs on the commandline.
    :appdir                                  # Compile the given program(s) at hand in a (versioned) appdir style.
    :autosymlink                             # This ad-hoc helper class can symlink from lib64/ to lib/. Rarely needed, though.
    :autoupdate_this_program                 # Autoupdate a specific program.
    :batch_validate_the_cookbook_recipes     # Validate all cookbook recipes. This is not so important for regular users, though.
    :beautify_configure_help_output          # Beautify the "./configure --help" output.
    :binary_of                               # Query to which program a specific binary belongs to.
    :blfs                                    # Show the BLFS entry of the given program. This only works if there is a registered BLFS entry for the given .yml file.
    :build_detector                          # The build detector can be used to determine whether a program uses "configure" or "cmake" or "meson" and so forth.
    :chainer                                 # Chain-compile a series of programs, such as the "KDE5 applications".
    :chroot_compile                          # Compile into a chrooted environment as prefix-target.
    :colour_make                             # Run "make" in a colourized manner, that is, with colour support.
    :colour_make_install                     # Run "make install" in a colourized manner, that is, with colour support.
    :compile_in_traditional_manner           # This will compile the passed programs via the /usr/ prefix.
    :compile_into_home_dir                   # This will compile the given program into the HOME directory of the user, e. g. /root/ for the superuser.
    :compile_program                         # Compile a specific program. Symbols exist for shortcuts such as :lfs1.
    :compile_strategies                      # Give an overview over the available compile-strategies in use.
    :compile_these_programs                  # Compile several programs one after the other, e. g. the batch-variant to the :compile_program action.
    :compile_the_python_addons               # Compile/Install all registered python add-ons (registered in the RBT suite that is)
    :cookbooks                               # Create a new instance of RBT::Cookbooks::SanitizeCookbook.
    :copy_these_archives                     # Copy different source archives to the current working directory.
    :create_appdir_skeleton                  # Create a new AppDir skeleton structure for the given program.
    :create_cookbook_yaml_file               # Create a new .yml file for the given program.
    :create_log_directory                    # Create a new base log directory for the RBT project.
    :create_pkgconfig_file                   # This action will attempt to create a (pkgconfig) .pc file.
    :create_program_skeleton                 # Create a new AppDir skeleton for the given program. This is the same as ^^^ above, thus just another aliased name for it.
    :create_programs_version_html_file       # Create a large programs-version .html file. Not that useful for most end users, though.
    :create_program_version_url_file         # This will create the default .md file containing all URLs, before the rbt gem
                                             # is uploaded. Not that useful for most end users, though.
    :create_programs_url_file                # This action will create the programs-URL file e. g. programs_version_url.md.
    :create_registered_tags                  # Create the registered-tags file. Normal users don't really need this.
    :create_snapcraft_file                   # Create a .snapcraft file for the given program.
    :custom_toolchain                        # This action will compile as if the user passed the three options '--static --home-dir --do-not-symlink' to RBT::Action::SoftwareManager.
    :download                                # Download a specific source archive. Alias "aliased" to :rbt_download.
    :download_all_source_archives            # Download all source archives, e. g. more than 3800 programs. Use only when you need to bootstrap your own local copy of archives.
    :dual_compile                            # First compile the program at hand via /usr/ prefix, then again via an AppDir prefix.
    :extra_information                       # Show extra information about the given program at hand.
    :extract                                 # Extract a tarball/zip archive to some location.
    :expand_cookbooks                        # This will expand from the short .yml files to the sanitized, longer
                                             # .yml files, for all cookbooks. class ExpandCookbooks will handle this.
    :expanded_cookbooks                      #
    :feedback_program_description            # This action will feedback the description of the given program at hand.
    :feedback_description_of                 # This action will feedback the description of the given program at hand - ^^^ similar to theabove.
    :filter_for_valid_program_names          # Try to turn the given input into a required program, such as the input "ph"
                                             # becoming "php" or "libar" becoming "libarchive".
    :find_all_archive_types                  # Find all local archives of a specific type, such as ".tar.gz".
    :find_url_for                            # Find the URL for a specific program, such as "htop".
    :generate_all_slack_desc_files           # Generate all slackware-description files for every registered program.
    :generate_version_file                   # Generate the large programs_version.yml file.
    :highest                                 # Show the "largest" programs, that is, the biggest file archives stored locally.
    :home_dir_without_symlinking             # Compile into the home directory, such as /root/, but do not symlink afterwards.
    :homepage                                # Simply report the homepage of the given argument, e. g. RBT.action(:homepage, 'php').
                                             # :report_the_homepage is an alias to :homepage, by the way.
    :install_this_rubygem                    # To quickly install a rubygem .gem file
    :libtool                                 # A wrapper over libtool, to try to make libtool suck less.
    :make                                    # A wrapper over "make", primarily done to add colour support when doing "make" on the commandline.
    :make_app_prefix                         # Run "make" but pass an explicit app-dir prefix towards it.
    :manual_steps                            # (Missing description right now.)
    :meson_appdir_prefix                     # Compile via a meson-based system, into the default appdir prefix (e. g. /Programs/Htop/3.1.2/ or a siilar prefix).
    :multi_url_displayer                     # This will show several URLs in one go, such as for "lxqt".
    :ntrad                                   # Compile in an AppDir manner.
    :parse_help                              # Parse the output that is yielded by issuing "./configure --help" normally, for configure-based programs.
    :paste_blfs                              # Simply show the BLFS entry of the given program. (It has to have such an entry, though, otherwise this will not work.)
    :query_file_association                  # This will query to which package a specific file belongs to (if it has been registered).
    :remove_libtool_files                    # This action allows the user to remove .la files, in the versioned AppDir prefix
    :remove_outdated_archives                # This will remove outdated (that is old) archives, if more than one such archive exists locally.
    :remove_symlinks                         # This action will remove all broken symlinks (at the least in the PROGRAMS_DIRECTORY hierarchy).
    :rename_konsole_tab                      # This action will (try to) rename a konsole tab (that is KDE konsole), which is the terminal I tend to use.
    :report_how_many_binaries_are_registered # Report how many binaries are registered in the RBT project.
    :report_host_cpu                         # Report the host CPU in use, such as "x86_64".
    :report_the_mate_desktop_version         # Report the mate-desktop version, on the commandline.
    :report_total_size_of_all_archives       # Report the total size of all local archives.
    :report_xfce_version                     # Report the XFCE version (if installed locally).
    :run_make_then_make_install              # This will first run "make" and then "make install". It is mostly a convenience method, with support for colours.
    :scookie                                 # Show a lot of information about a specific program.
    :search_for_tags                         # Search for all programs that have a specific tag.
    :show_all_about                          # Show all about a specific program, e. g. "htop".
    :show_compile_chain                      # Show the compile chain for the given program.
    :show_configuration_options              # Show the configuration options of a specific program, if it has any.
    :show_versions_of_these_programs         # Show versions of the given programs.
    :simple_appdir_configure                 # Compile a program via an app-dir prefix, e. g. /Programs/Htop/1.2.3/.
    :store_abbreviations                     # This will store all abbreviations to the registered program names.
    :suggest_cookbook_for                    # Suggest a cookbook for a specific program, such as "htop".
    :symlink_into_the_usr_bin_hierarchy      # Symlink the given Array into the /usr/bin/ hierarchy.
    :test_this_alias                         # Test whether the input is an alias to a program, such as "ht" towards "htop".
    :to_current                              # Create a "Current" symlink.
    :toolchain                               # This will attempt to build a standalone toolchain for compilation, similar to what LFS does.
    :trad                                    # Compile a program in the traditional manner, aka prefix /usr/. The symbol :traditional is an "alias" to this entry point.
    :uchroot_chompile                        # Compile via user-chroot prefix.
    :url_action                              # Support instructions such as /install/php/6.3.1, in particular for www-related use cases.
    :update_all_ruby_gems                    # This will update all ruby .gem files that are registered in the RBT project.
    :update_entry                            # Update a specific program-entry, into the corresponding .yml file.
    :update_kde_application                  # Update all KDE applications (kde apps).
    :update_tags                             # This will update all registered tags.

So, when you want to invoke :update_kde_application then you can simply
do this:

    RBT.action(:update_kde_application)

(Note that <b>RBT.actions()</b> is an alias to RBT.action(). Internally the
RBT project will default to <b>RBT.action()</b> only, though; <b>RBT.actions()</b>
exists mostly as a convenience-alias for e. g. working with IRB, if you
forget the API, e. g. plural or singular - both will work.)

In **February 2022** a **new filter-method** was added that can be applied
to turn a given input argument into a "registered" program. What this
is meant to imply is that, say, you pass in the argument **htop.yml**.
The .yml part is superfluous, so that filter-method would turn **htop.yml**
into **htop**. This is not the only modification that is done there;
the more important take-home message is that the end user shall never
have to wonder about any of this. The rbt project will try to make
sense of the given input at hand, as much as that is possible.

More actions will be added as time permits. There is a secondary advantage
when using actions, by the way. **If** an action is specified, such as
via Symbols, then we can internally change which class and .rb file
handles that action. So perhaps we have some bugs and fixing these
takes too long, but we still want the specified action to work - in
this event we could quickly write a small task that handles the
specified action, without having to worry about side effects.

Note that the above overview does **not** include all available 
actions; some are mostly internal actions that have very little
value for regular users.

The actions may be a bit verbose and not necessarily easy to
read compared to a method.

Consider the following:

    RBT.action(:install_this_rubygem, 'path_to_the.gem')
    RBT.action(:install_this_rubygem, '/tmp/thor-1.2.0.gem')

This would install this rubygem, if it exists locally, e. g.
the <b>thor</b>-gem.

Now compare this to this toplevel method:

    RBT.install_this_rubygem('/tmp/thor-1.2.0.gem')

The second variant is a bit shorter and easier to read, in
my opinion. So it is the better variant, yes?

Well, it depends. Brevity is useful, but think about the
benefit you get via RBT.action(): you can simply call
one unified method (e. g. action()) to do the required
action. And we can add lots of aliases to this, to 
make working with it easier. And you don't have to 
worry about **where** the code resides - you just
use the action without a need to do any manual require
call.

I think if you think this through for a while then you may
realise that RBT.action() is not such a bad idea - it
provides <b>actionable</b> entry points to the whole
RBT suite.

Since as of <b>September 2022</b> all executables that
are part of the RBT suite, under the bin/ subdirectory,
are "actionable". That is they are implemented via
<b>RBT.action()</b> calls. New executables will conform
to this new default. The only two exceptions are bin/rbt
and bin/rbt_config - these two will not use RBT.action().
But who knows - perhaps at some point in time in the
future they may.

## Permanently disabling trying to rename the KDE konsole tab

You can permanently disable the renaming of the KDE konsole
tab via:

    ry --permanently-do-not-rename-tab

## class RBT::KernelConfigSanitizer

class RBT::KernelConfigSanitizer, written in February 2024,
can help ensure a certain linux kernel config (for the
.config file that is typically found at /usr/src/linux/).

It reads a dataset from a .yml file, which is also distributed
via the RBT project. That .yml file is adjusted to my use
cases, so you may have to keep a separate .yml file adjusted
to your use cases.

At any rate, class RBT::KernelConfigSanitizer will read
in the content from that .yml file and ensure that the
.config file has the specified entries. In other words:
we can ensure that the linux kernel that is to be compiled
by you, also has these values. Note that this will only work
if class RBT::KernelConfigSanitizer can find the corresponding
key in the given line (for the whole dataset stored in
.config). In other words: if the configuration option is
NOT part of any line, then it will not be modified at all.
This is done so that we can avoid using potentially deprecating
configuration values, even IF they were specified in the
.yml file. 

## Pseudo Macros in use

Some Pseudo-Macros are used in the RBT Project - at the least in
the past.

This section here details them:

    PROGRAM_NAME    # Will be replaced with the name of
                    # the program, for instance: "htop"
    PROGRAM_VERSION # Will be replaced with the actual
                    # version of the program, example: "1.0.0"


<pre>
26.08.2022: 255 classes
</pre>





## Build and compiling inside of a subdirectory (build directory)

Sometimes you dont want to build in the current directory, but
may want to use a subdirectory instead. (For example, glibc requires
you to build inside a subdirectory).'

To do this from the commandline, simply do one of the following
commands:

    rbt php --subdir=PHP_BUILD_DIRECTORY'

The above would build in the directory called "PHP_BUILD_DIRECTORY".
If this directory does not exist (which is the case usually), then 
the RBT scripts will create that directory.'

The default name for the subdirectory is called
<b class="red">BUILD/</b> and you can do default to
this directory:

    rbt pango -b'

This will create a <b class="red">BUILD/</b> directory and change 
the working directory into it, while compiling.'

In practise, defaulting to the BUILD/ directory is the easiest
solution if you want to compile in your own directory.'

Please also note that you can specify build directories
in the respective cookbook file as well - look at the description
of the variables called `<span class="yel">use_build_directory</span>`, 
and `<span class="yel">use_this_build_directory</span>`.'

Alternative syntax exists as well,of course. If you want to
use the default build directory for a project you compile, you
can pass the option <b>usebuilddir</b> like so.'

    rbt automake --use-build-dir'
    rbt automake usebuilddir'
    rbt htop usebuilddir'
    rbt php use_build_dir'

You can also specify a specific build directory to use.'

One way that this works is via this:

    rbt htop --use-this-build-dir=/Depot/j'

The RBT scripts will append a trailing / if it is a
directory and if it does not yet have a trailing / character
presently, so the above command is the very same as passing
in <b>/Depot/j/</b>.'

If you want to use a build directory, but do not care
about the name, you can also use a random name, like 
so:

    rbt php --use-random-build-directory'

## class RBT::Action::SoftwareManager

This extremely important class was added in September 2022 and has
replaced the older class called <b>RBT::Compile</b>. In December 2022
class RBT::Compile has been deprecated, and in 2024 removed completely;
class RBT::Action::SoftwareManager is now the way to go. RBT::Compile
is no longer available.

class RBT::Action::SoftwareManager has been started from scratch. Note that for the time
being RBT::Compile will co-exist with RBT::Action::SoftwareManager; it may still
receive bug fixes and other updates. But other than that,
the code base in RBT::Action::SoftwareManager should be better, and it may
offer a greater functionality than does RBT::Compile - so in
the long term (future), class RBT::Action::SoftwareManager will become
the new default. It will then be decided whether RBT::Compile
will be retained or not after that.

Note that RBT::Compile will be maintained for a longer time,
so two ways to install something will co-exist. In the long
run RBT::Action::SoftwareManager will likely be better, but you may find
it easier to use RBT::Compile instead for now.

The rewritten class RBT::Action::SoftwareManager has integrated various
improvements. For instance, it is now possible to simply
ignore compilation errors and other errors - this is
sometimes necessary, because RBT erroneously reports
some mistakes that are not real mistakes. The display
and handling of messages has been improved in general -
you can now decide to NOT read the extract-archive
information, which used to be very spammy in the past.

The flag --use-this-program-version is still available,
but a new syntax has been added:

    installer htop@3.1.2

This may even work with locally existing archives.

The following subsections will explain the tasks handled by
class RBT::Action::SoftwareManager in more detail, as this is by
far the most important class of the <b>rbt</b> gem. This is
ongoing - right now many details are not yet explained, so
the following subsections will eventually be expanded.

### Internals of class RBT::Action::SoftwareManager

<b>class RBT::Action::SoftwareManager</b> is the main class of the RBT project, as it allows
us to compile or install a program from source. It is, more or less, <b>the
central entry point to RBT</b> - even though you can invoke the other .rb 
files directly, RBT::Action::SoftwareManager often provides a simpler convenience access
to the disparate functions of the RBT project. It integrates other 
classes, sort of like a <b>glue</b>.

This subsection here will explain a few key decisions made, in the long
run; and will also explain a few internals.

Do not worry if this may be a bit confusing at first - it is meant
primarily for me, and for others who may want to extend the RBT
project one day.

The method set_configure_base_directory(), defined in the file **misc.rb**,
is used to determine the directory where the configure script ought to
reside. That way we can enter a separate build directory yet still be
able to invoke configure (or cmake) at the right directory target.

### Commandline options for class RBT::Action::SoftwareManager

As was already written down somewhere else in this document, you
can pass in several commandline options to class RBT::Action::SoftwareManager.

You can also use commandline options that include 
<b>--</b> and these options can overrule other
configure options, on an ad-hoc basis.

For instance, let's assume that the configure options in a
given yaml file, such as <b>weechat.yml</b>, include an
option such as <b>--enable-gtk</b>. But you don't want
any GTK GUI for Weechat. So either you modify the .yml
file, or you decide to override this flag, on the
commandline, by doing:

    rbt weechat --disable-gtk

This will now overrule the setting in the weechat.yml
file for the given compilation run, and compile
weechat with gtk <b>disabled</b>. That way you can
leave weechat.yml unmodified, yet you are still
able to get the desired change. (For a permanent
change you would have to modify the .yml file of
course.)

If you want to get a quick overview, issue:

    rbt --overview

This should give a brief overview over
the available utility scripts.

### class RBT::Action::SoftwareManager - the commandline option --compile-the-first-entry-in-the-current-working-directory

On my computer system I have done the following alias:

    this → rbt --compile-the-first-entry-in-the-current-working-directory

So, I can then navigate to a directory containing a source archive
that can be compiled. Then I type "this" and hit enter. RBT::Action::SoftwareManager
will proceed to compile the first entry of this directory.

This allows me to be lazy and efficient. I will simply compile the first
entry in any given directory, without having to type the name or even
write the beginning of the name and use '*' as substitution character,
such as via:

    rbt php*.xz
    rbt php*.xz

I recommend that users of the rbt gem also use an alias such as "this",
but of course this is up to them, not me. For me, personally, just
typing "this" is very convenient should I need it.

## class RBT::Action::SoftwareManager: feedback the URL of various programs at the same time

Say that you <b>wish to find out the URL to various programs at the same
time</b>.

You can use this the following commandline invocation for this:

    rbt --url-for-these-programs=php,ruby,python,m4,php

This will show a result such as:

<img src="https://i.imgur.com/F9yA9vr.png" style="margin: 1em">

Entries that are included more than once - such as php in the above
made-up example - will only be shown once.

## BLFS - Beyond Linux From Scratch (and also LFS)

<b>class RBT::Blfs</b> has "support" for BLFS in that it will ... simply
show a URL to the remote BLFS page of a given package, if it exists,
on the commandline.

If you only need to know the URL to the <b>BLFS homepage</b>, to embed
it for display into a webpage perhaps or to merely display it onto the
commandline, you can use the following simple <b>toplevel-API</b> for
this:

    RBT.blfs(:name_of_the_program_goes_in_here)
    RBT.blfs(:openssl) # => "https://www.linuxfromscratch.org/blfs/view/8.1/postlfs/openssl.html"

    # You can also use a String as input to the method rather than a Symbol:
    RBT.blfs('ruby') # => "https://www.linuxfromscratch.org/blfs/view/svn/general/ruby.html"

This will return the remote BLFS page, as URL (a **String**, actually),
if it exists, and if it has been registered in the corresponding 
.yml file (cookbook file for the program at hand; in this example
the file <b>openssl.yml</b>). If no BLFS entry has been registered
then **nil** will be returned by this method.

You can also use class <b>RBT::LFS</b> to build/create a LFS from scratch.
This is presently (as of the year <b>2019</b>) quite incomplete, though,
and will not work. Lots of different things have to be done in the correct
sequence before a LFS can be built from scratch successfully, and possible
errors have to be checked before the build can continue. In the long run,
for the future, this will eventually work, one day - but for now it is an
incomplete stub and not recommended for testing much at all. It is simpler
to use the slow, semi-manual approach for now.

If you wish to quickly <b>paste</b> the BLFS page of a given program onto
the commandline, for display purpose, then you can do something like this:

    rbt php --parseblfs

Since as of <b>September 2021</b> a bin/ script exists for this functionality.
This was already planned back in <b>August 2019</b>, but I finally had a 
good use case (support for my older laptop) to add it. The executable
is called <b>paste_blfs</b> and it can be used in the following way
via the <b>commandline</b>:

    paste_blfs ruby
    paste_blfs htop

Since as of <b>December 2019</b>, it is now also possible to display,
on the commandline, <b>any</b> registered BLFS entry. This will help
in the event that you can not access the xorg-server at the moment,
yet still require information for different packages (I faced
exactly this problem, so I then added that functionality to RBT).

In order for this to work, you evidently need to have a working
**internet connection** available - but in principle, the information
stored in the BLFS project could be zipped up and distributed
too, within the RBT project.

For the time being, though, only pasting is supported - there is
no plan to bundle the information into the RBT project at this
stage in time.

Usage example for this functionality:

    rbt --parse-blfs-page-for=llvm

In <b>December 2019</b> another feature was added - the ability to
make use of the BLFS instructions directly, and run them.

The idea here is that you may wish to compile some program
from source, but may not access a working xorg-server, as
you are working on the commandline only.

Invocation example:

    rbt kerberos --use-blfs-instructions # Compile kerberos in the BLFS way.

Since LFS/BLFS is such a useful project, the RBT suite has some
more support in this regard. This is unsurprising, as the
<b>Linux From Scratch</b> (LFS) Project has instructions
on how to compile programs from source. So it has a somehwat
similar meta-goal, like RBT.

These instructions are immensely useful. A lot of the information
from LFS/BLFS was integrated into the RBT project.

Many individual cookbook yaml files can point towards the
LFS/BLFS page, which will often contain additional useful
information in case you get stuck with something.

You can try to show this URL by doing this:

    blfs curl

This would show the BLFS remote URL of the program called
<b>curl</b>.

Since as of <b>July 2017</b>, you can also directly paste the
content of the remote BLFS webpage onto the terminal, if there
is a remote BLFS page associated with a given program.

The way to do this is as follows:

    rbt gcc --paste-blfs-page

If you want to show all programs that have a blfs entry, use the
following command:

    rbt --show-programs-with-a-blfs-entry

If you want to obtain an Array of all programs containing
a BLFS entry, you can use the following toplevel API:

    RBT.return_all_blfs_entries

This is currently rather slow; I'll look into making it
faster in the future, making use of grep.

If you want to find out how many BLFS entries are registered,
use this toplevel method:

    RBT.n_BLFS_entries?
    
## Licence of this project

Now to some semi-boring legalese, aka the "no warrant disclaimer" in particular.

Forst, the copyright notice:

Copyright 2010-2024 Robert A. Heiler

Up until the beginning of <b>April 2021</b>, the rbt project was using the
<b>GPL-2.0 licence</b> (no later clause).

In <b>April 2021</b>, though, I decided to switch to the <b>MIT</b> licence
instead for this project. The older GPL code will remain available for some
time, most likely at the least a full year, perhaps even longer. But the
older code is now deprecated as far as I am concerned; others would have to
maintain it. I only focus on the MIT variant from this point onward.

You can read up on the MIT licence here:

https://opensource.org/licenses/MIT

To make it even more explicit, let me additionally formulate
the no-warranty disclaimer:

The source code is <b>provided as is</b>. No explicit
guarantees are given of any kind whatsoever.

Whenever possible, bugs will be fixed. However had, do
not expect there to be no bugs in this software suite.
Chances should be fairly high that it will run on
your system.

Why was it decided to switch to MIT rather than GPL?

Well, there are several reasons.

First, and most importantly: while I will continue to maintain the project
here for a long while (I am using it on a daily basis after all), it is not
really a project I particular "care" about in the sense of wanting to
restrict how users use it. It is just a ruby gem, not anything I am using
for a "mission-critical project". It also is not important to me in regards
to my financial status; nothing against donation by interested folks, but I
did not create the project for any of that. I created the project mostly
because I needed to compile software or otherwise install software.

Second, though, the GPL is a strict licence. This can be very
useful - see the Linux Kernel. You may also depend less on 
corporations controlling the whole software stack, so the GPL
has quite laudable goals. But ... is the GPL really important
for a project like this one here? I am not sure. I think you
can already "generate value" if a project is useful, so the 
licence then is of a secondary concern, in particular when
it is a smaller project anyway.

These were my two main reasons. There are a few smaller issues,
such as the MIT licence being <b>much</b> simpler to use and
adhere to, but by and large these were the main reasons.

And if a company ever decides to want to make use of RBT
then I feel flattered, anyway - it means that the project
has some real value after all, right? Otherwise people
would not use it.

Be wary of bugs, though; even the MIT licence comes with a
"no warranty" clause, so always test things first in a
secure environment (chrooted jail environment, for instance,
then you can copy or package the compiled packages to 
wherever you need them(.

While I use this project since over a decade, my use cases
may not be the same as how other people use the project.

Take note that the rbt-gem erroneously had <b>GPL-2.0</b> as
its licence in the last some months (in 2023). This
was a manual error on my behalf, due to rubygems
showing a warning on the commandline about "unspecified
licences". I am not sure why I changed to GPL-2.0 as
a result; perhaps I was working on another project that
was GPL-2.0 licenced and confused the two. Either way when 
the rbt gem was rewritten in the year 2024, this was again
fixed and the MIT licence was reinstated here - apologies
for any confusion in this regard, it was supposed
to be MIT licenced.

## RBT::Gitty

class RBT::Gitty is a helper class. It ultimately wraps over
the "--gitty" that RBT::Installer uses.

The RBT::Gitty class can be used to quickly checkout the
git sources of a project.

So, for instance, if you want to check out the latest
source code of mesa, you could do this via the commandline:

    gitty mesa

This will download mesa and repackage it to today's
timestamp, in dd.mm.yyyy notation.

You can download any program that is registered in the
RBT namespace, if it has a corresponding entry called
<b>git_url</b> in the .yml file. This is how I maintain
this list: I simply change the associated git URL,
such as for github or gitlab, in the corresponding
.yml file.

Since as of March 2024 gitty was slightly extended, in
that it can now work on any arbitrary remote URL that
you pass into this class.

For instance:

    gitty https://github.com/kennylevinsen/seatd

This would download the current git sources from
that remote URL, and repackage it automatically
for you, using a dd.mm.yyyy notation. This functionality
was added because I sometimes found new programs and
just wanted to quickly test whether I can compile it,
so I can now just copy/paste this URL onto the
commandline, as input for <b>gitty</b>.

## RBT::Action::SoftwareManager

class RBT::Action::SoftwareManager was added in March 2024. It
will eventually replace class Installer. The key idea behind
SoftwareManager, aside from fixing a few smaller bugs and
issues, will be to transition into an action-based system.
This means that everything that is important, to be done
by class SoftwareManager, should be handled through
the method called <b>RBT.action()</b> primarily.

The advantage of this approach is that we can easily change
aspects of class SoftwareManager, without having to 
modify the class directly.

This replacement effort may take quite a while, though. For
now, class Installer will remain in place and is still
the preferred variant to be used.

## Querying the prefix to be used

If you have the need to find out the prefix that will be used,
you can issue the following query:

    rbt htop prefix?
    rbt htop --prefix?

## Available programs versions


<pre>
0install                  2.3.14       22 February 2021 https://sourceforge.net/projects/zero-install/files/0install/2.3.14/0install-2.3.14.tar.bz2
3ddesktop                 0.2.9        01 June 2014 https://sourceforge.net/projects/desk3d/files/3ddesktop/0.2.9/3ddesktop-0.2.9.tar.gz
3dpong                    0.5          01 May 2014  https://tuxpaint.org/ftp/unix/x/3dpong/src/3dpong-0.5.tar.gz
a2png                     0.1.5        01 June 2014 http://sourceforge.net/projects/a2png/files/a2png/0.1.5/a2png-0.1.5.tar.gz
a2ps                      4.15.5       25 June 2023 https://ftp.gnu.org/pub/gnu/a2ps/a2ps-4.15.5.tar.gz
a52dec                    0.7.4        01 October 2013 http://liba52.sourceforge.net/files/a52dec-0.7.4.tar.gz
aalib                     1.4rc5       01 January 2013 http://sourceforge.net/projects/aa-project/files/aa-lib/1.4rc5/aalib-1.4rc5.tar.gz
aamath                    0.3          01 May 2014  http://fuse.superglue.se/aamath/aamath-0.3.tar.gz
abcde                     2.8.1        23 October 2017 https://abcde.einval.com/download/abcde-2.8.1.tar.gz
abe                       1.1          01 May 2014  https://sourceforge.net/projects/abe/files/abe/abe-1.1/abe-1.1.tar.gz
abiword                   3.0.5        04 July 2021 https://www.abisource.com/downloads/abiword/3.0.5/source/abiword-3.0.5.tar.gz
abnfgen                   0.17         16 September 2016 http://www.quut.com/abnfgen/abnfgen-0.17.tar.gz
abstk                     0.1          07 February 2016 https://gobolinux.org/abstk/AbsTK-0.1.tar.gz
abuse                     0.8          01 December 2012 http://abuse.zoy.org/raw-attachment/wiki/download/abuse-0.8.tar.gz
accerciser                3.42.0       16 October 2023 https://download.gnome.org/sources/accerciser/3.42/accerciser-3.42.0.tar.xz
accountsservice           22.08.8      07 March 2022 https://www.freedesktop.org/software/accountsservice/accountsservice-22.08.8.tar.xz
acct                      6.6.4        11 November 2019 http://ftp.gnu.org/gnu/acct/acct-6.6.4.tar.bz2
acl                       2.3.2        06 February 2024 https://download.savannah.gnu.org/releases/acl/acl-2.3.2.tar.xz
acoc                      0.7.1        24 November 2019 https://rubygems.org/downloads/acoc-0.7.1.gem
acpi                      1.7          28 February 2023 https://sourceforge.net/projects/acpiclient/files/acpiclient/1.7/acpi-1.7.tar.gz
acpica                    20080701     11 October 2017 http://www.acpica.org/download/acpica-unix-20080701.tar.gz
acpid                     2.0.34       18 September 2022 http://downloads.sourceforge.net/acpid2/acpid-2.0.34.tar.xz
acpitool                  0.5.1        12 October 2017 https://sourceforge.net/projects/acpitool/files/acpitool/0.5.1/acpitool-0.5.1.tar.gz
actioncable               7.0.3.1      28 August 2022 https://rubygems.org/downloads/actioncable-7.0.3.1.gem
actionmailer              7.0.3        27 May 2022  https://rubygems.org/downloads/actionmailer-7.0.3.gem
actionpack                7.0.3.1      09 September 2022 https://rubygems.org/downloads/actionpack-7.0.3.1.gem
actionview                7.0.3.1      26 August 2022 https://rubygems.org/downloads/actionview-7.0.3.1.gem
actionwebservice          1.2.6        21 September 2017 https://rubygems.org/downloads/actionwebservice-1.2.6.gem
activejob                 7.0.3        27 May 2022  https://rubygems.org/downloads/activejob-7.0.3.gem
activemodel               7.0.3        27 May 2022  https://rubygems.org/downloads/activemodel-7.0.3.gem
activerecord              7.0.3        27 May 2022  https://rubygems.org/downloads/activerecord-7.0.3.gem
activeresource            6.0.0        27 May 2022  https://rubygems.org/downloads/activeresource-6.0.0.gem
activestorage             7.0.3        27 May 2022  https://rubygems.org/downloads/activestorage-7.0.3.gem
activesupport             7.0.3        27 May 2022  https://rubygems.org/downloads/activesupport-7.0.3.gem
addressable               2.8.0        27 May 2022  https://rubygems.org/downloads/addressable-2.8.0.gem
adwaitaicontheme          46.0         19 March 2024 https://download.gnome.org/sources/adwaita-icon-theme/46/adwaita-icon-theme-46.0.tar.xz
aegisub                   3.2.2        24 January 2018 http://ftp.aegisub.org/pub/archives/releases/source/aegisub-3.2.2.tar.xz
aeolus                    0.9.7        24 November 2019 http://kokkinizita.linuxaudio.org/linuxaudio/downloads/aeolus-0.9.7.tar.bz2
afew                      2.0.0        24 November 2019 https://files.pythonhosted.org/packages/56/db/75c67cf650f64d5c5a294cbead17856aaadb4517911ba6f5de91d843c16a/afew-2.0.0.tar.gz
afterstep                 2.2.12       21 May 2020  ftp://ftp.afterstep.org/stable/AfterStep-2.2.12.tar.bz2
aircrackng                1.3          18 September 2018 http://download.aircrack-ng.org/aircrack-ng-1.3.tar.gz
airsnort                  0.2.7e       01 October 2013 http://sourceforge.net/projects/airsnort/files/airsnort/airsnort-0.2.7e/airsnort-0.2.7e.tar.gz
airstrike                 6a           01 December 2012 http://icculus.org/airstrike/airstrike-pre6a.tar.gz
aisleriot                 3.22.9       29 September 2019 http://ftp.gnome.org/pub/gnome/sources/aisleriot/3.22/aisleriot-3.22.9.tar.xz
akonadi                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-24.02.2.tar.xz
akonadicalendar           24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-calendar-24.02.2.tar.xz
akonadicalendartools      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-calendar-tools-24.02.2.tar.xz
akonadiconsole            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadiconsole-24.02.2.tar.xz
akonadicontacts           24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-contacts-24.02.2.tar.xz
akonadiimportwizard       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-import-wizard-24.02.2.tar.xz
akonadimime               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-mime-24.02.2.tar.xz
akonadinotes              24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-notes-24.02.2.tar.xz
akonadisearch             24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akonadi-search-24.02.2.tar.xz
akregator                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/akregator-24.02.2.tar.xz
alacarte                  3.52.0       24 March 2024 https://download.gnome.org/sources/alacarte/3.52/alacarte-3.52.0.tar.xz
alien                     8.95         06 October 2015 http://http.debian.net/debian/pool/main/a/alien/alien_8.95.tar.xz
allegro                   5.2.9.1      20 February 2024 https://github.com/liballeg/allegro5/releases/download/5.2.9.1/allegro-5.2.9.1.tar.gz
alligator                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/alligator-24.02.2.tar.xz
alltray                   0.70         12 November 2017 https://launchpad.net/alltray/historic-releases/0.70/+download/alltray-0.70.tar.gz
almanah                   0.12.3       08 March 2021 https://download.gnome.org/sources/almanah/0.12/almanah-0.12.3.tar.xz
alock                     94           01 July 2011 http://alock.googlecode.com/files/alock-94.tar.bz2
alsadriver                1.0.25       20 June 2015 ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.25.tar.bz2
alsafirmware              1.2.4        23 October 2020 https://www.alsa-project.org/files/pub/firmware/alsa-firmware-1.2.4.tar.bz2
alsalib                   1.2.11       30 January 2024 https://www.alsa-project.org/files/pub/lib/alsa-lib-1.2.11.tar.bz2
alsaoss                   1.1.8        26 January 2019 ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.1.8.tar.bz2
alsaplayer                0.99.81      01 June 2013 https://alsaplayer.sourceforge.net/alsaplayer-0.99.81.tar.gz
alsaplugins               1.2.7.1      21 June 2022 https://www.alsa-project.org/files/pub/plugins/alsa-plugins-1.2.7.1.tar.bz2
alsatools                 1.2.5        05 June 2021 https://www.alsa-project.org/files/pub/tools/alsa-tools-1.2.5.tar.bz2
alsautils                 1.2.11       04 April 2024 https://www.alsa-project.org/files/pub/utils/alsa-utils-1.2.11.tar.bz2
amarok                    2.9.0        07 March 2018 https://download.kde.org/stable/amarok/2.9.0/src/amarok-2.9.0.tar.xz
amidiplug                 0.7          01 November 2012 http://www.develia.org/files/amidi-plug-0.7.tar.bz2
amigadepacker             0.04         01 June 2014 http://zakalwe.fi/~shd/foss/amigadepacker/amigadepacker-0.04.tar.bz2
amoebax                   0.2.1        01 January 2013 https://www.emma-soft.com/games/amoebax/download/amoebax-0.2.1.tar.bz2
amphetamine               0.8.10       01 June 2014 http://n.ethz.ch/student/loehrerl/amph/files/amphetamine-0.8.10.tar.bz2
amtk                      5.6.1        17 November 2022 https://download.gnome.org/sources/amtk/5.6/amtk-5.6.1.tar.xz
amule                     2.3.1        01 June 2014 https://sourceforge.net/projects/amule/files/aMule/2.3.1/aMule-2.3.1.tar.xz
analitza                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/analitza-24.02.2.tar.xz
analogger                 1.1.0        08 July 2018 https://rubygems.org/downloads/analogger-1.1.0.gem
angelfish                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/angelfish-24.02.2.tar.xz
anjuta                    3.34.0       09 September 2019 https://ftp.gnome.org/pub/gnome/sources/anjuta/3.34/anjuta-3.34.0.tar.xz
anjutaextras              3.26.0       11 September 2017 http://ftp.gnome.org/pub/gnome/sources/anjuta-extras/3.26/anjuta-extras-3.26.0.tar.xz
ansi                      1.5.0        09 January 2018 https://rubygems.org/downloads/ansi-1.5.0.gem
antiword                  0.37         01 May 2014  http://www.winfield.demon.nl/linux/antiword-0.37.tar.gz
anyremote                 6.7.3        07 December 2019 https://sourceforge.net/projects/anyremote/files/anyremote/6.7.3/anyremote-6.7.3.tar.gz
aoetools                  36           22 February 2017 https://downloads.sourceforge.net/project/aoetools/aoetools/aoetools-36.tar.gz
apacheant                 1.10.2       19 February 2018 https://archive.apache.org/dist/ant/source/apache-ant-1.10.2.tar.xz
apachemaven               3.8.6        24 May 2022  https://dlcdn.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.6-bin.tar.gz
apl                       1.8          15 December 2019 http://ftp.gnu.org/gnu/apl/apl-1.8.tar.gz
apophenia                 19.01.2023   18 January 2023 http://osdn.dl.sourceforge.net/sourceforge/apophenia/apophenia-19.01.2023.tgz
aporia                    27.12.2011   01 June 2014 aporia-27.12.2011
appdatatools              0.1.8        01 September 2014 http://people.freedesktop.org/~hughsient/releases/appdata-tools-0.1.8.tar.xz
appfs                     1.14         23 September 2020 http://www.rkeene.org/devel/appfs/appfs-1.14.tar.gz
appres                    1.0.6        04 April 2022 https://www.x.org/releases/individual/app/appres-1.0.6.tar.xz
appstream                 1.0.2        07 March 2024 https://www.freedesktop.org/software/appstream/releases/AppStream-1.0.2.tar.xz
appstreamglib             05.04.2024   06 November 2022 https://people.freedesktop.org/~hughsient/appstream-glib/releases/appstream-glib-05.04.2024.tar.xz
apr                       1.7.3        02 April 2023 https://dlcdn.apache.org//apr/apr-1.7.3.tar.gz
apricots                  0.2.6        01 May 2014  http://www.fishies.org.uk/apricots-0.2.6.tar.gz
aproc                     0.1          22 March 2016 http://stinfwww.informatik.uni-leipzig.de/~mai00bgn/aproc/tb/aproc-0.1.tar.bz2
aprutil                   1.6.3        03 February 2023 http://archive.apache.org/dist/apr/apr-util-1.6.3.tar.bz2
apt                       2.1.7        06 August 2019 http://ftp.debian.org/debian/pool/main/a/apt/apt_2.1.7.tar.xz
apulse                    02.10.2017   02 October 2017 http://freedesktop.org/software/pulseaudio/releases/apulse-02.10.2017
arandr                    0.1.10       01 August 2014 http://christian.amsuess.com/tools/arandr/files/arandr-0.1.10.tar.gz
aravis                    0.8.10       13 May 2021  https://download.gnome.org/sources/aravis/0.8/aravis-0.8.10.tar.xz
archivezip                1.68         16 March 2020 https://cpan.metacpan.org/authors/id/P/PH/PHRED/Archive-Zip-1.68.tar.gz
ardour                    5.12         26 May 2022  https://github.com/Ardour/ardour/archive/5.12.tar.gz
arel                      9.0.0        22 July 2018 https://rubygems.org/downloads/arel-9.0.0.gem
argtable2                 13           09 September 2018 https://sourceforge.net/projects/argtable/files/argtable/argtable-2.13/argtable2-13.tar.gz
aria2                     1.36.0       06 October 2021 https://github.com/aria2/aria2/releases/download/release-1.36.0/aria2-1.36.0.tar.xz
arianna                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/arianna-24.02.2.tar.xz
aris                      2.2          11 December 2017 https://ftp.gnu.org/gnu/aris/aris-2.2.tar.gz
ark                       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/ark-24.02.2.tar.xz
armagetronad              0.2.9.1.0    14 April 2021 https://launchpad.net/armagetronad/0.2.9/0.2.9.1.0/+download/armagetronad-0.2.9.1.0.tbz
art                       5.3          01 December 2021 https://files.pythonhosted.org/packages/97/74/6d99019856b638a697547107e5904513452ff01f8036b52307eabdddc500/art-5.3.tar.gz
artanis                   0.4.1        26 December 2019 http://ftp.gnu.org/pub/gnu/artanis/artanis-0.4.1.tar.bz2
artemis                   v17.0.1      26 May 2020  ftp://ftp.sanger.ac.uk/pub4/resources/software/artemis/v17/v17.0.1/artemis-v17.0.1.jar
artikulate                24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/artikulate-24.02.2.tar.xz
asc                       2.6.1.0      14 February 2016 https://sourceforge.net/projects/asc-hq/files/ASC%20Source/2.6.1/asc-2.6.1.0.tar.bz2
ascal                     0.1.1        01 May 2014  https://sourceforge.net/projects/ascal/files/ascal/the%20last%20one%20this%20year/ascal-0.1.1.tar.bz2
asciidoc                  9.0.2        23 July 2020 https://github.com/asciidoc/asciidoc-py3/releases/download/9.0.2/asciidoc-9.0.2.tar.gz
asciidoctor               2.0.17       27 May 2022  https://rubygems.org/downloads/asciidoctor-2.0.17.gem
asciimatics               1.13.0       26 March 2022 https://files.pythonhosted.org/packages/ef/14/9021858085fc372a1df52bc3f216aa5defa4ba743859654e4bd9e3f85fcb/asciimatics-1.13.0.tar.gz
aspell                    0.60.8.1     01 March 2024 https://ftp.gnu.org/gnu/aspell/aspell-0.60.8.1.tar.gz
ast                       2.4.2        15 April 2021 https://rubygems.org/downloads/ast-2.4.2.gem
asunder                   2.9.5        09 January 2020 http://littlesvr.ca/asunder/releases/asunder-2.9.5.tar.bz2
asymptote                 2.88         11 March 2024 https://sourceforge.net/projects/asymptote/files/2.88/asymptote-2.88tgz
aterm                     1.0.1        01 May 2014  ftp://ftp.afterstep.org/apps/aterm/aterm-1.0.1.tar.bz2
atk                       2.38.0       25 March 2022 https://download.gnome.org/sources/atk/2.38/atk-2.38.0.tar.xz
atkmm                     2.36.3       08 February 2024 https://download.gnome.org/sources/atkmm/2.36/atkmm-2.36.3.tar.xz
atomix                    3.34.0       11 January 2020 http://ftp.gnome.org/pub/gnome/sources/atomix/3.34/atomix-3.34.0.tar.xz
atool                     0.39.0       01 May 2014  http://savannah.nongnu.org/download/atool/atool-0.39.0.tar.gz
atril                     1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/atril-1.28.0.tar.xz
atspi                     1.32.0       01 December 2012 http://ftp.gnome.org/pub/gnome/sources/at-spi/1.32/at-spi-1.32.0.tar.bz2
atspi2atk                 2.38.0       13 September 2020 http://ftp.gnome.org/pub/gnome/sources/at-spi2-atk/2.38/at-spi2-atk-2.38.0.tar.xz
atspi2core                2.52.0       20 March 2024 https://download.gnome.org/sources/at-spi2-core/2.52/at-spi2-core-2.52.0.tar.xz
attal                     1.0rc1       01 May 2014  http://www.attal-thegame.org/base.php?langue=en&page=accueil
attica                    5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/attica-5.115.0.tar.xz
attr                      2.5.2        07 February 2024 https://download.savannah.gnu.org/releases/attr/attr-2.5.2.tar.gz
attrs                     22.2.0       17 March 2024 https://files.pythonhosted.org/packages/source/a/attrs/attrs-22.2.0.tar.gz
aubio                     0.4.7        06 June 2019 https://aubio.org/pub/aubio-0.4.7.tar.bz2
audacious                 4.3          07 March 2023 https://distfiles.audacious-media-player.org/audacious-4.3.tar.bz2
audaciousplugins          4.1          11 May 2021  https://distfiles.audacious-media-player.org/audacious-plugins-4.1.tar.bz2
audacityhtml?dwl=audacitys 3.2.0        23 September 2022 https://www.fosshub.com/Audacity.html?dwl=audacity-sources-3.2.0.tar.gz
audiere                   1.9.4        01 May 2014  http://prdownloads.sourceforge.net/audiere/audiere-1.9.4.tar.gz
audiocdkio                24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/audiocd-kio-24.02.2.tar.xz
audiofile                 0.3.6        01 May 2014  https://github.com/downloads/mpruett/audiofile/audiofile-0.3.6.tar.gz
audiotube                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/audiotube-24.02.2.tar.xz
augeas                    1.12.0       03 February 2020 http://download.augeas.net/augeas-1.12.0.tar.gz
aumix                     2.9.1        17 November 2015 http://sourceforge.net/projects/aumix/files/aumix/2.9.1/aumix-2.9.1.tar.bz2
aurabrowser               5.27.11      06 March 2024 https://download.kde.org/stable/plasma/5.27.11/aura-browser-5.27.11.tar.xz
autoconf                  2.72         23 December 2023 https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz
autoconfarchive           2023.02.20   22 February 2023 https://ftp.gnu.org/pub/gnu/autoconf-archive/autoconf-archive-2023.02.20.tar.xz
autofs                    5.1.9        11 November 2023 https://www.kernel.org/pub/linux/daemons/autofs/v5/autofs-5.1.9.tar.xz
autogen                   5.18.16      09 September 2018 https://ftp.gnu.org/pub/gnu/autogen/rel5.18.16/autogen-5.18.16.tar.xz
automake                  1.16.5       04 October 2021 https://ftp.gnu.org/gnu/automake/automake-1.16.5.tar.xz
automoc4                  0.9.88       01 January 2014 http://download.kde.org/stable/automoc4/0.9.88/automoc4-0.9.88.tar.bz2
autotoolset               0.11.4       01 May 2014  autotoolset-0.11.4
autovivification          0.18         16 September 2020 http://search.cpan.org/CPAN/authors/id/V/VP/VPIT/autovivification-0.18.tar.gz
avahi                     0.8          02 March 2020 https://avahi.org/download/avahi-0.8.tar.gz
avantwindownavigator      0.4.2        01 September 2014 https://launchpad.net/awn/0.4/0.4.2/+download/avant-window-navigator-0.4.2.tar.gz
avc                       0.8.2        01 May 2014  http://avc.inrim.it/dist/avc-0.8.2.tar.gz
avidemux                  2.7.6        07 March 2021 http://downloads.sourceforge.net/avidemux/avidemux_2.7.6.tar.gz
7                         0.7.45       01 May 2014  https://sourceforge.net/projects/avifile/files/avifile/0.7.45-20060306/avifile-0.7-0.7.45.tar.bz2
avinfo                    1.0a12       01 May 2014  http://shounen.ru/soft/avinfo/avinfo-1.0a16.zip
awesome                   4.3          28 January 2019 https://github.com/awesomeWM/awesome/releases/download/v4.3/awesome-4.3.tar.xz
axel                      2.17.11      10 September 2022 https://github.com/axel-download-accelerator/axel/releases/download/v2.17.11/axel-2.17.11.tar.xz
axtls                     2.1.5        03 May 2020  https://sourceforge.net/projects/axtls/files/2.1.5/axTLS-2.1.5.tar.gz
axv                       0.2          10 May 2020  https://sourceforge.net/projects/axv/files/axv/0.2/axv.0.2.tar.gz
b43fwcutter               015          01 May 2014  http://bues.ch/b43/fwcutter/b43-fwcutter-015.tar.bz2
babl                      0.1.108      08 March 2024 https://download.gimp.org/pub/babl/0.1/babl-0.1.108.tar.xz
backports                 3.23.0       27 May 2022  https://rubygems.org/downloads/backports-3.23.0.gem
bacula                    9.6.3        03 May 2020  https://sourceforge.net/projects/bacula/files/bacula/9.6.3/bacula-9.6.3.tar.gz
bakery                    2.5.1        01 May 2014  http://ftp.gnome.org/pub/GNOME/sources/bakery/2.5/bakery-2.5.1.tar.bz2
ballbuster                1.1          01 January 2013 http://www.patrickavella.com/ballbuster-1.1.tar.bz2
baloo                     5.99.0       10 October 2022 https://download.kde.org/stable/frameworks/5.99/baloo-5.99.0.tar.xz
baloowidgets              24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/baloo-widgets-24.02.2.tar.xz
balsa                     2.6.4        24 September 2022 https://pawsa.fedorapeople.org/balsa/balsa-2.6.4.tar.xz
bandit                    1.5.1        02 February 2019 https://files.pythonhosted.org/packages/c9/60/2c967faf70596fcef42a0737c63fe1321b8e51e15eec8f7883e333eba5a5/bandit-1.5.1.tar.gz
baobab                    46.0         22 March 2024 https://download.gnome.org/sources/baobab/46/baobab-46.0.tar.xz
barcode                   0.99         11 May 2020  https://ftp.gnu.org/gnu/barcode/barcode-0.99.tar.xz
barrage                   1.0.6        04 March 2023 https://sourceforge.net/projects/lgames/files/barrage/barrage-1.0.6.tar.gz
bash                      5.2.21       10 November 2023 https://ftp.gnu.org/gnu/bash/bash-5.2.21.tar.gz
bashcompletion            2.10         11 May 2020  https://github.com/scop/bash-completion/releases/download/2.10/bash-completion-2.10.tar.xz
bazar                     1.3.1        15 May 2020  https://www.epfl.ch/labs/cvlab/wp-content/uploads/2018/08/bazar-1.3.1.tar.gz
bc                        6.7.5        07 February 2024 https://github.com/gavinhoward/bc/releases/download/6.7.5/bc-6.7.5.tar.xz
bcftools                  1.15.1       05 August 2022 https://sourceforge.net/projects/samtools/files/samtools/1.15.1/bcftools-1.15.1.tar.bz2
bchunk                    1.2.2        22 May 2020  https://github.com/hessu/bchunk/archive/release/bchunk-1.2.2.tar.gz
bdftopcf                  1.1          09 November 2017 https://www.x.org/releases/individual/app/bdftopcf-1.1.tar.gz
beagle                    0.3.6        01 May 2014  ftp://ftp.gnome.org/pub/GNOME/sources/beagle/0.3/beagle-0.3.6.tar.bz2
bedtools                  2.30.0       27 December 2021 https://github.com/arq5x/bedtools2/releases/download/v2.30.0/bedtools-2.30.0.tar.gz
beecrypt                  4.2.1        01 May 2014  https://sourceforge.net/projects/beecrypt/files/beecrypt/4.2.1/beecrypt-4.2.1.tar.gz
beforelight               1.0.6        29 January 2023 https://xorg.freedesktop.org/releases/individual/app/beforelight-1.0.6.tar.xz
benchmarkips              2.10.0       27 May 2022  https://rubygems.org/downloads/benchmark-ips-2.10.0.gem
bettererrors              2.9.1        15 April 2021 https://rubygems.org/downloads/better_errors-2.9.1.gem
bftpd                     5.0          29 October 2018 https://sourceforge.net/projects/bftpd/files/bftpd/bftpd-5.0/bftpd-5.0.tar.gz
bigdecimal                3.1.2        27 May 2022  https://rubygems.org/downloads/bigdecimal-3.1.2.gem
bigreqsproto              1.1.2        01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/bigreqsproto-1.1.2.tar.bz2
bijiben                   40.1         30 April 2021 https://download.gnome.org/sources/bijiben/40/bijiben-40.1.tar.xz
biloba                    0.9.3        12 March 2019 https://sourceforge.net/projects/biloba/files/Biloba/0.9.3/biloba-0.9.3.tar.gz
bind                      9.19.11      15 March 2023 https://ftp.isc.org/isc/bind9/9.19.11/bind-9.19.11.tar.xz
biniax                    1.2          01 January 2013 http://mordred.dir.bg/biniax/download.htm
binutils                  15.04.2024   15 April 2024 https://ftp.gnu.org/gnu/binutils/binutils-2.42.tar.gz
bio                       2.0.4        17 September 2022 https://rubygems.org/downloads/bio-2.0.4.gem
bioperl                   1.007002     02 January 2018 https://cpan.metacpan.org/authors/id/C/CJ/CJFIELDS/BioPerl-1.007002.tar.gz
biopython                 1.83         09 April 2024 http://biopython.org/DIST/biopython-1.83.tar.gz
biosdevname               0.7.2        15 May 2020  http://linux.dell.com/files/biosdevname/biosdevname-0.7.2/biosdevname-0.7.2.tar.gz
bird                      2.0.7        05 March 2021 https://bird.network.cz/download/bird-2.0.7.tar.gz
bison                     3.8.2        25 September 2021 ftp://ftp.gnu.org/gnu/bison/bison-3.8.2.tar.xz
bitlbee                   3.6          15 May 2020  http://get.bitlbee.org/src/bitlbee-3.6.tar.gz
bitmap                    1.1.1        20 February 2024 https://www.x.org/releases/individual/app/bitmap-1.1.1.tar.xz
bittorrent                4.4.0        01 June 2014 http://www.bittorrent.com/dl/BitTorrent-4.4.0.tar.gz
bkchem                    0.13.0       01 February 2014 http://bkchem.zirael.org/download/bkchem-0.13.0.tar.gz
blackbox                  0.77         06 March 2024 https://github.com/bbidulock/blackboxwm/releases/download/0.77/blackbox-0.77.tar.lz
blender                   3.3.0        07 September 2022 https://download.blender.org/source/blender-3.3.0.tar.xz
bless                     0.5.2        01 November 2012 http://download.gna.org/bless/bless-0.5.2.tar.gz
blessings                 1.7          16 May 2020  https://files.pythonhosted.org/packages/5c/f8/9f5e69a63a9243448350b44c87fae74588aa634979e6c0c501f26a4f6df7/blessings-1.7.tar.gz
blinken                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/blinken-24.02.2.tar.xz
blobwars                  1.04         01 January 2013 http://www.parallelrealities.co.uk/download.php?file=blobwars-1.04-1.tar.gz&type=zip
blocaled                  0.2          22 December 2019 https://github.com/pierre-labastie/blocaled/releases/download/v0.2/blocaled-0.2.tar.xz
blockattack               2.5.0        15 May 2020  https://github.com/blockattack/blockattack-game/releases/download/v2.5.0/blockattack-linux-2.5.0.tar.bz2
bluedevil                 6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/bluedevil-6.0.2.tar.xz
bluefish                  1.0.7        26 July 2017 http://www.bennewitz.com/bluefish/stable/source/bluefish-1.0.7.tar.bz2
blueman                   2.4.1        09 April 2024 https://github.com/blueman-project/blueman/releases/download/2.4.1/blueman-2.4.1.tar.xz
bluez                     5.74         15 April 2024 https://mirrors.edge.kernel.org/pub/linux/bluetooth/bluez-5.74.tar.xz
bluezalsa                 11.09.2022   11 September 2022 bluez-alsa-11.09.2022
bluezgnome                0.14         01 June 2014 http://www.kernel.org/pub/linux/bluetooth/bluez-gnome-0.14.tar.gz
bluezqt                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/bluez-qt-5.115.0.tar.xz
bluezutils                2.25         28 July 2016 http://bluez.sf.net/download/bluez-utils-2.25.tar.gz
bodr                      6            01 May 2014  http://www.blueobelisk.org/
bogofilter                1.2.5        21 October 2019 https://sourceforge.net/projects/bogofilter/files/bogofilter-stable/bogofilter-1.2.5.tar.xz
bomber                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/bomber-24.02.2.tar.xz
bomberclone               0.11.9       10 October 2017 https://sourceforge.net/projects/bomberclone/files/bomberclone/bomberclone-0.11.9.tar.gz
bombic                    0.0.1        01 January 2013 https://sourceforge.net/projects/bombic/files/bombic/Bombic%200.0.1/bombic-0.0.1.tar.gz
bomns                     0.99.1       01 June 2014 http://ovh.dl.sourceforge.net/sourceforge/greenridge/bomns-0.99.1.tar.bz2
bookify                   2.9.0        17 June 2020 https://rubygems.org/downloads/bookify-2.9.0.gem
boost                     1.84.0       01 February 2024 https://sourceforge.net/projects/boost/files/boost/1.84.0/boost_1_84_0.tar.bz2
boswars                   2.7          01 August 2013 https://www.boswars.org/dist/releases/boswars-2.7.tar.gz
botocore                  1.12.146     12 May 2019  https://files.pythonhosted.org/packages/5a/4b/85cd24763385a680df8de460be28d195f44880a9727fe34b71273a9cdd95/botocore-1.12.146.tar.gz
bovo                      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/bovo-24.02.2.tar.xz
brasero                   3.12.2       01 August 2017 http://ftp.gnome.org/pub/gnome/sources/brasero/3.12/brasero-3.12.2.tar.xz
breeze                    6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/breeze-6.0.2.tar.xz
breezegrub                6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/breeze-grub-6.0.2.tar.xz
breezegtk                 6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/breeze-gtk-6.0.2.tar.xz
breezeicons               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/breeze-icons-5.115.0.tar.xz
breezeplymouth            6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/breeze-plymouth-6.0.2.tar.xz
bridgeutils               1.7.1        27 March 2021 https://mirrors.edge.kernel.org/pub/linux/utils/net/bridge-utils/bridge-utils-1.7.1.tar.xz
briquolo                  0.5.7        01 June 2014 http://briquolo.free.fr/download/briquolo-0.5.7.tar.bz2
brlcad                    7.26.0       22 February 2017 https://sourceforge.net/projects/brlcad/files/BRL-CAD%20Source/7.26.0/brlcad-7.26.0.tar.bz2
brltty                    6.0          25 February 2019 http://mielke.cc/brltty/archive/brltty-6.0.tar.xz
brotli                    1.0.9        28 August 2020 https://github.com/google/brotli/archive/v1.0.9/brotli-v1.0.9.tar.gz
bsc                       bsc          01 June 2014 http://www.beesoft.org/download/bsc_2.27_src.tar.gz
btrbk                     0.27.1       06 December 2018 https://digint.ch/download/btrbk/releases/btrbk-0.27.1.tar.xz
btrfsprogs                v6.8         29 March 2024 https://mirrors.edge.kernel.org/pub/linux/kernel/people/kdave/btrfs-progs/btrfs-progs-v6.8.tar.xz
bubblewrap                0.9.0        29 March 2024 https://github.com/containers/bubblewrap/releases/download/v0.9.0/bubblewrap-0.9.0.tar.xz
bubbros                   1.6          01 June 2014 https://launchpad.net/ubuntu/+source/bubbros/1.6.2-1
budgiedesktop             10.5.3       28 April 2021 https://github.com/solus-project/budgie-desktop/releases/download/v10.5.3/budgie-desktop-v10.5.3.tar.xz
bugbuddy                  2.32.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/bug-buddy/2.32/bug-buddy-2.32.0.tar.bz2
builder                   3.2.4        28 May 2020  https://rubygems.org/downloads/builder-3.2.4.gem
buildroot                 2020.02.1    30 May 2020  https://git.busybox.net/buildroot/snapshot/buildroot-2020.02.1.tar.gz
buildstream               1.6.1        07 September 2021 https://download.gnome.org/sources/BuildStream/1.6/BuildStream-1.6.1.tar.xz
bullet                    3.09         17 April 2021 https://github.com/bulletphysics/bullet3/archive/bullet-3.09.tar.gz
bumprace                  1.5.8        30 May 2020  https://github.com/karlb/bumprace/archive/1.5.8.tar.gz
bundler                   2.3.16       22 June 2022 https://rubygems.org/downloads/bundler-2.3.16.gem
burgerspace               1.9.3        31 May 2020  http://perso.b2b2c.ca/~sarrazip/dev/burgerspace-1.9.3.tar.gz
businessisbn              3.005        13 December 2019 https://www.cpan.org/authors/id/B/BD/BDFOY/Business-ISBN-3.005.tar.gz
busybox                   1.36.1       19 May 2023  https://www.busybox.net/downloads/busybox-1.36.1.tar.bz2
butt                      0.1.17       04 March 2019 http://sourceforge.net/projects/butt/files/butt/butt-0.1.17/butt-0.1.17.tar.gz
byebug                    11.1.3       28 May 2020  https://rubygems.org/downloads/byebug-11.1.3.gem
bytename                  1.12         01 June 2020 http://billposer.org/Software/Downloads/Bytename-1.12.tar.gz
bzip2                     1.0.8        14 July 2019 https://sourceware.org/pub/bzip2/bzip2-1.0.8.tar.gz
bzr                       2.7.0        14 March 2017 https://launchpad.net/bzr/2.7/2.7.0/+download/bzr-2.7.0.tar.gz
cabextract                1.9.1        03 June 2020 https://www.cabextract.org.uk/cabextract-1.9.1.tar.gz
cachetools                5.3.2        28 October 2023 https://files.pythonhosted.org/packages/10/21/1b6880557742c49d5b0c4dcf0cf544b441509246cdd71182e0847ac859d5/cachetools-5.3.2.tar.gz
cacti                     1.2.13       14 July 2020 http://www.cacti.net/downloads/cacti-1.2.13.tar.gz
cairo                     11.03.2024   30 January 2024 https://www.cairographics.org/releases/cairo-1.18.0.tar.xz
cairodock                 3.4.1        04 March 2017 https://github.com/Cairo-Dock/cairo-dock-core/releases/download/3.4.1/cairo-dock-3.4.1.tar.gz
cairomm                   1.18.0       21 March 2024 https://www.cairographics.org/releases/cairomm-1.18.0.tar.xz
caja                      1.28.0       21 February 2024 https://pub.mate-desktop.org/releases/1.28/caja-1.28.0.tar.xz
cajadropbox               1.24.0       07 December 2022 https://pub.mate-desktop.org/releases/1.24/caja-dropbox-1.24.0.tar.xz
cajaextensions            1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/caja-extensions-1.28.0.tar.xz
cajun                     4.2          01 June 2014 https://sourceforge.net/projects/cajun/files/cajun/4.2/cajun-4.2.tar.gz
cal3d                     0.11.0       28 July 2016 http://download.gna.org/cal3d/sources/cal3d-0.11.0.tar.gz
calendarsupport           24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/calendarsupport-24.02.2.tar.xz
calf                      0.90.0       28 November 2017 https://github.com/calf-studio-gear/calf/archive/0.90.0.tar.gz
calibre                   7.8.0        05 April 2024 https://download.calibre-ebook.com/7.8.0/calibre-7.8.0.tar.xz
calindori                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/calindori-24.02.2.tar.xz
callgrind                 0.9.12       01 June 2014 https://kcachegrind.sourceforge.net/callgrind-0.9.12.tar.gz
calligra                  3.2.1        17 June 2020 https://download.kde.org/stable/calligra/3.2.1/calligra-3.2.1.tar.xz
camping                   2.1.532      30 November 2017 https://rubygems.org/downloads/camping-2.1.532.gem
cantarellfonts            0.303.1      10 December 2021 https://download.gnome.org/sources/cantarell-fonts/0.303/cantarell-fonts-0.303.1.tar.xz
cantor                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/cantor-24.02.2.tar.xz
capybara                  3.37.1       27 May 2022  https://rubygems.org/downloads/capybara-3.37.1.gem
capybaramechanize         1.12.0       27 May 2022  https://rubygems.org/downloads/capybara-mechanize-1.12.0.gem
cares                     1.28.1       31 March 2024 https://c-ares.org/download/c-ares-1.28.1.tar.gz
caribou                   0.4.20       16 February 2016 http://ftp.gnome.org/pub/GNOME/sources/caribou/0.4/caribou-0.4.20.tar.xz
castlecombat              0.8.1        28 July 2016 http://prdownloads.sourceforge.net/castle-combat/castle-combat-0.8.1.tar.gz
caxlsx                    3.2.0        27 May 2022  https://rubygems.org/downloads/caxlsx-3.2.0.gem
cbase                     1.3.7        28 September 2019 http://www.hyperrealm.com/packages/cbase-1.3.7.tar.gz
cbindgen                  0.26.0       11 September 2022 https://github.com/mozilla/cbindgen/archive/refs/tags/0.26.0.tar.gz
ccache                    4.8.2        14 June 2023 https://github.com/ccache/ccache/releases/download/v4.8.2/ccache-4.8.2.tar.gz
ccaudio2                  2.2.0        19 March 2019 http://ftp.gnu.org/pub/gnu/ccaudio/ccaudio2-2.2.0.tar.gz
ccmath                    2.2.1        01 June 2014 http://www.ibiblio.org/pub/Linux/libs/ccmath-2.2.1.tar.gz
cdemuclient               3.2.1        27 June 2020 http://downloads.sourceforge.net/cdemu/cdemu-client-3.2.1.tar.bz2
cdemudaemon               3.0.4        28 July 2016 http://downloads.sourceforge.net/cdemu/cdemu-daemon-3.0.4.tar.bz2
cdogs                     0.7.3        22 May 2020  https://github.com/cxong/cdogs-sdl/archive/0.7.3.tar.gz
cdparanoia                3.10.2       01 June 2014 https://xiph.org/paranoia/down.html
cdrdao                    1.2.4        28 June 2020 https://sourceforge.net/projects/cdrdao/files/cdrdao-1.2.4.tar.bz2
cdrkit                    1.1.11       01 June 2014 http://cdrkit.org/releases/cdrkit-1.1.11.tar.gz
cdrtools                  3.02a09      29 May 2021  https://sourceforge.net/projects/cdrtools/files/alpha/cdrtools-3.02a09.tar.gz
ceferino                  0.97.8       01 June 2014 http://www.loosersjuegos.com.ar/_media/juegos/ceferino/descargas/ceferino-0.97.8.tar.gz
cegui                     0.8.7        30 June 2020 http://prdownloads.sourceforge.net/crayzedsgui/cegui-0.8.7.tar.bz2
celt                      0.11.3       08 August 2016 http://downloads.xiph.org/releases/celt/celt-0.11.3.tar.gz
centericq                 4.21.0       31 October 2017 http://thekonst.net/download/centericq-4.21.0.tar.bz2
ceph                      15.2.4       02 July 2020 http://download.ceph.com/tarballs/ceph-15.2.4.tar.gz
certifi                   2019.11.28   01 December 2019 https://files.pythonhosted.org/packages/41/bf/9d214a5af07debc6acf7f3f257265618f1db242a3f8e49a9b516f24523a6/certifi-2019.11.28.tar.gz
cervisia                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/cervisia-24.02.2.tar.xz
cfengine                  3.16.0       03 July 2020 https://cfengine-package-repos.s3.amazonaws.com/tarballs/cfengine-3.16.0.tar.gz
cffi                      1.15.0       13 February 2022 https://files.pythonhosted.org/packages/00/9e/92de7e1217ccc3d5f352ba21e52398372525765b2e0c4530e6eb2ba9282a/cffi-1.15.0.tar.gz
cfitsio                   4.4.0        05 April 2024 https://heasarc.gsfc.nasa.gov/FTP/software/fitsio/c/cfitsio-4.4.0.tar.gz
cflow                     1.7          30 December 2021 https://ftp.gnu.org/pub/gnu/cflow/cflow-1.7.tar.xz
cgiirc                    0.5.9        04 July 2020 https://sourceforge.net/projects/cgiirc/files/cgi-irc/0.5.9/cgiirc-0.5.9.tar.gz
cgilib                    0.6          01 June 2014 http://www.infodrom.org/projects/cgilib/download/cgilib-0.6.tar.gz
changepassword            0.9          01 June 2014 http://prdownloads.sourceforge.net/changepassword/changepassword-0.9.tar.gz
char                      char         01 June 2014 http://ltsword.allegronetwork.com/char-linux.tar.gz
charlix                   0.4          01 June 2014 http://charlix.sourceforge.net/charlix-0.4.tar.gz
charsetnormalizer         2.0.9        06 December 2021 https://files.pythonhosted.org/packages/68/e4/e014e7360fc6d1ccc507fe0b563b4646d00e0d4f9beec4975026dd15850b/charset-normalizer-2.0.9.tar.gz
check                     0.15.2       09 August 2020 https://github.com/libcheck/check/releases/download/0.15.2/check-0.15.2.tar.gz
checkinstall              1.6.2        01 June 2014 http://asic-linux.com.mx/~izto/checkinstall/files/source/checkinstall-1.6.2.tar.gz
cheese                    44.0         10 April 2023 https://download.gnome.org/sources/cheese/44/cheese-44.0.tar.xz
cheetah                   2.4.4        15 January 2019 https://files.pythonhosted.org/packages/cd/b0/c2d700252fc251e91c08639ff41a8a5203b627f4e0a2ae18a6b662ab32ea/Cheetah-2.4.4.tar.gz
chemtool                  1.6.14       01 March 2014 http://ruby.chemie.uni-freiburg.de/~martin/chemtool/chemtool-1.6.14.tar.gz
cherokee                  1.2.99       01 April 2014 http://www.cherokee-project.com/download/1.2/1.2.99/cherokee-1.2.99.tar.gz
childprocess              4.1.0        27 May 2022  https://rubygems.org/downloads/childprocess-4.1.0.gem
chkrootkit                0.49         01 June 2014 ftp://ftp.pangeia.com.br/pub/seg/pac/chkrootkit-0.49.tar.gz
chmlib                    0.40         17 March 2017 http://www.jedrea.com/chmlib/chmlib-0.40.tar.gz
chromaprint               1.4.2        22 September 2018 https://bitbucket.org/acoustid/chromaprint/downloads/chromaprint-1.4.2.tar.gz
chromegnomeshell          10.1         02 October 2018 http://ftp.gnome.org/pub/gnome/sources/chrome-gnome-shell/10.1/chrome-gnome-shell-10.1.tar.xz
chromium                  64.0.3282.186 28 September 2019 https://ftp.osuosl.org/pub/blfs/conglomeration/chromium/chromium-64.0.3282.186.tar.xz
chromiumbsu               0.9.16.1     01 January 2017 https://sourceforge.net/projects/chromium-bsu/files/Chromium%20B.S.U.%20source%20code/chromium-bsu-0.9.16.1.tar.gz
chronic                   0.10.2       22 May 2020  https://rubygems.org/downloads/chronic-0.10.2.gem
chronojump                2.2.0        09 January 2022 https://download.gnome.org/sources/chronojump/2.2/chronojump-2.2.0.tar.xz
chrpath                   0.16         31 October 2015 https://alioth.debian.org/frs/download.php/latestfile/813/chrpath-0.16.tar.gz
chunkypng                 1.4.0        15 April 2021 https://rubygems.org/downloads/chunky_png-1.4.0.gem
cifsutils                 6.13         15 April 2021 https://www.samba.org/ftp/linux-cifs/cifs-utils/cifs-utils-6.13.tar.bz2
cinelerra                 7.3          08 July 2021 https://sourceforge.net/projects/heroines/files/cinelerra-7.3.tar.xz
cinepaint                 0.22.1       01 June 2014 http://sourceforge.net/projects/cinepaint/files/CinePaint/CinePaint-0.22-1/cinepaint-0.22.1.tar.gz
circuslinux               1.0.3        01 June 2014 ftp://ftp.tuxpaint.org/unix/x/circus-linux/src/circuslinux-1.0.3.tar.gz
clamav                    0.103.2      05 June 2021 https://www.clamav.net/downloads/production/clamav-0.103.2.tar.gz
clang                     14.0.0       28 March 2022 https://github.com/llvm/llvm-project/releases/download/llvmorg-14.0.0/clang-14.0.0tar.xz
clanlib                   24.10.2015   24 October 2015 http://www.clanlib.org/download/releases-3.0/ClanLib-24.10.2015
classaccessor             0.51         28 October 2017 http://search.cpan.org/CPAN/authors/id/K/KA/KASEI/Class-Accessor-0.51.tar.gz
classlib                  0.1          01 June 2014 http://students.washington.edu/aemk/cm/releases/classlib-0.1.tar.gz
classtiny                 1.004        01 April 2016 http://search.cpan.org/CPAN/authors/id/D/DA/DAGOLDEN/Class-Tiny-1.004.tar.gz
clawsmail                 clawsmail    01 June 2014 https://www.claws-mail.org/
clearsilver               0.10.5       01 June 2014 http://www.clearsilver.net/downloads/clearsilver-0.10.5.tar.gz
clementine                1.3.1        20 December 2019 https://github.com/clementine-player/Clementine/archive/1.3.1.tar.gz
click                     7.1.2        12 July 2020 https://files.pythonhosted.org/packages/27/6f/be940c8b1f1d69daceeb0032fee6c34d7bd70e3e649ccac0951500b4720e/click-7.1.2.tar.gz
clisp                     2.49         01 May 2014  https://sourceforge.net/projects/clisp/files/clisp/2.49/clisp-2.49.tar.gz
clive                     1.0.2        01 June 2014 http://download.gna.org/clive/1.0.x/clive-1.0.2.tar.bz2
cliver                    0.3.2        13 August 2018 https://rubygems.org/downloads/cliver-0.3.2.gem
cloog                     0.18.4       11 February 2017 http://www.bastoul.net/cloog/pages/download/cloog-0.18.4.tar.gz
cloogparma                0.16.1       01 November 2012 http://www.bastoul.net/cloog/pages/download/cloog-parma-0.16.1.tar.gz
cloogppl                  0.15.11      01 November 2012 ftp://gcc.gnu.org/pub/gcc/infrastructure/cloog-ppl-0.15.11.tar.gz
clucenecore               2.3.3.4      28 July 2016 https://sourceforge.net/projects/clucene/files/clucene-core-unstable/2.3/clucene-core-2.3.3.4.tar.gz
clustalomega              1.2.4        09 September 2018 http://www.clustal.org/omega/clustal-omega-1.2.4.tar.gz
clustalw                  2.1          11 April 2016 http://www.clustal.org/download/current/clustalw-2.1.tar.gz
clutter                   1.26.4       09 March 2020 https://download.gnome.org/sources/clutter/1.26/clutter-1.26.4.tar.xz
cluttergst                3.0.27       07 February 2019 http://ftp.gnome.org/pub/gnome/sources/clutter-gst/3.0/clutter-gst-3.0.27.tar.xz
cluttergtk                1.8.4        09 August 2017 http://ftp.gnome.org/pub/gnome/sources/clutter-gtk/1.8/clutter-gtk-1.8.4.tar.xz
cluttergtkmm              1.6.0        18 March 2015 http://ftp.gnome.org/pub/GNOME/sources/clutter-gtkmm/1.6/clutter-gtkmm-1.6.0.tar.xz
cluttermm                 1.17.3       01 May 2014  http://ftp.gnome.org/pub/GNOME/sources/cluttermm/1.17/cluttermm-1.17.3.tar.xz
cmake                     3.29.1       12 April 2024 https://github.com/Kitware/CMake/releases/download/v3.29.1/cmake-3.29.1.tar.gz
cmark                     0.29.0       26 May 2020  https://github.com/commonmark/cmark/archive/cmark-0.29.0.tar.gz
cmdftp                    0.9.7        01 June 2014 http://download.savannah.nongnu.org/releases/cmdftp/cmdftp-0.9.7.tar.gz
cmdparse                  3.0.7        06 March 2021 https://rubygems.org/downloads/cmdparse-3.0.7.gem
codeblocks                20.03        31 March 2020 https://sourceforge.net/projects/codeblocks/files/Sources/20.03/codeblocks-20.03.tar.xz
codebrowser               4.9          01 December 2012 http://tibleiz.net/download/code-browser-4.9.tar.gz
coderay                   1.1.3        17 June 2020 https://rubygems.org/downloads/coderay-1.1.3.gem
coffeescript              2.4.1        10 December 2017 https://rubygems.org/downloads/coffee-script-2.4.1.gem
cogito                    0.17.2       01 June 2014 http://www.kernel.org/pub/software/scm/cogito/cogito-0.17.2.tar.bz2
cogl                      1.22.8       06 June 2020 https://ftp.gnome.org/pub/gnome/sources/cogl/1.22/cogl-1.22.8.tar.xz
coin                      2.5.0        01 June 2014 http://www.coin3d.org/lib/coin/releases/2.5.0
collectd                  5.11.0       30 July 2020 https://storage.googleapis.com/collectd-tarballs/collectd-5.11.0.tar.bz2
collectl                  4.3.1        30 July 2013 https://sourceforge.net/projects/collectl/files/collectl/collectl-4.3.1/collectl-4.3.1tar.gz
colorama                  0.4.6        08 March 2023 https://files.pythonhosted.org/packages/d8/53/6f443c9a4a8358a93a6792e2acffb9d9d5cb0a5cfd8802644b7b1c9a02e4/colorama-0.4.6.tar.gz
colord                    1.4.6        19 March 2023 https://www.freedesktop.org/software/colord/releases/colord-1.4.6.tar.xz
colordgtk                 0.2.0        30 June 2019 https://www.freedesktop.org/software/colord/releases/colord-gtk-0.2.0.tar.xz
colordkde                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/colord-kde-24.02.2.tar.xz
colored                   1.4.3        07 July 2022 https://files.pythonhosted.org/packages/f4/57/fe3e4e96efa3c68d3781a0903de0933ea2afa744852d907b290a2cb2294e/colored-1.4.3.tar.gz
colortools                1.3.0        22 July 2017 https://rubygems.org/downloads/color-tools-1.3.0.gem
colour                    0.1.5        02 December 2018 https://files.pythonhosted.org/packages/a0/d4/5911a7618acddc3f594ddf144ecd8a03c29074a540f4494670ad8f153efe/colour-0.1.5.tar.gz
combinepdf                1.0.22       27 May 2022  https://rubygems.org/downloads/combine_pdf-1.0.22.gem
comix                     4.0.4        11 October 2017 https://sourceforge.net/projects/comix/files/comix/comix-4.0.4/comix-4.0.4.tar.gz
compface                  1.5.2        01 January 2013 http://ftp.xemacs.org/pub/xemacs/aux/compface-1.5.2.tar.gz
compilerrt                14.0.0       28 March 2022 https://github.com/llvm/llvm-project/releases/download/llvmorg-14.0.0/compiler-rt-14.0.0tar.xz
compiz                    0.9.14.1     27 November 2019 https://launchpad.net/compiz/0.9.14/0.9.14.1/+download/compiz-0.9.14.1.tar.xz
compositeproto            0.4.2        08 August 2016 https://www.x.org/releases/individual/proto/compositeproto-0.4.2.tar.gz
comptonconf               0.16.0       06 November 2020 https://github.com/lxqt/compton-conf/releases/download/0.16.0/compton-conf-0.16.0.tar.xz
concurrentruby            1.1.10       27 May 2022  https://rubygems.org/downloads/concurrent-ruby-1.1.10.gem
confuse                   3.3          03 August 2020 https://github.com/martinh/libconfuse/releases/download/v3.3/confuse-3.3.tar.xz
conky                     1.15.0       05 December 2022 https://github.com/brndnmtthws/conky/archive/refs/tags/v1.15.0.tar.gz
connections               3.38.1       19 October 2020 https://download.gnome.org/sources/connections/3.38/connections-3.38.1.tar.xz
connman                   1.33         22 February 2017 https://www.kernel.org/pub/linux/network/connman/connman-1.33.tar.xz
consolekit                0.4.6        01 June 2014 http://anduin.linuxfromscratch.org/sources/BLFS/svn/c/ConsoleKit-0.4.6.tar.xz
consolekit2               1.2.1        14 November 2018 https://github.com/Consolekit2/ConsoleKit2/releases/download/1.2.1/ConsoleKit2-1.2.1.tar.bz2
constype                  1.0.5        12 April 2023 https://xorg.freedesktop.org/releases/individual/app/constype-1.0.5.tar.xz
contextfree               3.3          24 June 2020 https://www.contextfreeart.org/download/ContextFreeSource3.3.tar.xz
convmv                    2.05         22 May 2020  https://www.j3e.de/linux/convmv/convmv-2.05.tar.gz
coreutils                 9.5          28 March 2024 https://ftp.gnu.org/gnu/coreutils/coreutils-9.5.tar.xz
cparser                   1.22.0       04 January 2016 https://github.com/MatzeB/cparser/archive/cparser-1.22.0.tar.gz
cpio                      2.14         02 May 2023  https://ftp.gnu.org/pub/gnu/cpio/cpio-2.14.tar.bz2
cppunit                   1.12.1       01 November 2012 https://sourceforge.net/projects/cppunit/files/cppunit/1.12.1/cppunit-1.12.1.tar.gz
cpufreqd                  2.4.2        24 December 2015 https://sourceforge.net/projects/cpufreqd/files/Source%20packages/2.4.2/cpufreqd-2.4.2.tar.bz2
cpux                      4.2.0        14 November 2021 https://github.com/X0rg/CPU-X/releases
cracklib                  2.9.11       06 April 2023 https://github.com/cracklib/cracklib/releases/download/v2.9.11/cracklib-2.9.11.tar.gz
crass                     1.0.6        28 May 2020  https://rubygems.org/downloads/crass-1.0.6.gem
cream                     0.43         01 June 2014 https://sourceforge.net/projects/cream/files/Cream/0.43/cream-0.43.tar.gz
crimson                   0.5.3        01 January 2013 http://crimson.seul.org/files/crimson-0.5.3.tar.bz2
cryopid                   0.5.9.1      01 June 2014 http://dagobah.ucc.asn.au/wacky/cryopid-0.5.9.1-i386.tar.gz
cryptopp                  8.7.0        04 December 2022 https://www.cryptopp.com/cryptopp870.zip
cryptsetup                2.7.2        09 April 2024 https://www.kernel.org/pub/linux/utils/cryptsetup/v2.7/cryptsetup-2.7.2.tar.xz
crystal                   0.28.0       05 April 2016 https://github.com/crystal-lang/crystal/archive/0.28.0.tar.gz
crystalspace              1.2          01 June 2014 http://www.crystalspace3d.org/downloads/release/crystalspace-2.0.tar.bz2
csmash                    0.6.6        01 June 2014 http://cannonsmash.sourceforge.net/
ctags                     5.8          01 June 2014 https://prdownloads.sourceforge.net/ctags/ctags-5.8.tar.gz
ctalk                     0.0.77a      01 June 2014 http://www.ctalklang.org/
ctioga                    1.11.1       01 December 2017 https://rubygems.org/downloads/ctioga-1.11.1.gem
ctorrent                  1.3.4        01 June 2014 https://sourceforge.net/projects/ctorrent/files/CTorrent-1.3.4/CTorrent-1.3.4/ctorrent-1.3.4.tar.bz2
ctris                     0.42         01 June 2014 http://www.hackl.dhs.org/ctris/
ctypes                    1.0.2        01 January 2013 https://downloads.sourceforge.net/project/ctypes/ctypes/1.0.2/ctypes-1.0.2.tar.gz
cuiterm                   0.9.9        01 June 2014 ftp://linux.pte.hu/pub/CUI/cuiterm-0.9.9.tar.gz
cunit                     2.1-3        20 February 2017 https://downloads.sourceforge.net/project/cunit/CUnit/2.1-3/CUnit-2.1-3.tar.bz2
cups                      2.4.7        20 September 2023 https://github.com/OpenPrinting/cups/releases/download/v2.4.7/cups-2.4.7-source.tar.gz
cupsfilters               1.28.17      24 February 2024 https://github.com/OpenPrinting/cups-filters/releases/download/1.28.17/cups-filters-1.28.17.tar.xz
curl                      8.7.1        27 March 2024 https://curl.se/download/curl-8.7.1.tar.xz
cutmp3                    3.0.1        12 December 2015 http://www.puchalla-online.de/cutmp3-3.0.1.tar.bz2
cvs                       1.11.23      01 March 2013 http://ftp.gnu.org/non-gnu/cvs/source/stable/1.11.23/cvs-1.11.23.tar.bz2
cvtool                    0.1.0        01 June 2014 https://sourceforge.net/projects/cvtool/cvtool-0.1.0.tar.gz
cxxtools                  3.0          28 June 2021 http://www.tntnet.org/download/cxxtools-3.0.tar.gz
cyrussasl                 2.1.28       25 February 2022 https://github.com/cyrusimap/cyrus-sasl/releases/download/cyrus-sasl-2.1.28/cyrus-sasl-2.1.28.tar.gz
cython                    3.0.10       31 March 2024 https://files.pythonhosted.org/packages/d5/f7/2fdd9205a2eedee7d9b0abbf15944a1151eb943001dbdc5233b1d1cfc34e/Cython-3.0.10.tar.gz
daemons                   1.4.1        27 May 2022  https://rubygems.org/downloads/daemons-1.4.1.gem
damageproto               1.2.1        08 August 2016 https://xorg.freedesktop.org/releases/individual/proto/damageproto-1.2.1.tar.bz2
daq                       2.0.5        20 May 2015  https://www.snort.org/downloads/snort/daq-2.0.5.tar.gz
darcs                     2.14.2       28 September 2019 http://darcs.net/releases/darcs-2.14.2.tar.gz
darktable                 4.2.1        22 May 2023  https://github.com/darktable-org/darktable/releases/download/release-4.2.1/darktable-4.2.1.tar.xz
dash                      0.5.12       04 March 2023 http://gondor.apana.org.au/~herbert/dash/files/dash-0.5.12.tar.gz
dasher                    4.11         01 June 2014 http://ftp.acc.umu.se/pub/GNOME/sources/dasher/4.11/dasher-4.11.tar.bz2
datamash                  1.6          24 February 2020 http://ftp.gnu.org/pub/gnu/datamash/datamash-1.6.tar.gz
dateutils                 0.4.6        19 March 2019 https://bitbucket.org/hroptatyr/dateutils/downloads/dateutils-0.4.6.tar.xz
db                        5.3.28       02 June 2020 http://anduin.linuxfromscratch.org/BLFS/bdb/db-5.3.28.tar.gz
dblatex                   0.3          01 June 2014 http://prdownloads.sourceforge.net/dblatex/dblatex-0.3.tar.bz2
dbus                      1.14.10      16 March 2024 https://dbus.freedesktop.org/releases/dbus/dbus-1.14.10.tar.xz
dbusglib                  0.112        30 March 2021 https://dbus.freedesktop.org/releases/dbus-glib/dbus-glib-0.112.tar.gz
dbuspython                1.3.2        08 September 2022 https://dbus.freedesktop.org/releases/dbus-python/dbus-python-1.3.2.tar.gz
dconf                     0.40.0       13 March 2021 https://download.gnome.org/sources/dconf/0.40/dconf-0.40.0.tar.xz
dconfeditor               3.38.2       24 November 2020 https://download.gnome.org/sources/dconf-editor/3.38/dconf-editor-3.38.2.tar.xz
dcraw                     9.15         01 June 2014 http://www.cybercom.net/~dcoffin/dcraw/archive/dcraw-9.15.tar.gz
ddclient                  3.8.3        07 February 2016 https://sourceforge.net/projects/ddclient/files/ddclient/ddclient-3.8.3/ddclient-3.8.3.tar.bz2
ddd                       3.3.12       01 June 2014 http://ftp.gnu.org/gnu/ddd/ddd-3.3.12.tar.gz
ddrescue                  1.27         23 January 2023 https://ftp.gnu.org/pub/gnu/ddrescue/ddrescue-1.27.tar.lz
defendguin                0.0.12       05 January 2019 ftp://ftp.tuxpaint.org/unix/x/defendguin/src/defendguin-0.0.12.tar.gz
dejagnu                   1.6.3        17 June 2021 https://ftp.gnu.org/pub/gnu/dejagnu/dejagnu-1.6.3.tar.gz
dejavufontsttf            2.37         22 April 2021 https://sourceforge.net/projects/dejavu/files/dejavu/2.37/dejavu-fonts-ttf-2.37.tar.bz2
deluge                    2.1.1        03 January 2022 http://download.deluge-torrent.org/source/2.1/deluge-2.1.1.tar.xz
denemo                    2.6.0        13 March 2022 https://ftp.gnu.org/pub/gnu/denemo/denemo-2.6.0.tar.gz
deplate                   0.8.5        15 April 2021 https://rubygems.org/downloads/deplate-0.8.5.gem
dermixd                   2.0.1        16 April 2016 http://thomas.orgis.org/dermixd/dermixd-2.0.1.tar.bz2
deskbarapplet             2.20.0       01 June 2014 http://ftp.acc.umu.se/pub/GNOME/sources/deskbar-applet/2.20/deskbar-applet-2.20.0.tar.bz2
desksanity                1.1.0        05 February 2016 https://download.enlightenment.org/rel/apps/enlightenment/desksanity-1.1.0.tar.xz
desktopfileutils          0.26         20 June 2020 http://freedesktop.org/software/desktop-file-utils/releases/desktop-file-utils-0.26.tar.xz
detect                    0.9.83       01 June 2014 http://www.hylius.fr/
devede                    4.5.0        02 February 2016 https://github.com/rastersoft/devedeng/archive/4.5.0.tar.gz
devhelp                   41.3         26 August 2022 https://download.gnome.org/sources/devhelp/41/devhelp-41.3.tar.xz
devil                     1.7.8        19 June 2015 http://downloads.sourceforge.net/openil/DevIL-1.7.8.tar.gz
dfeet                     0.3.16       08 May 2021  https://download.gnome.org/sources/d-feet/0.3/d-feet-0.3.16.tar.xz
dhcp                      4.4.3        10 March 2022 https://downloads.isc.org/isc/dhcp/4.4.3/dhcp-4.4.3.tar.gz
dhcpcd                    10.0.1       22 April 2023 https://github.com/NetworkConfiguration/dhcpcd/releases/download/v10.0.1/dhcpcd-10.0.1.tar.xz
dia                       0.97.3       05 September 2014 http://ftp.gnome.org/pub/GNOME/sources/dia/0.97/dia-0.97.3.tar.xz
diakonos                  0.9.4        15 November 2015 http://diakonos.pist0s.ca/archives/diakonos-0.9.4.tar.gz
dico                      2.11         27 April 2021 https://ftp.gnu.org/pub/gnu/dico/dico-2.11.tar.xz
dictd                     1.12.1       01 June 2014 https://sourceforge.net/projects/dict/files/dictd/dictd-1.12.1/dictd-1.12.1.tar.gz
didyoumean                1.6.1        27 May 2022  https://rubygems.org/downloads/did_you_mean-1.6.1.gem
dietlibc                  0.33         11 October 2017 https://www.fefe.de/dietlibc/dietlibc-0.33.tar.bz2
difflcs                   1.5.0        28 January 2022 https://rubygems.org/downloads/diff-lcs-1.5.0.gem
diffutils                 3.10         22 May 2023  https://ftp.gnu.org/gnu/diffutils/diffutils-3.10.tar.xz
digger                    20020314     04 April 2024 https://www.digger.org/digger-20020314.tar.gz
digikam                   8.3.0        15 March 2024 https://download.kde.org/stable/digikam/8.3.0/digiKam-8.3.0.tar.xz
dillo                     3.0.5        03 July 2015 http://www.dillo.org/download/dillo-3.0.5.tar.bz2
ding                      1.9          21 February 2022 https://ftp.tu-chemnitz.de/pub/Local/urz/ding/ding-1.9.tar.gz
dinglibs                  0.6.2        19 March 2024 https://github.com/SSSD/ding-libs/releases/download/0.6.2/ding-libs-0.6.2.tar.gz
dirac                     1.0.0        01 June 2014 https://sourceforge.net/projects/dirac/files/dirac-codec/Dirac-1.0.0/dirac-1.0.0.tar.gz
direvent                  5.3          31 December 2021 https://ftp.gnu.org/pub/gnu/direvent/direvent-5.3.tar.gz
discount                  2.2.3a       21 July 2018 https://www.pell.portland.or.us/~orc/Code/discount/discount-2.2.3a.tar.bz2
discover                  6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/discover-6.0.2.tar.xz
disko                     1.8.0        01 May 2014  http://www.diskohq.com/repository/sources/disko_1.8.0.tar.gz
distcc                    3.4          13 May 2021  https://github.com/distcc/distcc/releases/download/v3.4/distcc-3.4.tar.gz
dit                       0.9          05 October 2023 https://hisham.hm/dit/releases/0.9/dit-0.9.tar.gz
diva                      0.0.2        01 May 2014  http://files.diva-project.org/releases/diva-0.0.2.tar.gz
django                    4.1.5        30 January 2023 https://files.pythonhosted.org/packages/41/c8/b3c469353f9d1b7f0e99b45520582b891da02cd87408bc867affa6e039a3/Django-4.1.5.tar.gz
djview                    4.12         06 February 2024 http://downloads.sourceforge.net/djvu/djview-4.12.tar.gz
djvulibre                 3.5.28       16 October 2021 http://sourceforge.net/projects/djvu/files/DjVuLibre/3.5.28/djvulibre-3.5.28.tar.gz
dkms                      2.7.1        07 August 2019 https://github.com/dell/dkms/archive/v2.7.1.tar.gz
dmidecode                 3.3          05 April 2022 https://download.savannah.gnu.org/releases/dmidecode/dmidecode-3.3.tar.xz
dmxproto                  2.3.1        01 May 2014  https://xorg.freedesktop.org/releases/individual/proto/dmxproto-2.3.1.tar.bz2
dnsmasq                   2.89         06 February 2023 https://thekelleys.org.uk/dnsmasq/dnsmasq-2.89.tar.xz
dnspython                 1.15.0       04 November 2017 http://www.dnspython.org/kits/1.15.0/dnspython-1.15.0.tar.gz
docbook2x                 0.8.8        01 May 2014  http://downloads.sourceforge.net/docbook2x/docbook2X-0.8.8.tar.gz
docbookutils              0.6.14       27 October 2015 http://sources-redhat.mirrors.redwire.net/docbook-tools/new-trials/SOURCES/docbook-utils-0.6.14.tar.gz
docbookxml                4.5          10 February 2024 https://www.docbook.org/xml/4.5/docbook-xml-4.5.zip
docbookxsl                1.79.2       30 December 2017 https://github.com/docbook/xslt10-stylesheets/releases/download/release/1.79.2/docbook-xsl-1.79.2.tar.bz2
docutils                  0.21.1       13 April 2024 https://files.pythonhosted.org/packages/source/d/docutils/docutils-0.21.1.tar.gz
docx2txt                  1.4          24 October 2016 http://downloads.sourceforge.net/docx2txt/docx2txt-1.4.tgz
dolphin                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/dolphin-24.02.2.tar.xz
dolphinplugins            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/dolphin-plugins-24.02.2.tar.xz
domainname                0.5.20190701 26 August 2019 https://rubygems.org/downloads/domain_name-0.5.20190701.gem
dosbox                    0.74-3       23 June 2020 https://sourceforge.net/projects/dosbox/files/dosbox/0.74-3/dosbox-0.74-3.tar.gz
dosfstools                4.1          20 September 2018 https://github.com/dosfstools/dosfstools/releases/download/v4.1/dosfstools-4.1.tar.xz
dotconf                   09.04.2024   09 April 2024 http://www.azzit.de/dotconf/download/v1.0/dotconf-1.0.13.tar.gz
doubleconversion          3.3.0        17 March 2024 https://github.com/google/double-conversion/archive/v3.3.0/double-conversion-3.3.0.tar.gz
dovecot                   2.3.20       22 December 2022 http://www.dovecot.org/releases/2.3/dovecot-2.3.20.tar.gz
doxygen                   1.10.0       25 December 2023 https://sourceforge.net/projects/doxygen/files/rel-1.10.0/doxygen-1.10.0tar.gz
dpkg                      1.20.5       11 July 2020 http://ftp.debian.org/debian/pool/main/d/dpkg/dpkg_1.20.5.tar.xz
dragon                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/dragon-24.02.2.tar.xz
dragonhunt                3.56         01 June 2014 http://emhsoft.com/dh/Dragon_Hunt-3.56.tar.gz
dri2proto                 2.8          01 January 2014 http://xorg.freedesktop.org/releases/individual/proto/dri2proto-2.8.tar.bz2
dri3proto                 1.0          01 November 2013 http://xorg.freedesktop.org/releases/individual/proto/dri3proto-1.0.tar.bz2
drkonqi                   6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/drkonqi-6.0.2.tar.xz
drupal                    8.7.7        29 September 2019 http://ftp.drupal.org/files/projects/drupal-8.7.7.tar.gz
dssi                      1.1.1        01 June 2014 https://sourceforge.net/projects/dssi/files/dssi/1.1.1/dssi-1.1.1.tar.gz
duktape                   2.7.0        01 January 2023 https://duktape.org/duktape-2.7.0.tar.xz
duma                      2.5.15       27 May 2022  https://sourceforge.net/projects/duma/files/duma/2.5.15/duma_2_5_15.tar.gz
dumb                      2.0.3        29 September 2019 https://github.com/kode54/dumb/archive/2.0.3.tar.gz
dunelegacy                0.96.4       21 August 2017 https://sourceforge.net/projects/dunelegacy/files/dunelegacy/0.96.4/dunelegacy-0.96.4.tar.bz2
dvd+rwtools               7.1          01 May 2014  http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-7.1.tar.gz
dvdauthor                 0.7.1        01 September 2014 https://sourceforge.net/projects/dvdauthor/files/dvdauthor/0.7.1/dvdauthor-0.7.1.tar.gz
dvdrip                    0.98.11      01 May 2014  http://www.exit1.org/dvdrip/dist/dvdrip-0.98.11.tar.gz
dvdripomatic              0.94         01 May 2014  http://surfnet.dl.sourceforge.net/sourceforge/dvdripomatic/DVDRipOMatic-0.94.tar.bz2
dvdrtools                 0.3.1        01 May 2014  http://www.arklinux.org/download/dvdrtools-0.3.1.tar.bz2
dvdslideshow              0.7.5        01 May 2014  http://dvd-slideshow.sourceforge.net/
dvgrab                    04.04.2024   01 May 2014  https://github.com/ddennedy/dvgrab/dvgrab-04.04.2024
dvisvgm                   2.10         15 August 2020 https://github.com/mgieseki/dvisvgm/releases/download/2.10/dvisvgm-2.10.tar.gz
dwm                       6.1          25 December 2015 http://dl.suckless.org/dwm/dwm-6.1.tar.gz
dxpy                      0.172.0      06 December 2015 https://pypi.python.org/packages/source/d/dxpy/dxpy-0.172.0.tar.gz
dzen2                     0.4.5        28 July 2016 https://github.com/robm/dzen2-0.4.5.tar.xz
e16                       1.0.17       16 August 2015 http://sourceforge.net/projects/enlightenment/files/e16/1.0.17/e16-1.0.17.tar.gz
e2fsprogs                 1.47.0       07 February 2023 http://downloads.sourceforge.net/e2fsprogs/e2fsprogs-1.47.0.tar.gz
easytag                   2.4.3        10 September 2018 https://download.gnome.org/sources/easytag/2.4/easytag-2.4.3.tar.xz
ebooktools                0.2.2        09 September 2022 https://sourceforge.net/projects/ebook-tools/files/ebook-tools/0.2.2/ebook-tools-0.2.2.tar.gz
ecasound                  2.9.0        01 June 2014 http://ecasound.seul.org/download/ecasound-2.9.0.tar.gz
ecawave                   0.6.1        01 June 2014 http://ecasound.seul.org/download/ecawave-0.6.1.tar.gz
ecell                     3.2.2        01 November 2012 http://sourceforge.net/projects/ecell/files/E-Cell%203.2/3.2.2/ecell-3.2.2.tar.bz2
echievements              2            01 December 2012 http://download.enlightenment.fr/releases/echievements-2.tar.bz2
econnman                  1.1          13 April 2019 https://download.enlightenment.org/rel/apps/econnman/econnman-1.1.tar.xz
ecore                     1.7.10       01 January 2014 http://download.enlightenment.org/releases/ecore-1.7.10.tar.gz
ed                        1.20.1       21 February 2024 https://ftp.gnu.org/gnu/ed/ed-1.20.1.tar.lz
edbus                     1.7.10       01 January 2014 http://download.enlightenment.org/releases/e_dbus-1.7.10.tar.gz
ede                       2.1          17 September 2014 https://sourceforge.net/projects/ede/files/ede/2.1/ede-2.1.tar.gz
edelib                    2.1          24 February 2017 https://sourceforge.net/projects/ede/files/edelib/2.1/edelib-2.1.tar.gz
editres                   1.0.9        04 March 2024 https://www.x.org/releases/individual/app/editres-1.0.9.tar.xz
edje                      1.7.10       01 January 2014 http://download.enlightenment.org/releases/edje-1.7.10.tar.gz
edlib                     30.10.2022   30 October 2022 https://github.com/Martinsos/edlib/archive/refs/tags/v1.2.7.tar.gz
eet                       1.7.10       01 January 2014 http://download.enlightenment.org/releases/eet-1.7.10.tar.gz
eeze                      1.7.10       01 January 2014 http://download.enlightenment.org/releases/eeze-1.7.10.tar.gz
efivar                    39           21 February 2024 https://github.com/rhboot/efivar/archive/39/efivar-39.tar.gz
efl                       1.27.0       19 February 2024 https://download.enlightenment.org/rel/libs/efl/efl-1.27.0.tar.xz
efltk                     2.0.8        21 July 2019 https://sourceforge.net/projects/ede/files/efltk/2.0.8/efltk-2.0.8.tar.gz
efreet                    1.7.10       01 January 2014 http://download.enlightenment.org/releases/efreet-1.7.10.tar.bz2
eggdbus                   0.6          01 November 2012 http://cgit.freedesktop.org/~david/eggdbus/snapshot/eggdbus-0.6.tar.bz2
eigen                     3.4.0        28 August 2022 https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.tar.gz
eina                      1.7.10       01 January 2014 https://download.enlightenment.org/releases/eina-1.7.10.tar.gz
eio                       1.7.10       01 January 2014 http://download.enlightenment.org/releases/eio-1.7.10.tar.gz
eject                     2.1.5        01 November 2012 http://ca.geocities.com/jefftranter-rogers.com/eject-2.1.5.tar.gz
ekiga                     4.0.1        01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/ekiga/4.0/ekiga-4.0.1.tar.xz
eldbus                    1.7.9        01 December 2013 http://download.enlightenment.org/releases/eldbus-1.7.9.tar.bz2
elementary                1.7.10       28 January 2016 https://download.enlightenment.org/releases/elementary-1.7.10.tar.gz
elfutils                  0.191        17 March 2024 https://sourceware.org/elfutils/ftp/0.191/elfutils-0.191.tar.bz2
elinks                    0.11.7       28 August 2016 http://elinks.or.cz/download/elinks-0.11.7.tar.bz2
elisa                     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/elisa-24.02.2.tar.xz
elixir                    1.11.4       25 April 2021 https://github.com/elixir-lang/elixir/archive/refs/tags/v1.11.4.tar.gz
elogind                   252.23       22 March 2024 https://github.com/elogind/elogind/archive/v252.23/elogind-252.23.tar.gz
elph                      1.0.1        29 June 2017 ftp://ftp.cbcb.umd.edu/pub/software/elph/ELPH-1.0.1.tar.gz
emacs                     29.3         25 March 2024 https://ftp.gnu.org/gnu/emacs/emacs-29.3.tar.xz
emech                     3.0.99p3     01 June 2014 http://www.energymech.net/files/emech-3.0.99p3.tar.gz
emelfm                    0.9.2        01 June 2014 http://emelfm.sourceforge.net/emelfm-0.9.2.tar.gz
emotion                   1.7.10       01 January 2014 http://download.enlightenment.org/releases/emotion-1.7.10.tar.gz
emotiongenericplayers     1.15.0       04 August 2015 http://download.enlightenment.org/rel/libs/emotion_generic_players/emotion_generic_players-1.15.0.tar.gz
empathy                   3.25.90      17 August 2017 http://ftp.gnome.org/pub/gnome/sources/empathy/3.25/empathy-3.25.90.tar.xz
enca                      1.9          01 June 2014 http://trific.ath.cx/Ftp//enca/enca-1.9.tar.bz2
enchant                   2.6.9        05 April 2024 https://github.com/AbiWord/enchant/releases/download/v2.6.9/enchant-2.6.9.tar.gz
encodings                 1.1.0        04 March 2024 https://xorg.freedesktop.org/releases/individual/font/encodings-1.1.0.tar.xz
engrampa                  1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/engrampa-1.28.0.tar.xz
enigma                    1.30         09 June 2023 https://github.com/Enigma-Game/Enigma/releases/download/1.30/Enigma-1.30.tar.gz
enlightenment             0.26.0       24 December 2023 https://download.enlightenment.org/rel/apps/enlightenment/enlightenment-0.26.0.tar.xz
enscript                  1.6.6        01 September 2012 http://ftp.gnu.org/gnu/enscript/enscript-1.6.6.tar.gz
enter                     0.0.9        13 February 2016 https://sourceforge.net/projects/enter/files/enter/0.0.9/enter-0.0.9.tar.gz
entrance                  0.9.0.013    01 June 2014 http://download.enlightenment.org/snapshots/2007-08-26/entrance-0.9.0.013.tar.gz
enum34                    1.1.6        10 August 2018 https://files.pythonhosted.org/packages/bf/3e/31d502c25302814a7c2f1d3959d2a3b3f78e509002ba91aea64993936876/enum34-1.1.6.tar.gz
enventor                  0.3.2        01 September 2014 http://download.enlightenment.org/rel/apps/enventor/enventor-0.3.2.tar.gz
eog                       44.3         08 July 2023 https://download.gnome.org/sources/eog/44/eog-44.3.tar.xz
eogplugins                42.1         25 April 2022 https://download.gnome.org/sources/eog-plugins/42/eog-plugins-42.1.tar.xz
eom                       1.28.0       18 February 2024 https://pub.mate-desktop.org/releases/1.28/eom-1.28.0.tar.xz
epdfview                  0.1.8        01 June 2014 http://trac.emma-soft.com/epdfview/chrome/site/releases/epdfview-0.1.8.tar.bz2
epic5                     2.1.5        08 October 2021 http://ftp.epicsol.org/pub/epic/EPIC5-PRODUCTION/epic5-2.1.5.tar.xz
epiphany                  46.0         13 April 2024 https://download.gnome.org/sources/epiphany/46/epiphany-46.0.tar.xz
epkg                      2.3.9        01 June 2014 ftp://ftp.encap.org/pub/encap/epkg/epkg-2.3.9.tar.gz
epm                       4.1          01 June 2014 http://www.nu6.org/_/mirror/ftp.easysw.com/pub/epm/4.1/epm-4.1-source.tar.bz2
eps                       1.5          01 June 2014 http://www.inter7.com/eps/eps-1.5.tar.gz
erlang                    26.2.3       02 April 2024 https://github.com/erlang/otp/releases/download/OTP-26.2.3/otp_src_26.2.3.tar.gz
error                     0.17029      20 September 2022 https://cpan.metacpan.org/authors/id/S/SH/SHLOMIF/Error-0.17029.tar.gz
erubi                     1.10.0       15 April 2021 https://rubygems.org/downloads/erubi-1.10.0.gem
erubis                    2.7.0        03 December 2017 https://rubygems.org/downloads/erubis-2.7.0.gem
esdl                      1.3.1        02 August 2017 https://sourceforge.net/projects/esdl/files/esdl/esdl-1.3.1/esdl-1.3.1tgz
eselect                   1.4.27       02 April 2024 https://gitweb.gentoo.org/proj/eselect.git/snapshot/eselect-1.4.27.tar.bz2
esmtp                     1.2          01 June 2014 https://sourceforge.net/projects/esmtp/files/esmtp/1.2/esmtp-1.2.tar.bz2
esound                    0.2.41       05 December 2018 https://ftp.gnome.org/pub/GNOME/sources/esound/0.2/esound-0.2.41.tar.gz
espeak                    1.46.02      01 June 2014 http://sourceforge.net/projects/espeak/files/espeak/espeak-1.46/espeak-1.46.02-source.zip
eterm                     0.9.6        01 July 2013 http://www.eterm.org/download/Eterm-0.9.6.tar.gz
ethtool                   5.19         28 August 2022 https://mirrors.edge.kernel.org/pub/software/network/ethtool/ethtool-5.19.tar.xz
ethumb                    1.7.10       01 January 2014 http://download.enlightenment.org/releases/ethumb-1.7.10.tar.gz
eudev                     3.2.14       14 March 2024 https://github.com/eudev-project/eudev/releases/download/v3.2.14/eudev-3.2.14.tar.gz
evas                      1.7.10       01 January 2014 http://download.enlightenment.org/releases/evas-1.7.10.tar.gz
eve                       0.3.0        01 December 2012 http://download.enlightenment.org/snapshots/2010-12-03/eve-0.3.0.tar.bz2
event                     1.28         08 May 2021  https://cpan.metacpan.org/authors/id/E/ET/ETJ/Event-1.28.tar.gz
eventmachine              1.2.7        27 May 2019  https://rubygems.org/downloads/eventmachine-1.2.7.gem
eventviews                24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/eventviews-24.02.2.tar.xz
evieext                   1.1.1        01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/evieext-1.1.1.tar.bz2
evilvte                   0.5.2~pre1   01 June 2013 http://www.calno.com/evilvte/evilvte-0.5.2~pre1.tar.xz
evilwm                    1.4.3        14 April 2024 https://www.6809.org.uk/evilwm/dl/evilwm-1.4.3.tar.gz
evince                    46.0         21 March 2024 https://download.gnome.org/sources/evince/46/evince-46.0.tar.xz
evisum                    0.2.6        29 November 2019 https://download.enlightenment.org/rel/apps/evisum/evisum-0.2.6.tar.xz
evolution                 3.52.0       15 March 2024 https://download.gnome.org/sources/evolution/3.52/evolution-3.52.0.tar.xz
evolutiondataserver       3.48.2       27 May 2023  https://download.gnome.org/sources/evolution-data-server/3.48/evolution-data-server-3.48.2.tar.xz
evolutionews              3.48.2       27 May 2023  https://download.gnome.org/sources/evolution-ews/3.48/evolution-ews-3.48.2.tar.xz
evolutionmapi             3.48.1       27 May 2023  https://download.gnome.org/sources/evolution-mapi/3.48/evolution-mapi-3.48.1.tar.xz
exactimage                1.0.1        04 January 2018 http://dl.exactcode.de/oss/exact-image/exact-image-1.0.1.tar.bz2
execjs                    2.8.1        09 December 2021 https://rubygems.org/downloads/execjs-2.8.1.gem
exempi                    2.6.2        27 June 2022 https://libopenraw.freedesktop.org/download/exempi-2.6.2.tar.bz2
exfatprogs                1.1.2        22 May 2021  https://github.com/exfatprogs/exfatprogs/releases/download/1.1.2/exfatprogs-1.1.2.tar.xz
exfatutils                1.3.0        20 August 2020 https://github.com/relan/exfat/releases/download/v1.3.0/exfat-utils-1.3.0.tar.gz
exim                      4.97.1       29 December 2023 https://ftp.exim.org/pub/exim/exim4/exim-4.97.1.tar.xz
exiv2                     0.28.2       14 February 2023 https://github.com/Exiv2/exiv2/archive/v0.28.2/exiv2-0.28.2.tar.gz
exo                       4.18.0       23 December 2022 https://archive.xfce.org/src/xfce/exo/4.18/exo-4.18.0.tar.bz2
expat                     2.6.2        13 March 2024 https://sourceforge.net/projects/expat/files/expat/2.6.2/expat-2.6.2.tar.xz
expect                    5.45.4       18 February 2018 https://sourceforge.net/projects/expect/files/Expect/5.45.4/expect5.45.4.tar.gz
expedite                  1.7.10       22 December 2015 http://download.enlightenment.org/releases/expedite-1.7.10.tar.bz2
explore                   explore      01 June 2014 http://mesh.dl.sourceforge.net/sourceforge/openexplore/explore_v11_src.zip
exportertiny              1.006002     08 April 2024 https://cpan.metacpan.org/authors/id/T/TO/TOBYINK/Exporter-Tiny-1.006002.tar.gz
extracmakemodules         5.115.0      12 April 2024 https://download.kde.org/stable/frameworks/5.115/extra-cmake-modules-5.115.0.tar.xz
extutilsdepends           0.405        22 February 2016 http://search.cpan.org/CPAN/authors/id/X/XA/XAOC/ExtUtils-Depends-0.405.tar.gz
extutilshelpers           0.026        15 September 2016 http://search.cpan.org/CPAN/authors/id/L/LE/LEONT/ExtUtils-Helpers-0.026.tar.gz
extutilsmakemaker         7.38         09 November 2019 https://cpan.metacpan.org/authors/id/B/BI/BINGOS/ExtUtils-MakeMaker-7.38.tar.gz
extutilspkgconfig         1.16         30 August 2017 http://search.cpan.org/CPAN/authors/id/X/XA/XAOC/ExtUtils-PkgConfig-1.16.tar.gz
exult                     04.04.2024   04 April 2024 https://github.com/exult/exult/exult-04.04.2024.tar.xz
eyed3                     0.9.6        26 October 2021 https://files.pythonhosted.org/packages/fb/f2/27b42a10b5668df27ce87aa22407e5115af7fce9b1d68f09a6d26c3874ec/eyeD3-0.9.6.tar.gz
faac                      1.29.9       11 November 2017 https://downloads.sourceforge.net/faac/faac-1.29.9.tar.gz
faad2                     2.10.0       24 October 2022 https://github.com/knik0/faad2/archive/2_10_0/faad2-2_10_0.tar.gz
facter                    1.5.4rc1     01 May 2013  http://reductivelabs.com/downloads/facter/facter-1.5.4rc1.tgz
factorygirl               4.9.0        06 January 2018 https://rubygems.org/downloads/factory_girl-4.9.0.gem
falkon                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/falkon-24.02.2.tar.xz
fam                       2.7.0        01 June 2014 http://gd.tuwien.ac.at/opsys/linux/gentoo/distfiles/fam-2.7.0.tar.gz
faraday                   2.3.0        27 May 2022  https://rubygems.org/downloads/faraday-2.3.0.gem
farstream                 0.2.9        08 September 2022 https://freedesktop.org/software/farstream/releases/farstream/farstream-0.2.9.tar.gz
fbdesk                    1.4.1        01 June 2014 http://fluxbox.sourceforge.net/download/fbdesk-1.4.1.tar.gz
fbida                     2.14         29 September 2019 https://www.kraxel.org/releases/fbida/fbida-2.14.tar.gz
fcgi                      2.4.2        23 February 2022 https://github.com/FastCGI-Archives/fcgi2/archive/refs/tags/2.4.2.tar.gz
fdkaac                    2.0.1        13 October 2019 https://downloads.sourceforge.net/opencore-amr/fdk-aac-2.0.1.tar.gz
feh                       3.10         08 April 2023 https://feh.finalrewind.org/feh-3.10.tar.bz2
ferret                    0.11.8.7     09 January 2018 https://rubygems.org/downloads/ferret-0.11.8.7.gem
ferrum                    0.11         15 April 2021 https://rubygems.org/downloads/ferrum-0.11.gem
fetchmail                 6.4.34       29 October 2022 https://sourceforge.net/projects/fetchmail/files/branch_6.4/fetchmail-6.4.34.tar.xz
ffe                       0.3.9        14 February 2022 https://sourceforge.net/projects/ff-extractor/files/ff-extractor/0.3.9/ffe-0.3.9.tar.gz
ffi                       1.15.5       27 May 2022  https://rubygems.org/downloads/ffi-1.15.5.gem
ffirzmq                   2.0.7        30 May 2020  https://rubygems.org/downloads/ffi-rzmq-2.0.7.gem
ffmpeg                    09.04.2024   09 April 2024 https://ffmpeg.org/releases/ffmpeg-7.0.tar.xz
ffmpeg2theora             0.30         30 September 2017 http://v2v.cc/~j/ffmpeg2theora/downloads/ffmpeg2theora-0.30.tar.bz2
ffmpegphp                 .            01 June 2014 http://ffmpeg-php.sourceforge.net/
ffmpegthumbs              24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/ffmpegthumbs-24.02.2.tar.xz
ffpocket                  0.8.0        14 February 2022 https://members.hellug.gr/djart/ffpocket/ffpocket-0.8.0.tar.bz2
fftw                      3.3.10       18 September 2021 https://www.fftw.org/fftw-3.3.10.tar.gz
fiddle                    1.1.0        27 May 2022  https://rubygems.org/downloads/fiddle-1.1.0.gem
fife                      0.3.4        01 March 2013 http://sourceforge.net/projects/fife/files/active/src/fife_0.3.4.tar.gz
fifoembed                 2.1.1        01 June 2014 https://sourceforge.net/projects/fifoembed/files/fifoembed/2.1.1/fifoembed-2.1.1.tar.bz2
figaro                    1.2.0        28 May 2020  https://rubygems.org/downloads/figaro-1.2.0.gem
figlet                    2.2.5        23 August 2019 ftp://ftp.figlet.org/pub/figlet/program/unix/figlet-2.2.5.tar.gz
file                      5.45         21 January 2024 https://astron.com/pub/file/file-5.45.tar.gz
filechdir                 0.1010       12 April 2019 https://cpan.metacpan.org/authors/id/D/DA/DAGOLDEN/File-chdir-0.1010.tar.gz
filelight                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/filelight-24.02.2.tar.xz
fileroller                44.1         11 April 2024 https://download.gnome.org/sources/file-roller/44/file-roller-44.1.tar.xz
filesharedir              1.116        05 June 2018 https://cpan.metacpan.org/authors/id/R/RE/REHSACK/File-ShareDir-1.116.tar.gz
fileslurper               0.010        26 December 2017 http://search.cpan.org/CPAN/authors/id/L/LE/LEONT/File-Slurper-0.010.tar.gz
filetype                  1.1.0        21 August 2022 https://files.pythonhosted.org/packages/ba/42/53be9807e47b164a172721ad7960acdc7ec6ad45216c9962f5e933b0e314/filetype-1.1.0.tar.gz
filewhich                 1.23         03 January 2019 http://search.cpan.org/CPAN/authors/id/P/PL/PLICEASE/File-Which-1.23.tar.gz
filezilla                 ..2?=JMUN0BVFRWF&=1661556941 01 June 2014 https://dl3.cdn.filezilla-project.org/client/FileZilla_3.60.2_src.tar.bz2?h=JhMUNz0ahytBVzFRlgWxFg&x=1661556941
fim                       0.6          30 December 2018 http://download.savannah.nongnu.org/releases/fbi-improved/fim-0.6-trunk.tar.gz
findlib                   1.7.1        11 March 2017 http://download.camlcity.org/download/findlib-1.7.1.tar.gz
findutils                 4.9.0        02 February 2022 http://ftp.gnu.org/gnu/findutils/findutils-4.9.0.tar.xz
firebird                  0            01 October 2016 https://sourceforge.net/projects/firebird/files/firebird/3.0.1-Release/Firebird-3.0.1.32609-0.tar.bz2
firefox                   102.12.0esr  14 June 2023 https://archive.mozilla.org/pub/firefox/releases/102.12.0esr/source/firefox-102.12.0esr.source.tar.xz
firejail                  0.9.56       19 September 2018 https://sourceforge.net/projects/firejail/files/firejail/firejail-0.9.56.tar.xz
fische                    3.2.2        01 November 2012 http://26elf.at/files/fische-3.2.2.tar.gz
fish                      3.2.0        02 March 2021 https://github.com/fish-shell/fish-shell/releases/download/3.2.0/fish-3.2.0.tar.xz
fitd                      0.1          01 June 2014 http://sourceforge.net/project/showfiles.php?group_id=104884/fitd-0.1
fiveormore                3.32.2       28 March 2020 http://ftp.gnome.org/pub/gnome/sources/five-or-more/3.32/five-or-more-3.32.2.tar.xz
fixesproto                5.0          01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/fixesproto-5.0.tar.bz2
flac                      1.4.3        25 June 2023 https://downloads.xiph.org/releases/flac/flac-1.4.3.tar.xz
flagpoll                  0.3.0        01 June 2014 https://crate.io/packages/flagpoll/0.3.0/
flam3                     3.0.1        01 August 2014 http://flam3.googlecode.com/files/flam3-3.0.1.zip
flask                     2.0.1        23 May 2021  https://files.pythonhosted.org/packages/c0/df/c516b5f38a670b6b0de604c2637ed5860db03692c2f8542fd1f60c2552a7/Flask-2.0.1.tar.gz
flatbuffers               26.12.2018   26 December 2018 flatbuffers-26.12.2018
flatpak                   1.14.2       07 February 2023 https://github.com/flatpak/flatpak/releases/download/1.14.2/flatpak-1.14.2.tar.xz
flatpakkcm                6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/flatpak-kcm-6.0.2.tar.xz
flatzebra                 0.1.6        31 May 2020  http://perso.b2b2c.ca/sarrazip/dev/flatzebra-0.1.6.tar.gz
fldigi                    3.23.12      20 July 2016 https://sourceforge.net/projects/fldigi/files/fldigi/fldigi-3.23.12.tar.gz
flex                      2.6.4        07 May 2017  https://github.com/westes/flex/releases/download/v2.6.4/flex-2.6.4.tar.gz
flimp                     0.0.11       25 April 2015 http://www.ecademix.com/JohannesHofmann/flimp-0.0.11.tar.gz
flitcore                  3.9.0        07 February 2024 https://pypi.org/packages/source/f/flit-core/flit_core-3.9.0.tar.gz
florence                  0.6.3        25 April 2015 http://sourceforge.net/projects/florence/files/florence/0.6.3/florence-0.6.3.tar.bz2
fltk                      1.3.8        24 November 2021 https://fltk.org/pub/fltk/1.3.8/fltk-1.3.8-source.tar.gz
fluidsynth                2.3.5        29 March 2024 https://github.com/FluidSynth/fluidsynth/archive/refs/tags/v2.3.5.tar.gz
fluxbox                   1.3.7        17 May 2015  http://sourceforge.net/projects/fluxbox/files/fluxbox/1.3.7/fluxbox-1.3.7.tar.xz
folks                     0.15.9       24 March 2024 https://download.gnome.org/sources/folks/0.15/folks-0.15.9.tar.xz
fontadobe100dpi           1.0.0        01 June 2014 http://xorg.freedesktop.org/releases/individual/font/font-adobe-100dpi-1.0.0.tar.bz2
fontadobe75dpi            1.0.0        01 June 2014 https://xorg.freedesktop.org/releases/individual/font/font-adobe-75dpi-1.0.0.tar.bz2
fontadobeutopia100dpi     1.0.1        01 June 2014 http://xorg.freedesktop.org/releases/individual/font/font-adobe-utopia-100dpi-1.0.1.tar.bz2
fontadobeutopia75dpi      1.0.1        01 June 2014 http://xorg.freedesktop.org/releases/individual/font/font-adobe-utopia-75dpi-1.0.1.tar.bz2
fontadobeutopiatype1      1.0.4        01 May 2014  http://xorg.freedesktop.org/releases/individual/font/font-adobe-utopia-type1-1.0.4.tar.gz
fontalias                 1.0.4        09 August 2020 http://xorg.freedesktop.org/releases/individual/font/font-alias-1.0.4.tar.bz2
fontbh75dpi               1.0.0        01 January 2013 http://xorg.freedesktop.org/releases/individual/font/font-bh-75dpi-1.0.0.tar.bz2
fontbitstream100dpi       1.0.0        01 June 2014 http://xorg.freedesktop.org/releases/individual/font/font-bitstream-100dpi-1.0.0.tar.bz2
fontbitstream75dpi        1.0.3        01 June 2014 http://xorg.freedesktop.org/releases/individual/font/font-bitstream-75dpi-1.0.3.tar.bz2
fontcacheproto            0.1.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/proto/fontcacheproto-0.1.2.tar.bz2
fontconfig                2.14.2       29 January 2023 https://www.freedesktop.org/software/fontconfig/release/fontconfig-2.14.2.tar.xz
fontforge                 20200314     15 March 2020 https://github.com/fontforge/fontforge/releases/download/20200314/fontforge-20200314.tar.xz
fontmanager               0.7.4.3      19 December 2019 https://github.com/FontManager/master/releases/download/0.7.4.3/font-manager-0.7.4.3.tar.bz2
fontopia                  1.7          21 August 2016 http://ftp.gnu.org/pub/gnu/fontopia/fontopia-1.7.tar.gz
fontsonymisc              1.0.3        01 August 2013 http://xorg.freedesktop.org/releases/individual/font/font-sony-misc-1.0.3.tar.bz2
fontsproto                2.1.3        01 April 2014 http://xorg.freedesktop.org/releases/individual/proto/fontsproto-2.1.3.tar.bz2
fonttosfnt                1.2.1        17 December 2020 https://www.x.org/releases/individual/app/fonttosfnt-1.2.1.tar.bz2
fontttf                   1.06         16 December 2018 https://cpan.metacpan.org/authors/id/B/BH/BHALLISSY/Font-TTF-1.06.tar.gz
fontutil                  1.4.1        20 February 2024 https://www.x.org/releases/individual/font/font-util-1.4.1.tar.xz
fontxfree86type1          1.0.4        01 May 2014  http://xorg.freedesktop.org/releases/individual/font/font-xfree86-type1-1.0.4.tar.bz2
formatador                1.1.0        27 May 2022  https://rubygems.org/downloads/formatador-1.1.0.gem
fosfat                    0.2.3.       01 May 2014  https://download.gna.org/fosfat/fosfat_0.2.3.orig.tar.gz
fourinarow                3.38.1       03 December 2020 https://download.gnome.org/sources/four-in-a-row/3.38/four-in-a-row-3.38.1.tar.xz
fox                       1.6.83       02 April 2024 http://fox-toolkit.org/ftp/fox-1.6.83.tar.gz
fpdf                      1.5.317      01 June 2014 http://www.fpdf.de/downloads/fpdf-1.5.317.tgz
fpm                       1.14.2       27 May 2022  https://rubygems.org/downloads/fpm-1.14.2.gem
fprintd                   0.6.0        01 March 2015 http://people.freedesktop.org/~hadess/fprintd-0.6.0.tar.xz
frameworkintegration      5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/frameworkintegration-5.115.0.tar.xz
freealut                  1.1.0        01 June 2014 http://www.openal.org/openal_webstf/downloads/freealut-1.1.0.tar.gz
freebasic                 0.23.0       01 June 2014 https://sourceforge.net/projects/fbc/files/Source%20Code/FreeBASIC-0.23.0-source.tar.gz
freeciv                   2.5.4        21 July 2016 http://prdownloads.sourceforge.net/freeciv/freeciv-2.5.4.tar.bz2
freecol                   0.7.1        01 December 2012 http://www.freecol.org/news/freecol-0.10.5-released.html
freecycle                 0.6.1.1alpha 25 December 2015 http://download.savannah.gnu.org/releases/freecycle/freecycle-0.6.1.1alpha.tar.bz2
freeglut                  3.4.0        09 October 2022 https://sourceforge.net/projects/freeglut/files/freeglut/3.4.0/freeglut-3.4.0.tar.gz
freeimage                 3.18.0       08 September 2022 http://downloads.sourceforge.net/freeimage/FreeImage3180.zip
freeipmi                  1.6.14       29 March 2024 https://ftp.gnu.org/pub/gnu/freeipmi/freeipmi-1.6.14.tar.gz
freepop                   0.6.0        01 December 2012 https://sourceforge.net/projects/freepop/files/freepop/0.6.0/freepop-0.6.0.tar.gz
freerdp                   2.10.0       17 February 2023 https://github.com/FreeRDP/FreeRDP/releases/download/2.10.0/freerdp-2.10.0.tar.gz
freesteam                 2.0          01 June 2014 http://sourceforge.net/projects/freesteam/files/freesteam/2.0/freesteam-2.0.tar.bz2
freesynd                  0.7.5        14 April 2017 https://sourceforge.net/projects/freesynd/files/freesynd/freesynd-0.7.5/freesynd-0.7.5.tar.gz
freetds                   1.1.1        19 March 2019 ftp://ftp.freetds.org/pub/freetds/stable/freetds-1.1.1.tar.gz
freetype                  2.13.2       26 August 2023 https://downloads.sourceforge.net/freetype/freetype-2.13.2.tar.xz
freevo                    1.9.2b2      11 December 2017 https://sourceforge.net/projects/freevo/files/Freevo%20releases/1.9.2b2/freevo-1.9.2b2.tar.bz2
freewrl                   1.18.4       01 June 2014 http://ovh.dl.sourceforge.net/sourceforge/freewrl/freewrl-1.18.4.tar.gz
frei0rplugins             1.8.0        13 March 2024 https://files.dyne.org/frei0r/releases/frei0r-plugins-1.8.0.tar.gz
fribidi                   1.0.13       21 May 2023  https://github.com/fribidi/fribidi/releases/download/v1.0.13/fribidi-1.0.13.tar.xz
friction                  0.1          01 June 2014 http://remar.se/games/files/
frogr                     1.5          25 November 2018 http://ftp.gnome.org/pub/gnome/sources/frogr/1.5/frogr-1.5.tar.xz
frozenbubble              2.2.0        01 January 2013 http://www.frozen-bubble.org/data/frozen-bubble-2.2.0.tar.bz2
fslsfonts                 1.0.6        08 October 2022 https://www.x.org/releases/individual/app/fslsfonts-1.0.6.tar.xz
fspot                     0.6.2        01 June 2014 http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.6/f-spot-0.6.2.tar.bz2
fstobdf                   1.0.7        08 October 2022 https://www.x.org/releases/individual/app/fstobdf-1.0.7.tar.xz
ft2demos                  2.12.1       19 March 2023 https://download.savannah.gnu.org/releases/freetype/ft2demos-2.12.1.tar.xz
ftpd                      2.1.0        02 July 2020 https://rubygems.org/downloads/ftpd-2.1.0.gem
fuse                      3.16.2       14 October 2023 https://github.com/libfuse/libfuse/releases/download/fuse-3.16.2/fuse-3.16.2.tar.gz
fuseiso                   20070708     29 October 2014 https://sourceforge.net/projects/fuseiso/files/fuseiso/20070708/fuseiso-20070708.tar.bz2
fvwm                      2.7.0        05 November 2022 https://github.com/fvwmorg/fvwm/releases/download/2.7.0/fvwm-2.7.0.tar.gz
fvwm3                     1.0.4        04 January 2021 https://github.com/fvwmorg/fvwm3/releases/download/1.0.4/fvwm3-1.0.4.tar.gz
fxruby                    1.6.45       27 May 2022  https://rubygems.org/downloads/fxruby-1.6.45.gem
g3d                       10.00        01 May 2014  https://sourceforge.net/projects/g3d/files/g3d-cpp/10.00/G3D-10.00-source.zip
gaa                       1.6.6        01 May 2014  http://sourceforge.net/projects/gaa/files/gaa/gaa-1.6.6/gaa-1.6.6.tar.gz
gabedit                   2.1.8        01 June 2014 http://dfn.dl.sourceforge.net/sourceforge/gabedit/Gabedit218Src.tar.gz
galculator                2.1.4        02 August 2017 http://galculator.mnim.org/downloads/galculator-2.1.4.tar.bz2
gallipoli                 0.7.0        01 December 2012 http://www.um.com.au/gallipoli/
gama                      2.24         16 February 2023 https://ftp.gnu.org/pub/gnu/gama/gama-2.24.tar.gz
gambas                    3.17.3       19 September 2022 https://gitlab.com/gambas/gambas/-/archive/3.17.3/gambas-3.17.3.tar.bz2
gambit                    4.9.3        23 February 2019 https://github.com/gambit/gambit/archive/v4.9.3.tar.gz
gamgi                     13.          01 June 2014 http://www.gamgi.org/changelogs/changelogs13.html
gamin                     0.1.10       01 January 2013 http://www.gnome.org/~veillard/gamin/sources/gamin-0.1.10.tar.gz
garcon                    4.18.1       29 March 2023 https://archive.xfce.org/src/xfce/garcon/4.18/garcon-4.18.1.tar.bz2
garnome                   2.24.0       18 December 2018 http://ftp.gnome.org/pub/gnome/sources/garnome/2.24/garnome-2.24.0.tar.bz2
gaupol                    0.28.2       29 August 2015 http://download.gna.org/gaupol/0.28/gaupol-0.28.2.tar.xz
gav                       0.9.0        01 December 2012 https://sourceforge.net/projects/gav/files/gav/0.9.0/gav-0.9.0.tar.gz
gavl                      1.4.0        13 December 2019 https://sourceforge.net/projects/gmerlin/files/gavl/1.4.0/gavl-1.4.0.tar.gz
gawk                      5.3.0        02 November 2023 https://ftp.gnu.org/gnu/gawk/gawk-5.3.0.tar.xz
gbench                    2.6.0        01 October 2012 ftp://ftp.ncbi.nlm.nih.gov/toolbox/gbench/ver-2.6.0/gbench-2.6.0.tgz
gc                        8.2.4        29 May 2023  https://github.com/ivmai/bdwgc/releases/download/v8.2.4/gc-8.2.4.tar.gz
gcab                      1.5          24 December 2022 https://download.gnome.org/sources/gcab/1.5/gcab1.5.tar.xz
gcal                      3.6.2        01 June 2014 http://ftpmirror.gnu.org/gcal/gcal-3.6.2.tar.xz
gcalctool                 6.6.2        24 September 2014 http://ftp.gnome.org/pub/GNOME/sources/gcalctool/6.6/gcalctool-6.6.2.tar.xz
gcc                       02.04.2024   02 April 2024 https://ftp.gnu.org/gnu/gcc/gcc-13.2.0/gcc-02.04.2024.tar.xz
gccmakedep                1.0.3        01 May 2014  http://xorg.freedesktop.org/releases/individual/util/gccmakedep-1.0.3.tar.bz2
gcdemu                    1.2.0        01 June 2014 http://sourceforge.net/projects/cdemu/files/CDemu%20clients/gcdemu-1.2.0/gcdemu-1.2.0.tar.bz2
gchart                    1.0.0        01 December 2017 https://rubygems.org/downloads/gchart-1.0.0.gem
gcide                     0.53         27 April 2021 https://ftp.gnu.org/pub/gnu/gcide/gcide-0.53.tar.xz
gconf                     3.2.6        16 September 2017 http://ftp.acc.umu.se/pub/GNOME/sources/GConf/3.2/GConf-3.2.6.tar.xz
gconfcleaner              0.0.3        01 June 2014 https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/gconf-cleaner/gconf-cleaner-0.0.3.tar.gz
gconfmm                   2.28.3       20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/gconfmm/2.28/gconfmm-2.28.3.tar.xz
gcr                       4.3.0        13 April 2024 https://download.gnome.org/sources/gcr/4.3/gcr-4.3.0.tar.xz
gdado                     2.2          01 June 2014 http://sourceforge.net/projects/gdado/files/souce%20code/gdado-2.2/gdado-2.2.tar.gz
gdal                      2.1.4        20 September 2017 http://download.osgeo.org/gdal/2.1.4/gdal-2.1.4.tar.xz
gdb                       14.2         04 March 2024 https://ftp.gnu.org/gnu/gdb/gdb-14.2.tar.xz
gdbm                      1.23         16 September 2022 https://ftp.gnu.org/pub/gnu/gdbm/gdbm-1.23.tar.gz
gdesklets                 0.35.4       01 June 2014 http://www.gdesklets.de/files/gDesklets-0.35.4.tar.bz2
gdk3                      3.5.1        27 May 2022  https://rubygems.org/downloads/gdk3-3.5.1.gem
gdkpixbuf                 2.42.10      26 October 2022 https://download.gnome.org/sources/gdk-pixbuf/2.42/gdk-pixbuf-2.42.10.tar.xz
gdkpixbufxlib             2.40.2       13 November 2020 https://download.gnome.org/sources/gdk-pixbuf-xlib/2.40/gdk-pixbuf-xlib-2.40.2.tar.xz
gdl                       3.40.0       27 August 2021 https://download.gnome.org/sources/gdl/3.40/gdl-3.40.0.tar.xz
gdm                       46.0         19 March 2024 https://download.gnome.org/sources/gdm/46/gdm-46.0.tar.xz
gdsl                      1.8          25 April 2015 http://download.gna.org/gdsl/gdsl-1.8.tar.gz
geany                     1.38         17 October 2021 https://download.geany.org/geany-1.38.tar.gz
geanyplugins              1.38         18 March 2023 https://plugins.geany.org/geany-plugins/geany-plugins-1.38.tar.gz
geary                     44.1         18 August 2023 https://download.gnome.org/sources/geary/44/geary-44.1.tar.xz
gedit                     46.2         19 February 2024 https://download.gnome.org/sources/gedit/46/gedit-46.2.tar.xz
geditcodeassistance       3.16.0       30 April 2015 http://ftp.gnome.org/pub/GNOME/sources/gedit-code-assistance/3.16/gedit-code-assistance-3.16.0.tar.xz
geditplugins              44.1         26 April 2023 https://download.gnome.org/sources/gedit-plugins/44/gedit-plugins-44.1.tar.xz
gegl                      29.03.2024   08 March 2024 https://download.gimp.org/pub/gegl/0.4/gegl-0.4.48.tar.xz
geis                      2.2.16       01 September 2014 https://launchpad.net/geis/trunk/2.2.16/+download/geis-2.2.16.tar.xz
gengetopt                 2.23         09 June 2019 ftp://ftp.gnu.org/gnu/gengetopt/gengetopt-2.23.tar.xz
genius                    1.0.27       28 October 2021 https://download.gnome.org/sources/genius/1.0/genius-1.0.27.tar.xz
genshi                    0.7          10 August 2018 https://ftp.edgewall.org/pub/genshi/Genshi-0.7.tar.gz
genx4r                    0.05         01 June 2014 https://rubygems.org/downloads/genx4r-0.05.gem
geoclue                   2.7.1        14 September 2023 https://gitlab.freedesktop.org/geoclue/geoclue/-/archive/2.7.1/geoclue-2.7.1.tar.bz2
geocodeglib               3.26.4       19 September 2022 https://download.gnome.org/sources/geocode-glib/3.26/geocode-glib-3.26.4.tar.xz
geos                      3.6.2        20 September 2017 http://download.osgeo.org/geos/geos-3.6.2.tar.bz2
geshi                     1.0.9.0      20 September 2017 https://sourceforge.net/projects/geshi/files/geshi/GeSHi%201.0.9.0/GeSHi-1.0.9.0.tar.bz2
getmail                   5.15         01 January 2021 http://pyropus.ca/software/getmail/old-versions/getmail-5.15.tar.gz
gettext                   0.22.5       22 February 2024 https://ftp.gnu.org/gnu/gettext/gettext-0.22.5.tar.xz
gexiv2                    0.14.2       16 March 2024 https://download.gnome.org/sources/gexiv2/0.14/gexiv2-0.14.2.tar.xz
gfbgraph                  0.2.5        30 October 2021 https://download.gnome.org/sources/gfbgraph/0.2/gfbgraph-0.2.5.tar.xz
gftp                      2.0.19       01 January 2013 http://gftp.seul.org/gftp-2.0.19.tar.bz2
ggv                       2.12.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/ggv/2.12/ggv-2.12.0.tar.bz2
ghemical                  3.0.0        01 November 2012 https://bioinformatics.org/ghemical/download/current/ghemical-3.0.0.tar.gz
gherkin                   9.0.0        28 May 2020  https://rubygems.org/downloads/gherkin-9.0.0.gem
ghex                      46.0         22 March 2024 https://download.gnome.org/sources/ghex/46/ghex-46.0.tar.xz
ghostscript               10.03.0      11 March 2024 https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs10030/ghostscript-10.03.0.tar.xz
ghostwriter               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/ghostwriter-24.02.2.tar.xz
giblib                    1.2.4        01 June 2014 http://linuxbrit.co.uk/downloads/giblib-1.2.4.tar.gz
gif2apng                  1.6          01 June 2014 https://sourceforge.net/projects/gif2apng/files/1.6/gif2apng-1.6
giflib                    5.2.2        24 February 2024 https://sourceforge.net/projects/giflib/files/giflib-5.2.2.tar.gz
gifsicle                  1.88         18 March 2017 http://www.lcdf.org/gifsicle/gifsicle-1.88.tar.gz
gift                      0.1.14       01 June 2014 ftp://ftp.gnu.org/gnu/gift/gift-0.1.14.tar.gz
gimp                      15.03.2024   06 November 2023 https://download.gimp.org/mirror/pub/gimp/v2.10/gimp-15.03.2024.tar.bz2
gimpsharp                 0.13         01 June 2014 http://gimp-sharp.sourceforge.net/gimp-sharp-0.13.tar.gz
gingerblue                6.2.0        03 September 2022 https://download.gnome.org/sources/gingerblue/6.2/gingerblue-6.2.0.tar.xz
giostandalone             0.1.2        01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gio-standalone/0.1/gio-standalone-0.1.2.tar.bz2
girara                    0.2.6        18 August 2016 https://pwmt.org/projects/girara/download/girara-0.2.6.tar.gz
girl                      9.9.8        27 April 2017 http://ftp.gnome.org/pub/gnome/sources/girl/9.9/girl-9.9.8.tar.xz
gist                      6.0.0        15 April 2021 https://rubygems.org/downloads/gist-6.0.0.gem
git                       2.44.0       23 February 2024 https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.44.0.tar.xz
gitcola                   2.10         27 July 2017 https://github.com/git-cola/git-cola/archive/v2.10.tar.gz
gitdb                     0.6.4        10 August 2017 https://pypi.python.org/packages/e3/95/7e5d7261feb46c0539ac5e451be340ddd64d78c5118f2d893b052c76fe8c/gitdb-0.6.4.tar.gz#md5=44e4366b8bdfd306b075c3a52c96ae1a
gitg                      3.32.0       23 May 2019  http://ftp.gnome.org/pub/gnome/sources/gitg/3.32/gitg-3.32.0.tar.xz
giv                       0.9.15       01 June 2014 http://downloads.sourceforge.net/giv/giv-0.9.15.tar.gz
gjs                       1.80.2       27 March 2024 https://download.gnome.org/sources/gjs/1.80/gjs-1.80.2.tar.xz
gkrellm                   2.3.11       25 August 2022 http://gkrellm.srcbox.net/releases/gkrellm-2.3.11.tar.bz2
glabels                   3.4.1        29 April 2018 http://ftp.gnome.org/pub/gnome/sources/glabels/3.4/glabels-3.4.1.tar.xz
glad                      2.0.6        22 March 2024 https://github.com/Dav1dde/glad/archive/refs/tags/v2.0.6/glad-2.0.6.tar.gz
glade                     3.40.0       11 August 2022 https://download.gnome.org/sources/glade/3.40/glade-3.40.0.tar.xz
glade3                    3.8.6        08 August 2017 http://ftp.gnome.org/pub/gnome/sources/glade3/3.8/glade3-3.8.6.tar.xz
glamoregl                 0.6.0        01 January 2014 https://www.x.org/releases/individual/driver/glamor-egl-0.6.0.tar.bz2
glark                     1.7.10       28 July 2016 https://sourceforge.net/projects/glark/files/glark/1.7.10/glark-1.7.10.tar.gz
glew                      2.2.0        05 June 2020 https://sourceforge.net/projects/glew/files/glew/2.2.0/glew-2.2.0.tgz
glfw                      3.2.1        03 October 2019 https://github.com/glfw/glfw/releases/download/3.3/glfw-3.3.zip
glib                      2.80.0       09 March 2024 https://download.gnome.org/sources/glib/2.80/glib-2.80.0.tar.xz
glibc                     2.39         02 February 2024 https://ftp.gnu.org/gnu/glibc/glibc-2.39.tar.xz
glibclibidn               2.10.1       01 June 2014 http://ftp.gnu.org/gnu/libc/glibc-libidn-2.10.1.tar.bz2
glibmm                    2.78.1       08 February 2024 https://download.gnome.org/sources/glibmm/2.78/glibmm-2.78.1.tar.xz
glibnetworking            2.80.0       20 March 2024 https://download.gnome.org/sources/glib-networking/2.80/glib-networking-2.80.0.tar.xz
glibopenssl               2.50.7       27 February 2018 http://ftp.gnome.org/pub/gnome/sources/glib-openssl/2.50/glib-openssl-2.50.7.tar.xz
glimmer                   302          24 June 2017 http://ccb.jhu.edu/software/glimmer/glimmer302b.tar.gz
glm                       0.9.9.8      05 June 2020 https://github.com/g-truc/glm/releases/download/0.9.9.8/glm-0.9.9.8.7z
glob2                     0.9.4.4      01 July 2013 http://dl.sv.nongnu.org/releases/glob2/0.9.4/glob2-0.9.4.4.tar.gz
globalid                  1.0.0        27 May 2022  https://rubygems.org/downloads/globalid-1.0.0.gem
glom                      1.30.4       11 June 2016 http://ftp.gnome.org/pub/GNOME/sources/glom/1.30/glom-1.30.4.tar.xz
glpk                      5.0          17 December 2020 https://ftp.gnu.org/pub/gnu/glpk/glpk-5.0.tar.gz
glproto                   1.4.17       01 December 2013 http://xorg.freedesktop.org/releases/individual/proto/glproto-1.4.17.tar.bz2
glslang                   14.1.0       18 March 2024 https://github.com/KhronosGroup/glslang/archive/refs/tags/14.1.0/glslang-14.1.0.tar.gz
glu                       9.0.2        26 June 2021 ftp://ftp.freedesktop.org/pub/mesa/glu/glu-9.0.2.tar.xz
glue                      1.1.1        01 December 2017 https://rubygems.org/downloads/glue-1.1.1.gem
glut                      3.7          01 December 2012 http://www.opengl.org/resources/libraries/glut/glut-3.7.tar.gz
glycinloaders             1.0.1        31 March 2024 https://download.gnome.org/sources/glycin-loaders/1.0/glycin-loaders-1.0.1.tar.xz
gmail                     0.7.1        22 July 2018 https://rubygems.org/downloads/gmail-0.7.1.gem
gmailxoauth               0.4.2        27 December 2017 https://rubygems.org/downloads/gmail_xoauth-0.4.2.gem
gmerlin                   1.2.0        03 October 2019 https://sourceforge.net/projects/gmerlin/files/gmerlin/1.2.0/gmerlin-1.2.0.tar.gz
gmic                      1.5.7.1      01 October 2013 http://downloads.sourceforge.net/project/gmic/gmic_1.5.7.1.tar.gz
gmime                     3.2.13       20 March 2023 https://github.com/jstedfast/gmime/releases/download/3.2.13/gmime-3.2.13.tar.xz
gmp                       6.3.0        21 January 2024 https://gmplib.org/download/gmp/gmp-6.3.0.tar.xz
gmsh                      1.65.0       01 June 2014 http://geuz.org/gmsh/src/gmsh-1.65.0-source.tgz
gmtk                      1.0.9a       01 November 2013 http://gmtk.googlecode.com/files/gmtk-1.0.9a.tar.gz
gnash                     0.8.10       03 June 2014 http://ftp.gnu.org/gnu/gnash/0.8.10/gnash-0.8.10.tar.bz2
gnet                      2.0.8        01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gnet/2.0/gnet-2.0.8.tar.bz2
gneutronica               0.33         01 June 2014 https://sourceforge.net/projects/gneutronica/files/gneutronica/gneutronica-0.33/gneutronica-0.33.tar.gz
gno3dtet                  1.96.1       28 July 2016 http://www.eseb.net/ftp/gno3dtet/gno3dtet-1.96.1.tgz
gnoise                    0.1.15       01 June 2014 https://sourceforge.net/projects/gnoise/files/gnoise/0.1.15/gnoise-0.1.15.tar.gz
gnomeapplets              3.50.0       19 February 2024 https://download.gnome.org/sources/gnome-applets/3.50/gnome-applets-3.50.0.tar.xz
gnomeautoar               0.4.4        29 May 2023  https://download.gnome.org/sources/gnome-autoar/0.4/gnome-autoar-0.4.4.tar.xz
gnomebackgrounds          44.0         14 April 2023 https://download.gnome.org/sources/gnome-backgrounds/44/gnome-backgrounds-44.0.tar.xz
gnomebatterybench         3.15.4       07 March 2015 http://ftp.gnome.org/pub/GNOME/sources/gnome-battery-bench/3.15/gnome-battery-bench-3.15.4.tar.xz
gnomebluetooth            42.5         13 December 2022 https://download.gnome.org/sources/gnome-bluetooth/42/gnome-bluetooth-42.5.tar.xz
gnomebooks                40.0         16 October 2021 https://ftp.acc.umu.se/pub/gnome/sources/gnome-books/40/gnome-books-40.0.tar.xz
gnomeboxes                46.0         19 March 2024 https://download.gnome.org/sources/gnome-boxes/46/gnome-boxes-46.0.tar.xz
gnomebtdownload           0.0.32       01 June 2014 http://sourceforge.net/projects/gnome-bt/files/gnome-bt/0.0.32/gnome-btdownload-0.0.32.tar.gz
gnomebuild                0.2.4        01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-build/0.2/gnome-build-0.2.4.tar.bz2
gnomebuilder              44.2         28 April 2023 https://download.gnome.org/sources/gnome-builder/44/gnome-builder-44.2.tar.xz
gnomecalculator           42.2         02 July 2022 https://download.gnome.org/sources/gnome-calculator/42/gnome-calculator-42.2.tar.xz
gnomecalendar             44.1         22 August 2023 https://download.gnome.org/sources/gnome-calendar/44/gnome-calendar-44.1.tar.xz
gnomecharacters           42.0         04 September 2022 https://download.gnome.org/sources/gnome-characters/42/gnome-characters-42.0.tar.xz
gnomechemistryutils       0.9.2        01 June 2014 http://download.savannah.nongnu.org/releases/gchemutils/0.9/gnome-chemistry-utils-0.9.2.tar.bz2
gnomechess                42.1         16 September 2022 https://download.gnome.org/sources/gnome-chess/42/gnome-chess-42.1.tar.xz
gnomeclocks               41.0         17 October 2021 https://download.gnome.org/sources/gnome-clocks/41/gnome-clocks-41.0.tar.xz
gnomecodeassistance       3.16.0       30 April 2015 http://ftp.gnome.org/pub/GNOME/sources/gnome-code-assistance/3.16/gnome-code-assistance-3.16.0.tar.xz
gnomecolormanager         3.36.0       03 April 2020 http://ftp.gnome.org/pub/gnome/sources/gnome-color-manager/3.36/gnome-color-manager-3.36.0.tar.xz
gnomecommander            1.16.1       10 July 2023 https://download.gnome.org/sources/gnome-commander/1.16/gnome-commander-1.16.1.tar.xz
gnomecommon               3.18.0       22 September 2015 http://ftp.gnome.org/pub/GNOME/sources/gnome-common/3.18/gnome-common-3.18.0.tar.xz
gnomeconnections          44.1         24 April 2023 https://download.gnome.org/sources/gnome-connections/44/gnome-connections-44.1.tar.xz
gnomecontacts             42.0         22 March 2022 https://download.gnome.org/sources/gnome-contacts/42/gnome-contacts-42.0.tar.xz
gnomecontrolcenter        46.0.1       27 March 2024 https://download.gnome.org/sources/gnome-control-center/46/gnome-control-center-46.0.1.tar.xz
gnomecupsmanager          0.33         01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-cups-manager/0.33/gnome-cups-manager-0.33.tar.bz2
gnomedesktop              44.0         20 March 2023 https://download.gnome.org/sources/gnome-desktop/44/gnome-desktop-44.0.tar.xz
gnomedictionary           3.26.1       02 October 2017 http://ftp.gnome.org/pub/gnome/sources/gnome-dictionary/3.26/gnome-dictionary-3.26.1.tar.xz
gnomedirectorythumbnailer 0.1.10       26 January 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-directory-thumbnailer/0.1/gnome-directory-thumbnailer-0.1.10.tar.xz
gnomediskutility          46.0         09 March 2024 https://download.gnome.org/sources/gnome-disk-utility/46/gnome-disk-utility-46.0.tar.xz
gnomedocuments            3.30.1       19 January 2019 http://ftp.gnome.org/pub/gnome/sources/gnome-documents/3.30/gnome-documents-3.30.1.tar.xz
gnomedocutils             0.20.10      20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/gnome-doc-utils/0.20/gnome-doc-utils-0.20.10.tar.xz
gnomedvbdaemon            0.2.90       01 August 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-dvb-daemon/0.2/gnome-dvb-daemon-0.2.90.tar.xz
gnomeepubthumbnailer      1.6          02 October 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-epub-thumbnailer/1.6/gnome-epub-thumbnailer-1.6.tar.xz
gnomeflashback            3.42.1       26 November 2021 https://download.gnome.org/sources/gnome-flashback/3.42/gnome-flashback-3.42.1.tar.xz
gnomefontviewer           42.0         19 September 2022 https://download.gnome.org/sources/gnome-font-viewer/42/gnome-font-viewer-42.0.tar.xz
gnomegames                40.0         21 August 2022 https://download.gnome.org/sources/gnome-games/40/gnome-games-40.0.tar.xz
gnomehearts               0.2          01 June 2014 http://www.jejik.com/files/gnome-hearts/gnome-hearts-0.2.tar.gz
gnomeicontheme            3.12.0       01 April 2014 http://ftp.gnome.org/pub/gnome/sources/gnome-icon-theme/3.12/gnome-icon-theme-3.12.0.tar.xz
gnomeiconthemeextras      3.12.0       01 April 2014 http://ftp.gnome.org/pub/gnome/sources/gnome-icon-theme-extras/3.12/gnome-icon-theme-extras-3.12.0.tar.xz
gnomeiconthemesymbolic    3.12.0       01 April 2014 http://ftp.gnome.org/pub/gnome/sources/gnome-icon-theme-symbolic/3.12/gnome-icon-theme-symbolic-3.12.0.tar.xz
gnomeinitialsetup         46.0         16 March 2024 https://download.gnome.org/sources/gnome-initial-setup/46/gnome-initial-setup-46.0.tar.xz
gnomeinternetradiolocator 12.7.0       14 September 2022 https://download.gnome.org/sources/gnome-internet-radio-locator/12.7/gnome-internet-radio-locator-12.7.0.tar.xz
gnomekeyring              46.1         09 April 2024 https://download.gnome.org/sources/gnome-keyring/46/gnome-keyring-46.1.tar.xz
gnomekeyringmanager       2.20.0       01 June 2014 ftp://ftp.gnome.org/pub/gnome/sources/gnome-keyring-manager/2.20/gnome-keyring-manager-2.20.0.tar.bz2
gnomeklotski              3.38.2       24 November 2020 https://download.gnome.org/sources/gnome-klotski/3.38/gnome-klotski-3.38.2.tar.xz
gnomekraorathumbnailer    1.3          01 December 2013 http://ftp.gnome.org/pub/GNOME/sources/gnome-kra-ora-thumbnailer/1.3/gnome-kra-ora-thumbnailer-1.3.tar.xz
gnomelatex                3.42.0       03 November 2022 https://download.gnome.org/sources/gnome-latex/3.42/gnome-latex-3.42.0.tar.xz
gnomelogs                 42.0         28 March 2022 https://download.gnome.org/sources/gnome-logs/42/gnome-logs-42.0.tar.xz
gnomemag                  0.15.1       01 June 2014 http://ftp.gnome.org/pub/gnome/sources/gnome-mag/0.15/gnome-mag-0.15.1.tar.bz2
gnomemahjongg             3.38.1       19 September 2020 http://ftp.gnome.org/pub/gnome/sources/gnome-mahjongg/3.38/gnome-mahjongg-3.38.1.tar.xz
gnomemainmenu             1.8.0        01 June 2014 http://pub.mate-desktop.org/releases/1.8/gnome-main-menu-1.8.0.tar.xz
gnomemaps                 44.2         26 May 2023  https://download.gnome.org/sources/gnome-maps/44/gnome-maps-44.2.tar.xz
gnomemenus                3.36.0       12 March 2020 https://ftp.gnome.org/pub/gnome/sources/gnome-menus/3.36/gnome-menus-3.36.0.tar.xz
gnomemines                40.1         19 February 2022 https://download.gnome.org/sources/gnome-mines/40/gnome-mines-40.1.tar.xz
gnomemplayer              1.0.9b       01 November 2013 https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/gnome-mplayer/gnome-mplayer-1.0.9b.tar.gz
gnomemultiwriter          3.30.0       05 September 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-multi-writer/3.30/gnome-multi-writer-3.30.0.tar.xz
gnomemusic                44.0         23 March 2023 https://download.gnome.org/sources/gnome-music/44/gnome-music-44.0.tar.xz
gnomenetstatus            2.28.2       02 August 2017 http://ftp.gnome.org/pub/GNOME/sources/gnome-netstatus/2.28/gnome-netstatus-2.28.2.tar.gz
gnomenettool              42.0         07 April 2022 https://download.gnome.org/sources/gnome-nettool/42/gnome-nettool-42.0.tar.xz
gnomenetwork              1.99.5       01 June 2014 ftp://ftp.gnome.org/pub/GNOME/sources/gnome-network/1.99/gnome-network-1.99.5.tar.bz2
gnomenibbles              3.38.1       05 October 2020 http://ftp.gnome.org/pub/gnome/sources/gnome-nibbles/3.38/gnome-nibbles-3.38.1.tar.xz
gnomeonlineaccounts       3.50.0       09 April 2024 https://download.gnome.org/sources/gnome-online-accounts/3.50/gnome-online-accounts-3.50.0.tar.xz
gnomeonlineminers         3.34.0       11 September 2019 http://ftp.gnome.org/pub/gnome/sources/gnome-online-miners/3.34/gnome-online-miners-3.34.0.tar.xz
gnomepackagekit           3.30.0       05 September 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-packagekit/3.30/gnome-packagekit-3.30.0.tar.xz
gnomepanel                3.42.0       24 October 2021 https://download.gnome.org/sources/gnome-panel/3.42/gnome-panel-3.42.0.tar.xz
gnomephonemanager         0.69         24 September 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-phone-manager/0.69/gnome-phone-manager-0.69.tar.xz
gnomephotos               3.38.1       19 February 2021 https://download.gnome.org/sources/gnome-photos/3.38/gnome-photos-3.38.1.tar.xz
gnomepkgtool              0.5.2        01 June 2014 https://sourceforge.net/projects/gnome-pkgtool/files/gnome-pkgtool/0.5.2/
gnomepowermanager         3.30.0       05 September 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-power-manager/3.30/gnome-power-manager-3.30.0.tar.xz
gnomepythondesktop        2.23.0       01 January 2013 http://ftp.gnome.org/pub/GNOME/sources/gnome-python-desktop/2.23/gnome-python-desktop-2.23.0.tar.bz2
gnomeradio                64.0         09 November 2022 https://download.gnome.org/sources/gnome-radio/64/gnome-radio-64.0.tar.xz
gnomerecipes              1.2.0        08 May 2017  http://ftp.gnome.org/pub/gnome/sources/gnome-recipes/1.2/gnome-recipes-1.2.0.tar.xz
gnomeremotedesktop        46.0         17 March 2024 https://download.gnome.org/sources/gnome-remote-desktop/46/gnome-remote-desktop-46.0.tar.xz
gnomerobots               3.36.1       27 March 2020 http://ftp.gnome.org/pub/gnome/sources/gnome-robots/3.36/gnome-robots-3.36.1.tar.xz
gnomescan                 0.5.94       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-scan/0.5/gnome-scan-0.5.94.tar.bz2
gnomeschedule             2.2.2        01 June 2014 http://sourceforge.net/projects/gnome-schedule/files/gnome-schedule-2/gnome-schedule-2-2-2/gnome-schedule-2.2.2.tar.gz
gnomescreensaver          3.6.1        24 September 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-screensaver/3.6/gnome-screensaver-3.6.1.tar.xz
gnomescreenshot           41.0         15 November 2021 https://download.gnome.org/sources/gnome-screenshot/41/gnome-screenshot-41.0.tar.xz
gnomesession              46.0         13 April 2024 https://download.gnome.org/sources/gnome-session/46/gnome-session-46.0.tar.xz
gnomesettingsdaemon       44.1         18 April 2023 https://download.gnome.org/sources/gnome-settings-daemon/44/gnome-settings-daemon-44.1.tar.xz
gnomesharp                2.24.0       01 June 2014 http://ftp.gnome.org/pub/gnome/sources/gnome-sharp/2.24/gnome-sharp-2.24.0.tar.bz2
gnomeshell                46.0         16 March 2024 https://download.gnome.org/sources/gnome-shell/46/gnome-shell-46.0.tar.xz
gnomeshellextensions      42.1         06 May 2022  https://download.gnome.org/sources/gnome-shell-extensions/42/gnome-shell-extensions-42.1.tar.xz
gnomesoftware             40.4         13 August 2021 https://download.gnome.org/sources/gnome-software/40/gnome-software-40.4.tar.xz
gnomesoundrecorder        42.0         05 April 2022 https://download.gnome.org/sources/gnome-sound-recorder/42/gnome-sound-recorder-42.0.tar.xz
gnomespeech               0.4.16       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-speech/
gnomesubtitles            1.1          01 June 2014 http://downloads.sourceforge.net/gnome-subtitles/gnome-subtitles-1.1.tar.gz
gnomesudoku               42.0         17 March 2022 https://download.gnome.org/sources/gnome-sudoku/42/gnome-sudoku-42.0.tar.xz
gnomesystemmonitor        40.1         30 April 2021 https://download.gnome.org/sources/gnome-system-monitor/40/gnome-system-monitor-40.1.tar.xz
gnomesystemtools          3.0.0        20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/gnome-system-tools/3.0/gnome-system-tools-3.0.0.tar.bz2
gnometaquin               3.34.1       08 October 2019 http://ftp.gnome.org/pub/gnome/sources/gnome-taquin/3.34/gnome-taquin-3.34.1.tar.xz
gnometerminal             3.48.1       06 August 2023 https://gitlab.gnome.org/GNOME/gnome-terminal/-/archive/3.48.1/gnome-terminal-3.48.1.tar.gz
gnometetravex             3.38.2       24 November 2020 https://download.gnome.org/sources/gnome-tetravex/3.38/gnome-tetravex-3.38.2.tar.xz
gnomethemes               3.0.0        01 June 2014 ftp://ftp.gnome.org/pub/GNOME/sources/gnome-themes/3.0/gnome-themes-3.0.0.tar.bz2
gnomethemesextra          3.28         24 March 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-themes-extra/3.28/gnome-themes-extra-3.28.tar.xz
gnomethemesstandard       3.27.90      14 February 2018 http://ftp.gnome.org/pub/gnome/sources/gnome-themes-standard/3.27/gnome-themes-standard-3.27.90.tar.xz
gnometodo                 40.1         16 June 2021 https://download.gnome.org/sources/gnome-todo/40/gnome-todo-40.1.tar.xz
gnometweaks               46.0         13 April 2024 https://download.gnome.org/sources/gnome-tweaks/46/gnome-tweaks-46.0.tar.xz
gnometweaktool            3.26.4       30 December 2017 http://ftp.gnome.org/pub/gnome/sources/gnome-tweak-tool/3.26/gnome-tweak-tool-3.26.4.tar.xz
gnomeusage                3.37.1       05 August 2020 http://ftp.gnome.org/pub/gnome/sources/gnome-usage/3.37/gnome-usage-3.37.1.tar.xz
gnomeusershare            3.34.0       22 November 2019 http://ftp.gnome.org/pub/GNOME/sources/gnome-user-share/3.34/gnome-user-share-3.34.0.tar.xz
gnomeutils                3.2.1        20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/gnome-utils/3.2/gnome-utils-3.2.1.tar.xz
gnomevfsmm                2.26.0       01 June 2014 http://ftp.acc.umu.se/pub/GNOME/sources/gnome-vfsmm/2.26/gnome-vfsmm-2.26.0.tar.bz2
gnomevideoarcade          0.8.8        31 October 2017 http://ftp.gnome.org/pub/gnome/sources/gnome-video-arcade/0.8/gnome-video-arcade-0.8.8.tar.xz
gnomevideoeffects         0.4.1        01 March 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-video-effects/0.4/gnome-video-effects-0.4.1.tar.xz
gnomevoicecontrol         0.4          01 June 2014 http://prdownload.berlios.de/festlang/gnome-voice-control-0.4.tar.gz
gnomevolumemanager        2.17.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gnome-volume-manager/
gnomeweather              46.0         05 April 2024 https://download.gnome.org/sources/gnome-weather/46/gnome-weather-46.0.tar.xz
gnonlin                   1.2.0        01 April 2014 http://gstreamer.freedesktop.org/src/gnonlin/gnonlin-1.2.0.tar.xz
gnopernicus               1.1.2        01 June 2014 http://ftp.gnome.org/pub/gnome/sources/gnopernicus/1.1/gnopernicus-1.1.2.tar.bz2
gnormalize                0.63         01 June 2014 http://prdownloads.sourceforge.net/gnormalize/gnormalize-0.63.tar.gz
gnote                     46.0         23 March 2024 https://download.gnome.org/sources/gnote/46/gnote-46.0.tar.xz
gnuastro                  0.20         01 May 2023  https://ftp.gnu.org/pub/gnu/gnuastro/gnuastro-0.20.tar.gz
gnucash                   5.6          01 April 2024 https://github.com/Gnucash/gnucash/releases/download/5.6/gnucash-5.6.tar.bz2
gnuchess                  6.2.9        15 July 2021 https://ftp.gnu.org/pub/gnu/chess/gnuchess-6.2.9.tar.gz
gnucobol                  3.1.1        12 December 2020 https://ftp.gnu.org/pub/gnu/gnucobol/gnucobol-3.1.1.tar.xz
gnugo                     3.8          01 January 2013 http://ftp.gnu.org/gnu/gnugo/gnugo-3.8.tar.gz
gnuhealth                 4.2.0        13 February 2023 https://ftp.gnu.org/pub/gnu/health/gnuhealth-4.2.0.tar.gz
gnujump                   1.0.5        01 December 2012 http://download.savannah.gnu.org/releases/gnujump/gnujump-1.0.5.tar.gz
gnulib                    17.11.2019   17 November 2019 http://git.savannah.gnu.org/gitweb/?p=gnulib.git
gnumeric                  1.12.57      12 February 2024 https://download.gnome.org/sources/gnumeric/1.12/gnumeric-1.12.57.tar.xz
gnump3d                   3.0          01 June 2014 http://savannah.gnu.org/download/gnump3d/gnump3d-3.0.tar.bz2
gnun                      1.3          09 November 2022 https://ftp.gnu.org/pub/gnu/gnun/gnun-1.3.tar.gz
gnunet                    0.19.4       01 April 2023 https://ftp.gnu.org/pub/gnu/gnunet/gnunet-0.19.4.tar.gz
gnunetgtk                 0.21.0       04 April 2024 https://git.gnunet.org/gnunet-gtk.git/snapshot/gnunet-gtk-0.21.0.tar.gz
gnupdf                    04.04.2024   04 April 2024 https://www.gnu.org/software/pdf/gnupdf-04.04.2024
gnupg                     2.4.5        07 March 2024 https://gnupg.org/ftp/gcrypt/gnupg/gnupg-2.4.5.tar.bz2
gnuplot                   6.0.0        21 February 2024 https://sourceforge.net/projects/gnuplot/files/gnuplot/6.0.0/gnuplot-6.0.0.tar.gz
gnuradio                  3.9.0.0      18 January 2021 https://www.gnuradio.org/releases/gnuradio/gnuradio-3.9.0.0.tar.xz
gnurl                     7.70.0       01 May 2020  http://ftp.gnu.org/pub/gnu/gnunet/gnurl-7.70.0.tar.gz
gnustepbase               1.24.0       01 June 2014 ftp://ftp.gnustep.org/pub/gnustep/core/gnustep-base-1.24.0.tar.gz
gnustepmake               1.12.0       01 June 2014 ftp://ftp.gnustep.org/pub/gnustep/core/gnustep-make-1.12.0.tar.gz
gnutls                    3.8.5        05 April 2024 https://www.gnupg.org/ftp/gcrypt/gnutls/v3.8/gnutls-3.8.5.tar.xz
gnuuid                    0.5.1        14 October 2018 https://rubygems.org/downloads/gn_uuid-0.5.1.gem
go                        1.4.2        19 May 2015  https://storage.googleapis.com/golang/go1.4.2tar.gz
gob2                      2.0.20       01 December 2013 http://ftp.gnome.org/pub/GNOME/sources/gob2/2.0/gob2-2.0.20.tar.xz
gobby                     0.5.0        02 June 2018 http://releases.0x539.de/gobby/gobby-0.5.0.tar.gz
gobjectintrospection      1.80.1       01 April 2024 https://download.gnome.org/sources/gobject-introspection/1.80/gobject-introspection-1.80.1.tar.xz
gocr                      0.47         02 August 2017 https://sourceforge.net/projects/jocr/files/gocr/0.47/gocr-0.47.tar.gz
god                       0.13.7       03 September 2022 https://rubygems.org/downloads/god-0.13.7.gem
goffice                   0.10.57      23 February 2024 https://download.gnome.org/sources/goffice/0.10/goffice-0.10.57.tar.xz
gok                       2.30.1       20 August 2017 http://ftp.acc.umu.se/pub/GNOME/sources/gok/2.30/gok-2.30.1.tar.gz
golly                     4.0          18 January 2023 https://sourceforge.net/projects/golly/files/golly/golly-4.0/golly-4.0.tar.gz
gom                       0.5.1        11 April 2024 https://download.gnome.org/sources/gom/0.5/gom-0.5.1.tar.xz
gonzui                    1.2          01 June 2014 https://rubygems.org/downloads/gonzui-1.2.gem
goobox                    3.6.0        10 April 2019 https://ftp.gnome.org/pub/gnome/sources/goobox/3.6/goobox-3.6.0.tar.xz
goocanvas                 3.0.0        26 January 2021 https://download.gnome.org/sources/goocanvas/3.0/goocanvas-3.0.0.tar.xz
googleauth                1.1.3        27 May 2022  https://rubygems.org/downloads/googleauth-1.1.3.gem
googletest                27.03.2024   27 March 2024 https://download.kde.org/stable/googletest-27.03.2024
gosu                      1.4.3        27 May 2022  https://rubygems.org/downloads/gosu-1.4.3.gem
gpa                       0.10.0       30 October 2018 https://www.gnupg.org/ftp/gcrypt/gpa/gpa-0.10.0.tar.bz2
gpac                      0.7.1        27 February 2018 https://github.com/gpac/gpac/archive/v0.7.1.tar.gz
gpaint                    0.3.3        01 June 2014 ftp://alpha.gnu.org/gnu/gpaint/gpaint-2-0.3.3.tar.gz
gparted                   1.6.0        27 February 2024 https://downloads.sourceforge.net/gparted/gparted-1.6.0.tar.gz
gperf                     3.1          20 July 2017 https://ftp.gnu.org/pub/gnu/gperf/gperf-3.1.tar.gz
gperiodic                 2.0.10       01 June 2014 http://www.frantz.fi/software/gperiodic-2.0.10.tar.gz
gpgme                     1.23.2       03 December 2023 https://www.gnupg.org/ftp/gcrypt/gpgme/gpgme-1.23.2.tar.bz2
gphoto2                   2.5.28       05 January 2022 https://sourceforge.net/projects/gphoto/files/gphoto/2.5.28/gphoto2-2.5.28.tar.bz2
gpm                       1.20.7       18 February 2019 http://anduin.linuxfromscratch.org/BLFS/gpm/gpm-1.20.7.tar.bz2
gpredict                  2.2.1        04 April 2024 https://github.com/csete/gpredict/releases/download/v2.2.1/gpredict-2.2.1.tar.bz2
gprolog                   1.5.0        09 July 2021 https://ftp.gnu.org/pub/gnu/gprolog/gprolog-1.5.0.tar.gz
gpsd                      2.36         01 June 2014 http://download.berlios.de/gpsd/gpsd-2.36.tar.gz
gptfdisk                  1.0.10       24 February 2024 https://downloads.sourceforge.net/gptfdisk/gptfdisk-1.0.10.tar.gz
gqview                    2.1.5        02 January 2018 http://prdownloads.sourceforge.net/gqview/gqview-2.1.5.tar.gz
gr                        0.66.0       12 July 2022 https://github.com/sciapp/gr/archive/refs/tags/v0.66.0.tar.gz
grabc                     1.1          01 June 2014 http://freshmeat.net/projects/grabc-1.1.tar.xz
grace                     5.1.25       19 October 2018 ftp://plasma-gate.weizmann.ac.il/pub/grace/src/grace5/grace-5.1.25.tar.gz
gradle                    6.2-         22 February 2020 https://services.gradle.org/distributions/gradle-6.2-bin.zip
gramps                    5.1.3        22 September 2020 https://sourceforge.net/projects/gramps/files/Stable/5.1.3/gramps-5.1.3.tar.gz
granatier                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/granatier-24.02.2.tar.xz
grantlee                  5.3.1        16 November 2022 https://github.com/steveire/grantlee/releases/download/v5.3.1/grantlee-5.3.1.tar.gz
grantleeeditor            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/grantlee-editor-24.02.2.tar.xz
grantleetheme             24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/grantleetheme-24.02.2.tar.xz
grape                     1.6.2        27 May 2022  https://rubygems.org/downloads/grape-1.6.2.gem
graphene                  1.10.8       25 March 2022 https://download.gnome.org/sources/graphene/1.10/graphene-1.10.8.tar.xz
graphicsmagick            1.3.36       27 February 2021 https://sourceforge.net/projects/graphicsmagick/files/graphicsmagick/1.3.36/GraphicsMagick-1.3.36.tar.xz
graphite2                 1.3.14       11 January 2021 https://github.com/silnrsi/graphite/releases/download/1.3.14/graphite2-1.3.14.tgz
graphviz                  10.0.1       12 March 2024 https://gitlab.com/graphviz/graphviz/-/archive/10.0.1/graphviz-10.0.1.tar.bz2
graphvizcairo             2.8          01 June 2014 http://www.graphviz.org/pub/graphviz/ARCHIVE/graphviz-cairo-2.8.tar.gz
greenfish                 1.0.8        30 April 2021 greenfish-1.0.8
grep                      3.11         13 May 2023  https://ftp.gnu.org/gnu/grep/grep-3.11.tar.xz
grilo                     0.3.16       27 May 2023  https://download.gnome.org/sources/grilo/0.3/grilo-0.3.16.tar.xz
griloplugins              0.3.16       05 April 2023 https://download.gnome.org/sources/grilo-plugins/0.3/grilo-plugins-0.3.16.tar.xz
grism                     0.9.0        16 February 2017 http://www.grism.org/grism-0.9.0.tar.gz
groff                     1.23.0       06 July 2023 https://ftp.gnu.org/gnu/groff/groff-1.23.0.tar.gz
gromacs                   2022.2       28 August 2022 https://ftp.gromacs.org/gromacs/gromacs-2022.2.tar.gz
groonga                   10.0.7       29 October 2020 https://packages.groonga.org/source/groonga/groonga-10.0.7.tar.gz
grub                      2.12         20 December 2023 https://ftp.gnu.org/gnu/grub/grub-2.12.tar.xz
gruff                     0.17.0       22 June 2022 https://rubygems.org/downloads/gruff-0.17.0.gem
gsasl                     2.0.1        17 July 2022 https://ftp.gnu.org/pub/gnu/gsasl/gsasl-2.0.1.tar.gz
gscan2pdf                 2.2.0        01 December 2018 https://sourceforge.net/projects/gscan2pdf/files/gscan2pdf/2.2.0/gscan2pdf-2.2.0.tar.xz
gscanbus                  0.8          04 November 2017 https://sourceforge.net/projects/gscanbus.berlios/files/gscanbus-0.8.tar.gz
gsettingsdesktopschemas   46.0         20 March 2024 https://download.gnome.org/sources/gsettings-desktop-schemas/46/gsettings-desktop-schemas-46.0.tar.xz
gsl                       2.7.1        01 December 2021 https://ftp.gnu.org/pub/gnu/gsl/gsl-2.7.1.tar.gz
gslapt                    0.5.4c       16 October 2017 http://software.jaos.org/source/gslapt/gslapt-0.5.4c.tar.gz
gsmartcontrol             0.8.7        11 April 2015 http://sourceforge.net/projects/gsmartcontrol/files/0.8.7/gsmartcontrol-0.8.7.tar.bz2
gsound                    1.0.3        19 August 2021 https://download.gnome.org/sources/gsound/1.0/gsound-1.0.3.tar.xz
gspell                    1.12.1       01 May 2023  https://download.gnome.org/sources/gspell/1.12/gspell-1.12.1.tar.xz
gss                       1.0.4        09 August 2022 https://ftp.gnu.org/pub/gnu/gss/gss-1.0.4.tar.gz
gssdp                     1.6.3        09 November 2023 https://download.gnome.org/sources/gssdp/1.6/gssdp-1.6.3.tar.xz
gstdebugger               0.90.0       09 October 2015 http://ftp.gnome.org/pub/GNOME/sources/gst-debugger/0.90/gst-debugger-0.90.0.tar.xz
gsteditingservices        1.17.1       10 August 2020 https://gstreamer.freedesktop.org/src/gst-editing-services/gst-editing-services-1.17.1.tar.xz
gstlibav                  1.18.0       09 September 2020 https://gstreamer.freedesktop.org/src/gst-libav/gst-libav-1.18.0.tar.xz
gstpluginsbad             1.24.1       01 April 2024 https://gstreamer.freedesktop.org/src/gst-plugins-bad/gst-plugins-bad-1.24.1.tar.xz
gstpluginsbase            1.24.2       10 April 2024 https://gstreamer.freedesktop.org/src/gst-plugins-base/gst-plugins-base-1.24.2.tar.xz
gstpluginsgood            1.24.2       10 April 2024 https://gstreamer.freedesktop.org/src/gst-plugins-good/gst-plugins-good-1.24.2.tar.xz
gstpluginsugly            1.22.0       27 January 2023 https://gstreamer.freedesktop.org/src/gst-plugins-ugly/gst-plugins-ugly-1.22.0.tar.xz
gstpython                 12.10.2022   20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/gst-python/0.10/gst-python-0.10.22.tar.xz
gstreamer                 1.24.2       10 April 2024 https://gstreamer.freedesktop.org/src/gstreamer/gstreamer-1.24.2.tar.xz
gstreamermm               1.10.0       21 October 2017 http://ftp.gnome.org/pub/gnome/sources/gstreamermm/1.10/gstreamermm-1.10.0.tar.xz
gstrtspserver             1.4.5        02 March 2015 http://gstreamer.freedesktop.org/src/gst-rtsp/gst-rtsp-server-1.4.5.tar.xz
gsview                    4.9          01 June 2014 http://mirror.cs.wisc.edu/pub/mirrors/ghost/ghostgum/gsview-4.9.tar.gz
gtef                      1.99.2       12 March 2017 http://ftp.gnome.org/pub/GNOME/sources/gtef/1.99/gtef-1.99.2.tar.xz
gthumb                    3.12.6       12 March 2024 https://download.gnome.org/sources/gthumb/3.12/gthumb-3.12.6.tar.xz
gtk                       4.14.2       03 April 2024 https://download.gnome.org/sources/gtk/4.14/gtk-4.14.2.tar.xz
gtk+                      3.24.41      30 January 2024 https://download.gnome.org/sources/gtk+/3.24/gtk+-3.24.41.tar.xz
gtkam                     0.2.0        01 April 2014 http://sourceforge.net/projects/gphoto/files/gtkam/0.2.0/gtkam-0.2.0.tar.gz
gtkchtheme                0.3.1        01 December 2012 http://plasmasturm.org/code/gtk-chtheme/gtk-chtheme-0.3.1.tar.bz2
gtkclearlooks             0.5          01 December 2012 http://ftp.gnome.org/pub/GNOME/teams/art.gnome.org/themes/gtk_engines/gtk-clearlooks-0.5.tar.bz2
gtkdatabox                0.8.0.0      01 December 2012 http://www.eudoxos.net/gtk/gtkdatabox/download/gtkdatabox-0.8.0.0.tar.gz
gtkdoc                    1.34.0       18 March 2024 https://download.gnome.org/sources/gtk-doc/1.34/gtk-doc-1.34.0.tar.xz
gtkengines                2.91.1       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/gtk-engines/2.91/gtk-engines-2.91.1.tar.bz2
gtkglarea                 2.1.0        01 April 2014 http://ftp.gnome.org/pub/gnome/sources/gtkglarea/2.1/gtkglarea-2.1.0.tar.xz
gtkglext                  1.2.0        01 November 2012 http://downloads.sourceforge.net/gtkglext/gtkglext-1.2.0.tar.gz
gtkhtml                   4.10.0       21 September 2015 http://ftp.gnome.org/pub/GNOME/sources/gtkhtml/4.10/gtkhtml-4.10.0.tar.xz
gtkinternetradiolocator   0.0.3        14 July 2018 http://ftp.gnome.org/pub/gnome/sources/gtk-internet-radio-locator/0.0/gtk-internet-radio-locator-0.0.3.tar.xz
gtkiptables               0.5.0        01 June 2014 http://gtk-iptables.sourceforge.net/
gtkmm                     4.14.0       23 March 2024 https://download.gnome.org/sources/gtkmm/4.14/gtkmm-4.14.0.tar.xz
gtkperl                   0.7010       21 August 2017 http://search.cpan.org/CPAN/authors/id/M/ML/MLEHMANN/Gtk-Perl-0.7010.tar.gz
gtkrecordmydesktop        0.3.8        29 September 2018 https://sourceforge.net/projects/recordmydesktop/files/gtk-recordMyDesktop/0.3.8/gtk-recordmydesktop-0.3.8.tar.gz
gtksharp                  2.12.45      21 August 2017 https://download.mono-project.com/sources/gtk-sharp212/gtk-sharp-2.12.45.tar.gz
gtksourceview             5.12.0       09 April 2024 https://download.gnome.org/sources/gtksourceview/5.12/gtksourceview-5.12.0.tar.xz
gtksourceview2            3.4.3        28 May 2020  https://rubygems.org/downloads/gtksourceview2-3.4.3.gem
gtksourceview3            3.5.1        27 May 2022  https://rubygems.org/downloads/gtksourceview3-3.5.1.gem
gtksourceviewmm           3.91.1       04 December 2018 http://ftp.gnome.org/pub/gnome/sources/gtksourceviewmm/3.91/gtksourceviewmm-3.91.1.tar.xz
gtkspell3                 3.0.10       03 January 2019 https://sourceforge.net/projects/gtkspell/files/3.0.10/gtkspell3-3.0.10.tar.xz
gtkvnc                    1.3.1        18 July 2022 https://download.gnome.org/sources/gtk-vnc/1.3/gtk-vnc-1.3.1.tar.xz
gtkwave                   3.3.98       02 January 2019 http://gtkwave.sourceforge.net/gtkwave-3.3.98.tar.gz
gtkxfceengine             3.2.0        30 August 2017 http://archive.xfce.org/src/xfce/gtk-xfce-engine/3.2/gtk-xfce-engine-3.2.0.tar.bz2
gtranslator               46.0         21 March 2024 https://download.gnome.org/sources/gtranslator/46/gtranslator-46.0.tar.xz
gucharmap                 15.1.3       23 March 2024 https://gitlab.gnome.org/GNOME/gucharmap/-/archive/15.1.3/gucharmap-15.1.3.tar.bz2
guessit                   3.1.0        23 September 2019 https://files.pythonhosted.org/packages/3e/4d/0f3c55ff4fbef55e6e1086e9f273cef4f70d8aa1b975f2a4d9821e0fdc34/guessit-3.1.0.tar.gz
guichan                   0.8.2        01 June 2014 http://guichan.googlecode.com/files/guichan-0.8.2.tar.gz
guile                     3.0.9        25 January 2023 https://ftp.gnu.org/pub/gnu/guile/guile-3.0.9.tar.xz
guilib                    1.2.1        01 June 2014 http://www.libsdl.org/projects/GUIlib/src/GUIlib-1.2.1.tar.gz
guiloader                 2.99.0       01 June 2014 http://nothing-personal.googlecode.com/files/guiloader-2.99.0.tar.xz
gujin                     2.8.7        08 March 2017 https://sourceforge.net/projects/gujin/files/gujin/2.8.7/gujin-2.8.7.tar.gz
gumboparser               14.08.2013   01 August 2013 gumboparser-14.08.2013.tar.xz
gupnp                     1.6.6        04 November 2023 https://download.gnome.org/sources/gupnp/1.6/gupnp-1.6.6.tar.xz
gupnpav                   0.14.1       06 June 2022 https://download.gnome.org/sources/gupnp-av/0.14/gupnp-av-0.14.1.tar.xz
gupnpdlna                 0.11.0       09 July 2021 https://download.gnome.org/sources/gupnp-dlna/0.11/gupnp-dlna-0.11.0.tar.xz
gupnpigd                  1.6.0        15 April 2023 https://download.gnome.org/sources/gupnp-igd/1.6/gupnp-igd-1.6.0.tar.xz
gupnptools                0.12.0       12 October 2022 https://download.gnome.org/sources/gupnp-tools/0.12/gupnp-tools-0.12.0.tar.xz
gutenprint                5.3.4        18 December 2021 https://downloads.sourceforge.net/gimp-print/gutenprint-5.3.4.tar.xz
guyum                     0.4.1        01 June 2014 http://sourceforge.net/projects/guyum/files/guyum/guyum-0.4/guyum-0.4.1.tar.gz
gv                        3.7.4        21 January 2019 http://ftp.gnu.org/gnu/gv/gv-3.7.4.tar.gz
gvfs                      1.54.0       15 March 2024 https://download.gnome.org/sources/gvfs/1.54/gvfs-1.54.0.tar.xz
gvpe                      3.1          26 October 2018 https://ftp.gnu.org/pub/gnu/gvpe/gvpe-3.1.tar.gz
gwenhywfar                5.4.0        28 October 2018 https://github.com/aqbanking/gwenhywfar/archive/5.4.0.tar.gz
gwenview                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/gwenview-24.02.2.tar.xz
gwyddion                  2.52         19 December 2018 https://sourceforge.net/projects/gwyddion/files/gwyddion/2.52/gwyddion-2.52.tar.xz
gxine                     0.5.910      13 January 2018 https://sourceforge.net/projects/xine/files/gxine/0.5.910/gxine-0.5.910.tar.xz
gxml                      0.20.0       11 August 2020 http://ftp.gnome.org/pub/gnome/sources/gxml/0.20/gxml-0.20.0.tar.xz
gzip                      1.13         20 August 2023 https://ftp.gnu.org/gnu/gzip/gzip-1.13.tar.gz
hal                       0.5.14       01 June 2014 https://hal.freedesktop.org/releases/hal-0.5.14.tar.bz2
haml                      5.2.2        05 April 2022 https://rubygems.org/downloads/haml-5.2.2.gem
hanami                    1.3.5        27 May 2022  https://rubygems.org/downloads/hanami-1.3.5.gem
hanamiassets              1.3.5        15 April 2021 https://rubygems.org/downloads/hanami-assets-1.3.5.gem
harfbuzz                  8.4.0        29 March 2024 https://github.com/harfbuzz/harfbuzz/releases/download/8.4.0/harfbuzz-8.4.0.tar.xz
hashie                    5.0.0        27 May 2022  https://rubygems.org/downloads/hashie-5.0.0.gem
hatchling                 1.24.0       16 April 2024 https://files.pythonhosted.org/packages/af/53/044f4b7d42da9aff92c9efbd237d4bc69604ac7861239d0f83c28200f4e2/hatchling-1.24.0.tar.gz
haveged                   1.9.18       12 April 2022 https://github.com/jirka-h/haveged/archive/v1.9.18/haveged-1.9.18.tar.gz
hawknl                    1.70         01 June 2014 http://hawksoft.com/download/files/HawkNL17b1src.zip
hd2u                      1.0.4        11 April 2023 https://hany.sk/~hany/_data/hd2u/hd2u-1.0.4.tgz
hdf5                      1.10.4       30 January 2019 https://support.hdfgroup.org/ftp/HDF5/releases/hdf5-1.10/hdf5-1.10.4/src/hdf5-1.10.4.tar.gz
hdparm                    9.65         08 September 2022 https://downloads.sourceforge.net/hdparm/hdparm-9.65.tar.gz
heckle                    1.4.3        30 November 2017 https://rubygems.org/downloads/heckle-1.4.3.gem
heimdal                   1.6rc2       22 September 2015 http://www.h5l.org/dist/src/heimdal-1.6rc2.tar.gz
hello                     2.10         09 July 2018 http://ftp.gnu.org/gnu/hello/hello-2.10.tar.gz
help2man                  1.49.3       16 December 2022 https://ftp.gnu.org/pub/gnu/help2man/help2man-1.49.3.tar.xz
herbstluftwm              0.8.3        12 August 2020 https://www.herbstluftwm.org/tarballs/herbstluftwm-0.8.3.tar.gz
hexahop                   1.1.0        26 February 2017 https://sourceforge.net/projects/hexahop/files/1.1.0/hex-a-hop-1.1.0.tar.gz
hexapdf                   0.32.2       17 May 2023  https://rubygems.org/downloads/hexapdf-0.32.2.gem
hexchat                   2.16.2       12 March 2024 https://github.com/hexchat/hexchat/releases/download/v2.16.2/hexchat-2.16.2.tar.xz
hexedit                   0.9.7        01 June 2014 http://www.rogoyski.com/adam/programs/hexedit/hexedit-0.9.7.tar.gz
hicoloricontheme          0.17         15 September 2017 https://icon-theme.freedesktop.org/releases/hicolor-icon-theme-0.17.tar.xz
hiera                     3.9.0        27 May 2022  https://rubygems.org/downloads/hiera-3.9.0.gem
highlight                 4.5          19 March 2023 http://www.andre-simon.de/zip/highlight-4.5.tar.bz2
highline                  2.0.3        28 May 2020  https://rubygems.org/downloads/highline-2.0.3.gem
highmoon                  1.2.4        01 June 2014 http://highmoon.gerdsmeier.net/highmoon-1.2.4.tar.gz
highway                   0.12.2       06 July 2021 https://github.com/google/highway/archive/refs/tags/0.12.2.tar.gz
hiki                      =4578        01 February 2013 http://rubyforge.org/frs/?group_id=1444&release_id=4578
histogram                 0.2.4.1      02 February 2021 https://rubygems.org/downloads/histogram-0.2.4.1.gem
hitori                    44.0         03 March 2023 https://download.gnome.org/sources/hitori/44/hitori-44.0.tar.xz
hmmer                     3.4          19 October 2023 http://eddylab.org/software/hmmer/hmmer-3.4.tar.gz
hmount                    0.2.2        01 January 2013 https://sourceforge.net/project/showfiles.php?group_id=186602&package_id=217560
hoe                       3.24.0       22 June 2022 https://rubygems.org/downloads/hoe-3.24.0.gem
hornetseyeffmpeg          1.2.5        10 October 2017 https://rubygems.org/downloads/hornetseye-ffmpeg-1.2.5.gem
hotbabe                   1.1.1        01 June 2014 http://dindinx.net/hotbabe/hotbabe-1.1.1.tar.xz
hplip                     3.23.12      24 February 2024 https://sourceforge.net/projects/hplip/files/hplip/3.23.12/hplip-3.23.12.tar.gz
hpricot                   0.8.6        17 October 2018 https://rubygems.org/downloads/hpricot-0.8.6.gem
hsakmt                    1.0.0        26 October 2015 http://xorg.freedesktop.org/releases/individual/lib/hsakmt-1.0.0.tar.bz2
hspell                    1.4          31 December 2018 http://hspell.ivrix.org.il/hspell-1.4.tar.gz
html5lib                  1.1          10 September 2022 https://files.pythonhosted.org/packages/ac/b6/b55c3f49042f1df3dcd422b7f224f939892ee94f22abcf503a9b7339eaf2/html5lib-1.1.tar.gz
htmlentities              4.3.4        15 May 2020  https://rubygems.org/downloads/htmlentities-4.3.4.gem
htmlparser                3.76         13 March 2021 https://www.cpan.org/authors/id/O/OA/OALDERS/HTML-Parser-3.76.tar.gz
htop                      3.3.0        09 March 2024 https://github.com/htop-dev/htop/releases/download/3.3.0/htop-3.3.0.tar.xz
htslib                    1.15.1       24 April 2022 https://github.com/samtools/htslib/releases/download/1.15.1/htslib-1.15.1.tar.bz2
httparty                  0.20.0       05 March 2022 https://rubygems.org/downloads/httparty-0.20.0.gem
httpclient                2.8.3        13 November 2017 https://rubygems.org/downloads/httpclient-2.8.3.gem
httpcookie                1.0.5        27 May 2022  https://rubygems.org/downloads/http-cookie-1.0.5.gem
httpd                     2.4.59       04 April 2024 https://archive.apache.org/dist/httpd/httpd-2.4.59.tar.bz2
hugin                     2019.0.0     28 July 2019 https://sourceforge.net/projects/hugin/files/hugin/hugin-2019.0/hugin-2019.0.0.tar.bz2
humphrey                  24.06.2014   01 June 2014 http://retrospec.sgn.net/users/ignacio/downloads/humphrey-24.06.2014
hunspell                  1.7.2        13 March 2024 https://github.com/hunspell/hunspell/releases/download/v1.7.2/hunspell-1.7.2.tar.gz
hwd                       4.8.1        01 June 2014 http://user-contributions.org/projects/hwd/src/hwd-4.8.1.tar.gz
hwloc                     1.11.7       28 December 2018 https://www.open-mpi.org/software/hwloc/v1.11/downloads/hwloc-1.11.7.tar.gz
hydrogen                  0.9.5.1      01 November 2015 http://sourceforge.net/projects/hydrogen/files/Hydrogen/0.9.5%20Sources/hydrogen-0.9.5.1.tar.gz
hyperbole                 7.0.9        17 February 2020 http://ftp.gnu.org/pub/gnu/hyperbole/hyperbole-7.0.9.tar.gz
hypermammut               0.0.1        01 June 2014 http://switch.dl.sourceforge.net/sourceforge/hypermammut/hypermammut-0.0.1.tar.bz2
hyphen                    2.8.8        11 June 2015 https://sourceforge.net/projects/hunspell/files/Hyphen/2.8/hyphen-2.8.8.tar.gz
hypothesis                4.7.7        21 February 2019 https://files.pythonhosted.org/packages/02/52/0b683679bc27200d3fbc51beebf39075b0b28e139e56858b0c7be1b27cd5/hypothesis-4.7.7.tar.gz
i18n                      1.10.0       27 May 2022  https://rubygems.org/downloads/i18n-1.10.0.gem
i3                        4.18         17 February 2020 https://i3wm.org/downloads/i3-4.18.tar.bz2
iagno                     3.37.91      28 August 2020 http://ftp.gnome.org/pub/gnome/sources/iagno/3.37/iagno-3.37.91.tar.xz
ianaetc                   20240305     16 March 2024 https://github.com/Mic92/iana-etc/releases/download/20240305/iana-etc-20240305.tar.gz
iat                       0.1.7        12 April 2019 https://sourceforge.net/projects/iat.berlios/files/iat-0.1.7.tar.bz2
ibus                      1.5.30-rc2   01 April 2024 https://github.com/ibus/ibus/releases/download/1.5.30-rc2/ibus-1.5.30-rc2.tar.gz
ice                       3.4.2        01 June 2014 http://www.zeroc.com/download/Ice/3.4/Ice-3.4.2.tar.gz
iceauth                   1.0.10       12 March 2024 https://www.x.org/releases/individual/app/iceauth-1.0.10.tar.xz
icebreaker                1.9.8        01 June 2014 http://mattdm.org/icebreaker/1.9.x/icebreaker-1.9.8.tgz
icecast                   2.4.4        02 November 2018 https://downloads.xiph.org/releases/icecast/icecast-2.4.4.tar.gz
icecc                     1.3          14 September 2019 https://github.com/icecc/icecream/releases/download/1.3/icecc-1.3.tar.xz
icedtea                   2.4.7        01 May 2014  http://icedtea.classpath.org/download/source/icedtea-2.4.7.tar.xz
icewm                     3.4.7        26 March 2024 https://github.com/ice-wm/icewm/releases/download/3.4.7/icewm-3.4.7.tar.lz
icinga                    1.3.1        01 June 2014 https://www.icinga.org/
ico                       1.0.6        01 September 2022 https://www.x.org/releases/individual/app/ico-1.0.6.tar.xz
iconnamingutils           0.8.90       01 June 2014 http://tango.freedesktop.org/releases/icon-naming-utils-0.8.90.tar.bz2
icoutils                  0.31.2       08 March 2017 http://savannah.nongnu.org/download/icoutils/icoutils-0.31.2.tar.bz2
icu4c                     74.2         22 February 2024 https://github.com/unicode-org/icu/releases/download/release-74-2/icu4c-74_2.tgz
id3ed                     1.10.4       01 June 2014 http://www.ibiblio.org/pub/Linux/apps/sound/editors/id3ed-1.10.4.tar.gz
id3lib                    3.8.3        01 May 2014  https://sourceforge.net/projects/id3lib/files/id3lib/3.8.3/id3lib-3.8.3.tar.gz
idesk                     0.7.5        04 September 2015 https://nchc.dl.sourceforge.net/sourceforge/idesk/idesk-0.7.5.tar.bz2
idjc                      0.7.2        01 June 2014 http://worldforum.pardus-linux.nl/index.php?topic=1501.5;wap2
iftop                     0.17         01 June 2014 http://www.ex-parrot.com/pdw/iftop/download/iftop-0.17.tar.gz
igtgputools               1.26         23 April 2021 https://www.x.org/releases/individual/app/igt-gpu-tools-1.26.tar.xz
ijs                       0.35         01 January 2013 http://www.openprinting.org/download/ijs/download/ijs-0.35.tar.bz2
ilmbase                   2.2.0        09 July 2015 https://download.savannah.nongnu.org/releases/openexr/ilmbase-2.2.0.tar.gz
imageexiftool             12.60        08 April 2023 https://exiftool.org/Image-ExifTool-12.60.tar.gz
imagemagick               7.1.1.30     09 April 2024 https://imagemagick.org/archive/ImageMagick-7.1.1-30.tar.xz
imageworsener             1.3.0        02 December 2015 http://entropymine.com/imageworsener/imageworsener-1.3.0.tar.gz
imaging                   1.1.6        01 June 2014 http://effbot.org/downloads/Imaging-1.1.6.tar.gz
imake                     1.0.10       12 February 2024 https://www.x.org/releases/individual/util/imake-1.0.10.tar.xz
img2pdf                   0.5.1        16 December 2023 https://files.pythonhosted.org/packages/36/92/6ac4d61951ba507b499f674c90dfa7b48fa776b56f6f068507f8751c03f1/img2pdf-0.5.1.tar.gz
imlib                     1.9.15       01 September 2013 http://ftp.gnome.org/pub/GNOME/sources/imlib/1.9/imlib-1.9.15.tar.bz2
imlib2                    1.11.0       18 March 2023 https://downloads.sourceforge.net/enlightenment/imlib2-1.11.0.tar.xz
inch                      0.8.0        01 May 2018  https://rubygems.org/downloads/inch-0.8.0.gem
incidenceeditor           24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/incidenceeditor-24.02.2.tar.xz
incron                    0.5.10       20 September 2018 http://inotify.aiken.cz/download/incron/incron-0.5.10.tar.bz2
indent                    2.2.12       08 September 2018 http://mirror.rit.edu/gnu/indent/indent-2.2.12.tar.xz
inetutils                 2.4          26 October 2022 https://ftp.gnu.org/pub/gnu/inetutils/inetutils-2.4.tar.xz
inih                      r53          09 June 2021 https://github.com/benhoyt/inih/archive/r53/inih-r53.tar.gz
initdtools                0.1.3        24 July 2017 http://people.freedesktop.org/~dbn/initd-tools/releases/initd-tools-0.1.3.tar.gz
initng                    0.6.10.2     01 June 2014 http://download.initng.org/initng/v0.6/initng-0.6.10.2.tar.bz2
inkscape                  1.3.1        19 November 2023 https://inkscape.org/gallery/item/44467/inkscape-1.3.1.tar.xz
inotifytools              3.14         01 June 2014 http://github.com/downloads/rvoicilas/inotify-tools/inotify-tools-3.14.tar.gz
inputproto                2.3.2        31 July 2016 https://www.x.org/releases/individual/proto/inputproto-2.3.2.tar.bz2
inspec                    5.17.4       27 May 2022  https://rubygems.org/downloads/inspec-5.17.4.gem
instiki                   0.10.2       01 January 2013 https://rubygems.org/downloads/instiki-0.10.2.gem
intelgputools             1.21         23 January 2018 https://www.x.org/releases/individual/app/intel-gpu-tools-1.21.tar.xz
intelvaapidriver          2.4.1        30 June 2020 https://github.com/intel/intel-vaapi-driver/releases/download/2.4.1/intel-vaapi-driver-2.4.1.tar.bz2
intltool                  0.51.0       04 April 2015 https://launchpad.net/intltool/trunk/0.51.0/+download/intltool-0.51.0.tar.gz
iostring                  1.08         16 December 2018 https://cpan.metacpan.org/authors/id/G/GA/GAAS/IO-String-1.08.tar.gz
iotop                     0.6          01 June 2014 http://guichaz.free.fr/iotop/files/iotop-0.6.tar.gz
iowa                      0.99.2.14    01 July 2013 https://github.com/wyhaines/iowa
iproute2                  6.7.0        21 January 2024 https://mirrors.edge.kernel.org/pub/linux/utils/net/iproute2/iproute2-6.7.0.tar.xz
ipset                     7.7          31 October 2020 http://ipset.netfilter.org/ipset-7.7.tar.bz2
iptables                  1.8.8        14 May 2022  http://www.netfilter.org/projects/iptables/files/iptables-1.8.8.tar.bz2
iptraf                    3.0.0        01 July 2011 ftp://iptraf.seul.org/pub/iptraf/iptraf-3.0.0.tar.gz
ipython                   7.22.0       29 April 2021 https://files.pythonhosted.org/packages/bd/59/5e4caa1b226d79508c8601888bd94af1f12ff464613daad90193c0e5fc88/ipython-7.22.0.tar.gz
ire                       0.93         01 January 2013 http://ire.sourceforge.net/
irrlicht                  1.8.3        18 March 2016 http://downloads.sourceforge.net/irrlicht/irrlicht-1.8.3.zip
irssi                     1.4.4        03 April 2023 https://github.com/irssi-import/irssi/releases/download/1.4.4/irssi-1.4.4.tar.xz
isbf                      0.1          01 May 2014  http://freshmeat.net/redir/isbf/66799/url_tgz/isbf-0.1.tar.gz
isl                       0.26         16 May 2023  https://libisl.sourceforge.io/isl-0.26.tar.xz
isoimagewriter            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/isoimagewriter-24.02.2.tar.xz
itinerary                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/itinerary-24.02.2.tar.xz
itstool                   2.0.7        28 September 2021 https://files.itstool.org/itstool/itstool-2.0.7.tar.bz2
ivtv                      1.0.2        01 June 2014 http://dl.ivtvdriver.org/ivtv/archive/
iw                        5.19         29 May 2022  https://mirrors.edge.kernel.org/pub/software/network/iw/iw-5.19.tar.xz
jack2                     1.9.21       27 October 2022 https://github.com/jackaudio/jack2/archive/refs/tags/v1.9.21.tar.gz
jackaudioconnectionkit    0.125.0      15 November 2017 https://jackaudio.org/downloads/jack-audio-connection-kit-0.125.0.tar.gz
jailkit                   2.17         25 April 2015 https://olivier.sessink.nl/jailkit/jailkit-2.17.tar.bz2
jam                       1.05         01 June 2014 http://www.disi.unige.it/person/LagorioG/jam/jam105.zip
jansson                   2.14         29 October 2021 https://github.com/akheron/jansson/releases/download/v2.14/jansson-2.14.tar.bz2
jasper                    4.2.3        31 March 2024 https://github.com/jasper-software/jasper/releases/download/version-4.2.3/jasper-4.2.3.tar.gz
jawavedit                 1.16beta     01 June 2014 http://www.bome.com/JaWavedit/JaWavedit.tar.gz
jbig2dec                  0.20         18 March 2024 https://github.com/ArtifexSoftware/jbig2dec/releases/download/0.20/jbig2dec-0.20.tar.gz
jbuilder                  2.11.5       27 May 2022  https://rubygems.org/downloads/jbuilder-2.11.5.gem
jed                       0.99-19      11 March 2017 https://www.jedsoft.org/releases/jed/jed-0.99-19.tar.bz2
jekyll                    4.3.2        19 March 2023 https://rubygems.org/downloads/jekyll-4.3.2.gem
jemalloc                  5.3.0        15 September 2022 https://github.com/jemalloc/jemalloc/releases/download/5.3.0/jemalloc-5.3.0.tar.bz2
jfsutils                  1.1.15       11 June 2015 http://jfs.sourceforge.net/project/pub/jfsutils-1.1.15.tar.gz
jhbuild                   3.36.0       06 March 2020 http://ftp.gnome.org/pub/gnome/sources/jhbuild/3.36/jhbuild-3.36.0.tar.xz
jigdo                     0.8.0        08 April 2021 https://www.einval.com/~steve/software/jigdo/download/jigdo-0.8.0.tar.xz
jinja2                    3.1.3        03 February 2024 https://files.pythonhosted.org/packages/b2/5e/3a21abf3cd467d7876045335e681d276ac32492febe6d98ad89562d1a7e1/Jinja2-3.1.3.tar.gz
joe                       4.6          13 January 2018 https://downloads.sourceforge.net/joe-editor/joe-4.6.tar.gz
john                      1.8.0        18 March 2017 http://www.openwall.com/john/j/john-1.8.0.tar.xz
jokosher                  0.11.5       05 October 2019 https://launchpad.net/jokosher/trunk/0.11.5/+download/jokosher-0.11.5.tar.gz
jp2a                      1.0.6        01 June 2014 https://sourceforge.net/projects/jp2a/files/jp2a/1.0.6/jp2a-1.0.6.tar.bz2
jpeg                      9            09 December 2018 http://www.ijg.org/files/jpegsr-9c.zip
jpegoptim                 1.5.0        29 September 2022 https://github.com/tjko/jpegoptim/archive/refs/tags/v1.5.0.tar.gz
jquery                    3.6.0        24 May 2021  https://code.jquery.com/jquery-3.6.0.js
jqueryui                  1.12.1       16 July 2020 http://code.jquery.com/jquery-ui-1.12.1.js
jre                       1.8.0_45     01 May 2014  http://www.java.com/en/download/manual.jsp?locale=en
0                         0            04 July 2023 https://repo1.maven.org/maven2/org/jruby/jruby-dist/9.4.3.0/jruby-dist-9.4.3.0-bin.tar.gz
json                      2.6.2        27 May 2022  https://rubygems.org/downloads/json-2.6.2.gem
jsonc                     0.16         15 April 2022 https://s3.amazonaws.com/json-c_releases/releases/json-c-0.16.tar.gz
jsoncpp                   19.09.2017   19 September 2017 https://github.com/open-source-parsers/jsoncpp/archive/master.zip
jsonglib                  1.8.0        20 March 2024 https://download.gnome.org/sources/json-glib/1.8/json-glib-1.8.0.tar.xz
jsonpp                    4.04         09 November 2019 https://cpan.metacpan.org/authors/id/I/IS/ISHIGAKI/JSON-PP-4.04.tar.gz
jsonpure                  2.6.2        27 May 2022  https://rubygems.org/downloads/json_pure-2.6.2.gem
jsonrpcglib               3.41.0       07 January 2022 https://download.gnome.org/sources/jsonrpc-glib/3.41/jsonrpc-glib-3.41.0.tar.xz
jthread                   1.3.1        01 June 2014 http://research.edm.uhasselt.be/jori/jthread/jthread-1.3.1.tar.bz2
judy                      1.0.5        01 June 2014 http://sourceforge.net/projects/judy/files/judy/Judy-1.0.5/Judy-1.0.5.tar.gz
juk                       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/juk-24.02.2.tar.xz
julia                     1.9.2        15 August 2023 https://github.com/JuliaLang/julia/releases/download/v1.9.2/julia-1.9.2.tar.gz
jumpstart                 0.3          01 June 2014 http://bitwagon.com/jumpstart/jumpstart-0.3.tgz
jwm                       2.2.2        24 May 2015  http://joewing.net/projects/jwm/releases/jwm-2.2.2.tar.xz
k3b                       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/k3b-24.02.2.tar.xz
kaccountsintegration      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kaccounts-integration-24.02.2.tar.xz
kaccountsproviders        24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kaccounts-providers-24.02.2.tar.xz
kactivities               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kactivities-5.115.0.tar.xz
kactivitiesstats          5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kactivities-stats-5.115.0.tar.xz
kactivitymanagerd         6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kactivitymanagerd-6.0.2.tar.xz
kaddressbook              24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kaddressbook-24.02.2.tar.xz
kaffeine                  1.2.2        22 August 2022 http://downloads.sourceforge.net/kaffeine/kaffeine-1.2.2.tar.gz
kajaanikombat             0.7          01 January 2013 http://kombat.kajaani.net/dl/kajaani-kombat-0.7.tar.gz
kajongg                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kajongg-24.02.2.tar.xz
kalarm                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kalarm-24.02.2.tar.xz
kalarmcal                 21.12.3      03 March 2022 https://download.kde.org/stable/release-service/21.12.3/src/kalarmcal-21.12.3.tar.xz
kalendar                  23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/kalendar-23.04.3.tar.xz
kalgebra                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kalgebra-24.02.2.tar.xz
kalk                      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kalk-24.02.2.tar.xz
kalzium                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kalzium-24.02.2.tar.xz
kamera                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kamera-24.02.2.tar.xz
kamikaze                  0.2.2        01 June 2014 http://kamikaze.coolprojects.org/download/kamikaze-0.2.2.tar.gz
kamoso                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kamoso-24.02.2.tar.xz
kanagram                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kanagram-24.02.2.tar.xz
kapidox                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kapidox-5.115.0.tar.xz
kapman                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kapman-24.02.2.tar.xz
kapptemplate              24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kapptemplate-24.02.2.tar.xz
karchive                  5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/karchive-5.115.0.tar.xz
karmen                    0.11         01 June 2014 karmen.sourceforge.net
kasablanca                0.4.0.2      01 January 2013 http://download.berlios.de/kasablanca/kasablanca-0.4.0.2.tar.gz
kasts                     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kasts-24.02.2.tar.xz
katchtv                   katchtv      01 June 2014 http://www.digitalunleashed.com/downloads/katchtv/katchtv_latest_release.tar.bz2
kate                      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kate-24.02.2.tar.xz
katomic                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/katomic-24.02.2.tar.xz
kauth                     5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kauth-5.115.0.tar.xz
kawa                      3.1.1        17 January 2020 http://ftp.gnu.org/pub/gnu/kawa/kawa-3.1.1.tar.gz
kbackup                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kbackup-24.02.2.tar.xz
kbd                       2.6.4        21 January 2024 https://mirrors.edge.kernel.org/pub/linux/utils/kbd/kbd-2.6.4.tar.xz
kbfx                      1081006      01 June 2014 https://www.linux-apps.com/p/1081006/
kblackbox                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kblackbox-24.02.2.tar.xz
kblocks                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kblocks-24.02.2.tar.xz
kblog                     20.04.3      13 August 2020 https://download.kde.org/stable/release-service/20.04.3/src/kblog-20.04.3.tar.xz
kblogger                  1.0-alpha2   01 June 2014 http://kblogger.pwsp.net/files/kblogger-1.0-alpha2.tar.bz2
kbookmarks                5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kbookmarks-5.115.0.tar.xz
kbounce                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kbounce-24.02.2.tar.xz
kbproto                   1.0.7        04 May 2015  http://xorg.freedesktop.org/releases/individual/proto/kbproto-1.0.7.tar.bz2
kbreakout                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kbreakout-24.02.2.tar.xz
kbruch                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kbruch-24.02.2.tar.xz
kcachegrind               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kcachegrind-24.02.2.tar.xz
kcalc                     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kcalc-24.02.2.tar.xz
kcalcore                  19.08.3      01 December 2019 https://download.kde.org/stable/applications/19.08.3/src/kcalcore-19.08.3.tar.xz
kcalendarcore             5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcalendarcore-5.115.0.tar.xz
kcalutils                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kcalutils-24.02.2.tar.xz
kcharselect               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kcharselect-24.02.2.tar.xz
kchmviewer                7.7          16 September 2017 https://sourceforge.net/projects/kchmviewer/files/kchmviewer/7.7/kchmviewer-7.7.tar.gz
kclock                    24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kclock-24.02.2.tar.xz
kcmutils                  5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcmutils-5.115.0.tar.xz
kcodecs                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcodecs-5.115.0.tar.xz
kcolorchooser             24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kcolorchooser-24.02.2.tar.xz
kcompletion               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcompletion-5.115.0.tar.xz
kconfig                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kconfig-5.115.0.tar.xz
kconfigwidgets            5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kconfigwidgets-5.115.0.tar.xz
kcontacts                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcontacts-5.115.0.tar.xz
kcoreaddons               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcoreaddons-5.115.0.tar.xz
kcrash                    5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kcrash-5.115.0.tar.xz
kcron                     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kcron-24.02.2.tar.xz
kdav                      5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kdav-5.115.0.tar.xz
kdbg                      2.1.0        01 June 2014 http://prdownloads.sourceforge.net/kdbg/kdbg-2.1.0.tar.gz
kdbusaddons               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kdbusaddons-5.115.0.tar.xz
kdebaseruntime            4.3.90       08 March 2015 http://ftp.gwdg.de/pub/x11/kde/stable/4.0.2/src/kdebase-runtime-4.3.90.tar.xz
kdebugsettings            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdebugsettings-24.02.2.tar.xz
kdeclarative              5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kdeclarative-5.115.0.tar.xz
kdeclitools               6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kde-cli-tools-6.0.2.tar.xz
kdeconnectkde             24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdeconnect-kde-24.02.2.tar.xz
kdecoration               6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kdecoration-6.0.2.tar.xz
kded                      5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kded-5.115.0.tar.xz
kdedevscripts             24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kde-dev-scripts-24.02.2.tar.xz
kdedevutils               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kde-dev-utils-24.02.2.tar.xz
kdeedudata                24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdeedu-data-24.02.2.tar.xz
kdegraphicsmobipocket     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdegraphics-mobipocket-24.02.2.tar.xz
kdegraphicsstrigianalyzer 4.12.97      01 April 2014 ftp://gd.tuwien.ac.at/kde/unstable/4.12.97/src/kdegraphics-strigi-analyzer-4.12.97.tar.xz
kdegraphicsthumbnailers   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdegraphics-thumbnailers-24.02.2.tar.xz
kdegtkconfig              6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kde-gtk-config-6.0.2.tar.xz
kdeinotifysurvey          24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kde-inotify-survey-24.02.2.tar.xz
kdelibs4support           5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kdelibs4support-5.115.0.tar.xz
kdenetworkfilesharing     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdenetwork-filesharing-24.02.2.tar.xz
kdenlive                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdenlive-24.02.2.tar.xz
kdepimaddons              24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdepim-addons-24.02.2.tar.xz
kdepimappslibs            20.08.3      05 November 2020 https://download.kde.org/stable/release-service/20.08.3/src/kdepim-apps-libs-20.08.3.tar.xz
kdepimruntime             24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdepim-runtime-24.02.2.tar.xz
kdeplasmaaddons           6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kdeplasma-addons-6.0.2.tar.xz
kdesdkkio                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdesdk-kio-24.02.2.tar.xz
kdesdkkioslaves           22.04.3      07 July 2022 https://download.kde.org/stable/release-service/22.04.3/src/kdesdk-kioslaves-22.04.3.tar.xz
kdesdkthumbnailers        24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdesdk-thumbnailers-24.02.2.tar.xz
kdesignerplugin           5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kdesignerplugin-5.115.0.tar.xz
kdesu                     5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kdesu-5.115.0.tar.xz
kdesvn                    0.14.6       01 June 2014 http://www.alwins-world.de/programs/download/kdesvn/0.14.x/kdesvn-0.14.6.tar.bz2
kdevelop                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdevelop-24.02.2.tar.xz
kdevphp                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdev-php-24.02.2.tar.xz
kdevpython                24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdev-python-24.02.2.tar.xz
kdewebkit                 5.99.0       10 October 2022 https://download.kde.org/stable/frameworks/5.99/portingAids/kdewebkit-5.99.0.tar.xz
kdf                       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdf-24.02.2.tar.xz
kdiagram                  2.7.0        17 June 2020 https://github.com/KDE/kdiagram/archive/v2.7.0.tar.gz
kdialog                   24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdialog-24.02.2.tar.xz
kdiamond                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kdiamond-24.02.2.tar.xz
kdnssd                    5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kdnssd-5.115.0.tar.xz
kdoctools                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kdoctools-5.115.0.tar.xz
kdsoap                    2.1.1        18 September 2022 https://github.com/KDAB/KDSoap/releases/download/kdsoap-2.1.1/kdsoap-2.1.1.tar.gz
keditbookmarks            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/keditbookmarks-24.02.2.tar.xz
kemoticons                5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kemoticons-5.115.0.tar.xz
kexectools                2.0.18       31 October 2018 https://mirrors.edge.kernel.org/pub/linux/utils/kernel/kexec/kexec-tools-2.0.18.tar.xz
keybinder                 0.3.2        27 May 2020  https://github.com/kupferlauncher/keybinder/releases/download/keybinder-3.0-v0.3.2/keybinder-3.0-0.3.2.tar.gz
keysmith                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/keysmith-24.02.2.tar.xz
keytouch                  2.4.0beta    01 June 2014 http://keytouch.sourceforge.net/keytouch-2.4.0beta.tar.xz
keyutils                  1.6.1        30 November 2019 http://people.redhat.com/~dhowells/keyutils/keyutils-1.6.1.tar.bz2
kfilemetadata             5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kfilemetadata-5.115.0.tar.xz
kfind                     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kfind-24.02.2.tar.xz
kflickr                   20140907     24 April 2016 http://sourceforge.net/projects/kflickr/files/kflickr/20140907/kflickr-20140907.tar.bz2
kfloppy                   23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/kfloppy-23.04.3.tar.xz
kfourinline               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kfourinline-24.02.2.tar.xz
kgamma                    6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kgamma-6.0.2.tar.xz
kgeography                24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kgeography-24.02.2.tar.xz
kget                      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kget-24.02.2.tar.xz
kglobalaccel              5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kglobalaccel-5.115.0.tar.xz
kglobalacceld             6.0.2        17 March 2024 https://download.kde.org/stable/plasma/6.0.2/kglobalacceld-6.0.2.tar.xz
kgoldrunner               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kgoldrunner-24.02.2.tar.xz
kgpg                      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kgpg-24.02.2.tar.xz
kgraphviewer              1.99.1       01 June 2014 http://download.gna.org/kgraphviewer/kgraphviewer-1.99.1.tar.bz2
kguiaddons                5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kguiaddons-5.115.0.tar.xz
khangman                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/khangman-24.02.2.tar.xz
khard                     0.13.0       24 December 2018 https://files.pythonhosted.org/packages/75/17/5b97ce7dd15e835e801f513dd80fb4fee8c6f45f5c5be7c3a2b8b839121a/khard-0.13.0.tar.gz
khealthcertificate        24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/khealthcertificate-24.02.2.tar.xz
khelpcenter               24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/khelpcenter-24.02.2.tar.xz
kholidays                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kholidays-5.115.0.tar.xz
khotkeys                  5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/khotkeys-5.27.9.tar.xz
khtml                     5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/khtml-5.115.0.tar.xz
ki18n                     5.115.1      19 February 2024 https://download.kde.org/stable/frameworks/5.115/ki18n-5.115.1.tar.xz
kiconthemes               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kiconthemes-5.115.0.tar.xz
kid                       0.9.6        17 December 2018 https://files.pythonhosted.org/packages/85/59/5256812b4b90cf379be2947142aa384f0b2f739643933ffab66914c79332/kid-0.9.6.tar.gz
kid3                      3.9.5        25 February 2024 https://prdownloads.sourceforge.net/kid3/kid3-3.9.5.tar.gz
kidentitymanagement       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kidentitymanagement-24.02.2.tar.xz
kidletime                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kidletime-5.115.0.tar.xz
kig                       24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kig-24.02.2.tar.xz
kigo                      24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kigo-24.02.2.tar.xz
kildclient                2.7.0        01 June 2014 http://heanet.dl.sourceforge.net/sourceforge/kildclient/kildclient-2.7.0.tar.gz
kile                      2.9.93       26 July 2022 https://sourceforge.net/projects/kile/files/unstable/kile-3.0b3/kile-2.9.93.tar.bz2
killbots                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/killbots-24.02.2.tar.xz
kimageformats             5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kimageformats-5.115.0.tar.xz
kimagemapeditor           24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kimagemapeditor-24.02.2.tar.xz
kimap                     24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kimap-24.02.2.tar.xz
kimurai                   1.4.0        18 February 2019 https://rubygems.org/downloads/kimurai-1.4.0.gem
kimwitu++                 2.3.11       26 September 2017 https://www2.informatik.hu-berlin.de/sam/kimwitu++/kimwitu++-2.3.11.tar.gz
kinfocenter               5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kinfocenter-5.27.9.tar.xz
kinit                     5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kinit-5.115.0.tar.xz
kio                       5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kio-5.115.0.tar.xz
kioadmin                  24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kio-admin-24.02.2.tar.xz
kioextras                 24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kio-extras-24.02.2.tar.xz
kiogdrive                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kio-gdrive-23.08.5.tar.xz
kiozeroconf               23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kio-zeroconf-23.08.5.tar.xz
kipiplugins               23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kipi-plugins-23.08.5.tar.xz
kirigami2                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kirigami2-5.115.0.tar.xz
kirigamigallery           23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kirigami-gallery-23.08.5.tar.xz
kiriki                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kiriki-23.08.5.tar.xz
kismet2020                04-R3        23 May 2020  https://www.kismetwireless.net/code/kismet-2020-04-R3.tar.xz
kite                      1.0.4        01 June 2014 http://www.kite-language.org/files/kite-1.0.4.tar.gz
kitemmodels               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kitemmodels-5.115.0.tar.xz
kitemviews                5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kitemviews-5.115.0.tar.xz
kiten                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kiten-23.08.5.tar.xz
kitinerary                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kitinerary-23.08.5.tar.xz
kiwi                      1.9.29       20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/kiwi/1.9/kiwi-1.9.29.tar.xz
kjobwidgets               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kjobwidgets-5.115.0.tar.xz
kjournald                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kjournald-23.08.5.tar.xz
kjs                       5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kjs-5.115.0.tar.xz
kjsembed                  5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kjsembed-5.115.0.tar.xz
kjumpingcube              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kjumpingcube-23.08.5.tar.xz
klavaro                   3.03         01 June 2014 http://downloads.sourceforge.net/project/klavaro/klavaro-3.03.tar.bz2
kldap                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kldap-23.08.5.tar.xz
kleopatra                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kleopatra-23.08.5.tar.xz
klettres                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/klettres-23.08.5.tar.xz
klickety                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/klickety-23.08.5.tar.xz
klineakconfig             0.8beta2     01 June 2014 http://nchc.dl.sourceforge.net/sourceforge/lineak/klineakconfig-0.8-beta2.tar.gz
klines                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/klines-23.08.5.tar.xz
kmag                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmag-23.08.5.tar.xz
kmahjongg                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmahjongg-23.08.5.tar.xz
kmail                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmail-23.08.5.tar.xz
kmailaccountwizard        23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmail-account-wizard-23.08.5.tar.xz
kmailtransport            24.02.2      12 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/kmailtransport-24.02.2.tar.xz
kmarkdownwebview          0.3.0        01 November 2017 https://download.kde.org/stable/kmarkdownwebview/0.3.0/src/kmarkdownwebview-0.3.0.tar.xz
kmbox                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmbox-23.08.5.tar.xz
kmediaplayer              5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kmediaplayer-5.115.0.tar.xz
kmenuedit                 5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kmenuedit-5.27.9.tar.xz
kmime                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmime-23.08.5.tar.xz
kmines                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmines-23.08.5.tar.xz
kmix                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmix-23.08.5.tar.xz
kmod                      32           06 March 2024 https://www.kernel.org/pub/linux/utils/kernel/kmod/kmod-32.tar.xz
kmousetool                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmousetool-23.08.5.tar.xz
kmouth                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmouth-23.08.5.tar.xz
kmp3burn                  0.3.1        01 June 2014 http://www.martin-keil.de/Kmp3burn-0.3.1
kmpg2                     1.95         01 June 2014 http://nchc.dl.sourceforge.net/sourceforge/kmpg2/KmPg2-1.95.tar.bz2
kmplayer                  0.12.0b      15 June 2018 http://mirror.freedif.org/KDE/ftp/stable/kmplayer/0.12/kmplayer-0.12.0b.tar.bz2
kmplot                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kmplot-23.08.5.tar.xz
kmuddy                    1.0.1        22 March 2016 http://www.kmuddy.com/releases/stable/kmuddy-1.0.1.tar.gz
kmymoney                  5.1.3        30 July 2022 https://download.kde.org/stable/kmymoney/5.1.3/src/kmymoney-5.1.3.tar.xz
knavalbattle              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/knavalbattle-23.08.5.tar.xz
knetwalk                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/knetwalk-23.08.5.tar.xz
knewstuff                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/knewstuff-5.115.0.tar.xz
knights                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/knights-23.08.5.tar.xz
knotes                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/knotes-23.08.5.tar.xz
knotifications            5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/knotifications-5.115.0.tar.xz
knotifyconfig             5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/knotifyconfig-5.115.0.tar.xz
kobodeluxe                0.5.1        01 August 2013 http://www.olofson.net/kobodl/download/KoboDeluxe-0.5.1.tar.bz2
koko                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/koko-23.08.5.tar.xz
kolf                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kolf-23.08.5.tar.xz
kollision                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kollision-23.08.5.tar.xz
kolourpaint               23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kolourpaint-23.08.5.tar.xz
kompare                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kompare-23.08.5.tar.xz
konforka                  0.0          01 June 2014 http://kin.klever.net/dist/konforka-0.0.tar.bz2
kongress                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kongress-23.08.5.tar.xz
konqueror                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/konqueror-23.08.5.tar.xz
konquest                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/konquest-23.08.5.tar.xz
konsole                   24.02.2      15 April 2024 https://download.kde.org/stable/release-service/24.02.2/src/konsole-24.02.2.tar.xz
kontact                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kontact-23.08.5.tar.xz
kontactinterface          23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kontactinterface-23.08.5.tar.xz
kontrast                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kontrast-23.08.5.tar.xz
konversation              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/konversation-23.08.5.tar.xz
kopeninghours             23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kopeninghours-23.08.5.tar.xz
kopete                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kopete-23.08.5.tar.xz
korganizer                24.02.1      24 March 2024 https://download.kde.org/stable/release-service/24.02.1/src/korganizer-24.02.1.tar.xz
kosmindoormap             23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kosmindoormap-23.08.5.tar.xz
kpackage                  5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kpackage-5.115.0.tar.xz
kparts                    5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kparts-5.115.0.tar.xz
kpat                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kpat-23.08.5.tar.xz
kpeople                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kpeople-5.115.0.tar.xz
kpimtextedit              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kpimtextedit-23.08.5.tar.xz
kpipewire                 5.27.10      18 February 2024 https://download.kde.org/stable/plasma/5.27.10/kpipewire-5.27.10.tar.xz
kpkpass                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kpkpass-23.08.5.tar.xz
kplayer                   0.6.3        01 June 2014 http://prdownloads.sourceforge.net/kplayer/kplayer-0.6.3.tar.bz2
kplotting                 5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kplotting-5.115.0.tar.xz
kpmcore                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kpmcore-23.08.5.tar.xz
kpty                      5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kpty-5.115.0.tar.xz
kpublictransport          23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kpublictransport-23.08.5.tar.xz
kqtquickcharts            23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kqtquickcharts-23.08.5.tar.xz
kquickcharts              5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kquickcharts-5.115.0.tar.xz
kramdown                  2.4.0        27 May 2022  https://rubygems.org/downloads/kramdown-2.4.0.gem
kraptor                   03APR2004    01 June 2014 http://kraptor.sourceforge.net/
krb5                      1.21.2       23 February 2024 https://kerberos.org/dist/krb5/1.21/krb5-1.21.2.tar.gz
krb5authdialog            3.26.1       12 November 2017 http://ftp.gnome.org/pub/gnome/sources/krb5-auth-dialog/3.26/krb5-auth-dialog-3.26.1.tar.xz
krdc                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/krdc-23.08.5.tar.xz
krecord                   1.16         01 June 2014 http://dl.bytesex.org/releases/krecord/
krecorder                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/krecorder-23.08.5.tar.xz
kreversi                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kreversi-23.08.5.tar.xz
krfb                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/krfb-23.08.5.tar.xz
krita                     5.2.2        06 December 2023 https://download.kde.org/stable/krita/5.2.2/krita-5.2.2.tar.xz
kross                     5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kross-5.115.0.tar.xz
krossinterpreters         23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kross-interpreters-23.08.5.tar.xz
kruler                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kruler-23.08.5.tar.xz
krunner                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/krunner-5.115.0.tar.xz
krusader                  2.8.1        12 March 2024 https://download.kde.org/stable/krusader/2.8.1/krusader-2.8.1.tar.xz
ksanecore                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksanecore-23.08.5.tar.xz
kscreen                   5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kscreen-5.27.9.tar.xz
kscreenlocker             5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kscreenlocker-5.27.9.tar.xz
kseexpr                   14.09.2022   14 September 2022 kseexpr-14.09.2022
kservice                  5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kservice-5.115.0.tar.xz
kshisen                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kshisen-23.08.5.tar.xz
kshutdown                 1.0.2        01 June 2014 http://superb-west.dl.sourceforge.net/sourceforge/kshutdown/kshutdown-1.0.2.tar.bz2
ksirk                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksirk-23.08.5.tar.xz
ksmoothdock               5.11         22 December 2018 https://github.com/dangvd/ksmoothdock/archive/v5.11.tar.gz
ksmtp                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksmtp-23.08.5.tar.xz
ksnakeduel                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksnakeduel-23.08.5.tar.xz
ksniffer                  0.3.2        01 June 2014 http://www.ksniffer.org/
kspaceduel                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kspaceduel-23.08.5.tar.xz
ksquares                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksquares-23.08.5.tar.xz
ksshaskpass               5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/ksshaskpass-5.27.9.tar.xz
kstars                    3.7.0        09 April 2024 https://mirror.kumi.systems/kde/ftp/stable/kstars/kstars-3.7.0.tar.xz
ksudoku                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksudoku-23.08.5.tar.xz
ksysguard                 5.21.5       04 May 2021  https://download.kde.org/stable/plasma/5.21.5/ksysguard-5.21.5.tar.xz
ksystemlog                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ksystemlog-23.08.5.tar.xz
ksystemstats              5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/ksystemstats-5.27.9.tar.xz
kteatime                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kteatime-23.08.5.tar.xz
ktexteditor               5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/ktexteditor-5.115.0.tar.xz
ktextwidgets              5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/ktextwidgets-5.115.0.tar.xz
ktimer                    24.02.1      21 March 2024 https://download.kde.org/stable/release-service/24.02.1/src/ktimer-24.02.1.tar.xz
ktnef                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ktnef-23.08.5.tar.xz
ktorrent                  24.02.1      21 March 2024 https://download.kde.org/stable/release-service/24.02.1/src/ktorrent-24.02.1.tar.xz
ktouch                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ktouch-23.08.5.tar.xz
ktpaccountskcm            23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-accounts-kcm-23.04.3.tar.xz
ktpapprover               23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-approver-23.04.3.tar.xz
ktpauthhandler            23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-auth-handler-23.04.3.tar.xz
ktpcallui                 23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-call-ui-23.04.3.tar.xz
ktpcommoninternals        23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-common-internals-23.04.3.tar.xz
ktpcontactlist            23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-contact-list-23.04.3.tar.xz
ktpcontactrunner          23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-contact-runner-23.04.3.tar.xz
ktpdesktopapplets         23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-desktop-applets-23.04.3.tar.xz
ktpfiletransferhandler    23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-filetransfer-handler-23.04.3.tar.xz
ktpkdedmodule             23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-kded-module-23.04.3.tar.xz
ktpsendfile               23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-send-file-23.04.3.tar.xz
ktptextui                 23.04.3      06 July 2023 https://download.kde.org/stable/release-service/23.04.3/src/ktp-text-ui-23.04.3.tar.xz
ktrip                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ktrip-23.08.5.tar.xz
ktuberling                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/ktuberling-23.08.5.tar.xz
kturtle                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kturtle-23.08.5.tar.xz
kubrick                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kubrick-23.08.5.tar.xz
kuklomenos                0.4.5        10 October 2017 http://mbays.freeshell.org/kuklomenos/src/kuklomenos-0.4.5.tar.gz
kunitconversion           5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kunitconversion-5.115.0.tar.xz
kvideoencoder             .?=31385     01 June 2014 https://kde-apps.org/content/show.php?content=31385
kvkbd                     56019        01 June 2014 http://www.kde-apps.org/content/show.php/Kvkbd?content=56019
kwalify                   0.7.2        01 December 2017 https://rubygems.org/downloads/kwalify-0.7.2.gem
kwallet                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kwallet-5.115.0.tar.xz
kwalletmanager            23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kwalletmanager-23.08.5.tar.xz
kwalletpam                5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kwallet-pam-5.27.9.tar.xz
kwave                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kwave-23.08.5.tar.xz
kwayland                  5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kwayland-5.115.0.tar.xz
kwaylandintegration       5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kwayland-integration-5.27.9.tar.xz
kwaylandserver            5.24.5       04 May 2022  https://download.kde.org/stable/plasma/5.24.5/kwayland-server-5.24.5.tar.xz
kweather                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kweather-23.08.5.tar.xz
kwidgetsaddons            5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kwidgetsaddons-5.115.0.tar.xz
kwifiselector             0.8          01 June 2014 https://sourceforge.net/projects/kwifiselector/files/kwifiselector/0.8/kwifiselector-0.8.tar.gz
kwin                      5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kwin-5.27.9.tar.xz
kwindowsystem             5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kwindowsystem-5.115.0.tar.xz
kwordquiz                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/kwordquiz-23.08.5.tar.xz
kwrited                   5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/kwrited-5.27.9.tar.xz
kxmlgui                   5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/kxmlgui-5.115.0.tar.xz
kxmlrpcclient             5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/portingAids/kxmlrpcclient-5.115.0.tar.xz
lablgtk                   2.10.0       01 June 2014 http://wwwfun.kurims.kyoto-u.ac.jp/soft/olabl/dist/lablgtk-2.10.0.tar.gz
labplot                   2.9.0        03 September 2022 https://download.kde.org/stable/labplot/2.9.0/labplot-2.9.0.tar.xz
ladspasdk                 1.13         01 November 2012 https://www.ladspa.org/download/ladspa_sdk-1.13.tgz
lame                      3.100        26 October 2017 https://sourceforge.net/projects/lame/files/lame/3.100/lame-3.100.tar.gz
lapack                    15.03.2024   11 May 2019  http://www.netlib.org/lapack/lapack-15.03.2024.tar.gz
larswm                    7.5.3        27 July 2017 http://porneia.free.fr/larswm/larswm-7.5.3.tar.gz
lasem                     0.5.1        24 May 2019  http://ftp.gnome.org/pub/gnome/sources/lasem/0.5/lasem-0.5.1.tar.xz
latexila                  3.27.1       09 December 2017 http://ftp.gnome.org/pub/gnome/sources/latexila/3.27/latexila-3.27.1.tar.xz
launchy                   2.5.0        27 May 2022  https://rubygems.org/downloads/launchy-2.5.0.gem
layershellqt              5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/layer-shell-qt-5.27.9.tar.xz
lbreakout                 010315       01 December 2012 http://prdownloads.sourceforge.net/lgames/lbreakout-010315.tar.gz
lbreakout2                2.6.5        07 June 2018 http://prdownloads.sourceforge.net/lgames/lbreakout2-2.6.5.tar.gz
lbreakouthd               1.1.6        19 February 2024 https://sourceforge.net/projects/lgames/files/lbreakouthd/lbreakouthd-1.1.6.tar.gz
lbxproxy                  1.0.3        09 June 2018 https://www.x.org/releases/individual/app/lbxproxy-1.0.3.tar.bz2
lcms                      1.19         01 January 2013 http://sourceforge.net/projects/lcms/files/lcms/1.19/lcms-1.19.tar.gz
lcms2                     2.15         04 March 2023 https://github.com/mm2/Little-CMS/releases/download/lcms2.15/lcms2-2.15.tar.gz
ldmud                     3.5.0        22 February 2017 https://github.com/ldmud/ldmud/tarball/master/ldmud-3.5.0
ldns                      1.8.1        08 December 2021 https://www.nlnetlabs.nl/downloads/ldns/ldns-1.8.1.tar.gz
leafpad                   0.8.17       24 November 2017 http://savannah.nongnu.org/download/leafpad/leafpad-0.8.17.tar.gz
leptonica                 1.83.1       05 March 2023 https://github.com/DanBloomberg/leptonica/releases/download/1.83.1/leptonica-1.83.1.tar.gz
less                      643          13 April 2024 https://www.greenwoodsoftware.com/less/less-643.tar.gz
lesstif                   0.95.2       01 June 2014 https://sourceforge.net/projects/lesstif/files/lesstif/0.95.2/lesstif-0.95.2.tar.gz
lfhex                     0.4          01 June 2014 http://stoopidsimple.com/files/lfhex-0.4.tar.gz
lftp                      4.9.2        18 March 2024 http://lftp.yar.ru/ftp/lftp-4.9.2.tar.gz
lgeneral                  1.4.4        02 April 2022 http://prdownloads.sourceforge.net/lgeneral/lgeneral-1.4.4.tar.gz
libabigail                1.5          30 October 2018 http://mirrors.kernel.org/sourceware/libabigail/libabigail-1.5.tar.gz
libadwaita                1.5.0        18 March 2024 https://download.gnome.org/sources/libadwaita/1.5/libadwaita-1.5.0.tar.xz
libao                     1.2.0        14 August 2017 https://ftp.osuosl.org/pub/xiph/releases/ao/libao-1.2.0.tar.gz
libaom                    3.8.2        20 March 2024 https://storage.googleapis.com/aom-releases/libaom-3.8.2.tar.gz
libapplewm                1.3.0        01 June 2014 http://xorg.freedesktop.org/releases/individual/lib/libAppleWM-1.3.0.tar.bz2
libapreq2                 2.08         01 June 2014 http://apache.4any.org/httpd/libapreq/libapreq2-2.08.tar.gz
libarchive                3.7.3        08 April 2024 https://github.com/libarchive/libarchive/releases/download/v3.7.3/libarchive-3.7.3.tar.xz
libartlgpl                2.3.21       01 June 2014 ftp://ftp.gnome.org/pub/GNOME/sources/libart_lgpl/2.3/libart_lgpl-2.3.21.tar.bz2
libass                    0.17.1       03 March 2023 https://github.com/libass/libass/releases/download/0.17.1/libass-0.17.1.tar.xz
libassuan                 2.5.7        08 March 2024 https://gnupg.org/ftp/gcrypt/libassuan/libassuan-2.5.7.tar.bz2
libast                    0.7          09 July 2015 http://www.eterm.org/download/libast-0.7.tar.gz
libatasmart               0.19         01 June 2014 http://0pointer.de/public/libatasmart-0.19.tar.xz
libatomicops              7.8.0        05 April 2023 https://github.com/ivmai/libatomic_ops/releases/download/v7.8.0/libatomic_ops-7.8.0.tar.gz
libav                     11.3         22 May 2015  https://libav.org/releases/libav-11.3.tar.xz
libavc1394                0.5.4        01 June 2014 https://sourceforge.net/projects/libavc1394/files/libavc1394/libavc1394-0.5.4.tar.gz
libavg                    0.7.0        01 June 2014 http://www.libavg.de/libavg-0.7.0.tar.gz
libavif                   1.0.4        10 February 2024 https://github.com/AOMediaCodec/libavif/archive/v1.0.4/libavif-1.0.4.tar.gz
libbacktrace              22.03.2024   22 March 2024 https://download.kde.org/stable/libbacktrace-22.03.2024.tar.xz
libbash                   0.9.10       01 June 2014 http://surfnet.dl.sourceforge.net/sourceforge/libbash/libbash-0.9.10.tar.bz2
libblockdev               3.1.1        29 March 2024 https://github.com/storaged-project/libblockdev/releases/download/3.1.1-1/libblockdev-3.1.1.tar.gz
libbluray                 1.3.4        02 December 2022 https://download.videolan.org/pub/videolan/libbluray/1.3.4/libbluray-1.3.4.tar.bz2
libbonobo                 2.32.1       01 May 2012  http://ftp.gnome.org/pub/GNOME/sources/libbonobo/2.32/libbonobo-2.32.1.tar.bz2
libbpg                    0.9.8        10 November 2018 https://bellard.org/bpg/libbpg-0.9.8.tar.gz
libbtctl                  0.11.1       01 June 2014 http://ftp.gnome.org/pub/gnome/sources/libbtctl/0.11/libbtctl-0.11.1.tar.bz2
libburn                   1.5.6        25 June 2023 https://files.libburnia-project.org/releases/libburn-1.5.6.tar.gz
libbytesize               2.8          26 March 2023 https://github.com/storaged-project/libbytesize/releases/download/2.8/libbytesize-2.8.tar.gz
libcaca                   0.99.beta19  12 March 2015 http://caca.zoy.org/files/libcaca/libcaca-0.99.beta19.tar.gz
libcacard                 2.5.2        17 December 2015 http://www.spice-space.org/download/libcacard/libcacard-2.5.2.tar.xz
libcanberra               0.30         01 January 2013 http://0pointer.de/lennart/projects/libcanberra/libcanberra-0.30.tar.xz
libcap                    2.69         17 May 2023  https://mirrors.edge.kernel.org/pub/linux/libs/security/linux-privs/libcap2/libcap-2.69.tar.xz
libcap2                   2.24.        08 March 2015 ftp://ftp.de.debian.org/debian/pool/main/libc/libcap2/libcap2_2.24.orig.tar.xz
libcapng                  0.8          10 September 2020 https://people.redhat.com/sgrubb/libcap-ng/libcap-ng-0.8.tar.gz
libcddb                   1.3.2        01 June 2014 https://sourceforge.net/projects/libcddb/files/libcddb/libcddb-1.3.2.tar.bz2
libcdio                   2.1.0        18 April 2019 https://ftp.gnu.org/pub/gnu/libcdio/libcdio-2.1.0.tar.bz2
libcerf                   1.3          03 January 2016 https://sourceforge.net/projects/libcerf/files/libcerf-1.3.tgz
libcgroup                 0.41         02 August 2020 https://sourceforge.net/projects/libcg/files/libcgroup/v0.41/libcgroup-0.41.tar.gz
libchamplain              0.12.21      19 January 2023 https://download.gnome.org/sources/libchamplain/0.12/libchamplain-0.12.21.tar.xz
libcloudproviders         0.3.6        22 March 2024 https://download.gnome.org/sources/libcloudproviders/0.3/libcloudproviders-0.3.6.tar.xz
libcm                     0.1.1        01 June 2014 http://ftp.acc.umu.se/pub/GNOME/sources/libcm/0.1/libcm-0.1.1.tar.bz2
libconfig                 1.7.2        08 April 2018 https://github.com/hyperrealm/libconfig/archive/v1.7.2.tar.gz
libcroco                  0.6.13       06 April 2019 https://ftp.gnome.org/pub/gnome/sources/libcroco/0.6/libcroco-0.6.13.tar.xz
libcryptui                3.12.2       05 October 2019 http://ftp.acc.umu.se/pub/GNOME/sources/libcryptui/3.12/libcryptui-3.12.2.tar.xz
libcsv                    3.0.3        19 February 2022 https://sourceforge.net/projects/libcsv/files/libcsv/libcsv-3.0.3/libcsv-3.0.3.tar.gz
libdaemon                 0.14         01 August 2013 https://0pointer.de/lennart/projects/libdaemon/libdaemon-0.14.tar.gz
libdap                    3.20.3       19 April 2019 https://www.opendap.org/pub/source/libdap-3.20.3.tar.gz
libdatrie                 0.2.13       14 March 2024 https://github.com/tlwg/libdatrie/releases/download/v0.2.13/libdatrie-0.2.13.tar.xz
libdazzle                 3.44.0       25 March 2022 https://download.gnome.org/sources/libdazzle/3.44/libdazzle-3.44.0.tar.xz
libdbi                    0.9.0        04 July 2017 https://sourceforge.net/projects/libdbi/files/libdbi/libdbi-0.9.0/libdbi-0.9.0.tar.gz
libdbusmenu               16.04.0      12 November 2020 https://launchpad.net/libdbusmenu/16.04/16.04.0/+download/libdbusmenu-16.04.0.tar.gz
libdc1394                 2.2.6        03 March 2023 https://sourceforge.net/projects/libdc1394/files/libdc1394-2/2.2.6/libdc1394-2.2.6.tar.gz
libdca                    0.0.5        01 June 2014 http://download.videolan.org/pub/videolan/libdca/0.0.5/libdca-0.0.5.tar.bz2
libdeflate                1.20         23 Mar 2024  https://github.com/ebiggers/libdeflate/releases/download/v1.20/libdeflate-1.20.tar.gz
libdex                    0.5.0        23 February 2024 https://download.gnome.org/sources/libdex/0.5/libdex-0.5.0.tar.xz
libdisasm                 0.22         01 June 2014 http://freshmeat.net/redir/libdisasm/72406/url_tgz/libdisasm-0.22.tar.gz
libdiscid                 0.6.4        04 March 2023 http://ftp.musicbrainz.org/pub/musicbrainz/libdiscid/libdiscid-0.6.4.tar.gz
libdivecomputer           0.4.2        02 June 2015 http://www.libdivecomputer.org/releases/libdivecomputer-0.4.2.tar.gz
libdmtx                   0.7.4        19 September 2017 https://sourceforge.net/projects/libdmtx/files/libdmtx/0.7.4/libdmtx-0.7.4.tar.gz
libdmx                    1.1.5        05 June 2023 https://www.x.org/releases/individual/lib/libdmx-1.1.5.tar.xz
libdnet                   1.12         01 June 2014 http://libdnet.googlecode.com/files/libdnet-1.12.tgz
libdrm                    2.4.120      21 January 2024 https://dri.freedesktop.org/libdrm/libdrm-2.4.120.tar.xz
libdv                     1.0.0        27 November 2019 https://sourceforge.net/projects/libdv/files/libdv/1.0.0/libdv-1.0.0.tar.gz
libdvbpsi                 0.2.0        01 June 2014 http://download.videolan.org/pub/libdvbpsi/0.2.0/libdvbpsi-0.2.0.tar.bz2
libdvdcss                 1.4.3        20 April 2021 https://download.videolan.org/pub/libdvdcss/1.4.3/libdvdcss-1.4.3.tar.bz2
libdvdnav                 6.1.1        22 April 2021 http://download.videolan.org/pub/videolan/libdvdnav/6.1.1/libdvdnav-6.1.1.tar.bz2
libdvdread                6.1.3        26 May 2022  https://download.videolan.org/videolan/libdvdread/6.1.3/libdvdread-6.1.3.tar.bz2
libebml                   1.3.10       12 December 2019 https://dl.matroska.org/downloads/libebml/libebml-1.3.10.tar.xz
libebt                    1.3.0        01 June 2014 http://libebt.berlios.de/
libedit20170329           3.1          11 September 2017 https://thrysoee.dk/editline/libedit-20170329-3.1.tar.gz
libei                     1.2.1        18 March 2024 https://gitlab.freedesktop.org/libinput/libei/-/archive/1.2.1/libei-1.2.1.tar.gz
libelf                    0.8.13       01 June 2014 http://www.mr511.de/software/libelf-0.8.13.tar.gz
libepc                    0.4.5        04 December 2018 http://ftp.gnome.org/pub/gnome/sources/libepc/0.4/libepc-0.4.5.tar.xz
libepoxy                  1.5.10       25 March 2022 https://download.gnome.org/sources/libepoxy/1.5/libepoxy-1.5.10.tar.xz
liberror                  2.1.80011    01 June 2014 http://www.theiling.de/projects/liberror.html#download
libesmtp                  1.0.6        01 June 2014 http://www.stafford.uklinux.net/libesmtp/libesmtp-1.0.6.tar.bz2
libetc                    0.4          31 October 2017 http://ordiluc.net/fs/libetc/libetc-0.4.tar.gz
libetpan                  1.1          25 August 2016 https://sourceforge.net/projects/libetpan/files/libetpan/1.1/libetpan-1.1.tar.gz
libevdev                  1.13.1       06 May 2023  https://www.freedesktop.org/software/libevdev/libevdev-1.13.1.tar.xz
libevent                  2.1.12       06 July 2020 https://github.com/libevent/libevent/releases/download/release-2.1.12-stable/libevent-2.1.12-stable.tar.gz
libexif                   0.6.24       27 November 2021 https://github.com/libexif/libexif/releases/download/v0.6.24/libexif-0.6.24.tar.bz2
libextractor              1.11         08 February 2023 https://ftp.gnu.org/gnu/libextractor/libextractor-1.11.tar.gz
libfakekey                0.1          01 September 2014 http://downloads.yoctoproject.org/releases/matchbox/libfakekey/0.1/libfakekey-0.1.tar.bz2
libfame                   0.9.1        01 June 2014 https://puzzle.dl.sourceforge.net/sourceforge/fame/libfame-0.9.1.tar.gz
libferris                 1.5.19       11 November 2017 https://sourceforge.net/projects/witme/files/libferris/1.5.19/libferris-1.5.19.tar.xz
libffado                  2.3.0        13 April 2019 http://www.ffado.org/files/libffado-2.3.0.tgz
libffcall                 2.4          13 June 2021 https://ftp.gnu.org/pub/gnu/libffcall/libffcall-2.4.tar.gz
libffi                    3.4.6        24 February 2024 https://github.com/libffi/libffi/releases/download/v3.4.6/libffi-3.4.6.tar.gz
libfirm                   1.22.0       04 January 2016 https://github.com/MatzeB/libfirm/archive/libfirm-1.22.0.tar.gz
libfixbuf                 2.4.1        27 August 2022 https://tools.netsa.cert.org/releases/libfixbuf-2.4.1.tar.gz
libflowmanager            3.0.0        20 May 2018  http://research.wand.net.nz/software/libflowmanager/libflowmanager-2.0.2.tar.gz
libfm                     1.3.2        02 February 2023 https://sourceforge.net/projects/pcmanfm/files/PCManFM%20+%20Libfm%20%28tarball%20release%29/LibFM/libfm-1.3.2.tar.xz
libfmqt                   0.16.0       07 November 2020 https://github.com/lxqt/libfm-qt/releases/download/0.16.0/libfm-qt-0.16.0.tar.xz
libfontenc                1.1.8        04 March 2024 https://xorg.freedesktop.org/releases/individual/lib/libfontenc-1.1.8.tar.gz
libfprint                 1.90.0       24 December 2019 https://gitlab.freedesktop.org/libfprint/libfprint/uploads/1bba17b5daa130aa548bc7ea96dc58c4/libfprint-1.90.0.tar.xz
libfreebob                1.0.11       01 June 2014 https://sourceforge.net/projects/freebob/files/libfreebob-1.x/libfreebob-1.0.11/libfreebob-1.0.11.tar.gz
libfs                     1.0.9        28 August 2022 https://www.x.org/releases/individual/lib/libFS-1.0.9.tar.xz
libft                     0.4          01 June 2014 http://defiant.homedns.org/~erik/ft/libft/files/libft-0.4.tar.gz
libftdi                   0.13         01 June 2014 http://www.intra2net.com/de/produkte/opensource/ftdi/TGZ/libftdi-0.13.tar.gz
libgadu                   1.12.2       19 September 2017 http://github.com/wojtekka/libgadu/releases/download/1.12.2/libgadu-1.12.2.tar.gz
libgamessupport           1.0.2        07 May 2016  http://ftp.gnome.org/pub/GNOME/sources/libgames-support/1.0/libgames-support-1.0.2.tar.xz
libgcrypt                 1.10.2       08 April 2023 https://www.gnupg.org/ftp/gcrypt/libgcrypt/libgcrypt-1.10.2.tar.bz2
libgd                     2.3.3        15 September 2021 https://github.com/libgd/libgd/releases/download/gd-2.3.3/libgd-2.3.3.tar.xz
libgda                    6.0.0        21 February 2022 https://download.gnome.org/sources/libgda/6.0/libgda-6.0.0.tar.xz
libgdamm                  4.99.11      04 November 2015 http://ftp.gnome.org/pub/GNOME/sources/libgdamm/4.99/libgdamm-4.99.11.tar.xz
libgdata                  0.18.1       08 March 2021 https://download.gnome.org/sources/libgdata/0.18/libgdata-0.18.1.tar.xz
libgdiplus                2.10.9       01 January 2013 http://download.mono-project.com/sources/libgdiplus/libgdiplus-2.10.9.tar.bz2
libgee                    0.20.6       18 September 2022 https://download.gnome.org/sources/libgee/0.20/libgee-0.20.6.tar.xz
libgepub                  0.7.1        14 June 2023 https://download.gnome.org/sources/libgepub/0.7/libgepub-0.7.1.tar.xz
libggi                    2.2.2        01 June 2014 http://prdownloads.sourceforge.net/ggi/libggi-2.2.2tar.gz
libghemical               3.0.0        01 June 2014 https://bioinformatics.org/ghemical/download/current/libghemical-3.0.0.tar.gz
libgig                    3.3.0        01 June 2014 http://download.linuxsampler.org/packages/libgig-3.3.0.tar.bz2
program                   VERSION      08 August 2017 https://github.com/libgit2/libgit2/archive/v0.28.1.tar.gz
libgit2glib               1.1.0        18 July 2022 https://download.gnome.org/sources/libgit2-glib/1.1/libgit2-glib-1.1.0.tar.xz
libgksu                   2.0.12       27 December 2017 http://people.debian.org/~kov/gksu/libgksu-2.0.12.tar.gz
libglade                  2.6.4        01 June 2014 http://ftp.acc.umu.se/pub/GNOME/sources/libglade/2.6/libglade-2.6.4.tar.bz2
libglademm                2.6.6        01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/libglademm/2.6/libglademm-2.6.6.tar.bz2
libglvnd                  v1.7.0       14 September 2023 https://gitlab.freedesktop.org/glvnd/libglvnd/-/archive/v1.7.0/libglvnd-v1.7.0.tar.bz2
libgnomecanvasmm          2.20.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/libgnomecanvasmm/2.20/libgnomecanvasmm-2.20.0.tar.bz2
libgnomecups              0.2.3        01 June 2014 http://ftp.acc.umu.se/pub/gnome/sources/libgnomecups/0.2/libgnomecups-0.2.3.tar.bz2
libgnomedb                3.99.3       01 June 2014 http://www.gnome-db.org/
libgnomegamessupport      2.0.0        17 March 2022 https://download.gnome.org/sources/libgnome-games-support/2.0/libgnome-games-support-2.0.0.tar.xz
libgnomekbd               3.28.1       05 September 2022 https://download.gnome.org/sources/libgnomekbd/3.28/libgnomekbd-3.28.1.tar.xz
libgnomekeyring           3.12.0       10 September 2014 http://ftp.gnome.org/pub/GNOME/sources/libgnome-keyring/3.12/libgnome-keyring-3.12.0.tar.xz
libgnomemm                2.30.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/libgnomemm/2.30/libgnomemm-2.30.0.tar.bz2
libgnomeuimm              2.28.0       01 June 2014 http://ftp.acc.umu.se/pub/GNOME/sources/libgnomeuimm/2.28/libgnomeuimm-2.28.0.tar.bz2
libgovirt                 0.3.8        26 February 2021 https://download.gnome.org/sources/libgovirt/0.3/libgovirt-0.3.8.tar.xz
libgpgerror               1.48         24 February 2024 https://www.gnupg.org/ftp/gcrypt/libgpg-error/libgpg-error-1.48.tar.bz2
libgphoto2                2.5.28       05 January 2022 https://sourceforge.net/projects/gphoto/files/libgphoto/2.5.28/libgphoto2-2.5.28.tar.bz2
libgravatar               23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libgravatar-23.08.5.tar.xz
libgrss                   0.7.0        17 July 2015 http://ftp.gnome.org/pub/GNOME/sources/libgrss/0.7/libgrss-0.7.0.tar.xz
libgsasl                  1.10.0       01 January 2021 https://ftp.gnu.org/pub/gnu/gsasl/libgsasl-1.10.0.tar.gz
libgsf                    1.14.52      08 February 2024 https://download.gnome.org/sources/libgsf/1.14/libgsf-1.14.52.tar.xz
libgtop                   2.41.3       19 February 2024 https://download.gnome.org/sources/libgtop/2.41/libgtop-2.41.3.tar.xz
libgudev                  238          14 March 2024 https://download.gnome.org/sources/libgudev/238/libgudev-238.tar.xz
libgusb                   0.4.8        09 November 2023 https://github.com/hughsie/libgusb/releases/download/0.4.8/libgusb-0.4.8.tar.xz
libgweather               4.4.2        21 March 2024 https://download.gnome.org/sources/libgweather/4.4/libgweather-4.4.2.tar.xz
libgxps                   0.3.2        27 February 2021 https://download.gnome.org/sources/libgxps/0.3/libgxps-0.3.2.tar.xz
libhandy                  1.8.2        04 March 2023 https://download.gnome.org/sources/libhandy/1.8/libhandy-1.8.2.tar.xz
libheif                   05.04.2024   17 March 2024 https://github.com/strukturag/libheif/releases/download/v1.17.6/libheif-05.04.2024.tar.gz
libhttpseverywhere        0.8.3        11 September 2018 http://ftp.gnome.org/pub/GNOME/sources/libhttpseverywhere/0.8/libhttpseverywhere-0.8.3.tar.xz
libical                   3.0.18       31 March 2024 https://github.com/libical/libical/releases/download/v3.0.18/libical-3.0.18.tar.gz
libicalglib               1.0.4        23 January 2016 http://ftp.gnome.org/pub/GNOME/sources/libical-glib/1.0/libical-glib-1.0.4.tar.xz
libice                    1.1.1        12 December 2022 https://www.x.org/releases/individual/lib/libICE-1.1.1.tar.xz
libiconv                  1.17         22 February 2024 https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.17.tar.gz
libid3tag                 0.15.1b      01 June 2014 https://sourceforge.net/projects/mad/files/libid3tag/0.15.1b/libid3tag-0.15.1b.tar.gz
libidl                    0.8.14       01 January 2013 http://ftp.gnome.org/pub/gnome/sources/libIDL/0.8/libIDL-0.8.14.tar.bz2
libidn                    1.41         27 June 2022 https://ftp.gnu.org/pub/gnu/libidn/libidn-1.41.tar.gz
libidn2                   2.3.4        24 October 2022 https://ftp.gnu.org/pub/gnu/libidn/libidn2-2.3.4.tar.gz
libimobiledevice          1.3.0        10 September 2022 https://github.com/libimobiledevice/libimobiledevice/releases/download/1.3.0/libimobiledevice-1.3.0.tar.bz2
libinput                  1.25.0       01 February 2024 https://gitlab.freedesktop.org/libinput/libinput/-/archive/1.25.0/libinput-1.25.0.tar.gz
libintlperl               1.33         17 March 2023 https://cpan.metacpan.org/authors/id/G/GU/GUIDO/libintl-perl-1.33.tar.gz
libiodbc                  3.52.15      22 February 2023 https://downloads.sourceforge.net/iodbc/libiodbc-3.52.15.tar.gz
libisoburn                1.5.2        29 October 2019 http://files.libburnia-project.org/releases/libisoburn-1.5.2.tar.gz
libisofs                  1.5.4        11 April 2023 http://files.libburnia-project.org/releases/libisofs-1.5.4.tar.gz
libjpeg                   8d           07 March 2015 http://www.ijg.org/files/jpegsrc.v8d.tar.gz
libjpegturbo              3.0.1        19 October 2023 https://downloads.sourceforge.net/libjpeg-turbo/libjpeg-turbo-3.0.1.tar.gz
libkcddb                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkcddb-23.08.5.tar.xz
libkcompactdisc           23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkcompactdisc-23.08.5.tar.xz
libkdcraw                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkdcraw-23.08.5.tar.xz
libkdegames               23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkdegames-23.08.5.tar.xz
libkdepim                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkdepim-23.08.5.tar.xz
libkeduvocdocument        23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkeduvocdocument-23.08.5.tar.xz
libkexiv2                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkexiv2-23.08.5.tar.xz
libkface                  17.08.1      01 January 2018 https://download.kde.org/stable/applications/17.08.1/src/libkface-17.08.1.tar.xz
libkgapi                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkgapi-23.08.5.tar.xz
libkgeomap                20.08.3      05 November 2020 https://download.kde.org/stable/release-service/20.08.3/src/libkgeomap-20.08.3.tar.xz
libkipi                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkipi-23.08.5.tar.xz
libkleo                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkleo-23.08.5.tar.xz
libkmahjongg              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkmahjongg-23.08.5.tar.xz
libkomparediff2           23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libkomparediff2-23.08.5.tar.xz
libksane                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libksane-23.08.5.tar.xz
libksba                   1.6.6        25 February 2024 https://www.gnupg.org/ftp/gcrypt/libksba/libksba-1.6.6.tar.bz2
libkscreen                5.27.11      07 March 2024 https://download.kde.org/stable/plasma/5.27.11/libkscreen-5.27.11.tar.xz
libksieve                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libksieve-23.08.5.tar.xz
libksysguard              5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/libksysguard-5.27.9.tar.xz
libktorrent               23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/libktorrent-23.08.5.tar.xz
liblastfm                 1.1.0        29 July 2019 https://github.com/lastfm/liblastfm/archive/1.1.0.tar.gz
liblbxutil                1.1.0        01 June 2014 https://xorg.freedesktop.org/releases/individual/lib/liblbxutil-1.1.0.tar.bz2
liblinear                 246          03 March 2023 https://github.com/cjlin1/liblinear/archive/v246/liblinear-246.tar.gz
liblinebreak              2.1          18 January 2018 https://sourceforge.net/projects/vimgadgets/files/liblinebreak/2.1/liblinebreak-2.1.tar.gz
liblo                     0.31         26 May 2022  https://sourceforge.net/projects/liblo/files/liblo/0.31/liblo-0.31.tar.gz
liblrdf                   0.4.0        01 December 2012 https://sourceforge.net/projects/lrdf/files/liblrdf/0.4.0/liblrdf-0.4.0.tar.gz
liblxqt                   1.4.0        02 February 2024 https://github.com/lxqt/liblxqt/releases/download/1.4.0/liblxqt-1.4.0.tar.xz
libmad                    0.15.1b      01 September 2013 ftp://ftp.mars.org/pub/mpeg/libmad-0.15.1b.tar.gz
libmanette                0.2.6        30 November 2020 https://download.gnome.org/sources/libmanette/0.2/libmanette-0.2.6.tar.xz
libmatekbd                1.28.0       13 February 2024 https://pub.mate-desktop.org/releases/1.28/libmatekbd-1.28.0.tar.xz
libmatemixer              1.28.0       13 February 2024 https://pub.mate-desktop.org/releases/1.28/libmatemixer-1.28.0.tar.xz
libmateweather            1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/libmateweather-1.28.0.tar.xz
libmatheval               1.1.8        01 June 2012 http://ftp.gnu.org/gnu/libmatheval/libmatheval-1.1.8.tar.gz
libmatroska               1.6.3        08 March 2021 https://github.com/Matroska-Org/libmatroska/archive/release-1.6.3.tar.gz
libmbim                   1.26.4       29 April 2022 https://www.freedesktop.org/software/libmbim/libmbim-1.26.4.tar.xz
libmcs                    0.7.2        12 December 2015 https://distfiles.atheme.org/libmcs-0.7.2.tgz
libmd                     0.3          21 July 2016 ftp://ftp.penguin.cz/pub/users/mhi/libmd/libmd-0.3.tar.bz2
libmediaart               1.9.6        03 June 2022 https://download.gnome.org/sources/libmediaart/1.9/libmediaart-1.9.6.tar.xz
libmemcached              0.22         01 June 2014 http://download.tangent.org/libmemcached-0.22.tar.gz
libmicrohttpd             0.9.77       29 May 2023  https://ftp.gnu.org/pub/gnu/libmicrohttpd/libmicrohttpd-0.9.77.tar.gz
libmikmod                 3.1.12       01 June 2014 https://sourceforge.net/projects/mikmod/files/libmikmod%20%28source%29/3.1.12/libmikmod-3.1.12.tar.gz
libmirage                 1.5.0        01 June 2014 http://downloads.sourceforge.net/cdemu/libmirage-1.5.0.tar.bz2
libmng                    2.0.3        22 October 2015 http://sourceforge.net/projects/libmng/files/libmng-devel/2.0.3/libmng-2.0.3.tar.xz
libmnl                    1.0.5        07 April 2022 https://netfilter.org/projects/libmnl/files/libmnl-1.0.5.tar.bz2
libmodplug                0.8.9.0      25 September 2019 https://sourceforge.net/projects/modplug-xmms/files/libmodplug/0.8.9.0/libmodplug-0.8.9.0.tar.gz
libmowgli                 2.1.3        09 March 2017 https://github.com/atheme/libmowgli-2/archive/v2.1.3.tar.gz
libmp3splt                0.7.2        01 June 2014 http://downloads.sourceforge.net/project/mp3splt/libmp3splt/0.7.2/libmp3splt-0.7.2.tar.gz
libmpcdec                 1.2.6        01 June 2014 http://www.musepack.net/index.php?pg=src
libmpdclient              2.16         23 July 2019 https://www.musicpd.org/download/libmpdclient/2/libmpdclient-2.16.tar.xz
libmpeg2                  0.5.1        01 February 2013 http://libmpeg2.sourceforge.net/files/libmpeg2-0.5.1.tar.gz
libmpeg3                  1.8          01 February 2013 http://downloads.sourceforge.net/heroines/libmpeg3-1.8.tar.bz2
libmspack                 0.0.20060920alpha 01 June 2014 http://www.kyz.uklinux.net/downloads/libmspack-0.0.20040308alpha.tar.gz
libmtp                    1.1.21       26 April 2023 https://sourceforge.net/projects/libmtp/files/libmtp/1.1.21/libmtp-1.1.21.tar.gz
libmusicbrainz            5.1.0        26 November 2018 https://github.com/metabrainz/libmusicbrainz/releases/download/release-5.1.0/libmusicbrainz-5.1.0.tar.gz
libmxp                    0.2.2        01 June 2014 http://www.kmuddy.net/libmxp/files/libmxp-0.2.2.tar.gz
libmypaint                1.6.1        13 May 2020  https://github.com/mypaint/libmypaint/releases/download/v1.6.1/libmypaint-1.6.1.tar.xz
libndp                    1.8          22 May 2021  https://github.com/jpirko/libndp/archive/refs/tags/v1.8.tar.gz
libnet                    1.1.6        22 February 2019 https://sourceforge.net/projects/libnet-dev/files/libnet-1.1.6.tar.gz
libnftnl                  1.2.4        12 November 2022 https://netfilter.org/projects/libnftnl/files/libnftnl-1.2.4.tar.bz2
libnice                   06.03.2024   04 March 2024 http://nice.freedesktop.org/releases/libnice-0.1.19.tar.gz
libnids                   1.24         01 May 2013  https://sourceforge.net/projects/libnids/files/libnids/1.24/libnids-1.24.tar.gz
libnih                    1.0.3        01 January 2013 https://launchpad.net/libnih/1.0/1.0.3/+download/libnih-1.0.3.tar.gz
libnl                     3.7.0        17 July 2022 https://github.com/thom311/libnl/releases/download/libnl3_7_0/libnl-3.7.0.tar.gz
libnma                    1.10.6       11 January 2023 https://download.gnome.org/sources/libnma/1.10/libnma-1.10.6.tar.xz
libnotify                 0.8.3        14 October 2023 https://download.gnome.org/sources/libnotify/0.8/libnotify-0.8.3.tar.xz
libnsl                    2.0.1        19 October 2023 https://github.com/thkukuk/libnsl/releases/download/v2.0.1/libnsl-2.0.1.tar.xz
libnxml                   0.18.3       31 October 2017 http://www.autistici.org/bakunin/libnxml/libnxml-0.18.3.tar.gz
liboauth                  1.0.3        19 April 2015 http://sourceforge.net/projects/liboauth/files/liboauth-1.0.3.tar.gz
libogg                    1.3.5        08 June 2021 http://downloads.xiph.org/releases/ogg/libogg-1.3.5.tar.xz
liboggz                   1.1.1        01 June 2014 http://downloads.xiph.org/releases/liboggz/liboggz-1.1.1.tar.gz
liboil                    0.3.17       23 August 2017 https://liboil.freedesktop.org/download/liboil-0.3.17.tar.gz
liboobs                   3.0.0        20 March 2015 http://ftp.gnome.org/pub/GNOME/sources/liboobs/3.0/liboobs-3.0.0.tar.bz2
libopenglrecorder         26.09.2018   26 September 2018 http://hisham.hm/htop/releases/2.0.2/htop-2.0.2.tar.gz
libopenmodeller           0.4.2        20 September 2017 http://sourceforge.net/projects/openmodeller/files/openModeller/1.5.0/libopenmodeller-1.5.0.zip
libopenraw                0.3.0        10 April 2022 https://libopenraw.freedesktop.org/download/libopenraw-0.3.0.tar.bz2
libopusenc                0.2.1        20 October 2018 https://archive.mozilla.org/pub/opus/libopusenc-0.2.1.tar.gz
libosinfo                 1.10.0       01 April 2023 https://releases.pagure.org/libosinfo/libosinfo-1.10.0.tar.xz
libosip2                  5.3.1        12 October 2022 https://ftp.gnu.org/pub/gnu/osip/libosip2-5.3.1.tar.gz
libosmium                 2.13.0       16 August 2017 https://github.com/osmcode/libosmium/archive/v2.13.0.tar.gz
libostree                 2022.5       23 August 2022 https://github.com/ostreedev/ostree/releases/download/v2022.5/libostree-2022.5.tar.xz
libpaper                  2.2.5        12 March 2024 https://github.com/rrthomas/libpaper/releases/download/v2.2.5/libpaper-2.2.5.tar.gz
libpcap                   1.10.4       08 April 2023 https://www.tcpdump.org/release/libpcap-1.10.4.tar.gz
libpciaccess              0.18.1       24 March 2024 https://xorg.freedesktop.org/releases/individual/lib/libpciaccess-0.18.1.tar.xz
libpeas                   1.36.0       03 June 2023 https://download.gnome.org/sources/libpeas/1.36/libpeas-1.36.0.tar.xz
libpipeline               1.5.7        21 January 2024 https://download.savannah.gnu.org/releases/libpipeline/libpipeline-1.5.7.tar.gz
libplacebo                18.03.2024   18 March 2024 https://github.com/haasn/libplacebo/releases/tag/libplacebo-18.03.2024.tar.xz
libplist                  2.4.0        11 March 2024 https://github.com/libimobiledevice/libplist/releases/download/2.4.0/libplist-2.4.0.tar.bz2
libpng                    1.6.43       25 February 2024 https://sourceforge.net/projects/libpng/files/libpng16/1.6.43/libpng-1.6.43.tar.xz
libpod                    1.1.1        02 March 2019 https://github.com/containers/libpod/archive/libpod-1.1.1.tar.gz
libportal                 0.7.1        11 April 2024 https://github.com/flatpak/libportal/releases/download/0.7.1/libportal-0.7.1.tar.xz
libproxy                  0.5.5        05 April 2024 https://github.com/libproxy/libproxy/archive/refs/tags/0.5.5.tar.gz
libpsl                    0.21.5       20 February 2024 https://github.com/rockdaboot/libpsl/releases/download/0.21.5/libpsl-0.21.5.tar.gz
libpthreadstubs           0.5          10 August 2023 https://www.x.org/releases/individual/lib/libpthread-stubs-0.5.tar.xz
libptytty                 2.0          17 June 2022 http://dist.schmorp.de/libptytty/libptytty-2.0.tar.gz
libpwquality              1.4.5        21 November 2022 https://github.com/libpwquality/libpwquality/releases/download/libpwquality-1.4.5/libpwquality-1.4.5.tar.bz2
libqalculate              5.0.0        12 March 2024 https://github.com/Qalculate/libqalculate/releases/download/v5.0.0/libqalculate-5.0.0.tar.gz
libqglviewer              2.3.17       01 June 2014 http://www.libqglviewer.com/src/libQGLViewer-2.3.17.tar.gz
libqmi                    1.30.8       25 June 2022 https://www.freedesktop.org/software/libqmi/libqmi-1.30.8.tar.xz
libqtxdg                  3.9.1        15 July 2022 https://github.com/lxqt/libqtxdg/releases/download/3.9.1/libqtxdg-3.9.1.tar.xz
libquicktime              1.2.4        01 June 2014 https://sourceforge.net/projects/libquicktime/files/libquicktime/1.2.4/libquicktime-1.2.4.tar.gz
libquvi                   0.9.4        09 June 2016 https://sourceforge.net/projects/quvi/files/0.9/libquvi/libquvi-0.9.4.tar.xz
libquviscripts            0.9.20131130 09 June 2016 https://sourceforge.net/projects/quvi/files/0.9/libquvi-scripts/libquvi-scripts-0.9.20131130.tar.xz
libraw                    0.21.2       27 February 2024 https://www.libraw.org/data/LibRaw-0.21.2.tar.gz
libraw1394                2.0.5        01 June 2014 http://www.linux1394.org/dl/libraw1394-2.0.5.tar.gz
libredwg                  0.12.4       09 April 2021 https://ftp.gnu.org/pub/gnu/libredwg/libredwg-0.12.4.tar.xz
librejs                   7.18.1       14 February 2019 http://ftp.gnu.org/pub/gnu/librejs/librejs-7.18.1.tar.gz
libreoffice               6.3.3.2      15 November 2019 http://download.documentfoundation.org/libreoffice/src/6.3.3/libreoffice-6.3.3.2.tar.xz
libreofficebinfilter      3.6.4.1      08 March 2015 http://download.documentfoundation.org/libreoffice/src/4.2.2/libreoffice-binfilter-3.6.4.1.tar.xz
libreofficecore           3.6.4.3      06 March 2014 http://download.documentfoundation.org/libreoffice/src/4.2.2/libreoffice-core-3.6.4.3.tar.xz
libreofficehelp           6.1.0.3      16 August 2018 http://download.documentfoundation.org/libreoffice/src/6.1.0/libreoffice-help-6.1.0.3.tar.xz
librep                    0.92.6       25 July 2017 http://download.tuxfamily.org/librep/librep_0.92.6.tar.xz
libressl                  3.9.1        28 March 2024 https://ftp.openbsd.org/pub/OpenBSD/LibreSSL/libressl-3.9.1.tar.gz
librevenge                0.0.4        13 March 2016 https://sourceforge.net/projects/libwpd/files/librevenge/librevenge-0.0.4/librevenge-0.0.4.tar.xz
librsvg                   2.58.0       17 March 2024 https://download.gnome.org/sources/librsvg/2.58/librsvg-2.58.0.tar.xz
librsync                  2.3.2        26 November 2021 https://github.com/librsync/librsync/releases/download/v2.3.2/librsync-2.3.2.tar.gz
libsafe                   2.0.16       01 June 2014 https://github.com/tagatac/libsafe-CVE-2005-1125/blob/master/libsafe-2.0-16.tgz
libsamplerate             0.2.2        07 September 2021 https://github.com/libsndfile/libsamplerate/releases/download/0.2.2/libsamplerate-0.2.2.tar.xz
libsass                   3.6.5        22 May 2021  https://github.com/sass/libsass/archive/3.6.5/libsass-3.6.5.tar.gz
libseccomp                2.5.5        03 December 2023 https://github.com/seccomp/libseccomp/releases/download/v2.5.5/libseccomp-2.5.5.tar.gz
libsecret                 0.21.4       23 February 2024 https://download.gnome.org/sources/libsecret/0.21/libsecret-0.21.4.tar.xz
libselinux                3.5          23 February 2023 https://github.com/SELinuxProject/selinux/releases/download/3.5/libselinux-3.5.tar.gz
libsexy                   0.1.11       01 June 2014 http://releases.chipx86.com/libsexy/libsexy/libsexy-0.1.11.tar.gz
libshout                  2.4.6        22 September 2022 https://downloads.xiph.org/releases/libshout/libshout-2.4.6.tar.gz
libsigc++                 3.6.0        30 October 2023 https://download.gnome.org/sources/libsigc++/3.6/libsigc++-3.6.0.tar.xz
libsigsegv                2.14         07 January 2022 https://ftp.gnu.org/pub/gnu/libsigsegv/libsigsegv-2.14.tar.gz
libsixel                  15.03.2024   15 March 2024 https://download.kde.org/stable/foobar-1.0.0.tar.xz
libslab                   2.30.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/libslab/2.30/libslab-2.30.0.tar.gz
libsm                     1.2.4        08 January 2023 https://www.x.org/releases/individual/lib/libSM-1.2.4.tar.xz
libsndfile                1.2.0        18 August 2023 https://github.com/libsndfile/libsndfile/releases/download/1.2.0/libsndfile-1.2.0.tar.xz
libsodium                 1.0.18       01 June 2019 https://github.com/jedisct1/libsodium/releases/download/1.0.18-RELEASE/libsodium-1.0.18.tar.gz
libsolv                   0.7.14       12 July 2020 https://github.com/openSUSE/libsolv/archive/0.7.14.tar.gz
libsoup                   3.4.4        27 October 2023 https://download.gnome.org/sources/libsoup/3.4/libsoup-3.4.4.tar.xz
libspectre                0.2.12       11 March 2024 http://libspectre.freedesktop.org/releases/libspectre-0.2.12.tar.gz
libspnav                  0.2.3        04 June 2016 https://sourceforge.net/projects/spacenav/files/spacenav%20library%20%28SDK%29/libspnav%200.2.3/libspnav-0.2.3.tar.gz
libspng                   0.4.5        31 July 2019 https://gitlab.com/randy408/libspng/uploads/6ddcaa59367b2cea474213a994b82012/libspng-0.4.5.tar.xz
libsrtp                   2.2          22 September 2018 https://github.com/cisco/libsrtp/archive/v2.2.tar.gz
libssh                    0.10.4       07 September 2022 https://www.libssh.org/files/0.10/libssh-0.10.4.tar.xz
libssh2                   1.11.0       01 June 2023 https://www.libssh2.org/download/libssh2-1.11.0.tar.gz
libstatgrab               0.92         26 August 2020 http://www.mirrorservice.org/sites/ftp.i-scream.org/pub/i-scream/libstatgrab/libstatgrab-0.92.tar.gz
libstemmer                24.12.2018   24 December 2018 https://github.com/zvelo/libstemmer
libsysstat                0.4.6        14 February 2022 https://github.com/lxqt/libsysstat/releases/download/0.4.6/libsysstat-0.4.6.tar.xz
libtar                    1.2.11       01 June 2014 https://github.com/mdippery/libtar/libtar-1.2.11.tar.gz
libtasn1                  4.19.0       26 August 2022 https://ftp.gnu.org/pub/gnu/libtasn1/libtasn1-4.19.0.tar.gz
libtheora                 05.04.2024   12 August 2017 https://downloads.xiph.org/releases/theora/libtheora-05.04.2024.tar.xz
libtirpc                  1.3.3        09 August 2022 https://sourceforge.net/projects/libtirpc/files/libtirpc/1.3.3/libtirpc-1.3.3.tar.bz2
libtool                   2.4.7        17 March 2022 https://mirrors.kernel.org/gnu/libtool/libtool-2.4.7.tar.xz
libtorrent                0.13.7       30 May 2019  https://github.com/rakshasa/rtorrent/releases/download/v0.9.7/libtorrent-0.13.7.tar.gz
libtorrentrasterbar       2.0.9        19 June 2023 https://github.com/arvidn/libtorrent/releases/download/v2.0.9/libtorrent-rasterbar-2.0.9.tar.gz
libtrace                  3.0.14       01 June 2014 http://research.wand.net.nz/software/libtrace/libtrace-3.0.14.tar.bz2
libtranslate              0.99         01 June 2014 http://savannah.nongnu.org/download/libtranslate/libtranslate-0.99.tar.gz
libui                     0.0.15       12 March 2022 https://rubygems.org/downloads/libui-0.0.15.gem
libunibreak               3.0          30 August 2016 https://github.com/adah1972/libunibreak/releases/download/libunibreak_3_0/libunibreak-3.0.tar.gz
libunicap                 0.9.12       30 December 2015 http://unicap-imaging.org/downloads/libunicap-0.9.12.tar.gz
libuninameslist           20200413     15 June 2020 https://github.com/fontforge/libuninameslist/releases/download/20200413/libuninameslist-dist-20200413.tar.gz
libuninum                 2.6          01 June 2014 http://billposer.org/Software/libuninum.html#downloads
libunique                 3.0.2        01 August 2013 http://ftp.acc.umu.se/pub/GNOME/sources/libunique/3.0/libunique-3.0.2.tar.xz
libunistring              1.2          25 February 2024 https://ftp.gnu.org/pub/gnu/libunistring/libunistring-1.2.tar.xz
libunwind                 1.6.2        25 March 2022 https://download.savannah.nongnu.org/releases/libunwind/libunwind-1.6.2.tar.gz
libupnp                   1.6.21       17 April 2017 https://sourceforge.net/projects/pupnp/files/pupnp/libUPnP%201.6.21/libupnp-1.6.21.tar.bz2
liburing                  04.04.2024   04 April 2024 https://github.com/axboe/liburing/liburing-04.04.2024
libusb                    1.0.26       26 April 2022 https://github.com/libusb/libusb/releases/download/v1.0.26/libusb-1.0.26.tar.bz2
libusbcompat              0.1.7        18 May 2021  https://github.com/libusb/libusb-compat-0.1/releases/download/v0.1.7/libusb-compat-0.1.7.tar.bz2
libusbmuxd                2.0.2        04 March 2023 https://github.com/libimobiledevice/libusbmuxd/releases/download/2.0.2/libusbmuxd-2.0.2.tar.bz2
libutempter               1.1.6        24 February 2019 ftp://ftp.altlinux.org/pub/people/ldv/utempter/libutempter-1.1.6.tar.bz2
libuv                     v1.47.0      09 November 2023 https://dist.libuv.org/dist/v1.47.0/libuv-v1.47.0.tar.gz
libva                     2.21.0       29 March 2024 https://github.com/intel/libva/archive/2.21.0/libva-2.21.0.tar.gz
libvautils                2.20.0       23 October 2023 https://github.com/intel/libva-utils/releases/download/2.20.0/libva-utils-2.20.0.tar.bz2
libvdpau                  1.5          12 February 2023 https://gitlab.freedesktop.org/vdpau/libvdpau/-/archive/1.5/libvdpau-1.5.tar.bz2
libvdpauvagl              0.3.4        11 April 2015 https://github.com/i-rinat/libvdpau-va-gl/releases/download/v0.3.4/libvdpau-va-gl-0.3.4.tar.gz
libviper                  1.4.6        01 June 2014 http://sourceforge.net/projects/libviper/files/libviper-1.4.6.tar.gz
libvirt                   10.2.0       02 April 2024 https://libvirt.org/sources/libvirt-10.2.0.tar.xz
libvisio                  0.1.7        20 August 2019 https://dev-www.libreoffice.org/src/libvisio/libvisio-0.1.7.tar.xz
libvisual                 0.4.0        01 January 2013 http://sourceforge.net/projects/libvisual/files/libvisual/libvisual-0.4.0/libvisual-0.4.0.tar.bz2
libvncserver              0.9.13       12 March 2021 https://github.com/LibVNC/libvncserver/archive/LibVNCServer-0.9.13.tar.gz
libvolumeid               0.81.0       01 June 2014 http://www.marcuscom.com/downloads/libvolume_id-0.81.0.tar.bz2
libvorbis                 1.3.7        04 July 2020 http://downloads.xiph.org/releases/vorbis/libvorbis-1.3.7.tar.gz
libvpx                    1.13.0       11 February 2023 https://github.com/webmproject/libvpx/archive/v1.13.0/libvpx-1.13.0.tar.gz
libvterm                  0.1.1        04 October 2019 http://www.leonerd.org.uk/code/libvterm/libvterm-0.1.1.tar.gz
libwacom                  2.11.0       16 April 2024 https://github.com/linuxwacom/libwacom/releases/download/libwacom-2.11.0/libwacom-2.11.0.tar.xz
libwebp                   1.4.0        14 April 2024 https://github.com/webmproject/libwebp/archive/refs/tags/v1.4.0.tar.gz
libwindowswm              1.0.0        01 June 2014 http://ftp.cica.es/pub/X/pub/X11R7.3/src/lib/libWindowsWM-1.0.0.tar.bz2
libwmf                    0.2.13       22 April 2023 https://github.com/caolanm/libwmf/archive/refs/tags/v0.2.13.tar.gz
libwnck                   43.0         14 April 2023 https://download.gnome.org/sources/libwnck/43/libwnck-43.0.tar.xz
libwpe                    1.14.1       05 February 2023 https://wpewebkit.org/releases/libwpe-1.14.1.tar.xz
libwps                    0.4.10       17 September 2018 https://sourceforge.net/projects/libwps/files/libwps/libwps-0.4.10/libwps-0.4.10.tar.xz
libwwwperl                6.35         29 July 2018 http://search.cpan.org/CPAN/authors/id/O/OA/OALDERS/libwww-perl-6.35.tar.gz
libx11                    1.8.9        06 April 2024 https://www.x.org/releases/individual/lib/libX11-1.8.9.tar.xz
libxau                    1.0.11       12 December 2022 https://www.x.org/releases/individual/lib/libXau-1.0.11.tar.xz
libxaw                    1.0.16       12 March 2024 https://www.x.org/releases/individual/lib/libXaw-1.0.16.tar.xz
libxaw3d                  1.6.6        04 March 2024 https://www.x.org/releases/individual/lib/libXaw3d-1.6.6.tar.xz
libxaw3dxft               1.6.2h       06 October 2020 https://sourceforge.net/projects/sf-xpaint/files/libxaw3dxft/libXaw3dXft-1.6.2h.tar.bz2
libxcb                    1.17.0       16 April 2024 https://xcb.freedesktop.org/dist/libxcb-1.17.0.tar.xz
libxcm                    0.5.3        10 October 2015 https://sourceforge.net/projects/oyranos/files/libXcm/libXcm-0.5/libXcm-0.5.3.tar.gz
libxcomposite             0.4.6        05 December 2022 https://www.x.org/releases/individual/lib/libXcomposite-0.4.6.tar.xz
libxcrypt                 4.4.36       21 January 2024 https://github.com/besser82/libxcrypt/releases/download/v4.4.36/libxcrypt-4.4.36.tar.xz
libxcursor                1.2.2        04 March 2024 https://www.x.org/releases/individual/lib/libXcursor-1.2.2.tar.xz
libxcvt                   0.1.2        31 July 2022 https://www.x.org/releases/individual/lib/libxcvt-0.1.2.tar.xz
libxdamage                1.1.6        05 December 2022 https://www.x.org/releases/individual/lib/libXdamage-1.1.6.tar.xz
libxdmcp                  1.1.5        04 March 2024 https://www.x.org/releases/individual/lib/libXdmcp-1.1.5.tar.gz
libxevie                  1.0.3        01 June 2014 https://xorg.freedesktop.org/releases/individual/lib/libXevie-1.0.3.tar.bz2
libxext                   1.3.6        12 February 2024 https://www.x.org/releases/individual/lib/libXext-1.3.6.tar.xz
libxfce4ui                4.18.6       09 March 2024 https://archive.xfce.org/src/xfce/libxfce4ui/4.18/libxfce4ui-4.18.6.tar.bz2
libxfce4util              4.18.1       11 January 2023 https://archive.xfce.org/src/xfce/libxfce4util/4.18/libxfce4util-4.18.1.tar.bz2
libxfixes                 6.0.1        10 April 2023 https://www.x.org/releases/individual/lib/libXfixes-6.0.1.tar.xz
libxfont                  1.5.3        22 October 2017 https://www.x.org/releases/individual/lib/libXfont-1.5.3.tar.gz
libxfont2                 2.0.6        28 August 2022 https://www.x.org/releases/individual/lib/libXfont2-2.0.6.tar.xz
libxfontcache             1.0.4        01 June 2014 https://www.x.org/releases/individual/lib/libXfontcache-1.0.4.tar.bz2
libxft                    2.3.8        18 April 2023 https://www.x.org/releases/individual/lib/libXft-2.3.8.tar.xz
libxi                     1.8.1        08 May 2023  https://www.x.org/releases/individual/lib/libXi-1.8.1.tar.xz
libxinerama               1.1.5        31 October 2022 https://www.x.org/releases/individual/lib/libXinerama-1.1.5.tar.xz
libxkbcommon              1.7.0        25 March 2024 https://xkbcommon.org/download/libxkbcommon-1.7.0.tar.xz
libxkbfile                1.1.3        12 February 2024 https://www.x.org/releases/individual/lib/libxkbfile-1.1.3.tar.xz
libxkbui                  1.0.2        01 June 2014 https://www.x.org/releases/individual/lib/libxkbui-1.0.2.tar.bz2
libxklavier               5.3          01 September 2013 http://ftp.gnome.org/pub/GNOME/sources/libxklavier/5.3/libxklavier-5.3.tar.xz
libxls                    1.5.1        15 April 2019 https://github.com/libxls/libxls/releases/download/v1.5.1/libxls-1.5.1.tar.gz
libxml++                  5.0.3        23 March 2023 https://download.gnome.org/sources/libxml++/5.0/libxml++-5.0.3.tar.xz
libxml2                   2.12.6       15 March 2024 https://download.gnome.org/sources/libxml2/2.12/libxml2-2.12.6.tar.xz
libxml2python             2.6.15       01 January 2013 ftp://xmlsoft.org/libxml2/python/libxml2-python-2.6.15.tar.gz
libxmlb                   0.3.18       13 April 2024 https://github.com/hughsie/libxmlb/releases/download/0.3.18/libxmlb-0.3.18.tar.xz
libxmp                    4.6.0        17 March 2024 https://sourceforge.net/projects/xmp/files/libxmp/4.6.0/libxmp-4.6.0.tar.gz
libxmu                    1.2.0        25 March 2024 https://www.x.org/releases/individual/lib/libXmu-1.2.0.tar.xz
libxo                     1.0.4        15 May 2019  https://github.com/Juniper/libxo/releases/download/1.0.4/libxo-1.0.4.tar.gz
libxp                     1.0.4        13 September 2022 https://www.x.org/releases/individual/lib/libXp-1.0.4.tar.xz
libxpm                    3.5.16       18 April 2023 https://www.x.org/releases/individual/lib/libXpm-3.5.16.tar.xz
libxpresent               1.0.1        19 October 2022 https://www.x.org/releases/individual/lib/libXpresent-1.0.1.tar.xz
libxprintapputil          1.0.1        13 September 2018 https://www.x.org/releases/individual/lib/libXprintAppUtil-1.0.1.tar.gz
libxprintutil             1.0.1        01 June 2014 http://xorg.freedesktop.org/releases/individual/lib/libXprintUtil-1.0.1.tar.bz2
libxrandr                 1.5.4        18 November 2023 https://www.x.org/releases/individual/lib/libXrandr-1.5.4.tar.xz
libxrender                0.9.11       24 October 2022 https://www.x.org/releases/individual/lib/libXrender-0.9.11.tar.gz
libxres                   1.2.2        05 December 2022 https://www.x.org/releases/individual/lib/libXres-1.2.2.tar.gz
libxscrnsaver             1.2.4        05 December 2022 https://www.x.org/releases/individual/lib/libXScrnSaver-1.2.4.tar.gz
libxshmfence              1.3.2        12 December 2022 https://www.x.org/releases/individual/lib/libxshmfence-1.3.2.tar.xz
libxslt                   1.1.39       24 November 2023 https://download.gnome.org/sources/libxslt/1.1/libxslt-1.1.39.tar.xz
libxspf                   1.2.0        16 February 2017 http://downloads.xiph.org/releases/xspf/libxspf-1.2.0.tar.bz2
libxt                     1.3.0        10 April 2023 https://www.x.org/releases/individual/lib/libXt-1.3.0.tar.xz
libxtst                   1.2.4        28 September 2022 https://www.x.org/releases/individual/lib/libXtst-1.2.4.tar.gz
libxv                     1.0.12       05 December 2022 https://www.x.org/releases/individual/lib/libXv-1.0.12.tar.gz
libxvmc                   1.0.14       12 February 2024 https://www.x.org/releases/individual/lib/libXvMC-1.0.14.tar.xz
libxxf86dga               1.1.6        05 December 2022 https://www.x.org/releases/individual/lib/libXxf86dga-1.1.6.tar.xz
libxxf86misc              1.0.4        06 July 2018 https://www.x.org/releases/individual/lib/libXxf86misc-1.0.4.tar.bz2
libxxf86vm                1.1.5        28 September 2022 https://www.x.org/releases/individual/lib/libXxf86vm-1.1.5.tar.gz
libyuv                    15.03.2024   15 March 2024 https://chromium.googlesource.com/libyuv/libyuv/libyuv-15.03.2024
libzapojit                0.0.3        17 April 2015 http://ftp.gnome.org/pub/GNOME/sources/libzapojit/0.0/libzapojit-0.0.3.tar.xz
libzeitgeist              0.3.18       01 January 2014 https://launchpad.net/libzeitgeist/0.3/0.3.18/+download/libzeitgeist-0.3.18.tar.gz
libzim                    6.1.6        28 June 2020 https://github.com/openzim/libzim/archive/6.1.6.tar.gz
libzip                    1.10.0       25 June 2023 https://libzip.org/download/libzip-1.10.0.tar.xz
libzrtpcpp                2.0.0        01 June 2014 http://ftp.gnu.org/gnu/ccrtp/libzrtpcpp-2.0.0.tar.gz
licq                      1.8.2        09 July 2015 http://downloads.sourceforge.net/licq/licq-1.8.2.tar.bz2
liferea                   1.12.6b      10 December 2018 https://github.com/lwindolf/liferea/releases/download/v1.12.6/liferea-1.12.6b.tar.bz2
lightdm                   1.30.0       09 July 2019 https://github.com/CanonicalLtd/lightdm/releases/download/1.30.0/lightdm-1.30.0.tar.xz
lightning                 2.2.2        29 April 2023 https://ftp.gnu.org/pub/gnu/lightning/lightning-2.2.2.tar.gz
lightsoff                 46.0         16 March 2024 https://download.gnome.org/sources/lightsoff/46/lightsoff-46.0.tar.xz
lighttpd                  1.4.76       13 April 2024 https://download.lighttpd.net/lighttpd/releases-1.4.x/lighttpd-1.4.76.tar.xz
lilo                      24.2         23 November 2015 http://lilo.alioth.debian.org/ftp/sources/lilo-24.2.tar.gz
lilykde                   0.6.1        01 June 2014 http://lilykde.googlecode.com/files/lilykde-0.6.1.tar.gz
lilypond                  2.20.0       07 October 2020 https://lilypond.org/download/sources/v2.20/lilypond-2.20.0.tar.gz
lilyterm                  0.9.9.4      01 July 2013 http://lilyterm.luna.com.tw/file/lilyterm-0.9.9.4.tar.gz
linc                      1.0.3        03 March 2015 http://hisham.hm/htop/releases/1.0.3/linc-1.0.3.tar.gz
lincityng                 2.0          01 January 2013 http://download.berlios.de/lincity-ng/lincity-ng-2.0.tar.bz2
lineakconfig              0.3.2        01 June 2014 http://prdownloads.sourceforge.net/lineak/lineakconfig-0.3.2.tar.gz
lineakd                   0.9          01 May 2014  http://prdownloads.sourceforge.net/lineak/lineakd-0.9.tar.gz
linkgrammar               5.2.5        28 September 2015 http://www.abiword.org/downloads/link-grammar/5.2.5/link-grammar-5.2.5.tar.gz
links                     2.29         21 March 2023 http://links.twibright.com/download/links-2.29.tar.bz2
linlibertine              5.3.0        01 June 2014 https://sourceforge.net/projects/linuxlibertine/files/linuxlibertine/5.3.0/LinLibertineSRC_5.3.0_2012_07_02.tgz
linux                     6.8.6        13 April 2024 https://www.kernel.org/pub/linux/kernel/v6.x/linux-6.8.6.tar.xz
linuxlive                 6.2.4        01 June 2014 ftp://ftp.slax.org/Linux-Live/linux-live-6.2.4.tar.gz
linuxpam                  1.6.1        13 April 2024 https://github.com/linux-pam/linux-pam/releases/download/v1.6.1/Linux-PAM-1.6.1.tar.xz
liquidwar                 5.6.5        23 November 2019 http://www.ufoot.org/download/liquidwar/v5/5.6.5/liquidwar-5.6.5.tar.gz
listen                    3.7.1        27 May 2022  https://rubygems.org/downloads/listen-3.7.1.gem
listmoreutils             0.428        17 December 2017 https://www.cpan.org/authors/id/R/RE/REHSACK/List-MoreUtils-0.428.tar.gz
listres                   1.0.6        04 March 2024 https://www.x.org/releases/individual/app/listres-1.0.6.tar.xz
littleutils               1.0.37       18 July 2017 https://sourceforge.net/projects/littleutils/files/littleutils-source/1.0.37/littleutils-1.0.37.tar.xz
lives                     3.0.2        28 September 2019 https://sourceforge.net/projects/lives/files/lives/3.0.2/lives-3.0.2.tar.bz2
liveslak                  1.1.9.1      01 October 2017 http://bear.alienbase.nl/cgit/liveslak/snapshot/liveslak-1.1.9.1.tar.xz
lksctptools               1.0.17       14 October 2018 https://sourceforge.net/projects/lksctp/files/lksctp-tools/lksctp-tools-1.0.17.tar.gz
llvm                      18.1.2       06 April 2023 https://github.com/llvm/llvm-project/releases/download/llvmorg-18.1.2/llvm-18.1.2tar.xz
lmarbles                  1.0.8        26 March 2016 https://sourceforge.net/projects/lgames/files/lmarbles/lmarbles-1.0.8.tar.gz
lmsensors                 3.6.0        08 December 2019 https://github.com/lm-sensors/lm-sensors/archive/V3-6-0/lm-sensors-3-6-0.tar.gz
lndir                     1.0.5        25 March 2024 https://www.x.org/releases/individual/util/lndir-1.0.5.tar.xz
log4cplus                 2.1.1        18 March 2024 https://github.com/log4cplus/log4cplus/releases/download/REL_2_1_1/log4cplus-2.1.1.tar.xz
log4cpp                   1.1.2rc1     08 December 2015 https://sourceforge.net/projects/log4cpp/files/log4cpp-1.1.x%20%28new%29/log4cpp-1.1/log4cpp-1.1.2rc1.tar.gz
log4r                     1.1.10       25 November 2019 https://rubygems.org/downloads/log4r-1.1.10.gem
logrotate                 3.18.1       22 May 2021  https://github.com/logrotate/logrotate/releases/download/3.18.1/logrotate-3.18.1.tar.xz
lokalize                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/lokalize-23.08.5.tar.xz
lollypop                  1.2.20       23 January 2020 https://adishatz.org/lollypop/lollypop-1.2.20.tar.xz
longomatch                1.0.2        28 February 2015 http://ftp.gnome.org/pub/GNOME/sources/longomatch/1.0/longomatch-1.0.2.tar.xz
loofah                    2.18.0       27 May 2022  https://rubygems.org/downloads/loofah-2.18.0.gem
loopaes                   v3.7d        25 July 2015 http://sourceforge.net/projects/loop-aes/files/loop-aes/v3.7d/loop-AES-v3.7d.tar.bz2
lordsawar                 0.2.0        01 June 2014 http://download.savannah.gnu.org/releases-noredirect/lordsawar/lordsawar-0.2.0.tar.gz
loudmouth                 1.5.4        27 January 2021 https://github.com/mcabber/loudmouth/releases/download/1.5.4/loudmouth-1.5.4.tar.bz2
lpairs                    1.0.5        12 May 2019  http://prdownloads.sourceforge.net/lgames/lpairs-1.0.5.tar.gz
lpairs2                   2.1          15 July 2019 https://sourceforge.net/projects/lgames/files/lpairs2/lpairs2-2.1.tar.gz
lrzip                     0.650        02 March 2022 http://ck.kolivas.org/apps/lrzip/lrzip-0.650.tar.xz
lrzsz                     0.12.20      13 July 2017 https://ohse.de/uwe/releases/lrzsz-0.12.20.tar.gz
lsdvd                     0.17         15 November 2015 https://sourceforge.net/projects/lsdvd/files/lsdvd/
lshw                      B.02.19.2    11 September 2022 https://www.ezix.org/software/files/lshw-B.02.19.2.tar.gz
lshwd                     05.04.2024   01 June 2014 https://github.com/bbidulock/lshwd/lshwd-05.04.2024.tar.xz
lskat                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/lskat-23.08.5.tar.xz
lsof                      4.95.0.linux 31 October 2015 https://github.com/lsof-org/lsof/releases/download/4.95.0/lsof_4.95.0.linux.tar.bz2
lsscsi                    0.31         23 February 2020 http://sg.danny.cz/scsi/lsscsi-0.31.tgz
ltris                     1.2.3        02 April 2022 http://prdownloads.sourceforge.net/lgames/ltris-1.2.3.tar.gz
lua                       5.4.6        14 May 2023  https://www.lua.org/ftp/lua-5.4.6.tar.gz
luajit                    2.0.5        09 October 2017 http://luajit.org/download/LuaJIT-2.0.5.tar.gz
luarocks                  3.5.0        28 March 2021 https://luarocks.org/releases/luarocks-3.5.0.tar.gz
luit                      1.1.1        01 November 2012 https://www.x.org/releases/individual/app/luit-1.1.1.tar.bz2
lumina                    1.5.0        30 April 2019 https://github.com/lumina-desktop/lumina/archive/lumina-1.5.0.tar.gz
lxappearance              0.6.3        06 October 2017 https://sourceforge.net/projects/lxde/files/LXAppearance/lxappearance-0.6.3.tar.xz
lxc                       4.0.10       05 August 2021 https://linuxcontainers.org/downloads/lxc/lxc-4.0.10.tar.gz
lxdecommon                0.99.2       24 February 2017 https://sourceforge.net/projects/lxde/files/lxde-common%20%28default%20config%29/lxde-common%200.99/lxde-common-0.99.2.tar.xz
lxdm                      0.5.3        24 February 2017 https://sourceforge.net/projects/lxde/files/lxdm/lxdm%200.5.3/lxdm-0.5.3.tar.xz
lxdvdrip                  1.60         01 June 2014 http://lxdvdrip.berlios.de/
lximageqt                 0.16.0       07 November 2020 https://github.com/lxqt/lximage-qt/releases/download/0.16.0/lximage-qt-0.16.0.tar.xz
lxml                      5.2.1        04 April 2024 https://files.pythonhosted.org/packages/ea/e2/3834472e7f18801e67a3cd6f3c203a5456d6f7f903cfb9a990e62098a2f3/lxml-5.2.1.tar.gz
lxpanel                   0.10.1       07 February 2021 http://downloads.sourceforge.net/lxde/lxpanel-0.10.1.tar.xz
lxqtabout                 1.1.0        30 August 2022 https://github.com/lxqt/lxqt-about/releases/download/1.1.0/lxqt-about-1.1.0.tar.xz
lxqtadmin                 1.1.0        30 August 2022 https://github.com/lxqt/lxqt-admin/releases/download/1.1.0/lxqt-admin-1.1.0.tar.xz
lxqtarchiver              0.9.1        25 February 2024 https://github.com/lxqt/lxqt-archiver/releases/download/0.9.1/lxqt-archiver-0.9.1.tar.xz
lxqtbuildtools            0.13.0       02 February 2024 https://github.com/lxqt/lxqt-build-tools/releases/download/0.13.0/lxqt-build-tools-0.13.0.tar.xz
lxqtconfig                1.1.0        12 September 2022 https://github.com/lxqt/lxqt-config/releases/download/1.1.0/lxqt-config-1.1.0.tar.xz
lxqtglobalkeys            0.16.0       07 November 2020 https://github.com/lxqt/lxqt-globalkeys/releases/download/0.16.0/lxqt-globalkeys-0.16.0.tar.xz
lxqtl10n                  0.13.0       17 January 2019 https://downloads.lxqt.org/downloads/lxqt-l10n/0.13.0/lxqt-l10n-0.13.0.tar.xz
lxqtnotificationd         0.16.0       07 November 2020 https://github.com/lxqt/lxqt-notificationd/releases/download/0.16.0/lxqt-notificationd-0.16.0.tar.xz
lxqtopensshaskpass        0.16.0       07 November 2020 https://github.com/lxqt/lxqt-openssh-askpass/releases/download/0.16.0/lxqt-openssh-askpass-0.16.0.tar.xz
lxqtpanel                 1.4.0        05 November 2023 https://github.com/lxde/lxqt-panel/releases/download/1.4.0/lxqt-panel-1.4.0.tar.xz
lxqtpolicykit             0.16.0       07 November 2020 https://github.com/lxqt/lxqt-policykit/releases/download/0.16.0/lxqt-policykit-0.16.0.tar.xz
lxqtpowermanagement       0.16.0       07 November 2020 https://github.com/lxqt/lxqt-powermanagement/releases/download/0.16.0/lxqt-powermanagement-0.16.0.tar.xz
lxqtqtplugin              0.16.0       07 November 2020 https://github.com/lxqt/lxqt-qtplugin/releases/download/0.16.0/lxqt-qtplugin-0.16.0.tar.xz
lxqtrunner                0.16.0       07 November 2020 https://github.com/lxqt/lxqt-runner/releases/download/0.16.0/lxqt-runner-0.16.0.tar.xz
lxqtsession               0.17.1       16 April 2021 https://github.com/lxqt/lxqt-session/releases/download/0.17.1/lxqt-session-0.17.1.tar.xz
lxqtsudo                  0.16.0       07 November 2020 https://github.com/lxqt/lxqt-sudo/releases/download/0.16.0/lxqt-sudo-0.16.0.tar.xz
lxqtthemes                1.1.0        30 August 2022 https://github.com/lxqt/lxqt-themes/releases/download/1.1.0/lxqt-themes-1.1.0.tar.xz
lxsession                 0.5.5        02 March 2020 https://downloads.sourceforge.net/lxde/lxsession-0.5.5.tar.xz
lxterminal                0.4.0        07 February 2021 https://sourceforge.net/projects/lxde/files/LXTerminal%20%28terminal%20emulator%29/LXTerminal%200.4.x/lxterminal-0.4.0.tar.xz
lyntin                    4.2          01 June 2014 https://sourceforge.net/projects/lyntin/files/lyntin/4.2/lyntin-4.2.tar.gz
lynx                      2.9.0        17 March 2024 https://invisible-mirror.net/archives/lynx/tarballs/lynx2.9.0.tar.bz2
lyx                       2.3.6.1      04 January 2021 ftp://ftp.lyx.org/pub/lyx/stable/2.3.x/lyx-2.3.6.1.tar.xz
lz4                       20.03.2024   07 April 2024 https://github.com/lz4/lz4/releases/download/v1.9.4/lz4-1.9.4.tar.gz
lzip                      1.24.1       02 March 2024 https://download.savannah.gnu.org/releases/lzip/lzip-1.24.1.tar.lz
lzlib                     1.13         28 January 2022 http://download-mirror.savannah.gnu.org/releases/lzip/lzlib/lzlib-1.13.tar.gz
lzma                      4.32.7       01 December 2012 http://tukaani.org/lzma/lzma-4.32.7.tar.bz2
lzo                       2.10         07 January 2018 http://www.oberhumer.com/opensource/lzo/download/lzo-2.10.tar.gz
m17nlib                   1.7.0        03 January 2018 http://download.savannah.gnu.org/releases/m17n/m17n-lib-1.7.0.tar.gz
m2crypto                  0.36.0       16 July 2020 https://files.pythonhosted.org/packages/ff/df/84609ed874b5e6fcd3061a517bf4b6e4d0301f553baf9fa37bef2b509797/M2Crypto-0.36.0.tar.gz
m4                        1.4.19       29 May 2021  https://ftp.gnu.org/gnu/m4/m4-1.4.19.tar.xz
madplay                   0.15.2b      07 December 2019 ftp://ftp.mars.org/pub/mpeg/madplay-0.15.2b.tar.gz
madwifi                   0.9.4        01 June 2014 http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.bz2
mafft                     7.505        07 April 2023 https://mafft.cbrc.jp/alignment/software/mafft-7.505-with-extensions.tgz
magenta                   2.1.3        02 April 2021 https://files.pythonhosted.org/packages/f8/42/3d6443d3f93aebf88c10caaa32697fa5c350a6bada76ac6810e3cd94b5eb/magenta-2.1.3.tar.gz
mail                      2.7.1        14 October 2018 https://rubygems.org/downloads/mail-2.7.1.gem
mailcommon                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/mailcommon-23.08.5.tar.xz
mailimporter              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/mailimporter-23.08.5.tar.xz
mailman                   2.1.38       01 December 2021 https://ftp.gnu.org/pub/gnu/mailman/mailman-2.1.38.tgz
mailutils                 3.13         05 August 2021 https://ftp.gnu.org/pub/gnu/mailutils/mailutils-3.13.tar.xz
make                      4.4.1        27 February 2023 https://ftp.gnu.org/gnu/make/make-4.4.1.tar.lz
makedepend                1.0.9        12 February 2024 https://www.x.org/releases/individual/util/makedepend-1.0.9.tar.xz
mako                      1.3.3        13 April 2024 https://files.pythonhosted.org/packages/0a/dc/48e8853daf4b32748d062ce9cd47a744755fb60691ebc211ca689b849c1c/Mako-1.3.3.tar.gz
mandb                     2.12.1       05 April 2024 https://download.savannah.nongnu.org/releases/man-db/man-db-2.12.1.tar.xz
mandvd                    2.4          01 June 2014 http://csgib36.ifrance.com/FTP/mandvd-2.4.tar.gz
manpages                  6.7          19 March 2024 https://www.kernel.org/pub/linux/docs/man-pages/man-pages-6.7.tar.xz
mantisbt                  1.2.5        08 March 2015 http://sourceforge.net/projects/mantisbt/files/mantis-stable/1.2.5/mantisbt-1.2.5.tar.gz
mapacman                  1.00         01 January 2013 http://prdownloads.sourceforge.net/arianne/mapacman-1.00.tar.gz
mapmvideo                 5.32         01 May 2012  http://sourceforge.net/project/showfiles.php?group_id=215566/mapmvideo-5.32.tar.gz
marble                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/marble-23.08.5.tar.xz
marcel                    1.0.2        27 May 2022  https://rubygems.org/downloads/marcel-1.0.2.gem
marco                     1.28.1       19 February 2024 https://pub.mate-desktop.org/releases/1.28/marco-1.28.1.tar.xz
mariadb                   11.0.4       14 November 2023 https://ftp.osuosl.org/pub/mariadb/mariadb-11.0.4/source/mariadb-11.0.4.tar.gz
markdown                  3.6          18 March 2024 https://files.pythonhosted.org/packages/22/02/4785861427848cc11e452cc62bb541006a1087cf04a1de83aedd5530b948/Markdown-3.6.tar.gz
markdownpart              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/markdownpart-23.08.5.tar.xz
markupsafe                2.1.5        08 February 2024 https://files.pythonhosted.org/packages/87/5b/aae44c6655f3801e81aa3eef09dbbf012431987ba564d7231722f68df02d/MarkupSafe-2.1.5.tar.gz
mars                      0.2.1        01 December 2012 http://www.marsnomercy.org/cms2/
massxpert                 3.6.0        12 December 2015 http://download.tuxfamily.org/massxpert/source/massxpert_3.6.0.tar.gz
mateapplets               1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-applets-1.28.0.tar.xz
matebackgrounds           1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-backgrounds-1.28.0.tar.xz
matecalc                  1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-calc-1.28.0.tar.xz
matecommon                1.28.0       13 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-common-1.28.0.tar.xz
matecontrolcenter         1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-control-center-1.28.0.tar.xz
matedesktop               1.28.2       12 March 2024 https://pub.mate-desktop.org/releases/1.28/mate-desktop-1.28.2.tar.xz
mateicontheme             1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-icon-theme-1.28.0.tar.xz
mateiconthemefaenza       1.20.0       07 February 2018 https://pub.mate-desktop.org/releases/1.20/mate-icon-theme-faenza-1.20.0.tar.xz
mateindicatorapplet       1.28.0       25 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-indicator-applet-1.28.0.tar.xz
matemedia                 1.28.0       21 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-media-1.28.0.tar.xz
matemenus                 1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-menus-1.28.0.tar.xz
matenetbook               1.26.0       20 August 2021 https://pub.mate-desktop.org/releases/1.26/mate-netbook-1.26.0.tar.xz
matenotificationdaemon    1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-notification-daemon-1.28.0.tar.xz
matepanel                 1.28.1       05 April 2024 https://pub.mate-desktop.org/releases/1.28/mate-panel-1.28.1.tar.xz
matepolkit                1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-polkit-1.28.0.tar.xz
matepowermanager          1.28.0       21 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-power-manager-1.28.0.tar.xz
matescreensaver           1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-screensaver-1.28.0.tar.xz
matesensorsapplet         1.26.0       20 August 2021 https://pub.mate-desktop.org/releases/1.26/mate-sensors-applet-1.26.0.tar.xz
matesessionmanager        1.28.0       19 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-session-manager-1.28.0.tar.xz
matesettingsdaemon        1.26.1       23 January 2024 https://pub.mate-desktop.org/releases/1.26/mate-settings-daemon-1.26.1.tar.xz
matesystemmonitor         1.28.1       01 March 2024 https://pub.mate-desktop.org/releases/1.28/mate-system-monitor-1.28.1.tar.xz
mateterminal              1.28.1       24 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-terminal-1.28.1.tar.xz
matethemes                3.22.26      09 April 2024 https://pub.mate-desktop.org/releases/themes/3.22/mate-themes-3.22.26.tar.xz
mateuserguide             1.24.0       10 February 2020 https://pub.mate-desktop.org/releases/1.24/mate-user-guide-1.24.0.tar.xz
mateusershare             1.26.0       20 August 2021 https://pub.mate-desktop.org/releases/1.26/mate-user-share-1.26.0.tar.xz
mateutils                 1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/mate-utils-1.28.0.tar.xz
mathomatic                15.8.4       01 June 2014 http://mathomatic.org/mathomatic-15.8.4.tar.bz2
matplotlib                3.7.1        21 March 2023 https://files.pythonhosted.org/packages/b7/65/d6e00376dbdb6c227d79a2d6ec32f66cfb163f0cd924090e3133a4f85a11/matplotlib-3.7.1.tar.gz
maxemumtvguide            7.3.2        01 June 2014 http://sourceforge.net/projects/mtvg/files/mtvg/7.3.2/maxemumtvguide-7.3.2.tar.gz
maxima                    5.46.0       10 April 2023 https://sourceforge.net/projects/maxima/files/Maxima-source/5.46.0-source/maxima-5.46.0.tar.gz
mboximporter              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/mbox-importer-23.08.5.tar.xz
mc                        4.8.31       27 January 2024 https://www.midnight-commander.org/downloads/mc-4.8.31.tar.xz
mcabber                   1.1.0        25 October 2018 https://mcabber.com/files/mcabber-1.1.0.tar.bz2
mcelog                    176          22 July 2021 https://git.kernel.org/pub/scm/utils/cpu/mce/mcelog.git/snapshot/mcelog-176.tar.gz
mcron                     1.2.3        27 March 2023 https://ftp.gnu.org/pub/gnu/mcron/mcron-1.2.3.tar.gz
mcs                       0.4.1        01 June 2014 mcs-0.4.1
mcsim                     6.2.0        04 June 2020 http://ftp.gnu.org/pub/gnu/mcsim/mcsim-6.2.0.tar.gz
mdadm                     4.3          05 March 2024 https://mirrors.edge.kernel.org/pub/linux/utils/raid/mdadm/mdadm-4.3.tar.xz
meanwhile                 1.0.2        01 June 2014 https://sourceforge.net/projects/meanwhile/files/meanwhile/1.0.2/meanwhile-1.0.2.tar.gz
mechanize                 2.9.0        10 April 2023 https://rubygems.org/downloads/mechanize-2.9.0.gem
mediatomb                 0.12.1       01 June 2014 https://sourceforge.net/projects/mediatomb/files/MediaTomb/0.12.1/mediatomb-0.12.1.tar.gz
mediawiki                 1.25.1       28 May 2015  http://releases.wikimedia.org/mediawiki/1.25/mediawiki-1.25.1.tar.gz
medit                     1.2.0        09 May 2017  https://sourceforge.net/projects/mooedit/files/medit/1.2.0/medit-1.2.0.tar.bz2
megapov                   1.2.1        01 January 2013 http://megapov.inetart.net/packages/unix/megapov-1.2.1.tar.bz2
megatools                 1.10.3       18 June 2020 https://megatools.megous.com/builds/megatools-1.10.3.tar.gz
meld                      3.22.2       24 March 2024 https://download.gnome.org/sources/meld/3.22/meld-3.22.2.tar.xz
melons                    1.1.1        01 June 2014 http://www.imitationpickles.org/melons/melons-1.1.1.tgz
meme                      5.0.3        19 January 2019 http://meme-suite.org/meme-software/5.0.3/meme-5.0.3.tar.gz
memtester                 4.5.1        15 September 2022 https://pyropus.ca./software/memtester/old-versions/memtester-4.5.1.tar.gz
menucache                 1.1.0        11 November 2017 https://downloads.sourceforge.net/lxde/menu-cache-1.1.0.tar.xz
merb                      1.1.3        26 November 2019 https://rubygems.org/downloads/merb-1.1.3.gem
mercurial                 6.7.2        30 March 2024 https://www.mercurial-scm.org/release/mercurial-6.7.2.tar.gz
merkuro                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/merkuro-23.08.5.tar.xz
mesa                      24.0.5       11 April 2024 https://mesa.freedesktop.org/archive/mesa-24.0.5.tar.xz
mesademos                 6.5          01 June 2014 http://mesh.dl.sourceforge.net/sourceforge/mesa3d/MesaDemos-6.5.tar.bz2
mesaglut                  7.10         01 June 2014 ftp://ftp.freedesktop.org/pub/mesa/7.10/MesaGLUT-7.10.tar.bz2
mesk                      0.1.0        01 June 2014 http://mesk.nicfit.net/releases/mesk-0.1.0.tgz
meson                     1.4.0        13 March 2024 https://files.pythonhosted.org/packages/9a/bd/4843c2d8ce8395463b4cf843e81bf162f1757bfc4244fbc827dcdf633cb1/meson-1.4.0.tar.gz
messagelib                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/messagelib-23.08.5.tar.xz
metacity                  3.52.0       21 March 2024 https://download.gnome.org/sources/metacity/3.52/metacity-3.52.0.tar.xz
metaclass                 0.0.4        04 August 2018 https://rubygems.org/downloads/metaclass-0.0.4.gem
methodsource              1.0.0        28 May 2020  https://rubygems.org/downloads/method_source-1.0.0.gem
mftrace                   1.2.14       01 June 2013 http://www.xs4all.nl/~hanwen/mftrace/mftrace-1.2.14.tar.gz
mgaview                   0.0.30       01 June 2014 http://sourceforge.net/projects/mgaview/mgaview-0.0.30
midieye                   0.3.10       13 December 2019 https://rubygems.org/downloads/midi-eye-0.3.10.gem
midilib                   2.0.5        16 June 2015 https://rubygems.org/downloads/midilib-2.0.5.gem
midillo                   0.0          01 June 2014 http://kin.klever.net/konforka/
midori                    0.5.1        01 February 2012 http://archive.xfce.org/src/apps/midori/0.5/midori-0.5.1.tar.bz2
milkytracker              0.90.85      01 June 2014 http://milkytracker.org/files/milkytracker-0.90.85.tar.bz2
milou                     5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/milou-5.27.9.tar.xz
mimemagic                 0.4.3        15 April 2021 https://rubygems.org/downloads/mimemagic-0.4.3.gem
mimetypes                 3.4.1        27 May 2022  https://rubygems.org/downloads/mime-types-3.4.1.gem
mimetypesdata             3.2022.0105  27 May 2022  https://rubygems.org/downloads/mime-types-data-3.2022.0105.gem
ming                      =18365&.=187304&.=611489 01 June 2014 http://sourceforge.net/project/showfiles.php?group_id=18365&package_id=187304&release_id=611489
mingetty                  1.07.        01 June 2014 http://ftp.de.debian.org/debian/pool/main/m/mingetty/mingetty-1.07.orig.tar.gz
minimagick                4.11.0       15 April 2021 https://rubygems.org/downloads/mini_magick-4.11.0.gem
minimap2                  2.17         08 January 2021 https://github.com/lh3/minimap2/releases/download/v2.17/minimap2-2.17.tar.bz2
minimime                  1.1.2        27 May 2022  https://rubygems.org/downloads/mini_mime-1.1.2.gem
miniportile2              2.8.0        27 May 2022  https://rubygems.org/downloads/mini_portile2-2.8.0.gem
minit                     0.10         03 March 2015 http://hisham.hm/htop/releases/1.0.3/minit-0.10.tar.xz
minitar                   0.9          28 May 2020  https://rubygems.org/downloads/minitar-0.9.gem
minitest                  5.16.1       22 June 2022 https://rubygems.org/downloads/minitest-5.16.1.gem
minitestsprint            1.2.2        22 June 2022 https://rubygems.org/downloads/minitest-sprint-1.2.2.gem
minizipng                 3.0.8        13 February 2023 https://github.com/zlib-ng/minizip-ng/
minuet                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/minuet-23.08.5.tar.xz
mirage                    0.8          01 June 2014 http://raschix.de/article/mirage-image-viewer
missile                   1.0.1        01 June 2014 http://missile.sourceforge.net/dl/missile-1.0.1.tar.gz
mjpegtools                2.2.1        01 March 2023 https://sourceforge.net/projects/mjpeg/files/mjpegtools/2.2.1/mjpegtools-2.2.1.tar.gz
mkcfm                     1.0.1        01 June 2014 http://xorg.freedesktop.org/releases/individual/app/mkcfm-1.0.1.tar.bz2
mkcomposecache            1.2.2        04 April 2022 https://www.x.org/releases/individual/app/mkcomposecache-1.2.2.tar.xz
mkfontdir                 1.0.7        01 June 2014 http://xorg.freedesktop.org/releases/individual/app/mkfontdir-1.0.7.tar.bz2
mkfontscale               1.2.3        04 March 2024 https://www.x.org/releases/individual/app/mkfontscale-1.2.3.tar.xz
mkrf                      0.2.3        29 November 2017 https://rubygems.org/downloads/mkrf-0.2.3.gem
mktemp                    1.7          01 December 2012 https://www.mktemp.org/dist/mktemp-1.7.tar.gz
mkvtoolnix                41.0.0       01 February 2020 https://mkvtoolnix.download/sources/mkvtoolnix-41.0.0.tar.xz
mlr                       4.4.0        14 August 2016 https://github.com/johnkerl/miller/releases/download/v4.4.0/mlr-4.4.0.tar.gz
mlt                       23.03.2024   03 December 2023 https://github.com/mltframework/mlt/releases/download/v7.22.0/mlt-7.22.0.tar.gz
mmcommon                  1.0.5        03 December 2022 https://download.gnome.org/sources/mm-common/1.0/mm-common-1.0.5.tar.xz
mobs                      2.3.2        01 June 2014 http://www.dervishd.net/Projects/mobs-2.3.2.tar.gz
moc                       2.5.2        09 June 2017 http://ftp.daper.net/pub/soft/moc/stable/moc-2.5.2.tar.bz2
mocha                     1.14.0       27 May 2022  https://rubygems.org/downloads/mocha-1.14.0.gem
modemmanager              1.18.4       27 November 2021 https://www.freedesktop.org/software/ModemManager/ModemManager-1.18.4.tar.xz
modemmanagerqt            5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/modemmanager-qt-5.115.0.tar.xz
modmono                   1.2.5        01 June 2014 http://go-mono.com/sources/mod_mono/mod_mono-1.2.5.tar.bz2
modperl                   2.0.11       06 October 2019 http://archive.apache.org/dist/perl/mod_perl-2.0.11.tar.gz
modpython                 3.5.0        31 October 2017 http://dist.modpython.org/dist/mod_python-3.5.0.tgz
modulebuild               0.4224       13 October 2018 https://cpan.metacpan.org/authors/id/L/LE/LEONT/Module-Build-0.4224.tar.gz
moduleinittools           3.16         01 June 2014 ftp://ftp.kernel.org/pub/linux/utils/kernel/module-init-tools/module-init-tools-3.16.tar.bz2
modulemd                  1.3.3        12 July 2020 https://files.pythonhosted.org/packages/7c/e3/b066246183455e8437774bb4408ef3f61f23adfca52efab6285160299378/modulemd-1.3.3.tar.gz
modules                   3.2.10       27 August 2015 https://sourceforge.net/projects/modules/files/Modules/modules-3.2.10/modules-3.2.10.tar.bz2
moe                       1.10         12 April 2023 https://github.com/fox0430/moe/archive/refs/tags/moe-1.10.tar.gz
mojolicious               2.0          01 January 2013 http://cpan.metacpan.org/authors/id/S/SR/SRI/Mojolicious-2.0.tar.gz
momomoto                  0.2.1        01 December 2017 https://rubygems.org/downloads/momomoto-0.2.1.gem
moneta                    1.5.1        27 May 2022  https://rubygems.org/downloads/moneta-1.5.1.gem
money                     6.16.0       27 May 2022  https://rubygems.org/downloads/money-6.16.0.gem
mongodb                   r3.4.6       20 April 2015 https://fastdl.mongodb.org/src/mongodb-r3.4.6.tar.gz
mongrel                   1.1.5        01 August 2017 https://rubygems.org/downloads/mongrel-1.1.5.gem
mongrel2                  v1.10.0      22 December 2015 https://github.com/mongrel2/mongrel2/releases/download/v1.10.0/mongrel2-v1.10.0.tar.bz2
monit                     5.33.0       14 April 2023 https://mmonit.com/monit/dist/monit-5.33.0.tar.gz
mono                      6.13.0.1255  04 December 2022 https://download.mono-project.com/sources/mono/nightly/mono-6.13.0.1255.tar.xz
monoaddins                0.4          01 June 2014 http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.4.tar.bz2
monodevelop               7.8.4.1      28 September 2019 https://download.mono-project.com/sources/monodevelop/monodevelop-7.8.4.1.tar.bz2
monsterz                  0.7.1        10 October 2017 http://sam.zoy.org/monsterz/monsterz-0.7.1.tar.gz
moodle                    3.4          08 December 2017 https://sourceforge.net/projects/moodle/files/Moodle/stable34/moodle-3.4.tgz
moonbuggy                 1.0.51       24 March 2016 http://m.seehuhn.de/programs/moon-buggy-1.0.51.tar.gz
moserial                  3.0.21       27 November 2021 https://download.gnome.org/sources/moserial/3.0/moserial-3.0.21.tar.xz
mosh                      1.3.2        07 April 2019 https://mosh.org/mosh-1.3.2.tar.gz
most                      5.0.0        01 June 2014 ftp://space.mit.edu/pub/davis/most/most-5.0.0a.tar.bz2
motif                     2.3.8        09 December 2017 https://sourceforge.net/projects/motif/files/Motif%202.3.8%20Source%20Code/motif-2.3.8.tar.gz
mousepad                  0.6.0        11 February 2023 https://archive.xfce.org/src/apps/mousepad/0.6/mousepad-0.6.0.tar.bz2
mousetrap                 3.17.3       23 June 2015 http://ftp.gnome.org/pub/GNOME/sources/mousetrap/3.17/mousetrap-3.17.3.tar.xz
mozart2                   13.12.2015   13 December 2015 http://www.mozart-oz.org/download/mozart-ftp/store/1.3.1-2004-06-16/mozart2-13.12.2015.tar.xz
firefox                   115.9.1      11 April 2024 https://archive.mozilla.org/pub/firefox/releases/115.9.1esr/source/firefox-115.9.1esr.source.tar.xz
mozo                      1.26.2       02 November 2022 https://pub.mate-desktop.org/releases/1.26/mozo-1.26.2.tar.xz
mp                        5.2.2        01 June 2014 http://triptico.com/download/mp-5.2.2.tar.gz
mp3blaster                3.2.6        17 November 2017 https://sourceforge.net/projects/mp3blaster/files/mp3blaster/mp3blaster-3.2.6/mp3blaster-3.2.6.tar.gz
mp3cat                    0.4          01 June 2014 http://tomclegg.net/software/mp3cat-0.4.tar.gz
mp3daemon                 0.63         01 May 2014  http://search.cpan.org/CPAN/authors/id/B/BE/BEPPU/MP3-Daemon-0.63.tar.gz
mp3diags                  1.0.12.079   01 January 2013 http://sourceforge.net/projects/mp3diags/files/mp3diags/MP3Diags-1.0.12.079.tar.gz
mp3gain                   1.6.2        10 May 2020  https://sourceforge.net/projects/mp3gain/files/mp3gain/1.6.2/mp3gain-1_6_2.zip
mp3info                   0.8.5        01 June 2014 ftp://ftp.ibiblio.org/pub/linux/apps/sound/mp3-utils/mp3info/mp3info-0.8.5.tgz
mp3splt                   2.4.2        01 June 2014 http://downloads.sourceforge.net/project/mp3splt/mp3splt/2.4.2/mp3splt-2.4.2.tar.gz
mp3val                    0.1.8        01 January 2013 http://downloads.sourceforge.net/mp3val/mp3val-0.1.8.tar.gz
mp3wrap                   0.5          01 June 2014 http://prdownloads.sourceforge.net/mp3wrap/mp3wrap-0.5.tar.gz
mpage                     2.5.6        07 February 2016 http://www.mesa.nl/pub/mpage/mpage-2.5.6.tgz
mpc                       1.3.1        16 December 2022 https://ftp.gnu.org/pub/gnu/mpc/mpc-1.3.1.tar.gz
mpd                       0.21.25      31 August 2020 http://www.musicpd.org/download/mpd/0.21/mpd-0.21.25.tar.xz
mpdecimal                 4.0.0        27 March 2024 https://www.bytereef.org/software/mpdecimal/releases/mpdecimal-4.0.0.tar.gz
mpeg2dec                  0.4.1        01 June 2014 https://libmpeg2.sourceforge.net/files/mpeg2dec-0.4.1.tar.gz
mpeg4ip                   1.5.0.1      01 June 2014 http://wiki.ubuntuusers.de/Archiv/mpeg4ip-1.5.0.1
mpfr                      4.2.1        22 August 2023 https://ftp.gnu.org/pub/gnu/mpfr/mpfr-4.2.1.tar.xz
mpg123                    1.32.6       06 April 2024 http://www.mpg123.de/download/mpg123-1.32.6.tar.bz2
mpg321                    0.2.13.3     01 June 2014 https://sourceforge.net/projects/mpg321/files/mpg321/0.2.13/mpg321-0.2.13.3.tar.gz
mpgedit                   0.75dev2     01 June 2014 http://mpgedit.org/mpgedit/download/0_75/mpgedit_0-75dev2_src.tgz
mpgtx                     1.3.1        01 June 2014 http://ovh.dl.sourceforge.net/sourceforge/mpgtx/mpgtx-1.3.1.tgz
mplayer                   1.5          28 February 2022 https://mplayerhq.hu/MPlayer/releases/MPlayer-1.5.tar.xz
mpmath                    1.2.1        12 June 2021 https://files.pythonhosted.org/packages/95/ba/7384cb4db4ed474d4582944053549e02ec25da630810e4a23454bc9fa617/mpmath-1.2.1.tar.gz
mpop                      1.4.3        12 February 2019 https://marlam.de/mpop/releases/mpop-1.4.3.tar.xz
mppenc                    1.16         01 June 2014 http://files.musepack.net/source/mppenc-1.16.tar.bz2
mpv                       05.04.2024   05 April 2024 https://github.com/mpv-player/mpv/archive/refs/tags/v0.37.0.tar.gz
mrepo                     0.8.4        01 June 2014 http://dag.wieers.com/home-made/mrepo/
mruby                     2.1.1        06 June 2020 https://github.com/mruby/mruby/archive/2.1.1.tar.gz
mrxvt                     0.5.4        01 June 2014 http://prdownloads.sourceforge.net/materm/mrxvt-0.5.4.tar.gz
msgpack                   3.2.0        05 December 2019 https://github.com/msgpack/msgpack-c/releases/download/cpp-3.2.0/msgpack-3.2.0.tar.gz
msitools                  0.102        25 June 2023 https://download.gnome.org/sources/msitools/0.102/msitools-0.102.tar.xz
msleep                    0.1.0        25 July 2009 https://rubygems.org/downloads/msleep-0.1.0.gem
msmtp                     1.8.1        09 December 2018 https://marlam.de/msmtp/releases/msmtp-1.8.1.tar.xz
mssys                     2.1.2        01 June 2014 http://ms-sys.sourceforge.net/
mtail                     1.1.1        01 January 2013 http://matt.immute.net/src/mtail/mtail-1.1.1.tgz
mtdev                     1.1.7        06 April 2024 http://bitmath.org/code/mtdev/mtdev-1.1.7.tar.bz2
mtools                    4.0.43       22 March 2023 https://ftp.gnu.org/pub/gnu/mtools/mtools-4.0.43.tar.bz2
mtpaint                   3.50         30 January 2021 https://sourceforge.net/projects/mtpaint/files/mtpaint/3.50/mtpaint-3.50.tar.bz2
mtr                       0.95         13 January 2022 ftp://ftp.bitwizard.nl/mtr/mtr-0.95.tar.gz
mudlet                    1.0.5        01 June 2014 mudlet-1.0.5.tar.gz
mudmagic                  1.9          01 June 2014 https://sourceforge.net/projects/kyndig/files/Mud%20Magic%20Source/1.9/mudmagic-1.9.tar.gz
multiaterm                0.2.1        01 June 2014 http://www.nongnu.org/materm/multi-aterm-0.2.1.tar.gz
multijson                 1.15.0       15 April 2021 https://rubygems.org/downloads/multi_json-1.15.0.gem
multipartpost             2.2.3        22 June 2022 https://rubygems.org/downloads/multipart-post-2.2.3.gem
mummer                    3.23         01 November 2013 https://sourceforge.net/projects/mummer/files/mummer/3.23/MUMmer3.23.tar.gz
muparser                  2.2.6.1      19 January 2019 https://github.com/beltoforion/muparser/archive/muparser-2.2.6.1.tar.gz
mupdf                     1.24.1       06 April 2024 https://www.mupdf.com/downloads/archive/mupdf-1.24.1-source.tar.gz
murmurhash3               0.1.7        22 March 2023 https://rubygems.org/downloads/murmurhash3-0.1.7.gem
muse                      2.2.1        25 September 2015 http://sourceforge.net/projects/lmuse/files/muse-2.2/muse-2.2.1.tar.gz
musepack                  r475         01 November 2012 http://files.musepack.net/source/musepack_src_r475.tar.gz
musescore                 3.0.1        17 January 2019 https://github.com/musescore/MuseScore/archive/musescore-3.0.1.tar.gz
musikcube                 0.61.0       14 January 2019 https://github.com/clangen/musikcube/archive/musikcube-0.61.0.tar.gz
musl                      1.2.3        02 August 2022 https://musl.libc.org/releases/musl-1.2.3.tar.gz
mustermann                1.1.1        28 May 2020  https://rubygems.org/downloads/mustermann-1.1.1.gem
mutagen                   1.43.0       04 December 2019 https://files.pythonhosted.org/packages/aa/fd/ed738775442e3614849fefdf41417d7bff3ccb010d49c8f729432cc3c1e5/mutagen-1.43.0.tar.gz
mutt                      2.2.13       09 March 2024 http://ftp.mutt.org/pub/mutt/mutt-2.2.13.tar.gz
mutter                    46.0         16 March 2024 https://download.gnome.org/sources/mutter/46/mutter-46.0.tar.xz
mxk                       1.10         01 June 2014 http://welz.org.za/projects/mxk/mxk-1.10.tar.gz
mxml                      3.2          07 March 2021 https://github.com/michaelrsweet/mxml/releases/download/v3.2/mxml-3.2.tar.gz
myghty                    1.0          01 June 2014 http://easynews.dl.sourceforge.net/sourceforge/myghty/Myghty-1.0.tar.gz
myman                     0.7.0        10 October 2017 https://sourceforge.net/projects/myman/files/myman/myman-0.7.0/myman-0.7.0.tar.gz
mypaint                   2.0.1        30 May 2020  https://github.com/mypaint/mypaint/releases/download/v2.0.1/mypaint-2.0.1.tar.xz
mypaintbrushes            2.0.2        22 June 2020 https://github.com/mypaint/mypaint-brushes/releases/download/v2.0.2/mypaint-brushes-2.0.2.tar.xz
mysql                     8.0.32       17 January 2023 https://cdn.mysql.com/Downloads/MySQL-8.0/mysql-8.0.32.tar.gz
mythplugins               0.20a        01 June 2014 http://www.mythtv.org/modules.php?name=Downloads&d_op=getit&lid=124/mythplugins-0.20a
nagios                    4.3.1        01 June 2014 https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.3.1.tar.gz#_ga=1.110313093.1455961778.1489835372
naim                      0.11.8.3.1   01 June 2014 http://naim.googlecode.com/files/naim-0.11.8.3.1.tar.bz2
najitool                  0.8.4        07 October 2017 https://sourceforge.net/projects/najitool/files/najitool/0.8.4/najitool-0.8.4tar.bz2
nana                      1.5.4        08 August 2017 https://sourceforge.net/projects/nanapro/files/Nana/Nana%201.x/nana%201.5.4.zip
nano                      7.2          18 January 2023 https://www.nano-editor.org/dist/latest/nano-7.2.tar.gz
nanomsg                   1.1.5        29 September 2019 https://github.com/nanomsg/nanomsg/archive/1.1.5.tar.gz
nap                       1.5.4        01 June 2014 http://nap.sourceforge.net/dist/nap-1.5.4.tar.gz
nas                       1.9.3        01 August 2013 http://sourceforge.net/projects/nas/files/nas/nas.1.9.3%20%28stable%29/nas-1.9.3tar.gz
nasm                      2.16.02      06 April 2024 https://www.nasm.us/pub/nasm/releasebuilds/2.16.02/nasm-2.16.02.tar.xz
nast                      0.2.0        05 June 2014 http://download.berlios.de/nast/nast-0.2.0.tar.gz
nativepackageinstaller    1.1.4        27 May 2022  https://rubygems.org/downloads/native-package-installer-1.1.4.gem
nautilus                  46.0         18 March 2024 https://download.gnome.org/sources/nautilus/46/nautilus-46.0.tar.xz
nautilusactions           3.2.4        01 August 2014 http://ftp.gnome.org/pub/GNOME/sources/nautilus-actions/3.2/nautilus-actions-3.2.4.tar.xz
nautiluscdburner          2.22.1       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/nautilus-cd-burner/2.22/nautilus-cd-burner-2.22.1.tar.bz2
nautilusmedia             0.8.1        01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/nautilus-media/0.8/nautilus-media-0.8.1.tar.bz2
nautiluspython            1.2.3        19 July 2019 http://ftp.gnome.org/pub/gnome/sources/nautilus-python/1.2/nautilus-python-1.2.3.tar.xz
nautilussendto            3.8.6        09 August 2017 http://ftp.gnome.org/pub/gnome/sources/nautilus-sendto/3.8/nautilus-sendto-3.8.6.tar.xz
nazghul                   0.7.1        31 March 2015 https://downloads.sourceforge.net/project/nazghul/nazghul/nazghul-0.7.1/nazghul-0.7.1.tar.gz
ncbiblast                 2.11.0+      26 April 2021 https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.11.0+.zip
ncbicxx                   22.0.0       19 April 2019 ftp://ftp.ncbi.nlm.nih.gov/toolbox/ncbi_tools++/2019/Mar_28_2019/ncbi_cxx--22_0_0.tar.gz
ncc                       2.8          01 June 2014 http://students.ceid.upatras.gr/~sxanth/ncc/ncc-2.8.tar.gz
ncdu                      1.19         05 April 2024 https://dev.yorhel.nl/download/ncdu-1.19.tar.gz
ncftp                     3.2.6        28 November 2016 ftp://ftp.ncftp.com/ncftp/ncftp-3.2.6.tar.xz
ncmpcpp                   0.5.10       01 June 2014 http://unkart.ovh.org/ncmpcpp/ncmpcpp-0.5.10.tar.bz2
ncompress                 4.2.4.5      29 April 2018 https://sourceforge.net/projects/ncompress/files/ncompress-4.2.4.5.tar.gz
ncurses                   6.4-20230520 01 January 2023 https://invisible-mirror.net/archives/ncurses/ncurses-6.4-20230520.tar.gz
ndeskdbus                 0.6.0        01 June 2014 http://www.ndesk.org/DBusSharp
ndeskdbusglib             0.4.1        01 February 2013 http://www.ndesk.org/archive/dbus-sharp/ndesk-dbus-glib-0.4.1.tar.gz
ndiswrapper               1.63         30 July 2020 https://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-1.63.tar.gz
nemesis                   1.5          22 February 2019 https://github.com/troglobit/nemesis/releases/download/v1.5/nemesis-1.5.tar.xz
nemiver                   0.9.6        24 September 2015 http://ftp.gnome.org/pub/GNOME/sources/nemiver/0.9/nemiver-0.9.6.tar.xz
neochat                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/neochat-23.08.5.tar.xz
neofetch                  7.0.0        23 June 2020 https://github.com/dylanaraps/neofetch/archive/neofetch-7.0.0.tar.gz
neon                      0.32.5       24 January 2023 https://fossies.org/linux/www/neon-0.32.5.tar.gz
net6                      1.3.14       16 December 2018 http://releases.0x539.de/net6/net6-1.3.14.tar.gz
netatalk                  3.1.12       22 December 2018 https://sourceforge.net/projects/netatalk/files/netatalk/3.1.12/netatalk-3.1.12.tar.gz
netcat                    0.7.1        01 June 2014 http://sourceforge.net/projects/netcat/files/netcat/0.7.1/netcat-0.7.1.tar.gz
netdns                    1.27         17 September 2020 https://www.cpan.org/authors/id/N/NL/NLNETLABS/Net-DNS-1.27.tar.gz
nethack                   3.6.2        20 October 2019 https://sourceforge.net/projects/nethack/files/nethack/3.6.2/nethack-3.6.2.tgz
nethttp                   6.17         27 September 2017 http://search.cpan.org/CPAN/authors/id/O/OA/OALDERS/Net-HTTP-6.17.tar.gz
netkitbase                0.17         01 June 2014 ftp://ftp.uk.linux.org/pub/linux/Networking/netkit/netkit-base-0.17.tar.gz
netkitrsh                 0.17         01 June 2014 ftp://ftp.uk.linux.org/pub/linux/Networking/netkit/netkit-rsh-0.17.tar.gz
netpbm                    10.73.35     09 April 2021 https://sourceforge.net/projects/netpbm/files/super_stable/10.73.35/netpbm-10.73.35.tgz
netping                   2.0.8        27 May 2022  https://rubygems.org/downloads/net-ping-2.0.8.gem
netrc                     0.11.0       29 September 2017 https://rubygems.org/downloads/netrc-0.11.0.gem
netscp                    3.0.0        28 May 2020  https://rubygems.org/downloads/net-scp-3.0.0.gem
nettle                    3.9.1        03 June 2023 https://ftp.gnu.org/pub/gnu/nettle/nettle-3.9.1.tar.gz
networkmanager            1.46.0       22 February 2024 https://download.gnome.org/sources/NetworkManager/1.46/NetworkManager-1.46.0.tar.xz
networkmanagerapplet      1.32.0       17 April 2023 https://download.gnome.org/sources/network-manager-applet/1.32/network-manager-applet-1.32.0.tar.xz
networkmanagerfortisslvpn 1.3.90       16 July 2019 http://ftp.gnome.org/pub/gnome/sources/NetworkManager-fortisslvpn/1.3/NetworkManager-fortisslvpn-1.3.90.tar.xz
networkmanagerlibreswan   1.2.10       15 October 2018 http://ftp.gnome.org/pub/gnome/sources/NetworkManager-libreswan/1.2/NetworkManager-libreswan-1.2.10.tar.xz
networkmanageropenconnect 1.2.2        14 May 2016  http://ftp.gnome.org/pub/GNOME/sources/NetworkManager-openconnect/1.2/NetworkManager-openconnect-1.2.2.tar.xz
networkmanageropenvpn     1.8.14       30 March 2021 https://download.gnome.org/sources/NetworkManager-openvpn/1.8/NetworkManager-openvpn-1.8.14.tar.xz
networkmanagerpptp        1.2.8        04 October 2018 http://ftp.gnome.org/pub/gnome/sources/NetworkManager-pptp/1.2/NetworkManager-pptp-1.2.8.tar.xz
networkmanagerqt          5.115.0      19 February 2024 https://download.kde.org/stable/frameworks/5.115/networkmanager-qt-5.115.0.tar.xz
networkmanagervpnc        1.2.6        20 July 2018 http://ftp.gnome.org/pub/gnome/sources/NetworkManager-vpnc/1.2/NetworkManager-vpnc-1.2.6.tar.xz
networkx                  2.3          12 April 2019 https://files.pythonhosted.org/packages/85/08/f20aef11d4c343b557e5de6b9548761811eb16e438cee3d32b1c66c8566b/networkx-2.3.zip
neverball                 1.6.0        27 March 2016 http://neverball.org/neverball-1.6.0.tar.gz
newlib                    2.0.0        01 June 2014 ftp://sourceware.org/pub/newlib/newlib-2.0.0.tar.gz
newrelicrpm               8.8.0        22 June 2022 https://rubygems.org/downloads/newrelic_rpm-8.8.0.gem
newsbeuter                2.9          03 October 2017 https://www.newsbeuter.org/downloads/newsbeuter-2.9.tar.gz
newt                      0.52.23      02 December 2022 https://releases.pagure.org/newt/newt-0.52.23.tar.gz
nfsutils                  2.6.2        11 August 2022 https://www.kernel.org/pub/linux/utils/nfs-utils/2.6.2/nfs-utils-2.6.2.tar.xz
nftables                  1.0.8        14 July 2023 https://www.nftables.org/projects/nftables/files/nftables-1.0.8.tar.xz
nghttp2                   1.61.0       05 April 2024 https://github.com/nghttp2/nghttp2/releases/download/v1.61.0/nghttp2-1.61.0.tar.xz
nginx                     1.24.0       12 April 2023 https://nginx.org/download/nginx-1.24.0.tar.gz
nglview                   3.0.8        28 October 2023 https://files.pythonhosted.org/packages/6a/3e/40ee8822c10bf8b00d037ede875ac2a1a26b07fae5e26fbd8af3404257e3/nglview-3.0.8.tar.gz
ngstar                    1.3.3        01 June 2014 http://cycojesus.free.fr/faire/coder/jouer/ng-star/files/
nihtest                   1.5.2        05 April 2024 https://github.com/nih-at/nihtest/releases/download/v1.5.2/nihtest-1.5.2.tar.gz
nim                       1.6.12       01 May 2023  https://nim-lang.org/download/nim-1.6.12.tar.xz
ninja                     1.11.1       01 September 2022 https://github.com/ninja-build/ninja/archive/refs/tags/v1.11.1.tar.gz
nio4r                     2.5.8        27 May 2022  https://rubygems.org/downloads/nio4r-2.5.8.gem
nmap                      7.93         02 September 2022 http://download.insecure.org/nmap/dist/nmap-7.93.tgz
node                      v20.12.2     11 April 2024 https://nodejs.org/dist/v20.12.2/node-v20.12.2.tar.gz
nokogiri                  1.13.8       04 September 2022 https://rubygems.org/downloads/nokogiri-1.13.8.gem
normalize                 0.7.7        01 June 2014 http://savannah.nongnu.org/download/normalize/normalize-0.7.7.tar.bz2
notificationdaemon        3.18.2       16 February 2016 http://ftp.gnome.org/pub/GNOME/sources/notification-daemon/3.18/notification-daemon-3.18.2.tar.xz
notify2                   0.3.1        04 September 2017 https://pypi.python.org/packages/aa/e8/d4b335aa739dc299a77766ecc5f1972d1de1993524aa94acef3219bba315/notify2-0.3.1.tar.gz
notifypython              0.1.1        25 April 2015 http://www.galago-project.org/files/releases/source/notify-python/notify-python-0.1.1.tar.bz2
npth                      1.7          25 February 2024 https://gnupg.org/ftp/gcrypt/npth/npth-1.7.tar.bz2
nsd                       4.2.1        11 July 2019 https://www.nlnetlabs.nl/downloads/nsd/nsd-4.2.1.tar.gz
nspluginwrapper           1.2.2        01 June 2014 http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-1.2.2.tar.bz2
nspr                      4.35         17 September 2022 https://archive.mozilla.org/pub/nspr/releases/v4.35/src/nspr-4.35.tar.gz
nss                       3.99         18 March 2024 https://archive.mozilla.org/pub/security/nss/releases/NSS_3_99_RTM/src/nss-3.99.tar.gz
ntp                       4.2.8p15     24 June 2020 https://www.eecis.udel.edu/~ntp/ntp_spool/ntp4/ntp-4.2/ntp-4.2.8p15.tar.gz
ntrack                    017          09 July 2015 https://launchpad.net/ntrack/main/017/+download/ntrack-017.tar.gz
numactl                   2.0.13       18 July 2020 https://github.com/numactl/numactl/releases/download/v2.0.13/numactl-2.0.13.tar.gz
numonarray                0.9.2.0      27 May 2022  https://rubygems.org/downloads/numo-narray-0.9.2.0.gem
numpy                     1.26.4       21 March 2024 https://files.pythonhosted.org/packages/source/n/numpy/numpy-1.26.4.tar.gz
nuvie                     0.5          19 October 2014 http://sourceforge.net/projects/nuvie/files/Nuvie/0.5/nuvie-0.5.tgz
nvclock                   0.8          01 June 2014 http://www.linuxhardware.org/nvclock/nvclock0.8b4.tar.gz
nvmecli                   1.11.2       29 May 2020  https://github.com/linux-nvme/nvme-cli/releases
nwcc                      0.8.2        01 June 2014 http://sourceforge.net/projects/nwcc/files/nwcc/nwcc%200.8.2/nwcc_0.8.2.tar.gz
nzbget                    17.1         06 September 2016 https://github.com/nzbget/nzbget/releases/download/v17.1/nzbget-17.1.tar.gz
obby                      0.4.6        01 June 2014 http://releases.0x539.de/obby/obby-0.4.6.tar.gz
obconf                    2.0.4        23 August 2017 http://openbox.org/dist/obconf/obconf-2.0.4.tar.gz
obconfqt                  0.16.0       07 November 2020 https://github.com/lxqt/obconf-qt/releases/download/0.16.0/obconf-qt-0.16.0.tar.xz
obexdataserver            0.4.6        01 December 2012 http://tadas.dailyda.com/software/obex-data-server-0.4.6.tar.gz
ocaml                     4.04.0       25 February 2017 http://caml.inria.fr/pub/distrib/ocaml-4.04/ocaml-4.04.0.tar.gz
oclock                    1.0.5        01 September 2022 https://www.x.org/releases/individual/app/oclock-1.0.5.tar.xz
ocra                      1.3.11       28 May 2020  https://rubygems.org/downloads/ocra-1.3.11.gem
ocrad                     0.28         19 January 2022 https://ftp.gnu.org/pub/gnu/ocrad/ocrad-0.28.tar.lz
ocrfeeder                 0.8.3        09 March 2020 http://ftp.gnome.org/pub/gnome/sources/ocrfeeder/0.8/ocrfeeder-0.8.3.tar.xz
octave                    9.1.0        15 March 2024 https://ftp.gnu.org/gnu/octave/octave-9.1.0.tar.xz
ogmrip                    1.0.1        30 August 2015 http://sourceforge.net/projects/ogmrip/files/ogmrip/1.0/1.0.1/ogmrip-1.0.1.tar.gz
ogmtools                  1.5          01 June 2014 http://www.bunkus.org/videotools/ogmtools/ogmtools-1.5.tar.bz2
ogre                      13.4.4       12 September 2022 https://github.com/OGRECave/ogre/archive/refs/tags/v13.4.4.tar.gz
oki                       0.1.6        01 June 2014 http://free.of.pl/s/szatkus/soft/gry/oki-0.1.6.tar.gz
okular                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/okular-23.08.5.tar.xz
omake                     0.10.5       28 August 2022 http://download.camlcity.org/download/omake-0.10.5.tar.gz
onig                      6.9.9        19 October 2023 https://github.com/kkos/oniguruma/releases/download/v6.9.9/onig-6.9.9.tar.gz
opal                      1.5.0        27 May 2022  https://rubygems.org/downloads/opal-1.5.0.gem
openal                    0.0.8        01 June 2014 http://www.openal.org/openal_webstf/downloads/openal-0.0.8.tar.gz
openalsoft                1.23.0       14 April 2023 https://openal-soft.org/openal-releases/openal-soft-1.23.0.tar.bz2
openbabel                 19.12.2018   20 September 2017 https://sourceforge.net/projects/openbabel/files/openbabel/2.4.1/openbabel-2.4.1.tar.gz
openblas                  0.3.19       27 March 2024 https://github.com/xianyi/OpenBLAS/releases/download/v0.3.19/OpenBLAS-0.3.19.tar.gz
openbox                   3.6.1        01 July 2015 http://openbox.org/dist/openbox/openbox-3.6.1.tar.gz
opencobol                 1.1          01 December 2013 https://downloads.sourceforge.net/project/open-cobol/open-cobol/1.1/open-cobol-1.1.tar.gz
openconnect               8.05         09 March 2020 ftp://ftp.infradead.org/pub/openconnect/openconnect-8.05.tar.gz
opencv                    4.9.0        06 March 2024 https://github.com/opencv/opencv/archive/4.9.0/opencv-4.9.0.tar.gz
openexr                   3.2.4        27 March 2024 https://github.com/AcademySoftwareFoundation/openexr/releases/download/v3.2.4/openexr-v3.2.4.tar.gz
openinvaders              0.3          01 December 2012 http://www.jamyskis.net/invaders.php/open-invaders-0.3.tar.gz
openjade                  1.3.2        01 June 2014 https://prdownloads.sourceforge.net/openjade/openjade-1.3.2.tar.gz
openjpeg                  2.5.2        01 March 2024 https://github.com/uclouvain/openjpeg/archive/v2.5.2/openjpeg-2.5.2.tar.gz
openldap                  2.6.7        29 January 2024 https://openldap.org/software/download/OpenLDAP/openldap-release/openldap-2.6.7.tgz
openldev                  1.0          21 August 2017 https://sourceforge.net/projects/openldev/files/openldev/1.0/openldev-1.0.tar.gz
openmovieeditor           0.0.20090105 05 April 2024 http://downloads.sourceforge.net/openmovieeditor/openmovieeditor-0.0.20090105.tar.gz
openmpi                   4.1.4        20 December 2022 https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.4.tar.bz2
openobex                  1.7.2        12 January 2019 https://sourceforge.net/projects/openobex/files/openobex/1.7.2/openobex-1.7.2-Source.tar.gz
openresolv                3.13.2       09 February 2024 https://github.com/NetworkConfiguration/openresolv/releases/download/v3.13.2/openresolv-3.13.2.tar.xz
openscenegraph            2.4.0        01 June 2014 OpenSceneGraph-2.4.0
openshot                  1.4.3        01 June 2014 http://launchpad.net/openshot/1.4/1.4.3/+download/openshot-1.4.3.tar.gz
openshotqt                2.5.1        03 March 2020 https://github.com/OpenShot/openshot-qt/archive/v2.5.1.tar.gz
opensp                    1.5.2        01 June 2014 http://ovh.dl.sourceforge.net/sourceforge/openjade/OpenSP-1.5.2.tar.gz
openssh                   9.7p1        12 March 2024 https://ftp3.usa.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-9.7p1.tar.gz
openssl                   3.3.0        09 April 2024 https://ftp.openssl.org/source/openssl-3.3.0.tar.gz
openssn                   1.3          01 December 2012 http://sourceforge.net/projects/openssn/files/openssn-1.3/openssn-1.3.tar.gz
openttd                   13.1         10 June 2023 https://cdn.openttd.org/openttd-releases/13.1/openttd-13.1-source.tar.xz
openvpn                   2.6.10       21 March 2024 https://swupdate.openvpn.org/community/releases/openvpn-2.6.10.tar.gz
openvrml                  0.18.9       01 June 2014 http://sourceforge.net/projects/openvrml/files/openvrml/0.18.9/openvrml-0.18.9.tar.gz
opera                     12.00        01 June 2014 http://snapshot.opera.com/unix/bonkers_12.00-1440/opera-next-12.00-1440.x86_64.linux.tar.xz
ophcrack                  3.6.0        01 July 2013 http://downloads.sourceforge.net/project/ophcrack/ophcrack/3.6.0/ophcrack-3.6.0.tar.bz2
oprofile                  1.4.0        25 July 2020 http://prdownloads.sourceforge.net/oprofile/oprofile-1.4.0.tar.gz
optimist                  3.0.1        06 June 2021 https://rubygems.org/downloads/optimist-3.0.1.gem
optipng                   0.7.7        31 July 2018 https://sourceforge.net/projects/optipng/files/OptiPNG/optipng-0.7.7/optipng-0.7.7.tar.gz
opus                      1.5.2        14 April 2024 https://ftp.osuosl.org/pub/xiph/releases/opus/opus-1.5.2.tar.gz
opusfile                  0.12         01 July 2020 https://github.com/xiph/opusfile/releases/download/v0.12/opusfile-0.12.tar.gz
opustools                 0.2          20 November 2022 https://ftp.mozilla.org/pub/opus/opus-tools-0.2.tar.gz
orbit2                    2.14.19      01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/ORBit2/2.14/ORBit2-2.14.19.tar.bz2
orc                       0.4.32       16 December 2020 https://github.com/GStreamer/orc/archive/orc-0.4.32.tar.gz
orca                      46.0         14 March 2024 https://download.gnome.org/sources/orca/46/orca-46.0.tar.xz
ostree                    2014.4       01 April 2014 http://ftp.gnome.org/pub/gnome/sources/ostree/2014.4/ostree-2014.4.tar.xz
oxygen                    5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/oxygen-5.27.9.tar.xz
oxygengtk                 1.1.6        01 August 2013 http://download.kde.org/stable/oxygen-gtk/1.1.6/src/oxygen-gtk-1.1.6.tar.bz2
oxygenicons               5.115.0      04 December 2023 https://download.kde.org/stable/frameworks/5.115/oxygen-icons-5.115.0.tar.xz
oxygensounds              5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/oxygen-sounds-5.27.9.tar.xz
p11kit                    0.25.3       30 January 2024 https://github.com/p11-glue/p11-kit/releases/download/0.25.3/p11-kit-0.25.3.tar.xz
p7zip                     17.04        17 August 2022 https://github.com/jinfeihan57/p7zip/archive/v17.04/p7zip-17.04.tar.gz
packagekit                1.1.11       05 October 2018 https://www.freedesktop.org/software/PackageKit/releases/PackageKit-1.1.11.tar.xz
packaging                 24.0         19 March 2024 https://files.pythonhosted.org/packages/ee/b5/b43a27ac7472e1818c4bafd44430e69605baefe1f34440593e0332ec8b4d/packaging-24.0.tar.gz
pacman                    v6.1.0       04 March 2024 https://gitlab.archlinux.org/pacman/pacman/-/archive/v6.1.0/pacman-v6.1.0.tar.bz2
padrino                   0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-0.15.1.gem
padrinoadmin              0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-admin-0.15.1.gem
padrinocache              0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-cache-0.15.1.gem
padrinocore               0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-core-0.15.1.gem
padrinogen                0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-gen-0.15.1.gem
padrinohelpers            0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-helpers-0.15.1.gem
padrinomailer             0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-mailer-0.15.1.gem
padrinosupport            0.15.1       27 May 2022  https://rubygems.org/downloads/padrino-support-0.15.1.gem
paint                     2.3.0        17 November 2022 https://rubygems.org/downloads/paint-2.3.0.gem
paintown                  3.6.0        25 September 2019 https://github.com/kazzmir/paintown/releases/download/v3.6.0/paintown-3.6.0.tar.bz2
palapeli                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/palapeli-23.08.5.tar.xz
paludis                   2.6.0        18 July 2017 http://paludis.exherbo.org/download/paludis-2.6.0.tar.bz2
panda3d                   1.8.0        01 December 2012 http://www.panda3d.org/download/panda3d-1.8.0/panda3d-1.8.0.tar.gz
pandas                    1.4.3        26 June 2022 https://files.pythonhosted.org/packages/f4/00/2de395c769335956b8650f990ef2a15e860be83b544c408ff95713446329/pandas-1.4.3.tar.gz
pandoc                    2.7.2        14 April 2019 https://hackage.haskell.org/package/pandoc-2.7.2/pandoc-2.7.2.tar.gz
pandora                   0.1.2        01 June 2014 https://rubygems.org/downloads/pandora-0.1.2.gem
pango                     1.52.2       31 March 2024 https://download.gnome.org/sources/pango/1.52/pango-1.52.2.tar.xz
pangomm                   2.50.1       29 March 2023 https://download.gnome.org/sources/pangomm/2.50/pangomm-2.50.1.tar.xz
pangzero                  1.3          01 December 2012 http://sourceforge.net/projects/pangzero/files/pangzero/1.3/pangzero-1.3.tar.gz
papyrus                   0.13.3       28 March 2016 https://sourceforge.net/projects/libpapyrus/files/papyrus/0.13.3/papyrus-0.13.3.tar.gz
paragui                   05.04.2024   05 April 2024 https://github.com/pipelka/paragui/paragui-05.04.2024
parallel                  20231122     24 November 2023 https://ftp.gnu.org/pub/gnu/parallel/parallel-20231122.tar.bz2
paratim                   0.2.0.1      05 April 2024 https://sourceforge.net/projects/paratim/files/paratim/paratim-0.2.0/paratim-0.2.0.1.tar.bz2
parley                    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/parley-23.08.5.tar.xz
parole                    4.18.0       10 June 2023 https://archive.xfce.org/src/apps/parole/4.18/parole-4.18.0.tar.bz2
parser                    3.1.2.0      27 May 2022  https://rubygems.org/downloads/parser-3.1.2.0.gem
parsetree                 3.0.9        01 August 2017 https://rubygems.org/downloads/ParseTree-3.0.9.gem
parseyapp                 1.21         07 August 2017 https://cpan.metacpan.org/authors/id/W/WB/WBRASWELL/Parse-Yapp-1.21.tar.gz
parted                    3.6          11 April 2023 https://ftp.gnu.org/gnu/parted/parted-3.6.tar.xz
partimage                 0.6.9        28 March 2016 https://sourceforge.net/projects/partimage/files/stable/0.6.9/partimage-0.6.9.tar.bz2
partitionmanager          23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/partitionmanager-23.08.5.tar.xz
passenger                 6.0.8        15 April 2021 https://rubygems.org/downloads/passenger-6.0.8.gem
patch                     2.7.6        06 February 2018 https://ftp.gnu.org/pub/gnu/patch/patch-2.7.6.tar.xz
patchelf                  0.18.0       26 April 2023 https://github.com/NixOS/patchelf/releases/download/0.18.0/patchelf-0.18.0.tar.gz
patchutils                0.4.2        21 July 2020 http://cyberelk.net/tim/data/patchutils/stable/patchutils-0.4.2.tar.xz
pathexpander              1.1.0        28 May 2020  https://rubygems.org/downloads/path_expander-1.1.0.gem
pathlib                   1.0.1        27 December 2017 https://pypi.python.org/packages/ac/aa/9b065a76b9af472437a0059f77e8f962fe350438b927cb80184c32f075eb/pathlib-1.0.1.tar.gz
pathlib2                  2.3.5        27 October 2019 https://files.pythonhosted.org/packages/94/d8/65c86584e7e97ef824a1845c72bbe95d79f5b306364fa778a3c3e401b309/pathlib2-2.3.5.tar.gz
pathspec                  0.12.1       16 April 2024 https://files.pythonhosted.org/packages/ca/bc/f35b8446f4531a7cb215605d100cd88b7ac6f44ab3fc94870c120ab3adbf/pathspec-0.12.1.tar.gz
pavucontrol               5.0          27 August 2021 https://freedesktop.org/software/pulseaudio/pavucontrol/pavucontrol-5.0.tar.xz
pavucontrolqt             0.16.0       07 November 2020 https://github.com/lxqt/pavucontrol-qt/releases/download/0.16.0/pavucontrol-qt-0.16.0.tar.xz
pawm                      2.3.0        01 June 2014 http://www.pleyades.net/david/projects/pawm/pawm-2.3.0.tar.bz2
paxutils                  1.3.6        25 January 2023 https://gitweb.gentoo.org/proj/pax-utils.git/snapshot/pax-utils-1.3.6.tar.gz
pbbam                     1.6.0        20 March 2024 https://github.com/PacificBiosciences/pbbam/archive/v1.6.0.tar.gz
pbzip2                    1.1.13       21 September 2017 https://launchpad.net/pbzip2/1.1/1.1.13/+download/pbzip2-1.1.13.tar.gz
pcaudiolib                1.1          29 July 2020 https://github.com/espeak-ng/pcaudiolib/archive/1.1.tar.gz
pcc                       02.10.2007   01 June 2014 ftp://226.net120.skekraft.net/pcc/
pciutils                  3.12.0       06 April 2024 https://mj.ucw.cz/download/linux/pci/pciutils-3.12.0.tar.gz
pcmanfmqt                 0.16.0       07 November 2020 https://github.com/lxqt/pcmanfm-qt/releases/download/0.16.0/pcmanfm-qt-0.16.0.tar.xz
pcmciautils               014          01 May 2012  http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmciautils-014.tar.bz2
pcre                      8.45         16 June 2021 ftp://ftp.pcre.org/pub/pcre/pcre-8.45.tar.bz2
pcre2                     10.43        24 February 2024 https://github.com/PhilipHazel/pcre2/releases/download/pcre2-10.43/pcre2-10.43.tar.bz2
pcsclite                  1.8.18       11 August 2016 https://alioth.debian.org/frs/download.php/file/4173/pcsc-lite-1.8.18.tar.bz2
pdal                      1.5.0        21 September 2017 http://download.osgeo.org/pdal/PDAL-1.5.0.tar.gz
pdfcore                   0.9.0        15 April 2021 https://rubygems.org/downloads/pdf-core-0.9.0.gem
pdfcrack                  0.19         19 March 2021 https://sourceforge.net/projects/pdfcrack/files/pdfcrack/pdfcrack-0.19/pdfcrack-0.19.tar.gz
pdfedit                   0.4.5        01 June 2014 http://sourceforge.net/projects/pdfedit/files/pdfedit/0.4.5/pdfedit-0.4.5.tar.bz2
pdfgrep                   2.0.1        25 March 2017 https://pdfgrep.org/download/pdfgrep-2.0.1.tar.gz
pdfpc                     4.3.0        22 December 2018 https://github.com/pdfpc/pdfpc/archive/pdfpc-4.3.0.tar.gz
pdfreader                 2.5.0        13 June 2021 https://rubygems.org/downloads/pdf-reader-2.5.0.gem
pdftk                     2.02         10 May 2015  https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/pdftk-2.02.zip
pdl                       2.016        29 June 2016 https://sourceforge.net/projects/pdl/files/PDL-2.016/PDL-2.016.tar.gz/
peewee                    3.8.0        18 December 2018 https://files.pythonhosted.org/packages/b2/38/fe304c84dd7b771e6c313e2905d54944b9577b212e3247cfa58fac2ac935/peewee-3.8.0.tar.gz
peg                       0.1.18       30 December 2018 http://piumarta.com/software/peg/peg-0.1.18.tar.gz
pekwm                     0.1.17       01 January 2014 https://www.pekwm.org/projects/pekwm/files/pekwm-0.1.17.tar.bz2
penguincommand            1.6.11       01 January 2013 http://user.cs.tu-berlin.de/~karlb/penguin-command/penguincommand-1.6.11.tar.gz
pengupop                  2.1.9        01 June 2014 http://www.junoplay.com/files/pengupop-2.1.9.tar.gz
pentagram                 16.02.2008   01 December 2012 http://pentagram.sourceforge.net/download.php
perl                      5.38.2       29 January 2024 https://www.cpan.org/src/5.0/perl-5.38.2.tar.gz
gettext                   1.07         05 June 2020 https://cpan.metacpan.org/authors/id/P/PV/PVANDRY/gettext-1.07.tar.gz
pg                        1.4.6        27 February 2023 https://rubygems.org/downloads/pg-1.4.6.gem
phodav                    3.0          02 July 2022 https://download.gnome.org/sources/phodav/3.0/phodav-3.0.tar.xz
phonon                    4.12.0       04 November 2023 https://download.kde.org/stable/phonon/4.12.0/phonon-4.12.0.tar.xz
phononbackendgstreamer    4.9.0        13 October 2017 http://download.kde.org/stable/phonon/phonon-backend-gstreamer/4.9.0/phonon-backend-gstreamer-4.9.0.tar.xz
phononbackendvlc          0.11.2       07 February 2021 https://download.kde.org/stable/phonon/phonon-backend-vlc/0.11.2/phonon-backend-vlc-0.11.2.tar.xz
php                       8.3.6        11 April 2024 https://www.php.net/distributions/php-8.3.6.tar.xz
phpbb                     3.2.3        30 September 2018 https://www.phpbb.com/files/release/phpBB-3.2.3.zip
phpunit                   6.3          24 Sep 2017  https://phar.phpunit.de/phpunit-6.3.phar
phpwiki                   1.5.5        02 August 2017 https://sourceforge.net/projects/phpwiki/files/PhpWiki%201.5%20%28current%29/phpwiki-1.5.5.zip
phylip                    3.68         01 June 2014 http://evolution.gs.washington.edu/phylip/download/phylip-3.68.tar.gz
physfs                    3.0.2        27 March 2024 https://icculus.org/physfs/downloads/physfs-3.0.2.tar.bz2
picmi                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/picmi-23.08.5.tar.xz
pidgin                    2.14.13      23 February 2024 https://downloads.sourceforge.net/pidgin/pidgin-2.14.13.tar.bz2
pigz                      2.4          10 August 2020 https://zlib.net/pigz/pigz-2.4.tar.gz
pikepdf                   7.1.1        21 February 2023 https://files.pythonhosted.org/packages/bb/22/87185add91a015aaebe82a8f96c60c948a00f1ecf6e750b34cb4c368f162/pikepdf-7.1.1.tar.gz
pillow                    9.4.0        21 March 2023 https://files.pythonhosted.org/packages/bc/07/830784e061fb94d67649f3e438ff63cfb902dec6d48ac75aeaaac7c7c30e/Pillow-9.4.0.tar.gz
pimcommon                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/pimcommon-23.08.5.tar.xz
pimdataexporter           23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/pim-data-exporter-23.08.5.tar.xz
pimsieveeditor            23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/pim-sieve-editor-23.08.5.tar.xz
pine                      4.64         01 June 2014 ftp://ftp.cac.washington.edu/pine/pine.tar.bz2/pine-4.64.tar.xz
pinentry                  1.3.0        19 March 2024 https://www.gnupg.org/ftp/gcrypt/pinentry/pinentry-1.3.0.tar.bz2
pinfo                     0.6.8        01 June 2014 http://freshmeat.net/redir/pinfo/8107/url_tgz/pinfo-0.6.8.tar.gz
pingus                    0.7.6        01 July 2013 http://pingus.googlecode.com/files/pingus-0.7.6.tar.bz2
pinpoint                  0.1.8        23 September 2015 http://ftp.gnome.org/pub/GNOME/sources/pinpoint/0.1/pinpoint-0.1.8.tar.xz
pinta                     1.7          14 August 2020 https://github.com/PintaProject/Pinta/releases/download/1.7/pinta-1.7.tar.gz
pioneers                  15.4         01 November 2017 https://sourceforge.net/projects/pio/files/Source/pioneers-15.4.tar.gz
pip                       24.0         11 February 2024 https://files.pythonhosted.org/packages/94/59/6638090c25e9bc4ce0c42817b5a234e183872a1129735a9330c472cc2056/pip-24.0.tar.gz
pipenv                    2018.11.26   12 February 2019 https://files.pythonhosted.org/packages/fd/e9/01822318551caa0d62a181ba3b10f0f3757bb1e270da97165bd52db92776/pipenv-2018.11.26.tar.gz
pipepanic                 0.1.3        01 December 2012 http://www.users.waitrose.com/~thunor/pipepanic/#downloads
pipewalker                0.4.3        01 December 2012 http://sourceforge.net/project/showfiles.php?group_id=198283
pipewire                  1.0.5        15 April 2024 https://gitlab.freedesktop.org/pipewire/pipewire/-/archive/1.0.5/pipewire-1.0.5.tar.bz2
pitivi                    2023.03      27 March 2023 https://download.gnome.org/sources/pitivi/2023/pitivi-2023.03.tar.xz
pixman                    0.43.4       01 March 2024 https://www.x.org/releases/individual/lib/pixman-0.43.4.tar.xz
pjproject                 1.14.2       01 June 2014 http://www.pjsip.org/release/1.14.2/pjproject-1.14.2.tar.bz2
pkgconfig                 0.29.2       26 March 2017 https://pkgconfig.freedesktop.org/releases/pkg-config-0.29.2.tar.gz
pl                        6.2.2        01 June 2014 http://www.swi-prolog.org/download/stable/src/pl-6.2.2.tar.gz
plankplayer               5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plank-player-5.27.9.tar.xz
plasmabigscreen           5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-bigscreen-5.27.9.tar.xz
plasmabrowserintegration  5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-browser-integration-5.27.9.tar.xz
plasmadesktop             6.0.0        29 February 2024 https://download.kde.org/stable/plasma/6.0.0/plasma-desktop-6.0.0.tar.xz
plasmadisks               5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-disks-5.27.9.tar.xz
plasmafirewall            5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-firewall-5.27.9.tar.xz
plasmaframework           5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/plasma-framework-5.115.0.tar.xz
plasmaintegration         5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-integration-5.27.9.tar.xz
plasmamobile              5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-mobile-5.27.9.tar.xz
plasmanano                5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-nano-5.27.9.tar.xz
plasmanm                  5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-nm-5.27.9.tar.xz
plasmapa                  5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-pa-5.27.9.tar.xz
plasmaphonecomponents     5.24.0       08 February 2022 https://download.kde.org/stable/plasma/5.24.0/plasma-phone-components-5.24.0.tar.xz
plasmaremotecontrollers   5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-remotecontrollers-5.27.9.tar.xz
plasmasdk                 5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-sdk-5.27.9.tar.xz
plasmasystemmonitor       5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-systemmonitor-5.27.9.tar.xz
plasmatests               5.27.3       23 March 2023 https://download.kde.org/stable/plasma/5.27.3/plasma-tests-5.27.3.tar.xz
plasmathunderbolt         5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-thunderbolt-5.27.9.tar.xz
plasmatube                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/plasmatube-23.08.5.tar.xz
plasmavault               5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-vault-5.27.9.tar.xz
plasmawaylandprotocols    1.12.0       21 February 2024 https://download.kde.org/stable/plasma-wayland-protocols/plasma-wayland-protocols-1.12.0.tar.xz
plasmawelcome             5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-welcome-5.27.9.tar.xz
plasmaworkspace           5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-workspace-5.27.9.tar.xz
plasmaworkspacewallpapers 5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plasma-workspace-wallpapers-5.27.9.tar.xz
plib                      1.8.4        01 June 2014 http://plib.sourceforge.net/download.html
ploticus                  2.3.2        01 June 2014 http://ploticus.sourceforge.net/download/pl232src.tar.gz
pluma                     1.28.0       21 February 2024 https://pub.mate-desktop.org/releases/1.28/pluma-1.28.0.tar.xz
plumaplugins              1.26.0       20 August 2021 https://pub.mate-desktop.org/releases/1.26/pluma-plugins-1.26.0.tar.xz
ply                       3.11         22 November 2018 https://files.pythonhosted.org/packages/e5/69/882ee5c9d017149285cab114ebeab373308ef0f874fcdac9beb90e0ac4da/ply-3.11.tar.gz
plymouth                  0.9.4        04 December 2018 https://www.freedesktop.org/software/plymouth/releases/plymouth-0.9.4.tar.xz
plymouthkcm               5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/plymouth-kcm-5.27.9.tar.xz
plzip                     1.9          09 January 2021 http://download.savannah.gnu.org/releases/lzip/plzip/plzip-1.9.tar.gz
pmacct                    0.14.1       01 June 2014 http://www.pmacct.net/pmacct-0.14.1.tar.gz
pmk                       0.10.4       01 June 2014 http://prdownloads.sourceforge.net/pmk/pmk-0.10.4.tar.gz
png++                     0.2.9        30 July 2016 http://download.savannah.gnu.org/releases/pngpp/png++-0.2.9.tar.gz
pngcrush                  1.7.41       01 December 2012 http://sourceforge.net/projects/pmt/files/pngcrush/1.7.41/pngcrush-1.7.41.tar.xz
pngquant                  2.18.0       25 February 2023 https://pngquant.org/pngquant-2.18.0.tar.gz
pnmixer                   v0.7.2       10 September 2018 https://github.com/nicklan/pnmixer/releases/download/v0.7.2/pnmixer-v0.7.2.tar.gz
poco                      1.1.2        01 June 2014 http://www.basha.org/poco.shtml
podofo                    0.9.8        27 May 2022  https://sourceforge.net/projects/podofo/files/podofo/0.9.8/podofo-0.9.8.tar.gz
poetry                    1.0.0        28 December 2019 https://files.pythonhosted.org/packages/59/b9/79e078a303b6b813aa16c1f9cffe22e048c6edfef9a31574670193d09fc4/poetry-1.0.0.tar.gz
poke                      4.0          31 March 2024 https://ftp.gnu.org/gnu/poke/poke-4.0.tar.gz
polari                    43.0         12 October 2022 https://download.gnome.org/sources/polari/43/polari-43.0.tar.xz
policykit                 0.9          01 June 2014 PolicyKit-0.9
polkit                    124          12 April 2024 https://gitlab.freedesktop.org/polkit/polkit/-/archive/124/polkit-124.tar.gz
polkitgnome               0.105        01 June 2014 ftp://ftp.gnome.org/pub/gnome/sources/polkit-gnome/0.105/polkit-gnome-0.105.tar.xz
polkitkdeagent1           5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/polkit-kde-agent-1-5.27.9.tar.xz
polkitqt1                 0.114.0      03 March 2015 https://github.com/KDE/polkit-qt-1/archive/refs/tags/v0.114.0.tar.gz
poltergeist               1.18.1       13 August 2018 https://rubygems.org/downloads/poltergeist-1.18.1.gem
polyglot                  0.3.5        14 October 2018 https://rubygems.org/downloads/polyglot-0.3.5.gem
polylib                   5.22.5       01 November 2012 http://icps.u-strasbg.fr/polylib/polylib_src/polylib-5.22.5.tar.gz
poppler                   24.04.0      02 April 2024 https://poppler.freedesktop.org/poppler-24.04.0.tar.xz
popplerdata               0.4.12       04 February 2023 http://poppler.freedesktop.org/poppler-data-0.4.12.tar.gz
popt                      1.19         18 September 2022 http://ftp.rpm.org/popt/releases/popt-1.x/popt-1.19.tar.gz
porcupine                 0.0.7        01 June 2014 http://www.innoscript.org/component/option,com_remository/Itemid,33/porcupine-0.0.7
porg                      0.10         01 September 2016 https://sourceforge.net/projects/porg/files/porg-0.10.tar.gz
portaudio                 v190700      26 January 2023 http://files.portaudio.com/archives/pa_stable_v190700_20210406.tgz
postfix                   3.9.0        10 March 2024 http://ftp.porcupine.org/mirrors/postfix-release/official/postfix-3.9.0.tar.gz
postgis                   2.3.1        18 March 2017 http://download.osgeo.org/postgis/source/postgis-2.3.1.tar.gz
postgresql                16.2         27 March 2024 https://ftp.postgresql.org/pub/source/v16.2/postgresql-16.2.tar.bz2
postr                     0.13.1       05 September 2014 http://ftp.gnome.org/pub/GNOME/sources/postr/0.13/postr-0.13.1.tar.xz
potrace                   1.16         21 September 2019 https://potrace.sourceforge.net/download/1.16/potrace-1.16.tar.gz
povray                    05.06.2021   05 June 2021 http://www.povray.org/redirect/www.povray.org/ftp/pub/povray/Official/Linux/povlinux-3.6.tgz
powerassert               2.0.3        19 June 2023 https://rubygems.org/downloads/power_assert-2.0.3.gem
powerdevil                5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/powerdevil-5.27.9.tar.xz
powermanga                0.93         10 October 2017 http://linux.tlk.fr/games/Powermanga/download/powermanga-0.93.tgz
powerpack                 0.1.3        15 April 2021 https://rubygems.org/downloads/powerpack-0.1.3.gem
powertop                  2.15         01 October 2022 https://github.com/fenrus75/powertop/archive/refs/tags/v2.15.tar.gz
poxml                     23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/poxml-23.08.5.tar.xz
ppl                       1.2          18 February 2016 ftp://ftp.cs.unipr.it/pub/ppl/releases/1.2/ppl-1.2.tar.gz
ppp                       2.5.0        04 April 2023 https://github.com/paulusmack/ppp/archive/ppp-2.5.0.tar.gz
prawn                     2.4.0        15 April 2021 https://rubygems.org/downloads/prawn-2.4.0.gem
prefixsuffix              0.6.9        08 December 2015 http://ftp.gnome.org/pub/GNOME/sources/prefixsuffix/0.6/prefixsuffix-0.6.9.tar.xz
presentproto              1.1          18 March 2017 https://www.x.org/releases/individual/proto/presentproto-1.1.tar.bz2
primer3                   2.3.7        12 April 2016 https://sourceforge.net/projects/primer3/files/primer3/2.3.7/primer3-2.3.7.tar.gz
printmanager              23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/print-manager-23.08.5.tar.xz
printproto                1.0.5        01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/printproto-1.0.5.tar.bz2
prison                    5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/prison-5.115.0.tar.xz
processing                0111         01 June 2014 http://processing.org/download/processing-0111.tgz
procinfong                2.0.304      18 April 2019 https://sourceforge.net/projects/procinfo-ng/files/procinfo-ng/2.0.304/procinfo-ng-2.0.304.tar.bz2
procps                    v3.3.15      21 August 2019 https://gitlab.com/procps-ng/procps/-/archive/v3.3.15/procps-v3.3.15.tar.bz2
procpsng                  4.0.4        21 January 2024 https://sourceforge.net/projects/procps-ng/files/Production/procps-ng-4.0.4.tar.xz
prodigal                  2.6.3        26 June 2020 https://github.com/hyattpd/Prodigal/archive/v2.6.3.tar.gz
proftpd                   1.3.7a       10 April 2017 https://github.com/proftpd/proftpd/archive/v1.3.7a.tar.gz
progsreiserfs             0.3.0.4      01 June 2014 http://reiserfs.osdn.org.ua/progsreiserfs-0.3.0.4.tar.gz
protobuf                  26.1         29 March 2024 https://github.com/protocolbuffers/protobuf/releases/download/v26.1/protobuf-26.1.tar.gz
protobufcpp               3.21.12      14 December 2022 https://github.com/protocolbuffers/protobuf/releases/download/v21.12/protobuf-cpp-3.21.12.tar.gz
protocol                  2.0.0        28 May 2020  https://rubygems.org/downloads/protocol-2.0.0.gem
protoeditor               1.0          09 February 2018 https://sourceforge.net/projects/protoeditor/files/protoeditor/1.0/protoeditor-1.0.tar.gz
proxymngr                 1.0.4        18 April 2015 http://xorg.freedesktop.org/releases/individual/app/proxymngr-1.0.4.tar.gz
pry                       0.14.1       15 April 2021 https://rubygems.org/downloads/pry-0.14.1.gem
prybyebug                 3.9.0        28 May 2020  https://rubygems.org/downloads/pry-byebug-3.9.0.gem
pscpug                    0.3.2        01 June 2014 http://www.diablonet.net/~mercadal/projects/pscpug/pscpug030.tgz
psftools                  1.0.12       25 March 2019 http://www.seasip.info/Unix/PSF/psftools-1.0.12.tar.gz
psmisc                    23.7         17 March 2024 https://sourceforge.net/projects/psmisc/files/psmisc/psmisc-23.7.tar.xz
pspp                      2.0.1        22 March 2024 https://ftp.gnu.org/pub/gnu/pspp/pspp-2.0.1.tar.gz
pssh                      2.3.1        09 August 2020 https://files.pythonhosted.org/packages/60/9a/8035af3a7d3d1617ae2c7c174efa4f154e5bf9c24b36b623413b38be8e4a/pssh-2.3.1.tar.gz
psych                     3.3.1        15 April 2021 https://rubygems.org/downloads/psych-3.3.1.gem
pth                       2.0.7        01 June 2014 ftp://ftp.gnu.org/gnu/pth/pth-2.0.7.tar.gz
ptlib                     2.10.11      07 November 2015 http://ftp.gnome.org/pub/GNOME/sources/ptlib/2.10/ptlib-2.10.11.tar.xz
publicsuffix              4.0.6        15 April 2021 https://rubygems.org/downloads/public_suffix-4.0.6.gem
pugixml                   1.11         04 January 2021 http://github.com/zeux/pugixml/releases/download/v1.11/pugixml-1.11.tar.gz
pulseaudio                17.0         14 January 2024 https://freedesktop.org/software/pulseaudio/releases/pulseaudio-17.0.tar.xz
puma                      5.6.0        16 September 2022 https://rubygems.org/downloads/puma-5.6.0.gem
puppet                    7.23.0       28 February 2023 https://rubygems.org/downloads/puppet-7.23.0.gem
purpose                   5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/purpose-5.115.0.tar.xz
putty                     0.73         02 October 2019 https://the.earth.li/~sgtatham/putty/latest/putty-0.73.tar.gz
pwdutils                  3.0          01 June 2014 http://www.thkukuk.de/pam/pwdutils/
py2cairo                  1.10.0       25 April 2015 http://cairographics.org/releases/py2cairo-1.10.0.tar.bz2
pyatspi                   2.46.0       22 September 2022 https://download.gnome.org/sources/pyatspi/2.46/pyatspi-2.46.0.tar.xz
pybliographer             1.4.0        05 April 2018 http://ftp.gnome.org/pub/gnome/sources/pybliographer/1.4/pybliographer-1.4.0.tar.xz
pycairo                   1.26.0       02 March 2024 https://github.com/pygobject/pycairo/releases/download/v1.26.0/pycairo-1.26.0.tar.gz
pycdio                    2.1.0        05 December 2019 http://ftp.gnu.org/pub/gnu/libcdio/pycdio-2.1.0.tar.gz
pycha                     0.7.0        01 June 2014 https://pypi.python.org/packages/source/p/pycha/pycha-0.7.0.tar.gz
pycp                      8.0.6        18 January 2019 https://files.pythonhosted.org/packages/fa/2c/b01afb9eacaaeef8c9a733080da62c68545bdbced3c07ae78faad95d3af0/pycp-8.0.6.tar.gz
pycryptodome              3.10.4       28 September 2021 https://files.pythonhosted.org/packages/f8/8e/14a8238190bcf1bab3d58432cd795c859edbc2f5abd8460f80438046a799/pycryptodome-3.10.4.tar.gz
pycups                    2.0.1        01 May 2020  https://files.pythonhosted.org/packages/0c/bb/82546806a86dc16f5eeb76f62ffdc42cce3d43aacd4e25a8b5300eec0263/pycups-2.0.1.tar.gz
pycurl                    7.44.1       19 August 2021 https://files.pythonhosted.org/packages/47/f9/c41d6830f7bd4e70d5726d26f8564538d08ca3a7ac3db98b325f94cdcb7f/pycurl-7.44.1.tar.gz
pydisplay                 0.2.0        01 June 2014 http://downloads.sourceforge.net/pydisplay/pydisplay-0.2.0.tar.gz
pyensembl                 1.9.1        24 April 2021 https://files.pythonhosted.org/packages/39/65/0dbcaebd1f376a0907ba625ba86b3aa04b57dff7b026ab41dd062975b7ba/pyensembl-1.9.1.tar.gz
pygame                    1.9.6        20 September 2019 https://www.pygame.org/ftp/pygame-1.9.6.tar.gz
pyglet                    1.0          01 November 2012 http://pyglet.googlecode.com/files/pyglet-1.0.tar.gz
pygments                  2.17.2       18 March 2024 https://files.pythonhosted.org/packages/55/59/8bccf4157baf25e4aa5a0bb7fa3ba8600907de105ebc22b0c78cfbf6f565/pygments-2.17.2.tar.gz
pygobject                 3.48.2       06 April 2024 https://download.gnome.org/sources/pygobject/3.48/pygobject-3.48.2.tar.xz
pygraphviz                0.22         01 June 2014 http://surfnet.dl.sourceforge.net/sourceforge/networkx/pygraphviz-0.22.tar.gz
pygtksourceview           2.10.1       12 May 2019  http://ftp.gnome.org/pub/gnome/sources/pygtksourceview/2.10/pygtksourceview-2.10.1.tar.gz
pygui                     2.2          01 June 2014 http://www.cosc.canterbury.ac.nz/greg.ewing/python_gui/PyGUI-2.2.tar.gz
pymol                     2.3.4        14 January 2019 https://sourceforge.net/projects/pymol/files/pymol/2/pymol-v2.3.4.tar.bz2
pymysql                   0.9.2        05 December 2018 https://files.pythonhosted.org/packages/d9/ab/bc9be64876fc9b1590d8ae62b471981b4489c23d6c3f0319af570748d408/PyMySQL-0.9.2.tar.gz
pyorbit                   2.24.0       01 June 2014 http://ftp.gnome.org/pub/GNOME/sources/pyorbit/2.24/pyorbit-2.24.0.tar.bz2
pyparsing                 3.1.2        08 March 2024 https://files.pythonhosted.org/packages/46/3a/31fd28064d016a2182584d579e033ec95b809d8e220e74c4af6f0f2e8842/pyparsing-3.1.2.tar.gz
pype                      2.9.4        01 January 2013 https://sourceforge.net/projects/pype/files/pype/PyPE%202.9.4/PyPE-2.9.4.zip
pypy                      7.3.9        28 August 2022 https://downloads.python.org/pypy/pypy3.9-v7.3.9.tar.bz2
pyqt5                     5.15.4       12 June 2021 https://files.pythonhosted.org/packages/8e/a4/d5e4bf99dd50134c88b95e926d7b81aad2473b47fde5e3e4eac2c69a8942/PyQt5-5.15.4.tar.gz
pyrex                     0.9.9        06 October 2017 http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/Pyrex-0.9.9.tar.gz
pyserial                  =46487&.=39324&.=346093 01 January 2013 http://sourceforge.net/project/showfiles.php?group_id=46487&package_id=39324&release_id=346093
pysimplegui               4.33.0       14 January 2021 https://files.pythonhosted.org/packages/3e/8e/3def3ea64635d5d3fb31022f917cdea50ab2fbc39051b9320d55bb9ebcb8/PySimpleGUI-4.33.0.tar.gz
pysqlite                  2.8.3        27 November 2019 https://files.pythonhosted.org/packages/42/02/981b6703e3c83c5b25a829c6e77aad059f9481b0bbacb47e6e8ca12bd731/pysqlite-2.8.3.tar.gz
pytesseract               0.3.8        17 July 2021 https://files.pythonhosted.org/packages/a3/c9/d6e8903482bd6fb994c32722831d15842dd8b614f94ad9ca735807252671/pytesseract-0.3.8.tar.gz
pytest                    7.2.1        14 February 2023 https://files.pythonhosted.org/packages/e5/6c/f3a15217ac72912c28c5d7a7a8e87ff6d6475c9530595ae9f0f8dedd8dd8/pytest-7.2.1.tar.gz
python                    3.12.3       09 April 2024 https://www.python.org/ftp/python/3.12.3/Python-3.12.3.tgz
pythoncaja                1.28.0       23 February 2024 https://pub.mate-desktop.org/releases/1.28/python-caja-1.28.0.tar.xz
pythondbusmock            0.28.1       30 June 2022 https://github.com/martinpitt/python-dbusmock/releases/download/0.28.1/python-dbusmock-0.28.1.tar.gz
pythonefl                 1.20.0       06 July 2018 https://download.enlightenment.org/rel/bindings/python/python-efl-1.20.0.tar.xz
pytone                    3.0.3        01 June 2014 http://www.luga.de/pytone/download/PyTone-3.0.3.tar.gz
pyvorbis                  1.4          01 August 2013 http://ekyo.nerim.net/software/pyogg/index.html
pywal                     3.3.0        24 May 2020  https://files.pythonhosted.org/packages/57/55/2b694e4f42837653258540f7bbf7206e4fac651960aba69ce4fbb5427875/pywal-3.3.0.tar.gz
pyxdg                     0.27         07 December 2020 https://files.pythonhosted.org/packages/6f/2e/2251b5ae2f003d865beef79c8fcd517e907ed6a69f58c32403cec3eba9b2/pyxdg-0.27.tar.gz
pyxml                     0.8.4        01 June 2014 http://mesh.dl.sourceforge.net/sourceforge/pyxml/PyXML-0.8.4.tar.gz
pyyaml                    6.0          06 June 2022 https://files.pythonhosted.org/packages/36/2b/61d51a2c4f25ef062ae3f74576b01638bebad5e045f747ff12643df63844/PyYAML-6.0.tar.gz
qalculategtk              3.7.0        29 February 2020 https://github.com/Qalculate/qalculate-gtk/releases/download/v3.7.0/qalculate-gtk-3.7.0.tar.gz
qbittorrent               4.6.4        25 March 2024 https://downloads.sourceforge.net/qbittorrent/qbittorrent-4.6.4.tar.xz
qca                       2.3.8        07 April 2024 https://download.kde.org/stable/qca/2.3.8/qca-2.3.8.tar.xz
qcaqt5                    2.1.0.3      22 September 2017 https://download.kde.org/stable/qca-qt5/2.1.0.3/src/qca-qt5-2.1.0.3.tar.xz
qdbm                      1.8.77       12 September 2015 http://sourceforge.net/projects/qdbm/files/qdbm/1.8.77/qdbm-1.8.77.tar.gz
qdvdauthor                2.3.1        01 September 2014 http://sourceforge.net/projects/qdvdauthor/files/qdvdauthor/2.3.1/qdvdauthor-2.3.1.tar.gz
qemu                      8.2.2        06 March 2024 https://wiki.qemu.org/download/qemu-8.2.2.tar.xz
qgis                      2.18.13      20 September 2017 http://qgis.org/downloads/qgis-2.18.13.tar.bz2
qimageblitz               0.0.6        01 January 2014 http://download.kde.org/stable/qimageblitz/qimageblitz-0.0.6.tar.bz2
qimgv                     0.8.4        25 September 2019 https://github.com/easymodo/qimgv/archive/v0.8.4.tar.gz
qiv                       2.1pre12     01 June 2014 http://www.klografx.net/qiv/download/
qjackctl                  0.3.11       01 April 2014 https://downloads.sourceforge.net/qjackctl/qjackctl-0.3.11.tar.gz
qjson                     0.9.0        24 May 2015  https://github.com/flavio/qjson/archive/0.9.0.tar.gz
qmlkonsole                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/qmlkonsole-23.08.5.tar.xz
qpdf                      11.9.0       25 February 2024 https://github.com/qpdf/qpdf/releases/download/v11.9.0/qpdf-11.9.0.tar.gz
qps                       2.2.0        07 November 2020 https://github.com/lxqt/qps/releases/download/2.2.0/qps-2.2.0.tar.xz
qqc2breezestyle           5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/qqc2-breeze-style-5.27.9.tar.xz
qqc2desktopstyle          5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/qqc2-desktop-style-5.115.0.tar.xz
qqwing                    1.3.4        09 August 2015 https://github.com/stephenostermiller/qqwing/archive/v1.3.4.zip
qrencode                  4.1.1        22 December 2021 https://fukuchi.org/works/qrencode/qrencode-4.1.1.tar.bz2
qsynth                    0.5.5        16 March 2019 https://downloads.sourceforge.net/qsynth/qsynth-0.5.5.tar.gz
qt                        6.7.0        02 April 2024 https://download.qt-project.org/official_releases/qt/6.7/6.7.0/single/qt-everywhere-6.7.0.tar.xz
qterminal                 1.1.0        30 August 2022 https://github.com/lxqt/qterminal/releases/download/1.1.0/qterminal-1.1.0.tar.xz
qtermwidget               1.4.0        02 February 2024 https://github.com/lxqt/qtermwidget/releases/download/1.4.0/qtermwidget-1.4.0.tar.xz
qtgstreamer               1.2.0        10 July 2015 http://gstreamer.freedesktop.org/src/qt-gstreamer/qt-gstreamer-1.2.0.tar.xz
qtwebengine               5.15.13      10 March 2023 https://anduin.linuxfromscratch.org/BLFS/qtwebengine/qtwebengine-5.15.13.tar.xz
quadkonsole               2.0.3        01 June 2014 http://nomis80.org/quadkonsole/quadkonsole-2.0.3.tar.bz2
quadrapassel              40.2         11 June 2021 https://download.gnome.org/sources/quadrapassel/40/quadrapassel-40.2.tar.xz
quagga                    1.2.2        02 January 2018 http://download.savannah.gnu.org/releases/quagga/quagga-1.2.2.tar.gz
quazip                    1.3          24 April 2022 https://github.com/stachenov/quazip/archive/refs/tags/v1.3.tar.gz
quelcom                   0.4.0        01 November 2012 http://www.etse.urv.es/~dmanye/quelcom/src/quelcom-0.4.0.tar.gz
quodlibet                 3.9.1        28 July 2017 https://github.com/quodlibet/quodlibet/releases/download/release-3.9.1/quodlibet-3.9.1.tar.gz
quota                     4.05         01 April 2019 https://sourceforge.net/projects/linuxquota/files/quota-tools/4.05/quota-4.05.tar.gz
quvi                      0.9.5        09 June 2016 https://sourceforge.net/projects/quvi/files/0.9/quvi/quvi-0.9.5.tar.xz
qwt                       6.0.2        01 December 2012 http://sourceforge.net/projects/qwt/files/qwt/6.0.2/qwt-6.0.2.tar.bz2
r                         4.3.2        30 January 2024 https://cran.r-project.org/src/base/R-4/R-4.3.2.tar.gz
rabbit                    3.0.0        28 May 2020  https://rubygems.org/downloads/rabbit-3.0.0.gem
racc                      1.5.2        15 April 2021 https://rubygems.org/downloads/racc-1.5.2.gem
rack                      3.0.7        06 April 2023 https://rubygems.org/downloads/rack-3.0.7.gem
rackaccept                0.4.5        04 August 2018 https://rubygems.org/downloads/rack-accept-0.4.5.gem
rackcomponent             0.5.0        18 February 2019 https://rubygems.org/downloads/rack-component-0.5.0.gem
rackprotection            2.1.0        15 April 2021 https://rubygems.org/downloads/rack-protection-2.1.0.gem
racktest                  1.1.0        13 October 2018 https://rubygems.org/downloads/rack-test-1.1.0.gem
rage                      0.4.0        08 February 2022 https://download.enlightenment.org/rel/apps/rage/rage-0.4.0.tar.xz
ragel                     6.10         27 March 2017 http://www.colm.net/files/ragel/ragel-6.10.tar.gz
rails                     7.0.1        05 February 2022 https://rubygems.org/downloads/rails-7.0.1.gem
railsdomtesting           2.0.3        13 October 2018 https://rubygems.org/downloads/rails-dom-testing-2.0.3.gem
railshtmlsanitizer        1.3.0        28 May 2020  https://rubygems.org/downloads/rails-html-sanitizer-1.3.0.gem
railties                  6.1.3.1      15 April 2021 https://rubygems.org/downloads/railties-6.1.3.1.gem
rainbow                   3.0.0        09 January 2018 https://rubygems.org/downloads/rainbow-3.0.0.gem
rak                       1.0.21       01 June 2014 rak-1.0.21.tar.xz
rake                      13.0.6       24 September 2022 https://rubygems.org/downloads/rake-13.0.6.gem
randrproto                1.5.0        17 May 2015  https://xorg.freedesktop.org/releases/individual/proto/randrproto-1.5.0.tar.gz
rant                      0.5.7        01 December 2017 https://rubygems.org/downloads/rant-0.5.7.gem
raptor2                   2.0.16       04 March 2023 https://download.librdf.org/source/raptor2-2.0.16.tar.gz
rarian                    0.8.1        01 January 2013 http://ftp.gnome.org/pub/gnome/sources/rarian/0.8/rarian-0.8.1.tar.bz2
rasmol                    2.7.5.2      01 June 2014 http://www.rasmol.org/software/RasMol_2.7.5.2.tar.gz
rasqal                    0.9.30       01 January 2014 http://download.librdf.org/source/rasqal-0.9.30.tar.gz
ratpoison                 1.4.9        31 July 2018 http://download.savannah.nongnu.org/releases/ratpoison/ratpoison-1.4.9.tar.xz
rawrec                    0.9.991      01 June 2014 https://sourceforge.net/projects/rawrec/files/rawrec/rawrec-0.9.991/rawrec-0.9.991.tar.gz
rbcat                     0.2.1        25 November 2019 https://rubygems.org/downloads/rbcat-0.2.1.gem
rcairo                    1.17.13      30 January 2024 https://www.cairographics.org/releases/rcairo-1.17.13.tar.gz
rcov                      1.0.0        31 October 2017 https://rubygems.org/downloads/rcov-1.0.0.gem
rdesktop                  1.9.0        12 October 2019 https://github.com/rdesktop/rdesktop/releases/download/v1.9.0/rdesktop-1.9.0.tar.gz
rdtool                    0.6.38       17 January 2019 https://rubygems.org/downloads/rdtool-0.6.38.gem
re2c                      2.1.1        28 March 2021 https://github.com/skvadrik/re2c/releases/download/2.1.1/re2c-2.1.1.tar.xz
readedid                  2.0.0        01 June 2014 http://polypux.org/projects/read-edid/read-edid-2.0.0.tar.gz
readline                  8.2          27 September 2022 https://ftp.gnu.org/pub/gnu/readline/readline-8.2.tar.gz
recode                    3.7.1        12 May 2019  https://github.com/rrthomas/recode/releases/download/v3.7.1/recode-3.7.1.tar.gz
recordmydesktop           0.3.8.1      01 June 2014 http://sourceforge.net/projects/recordmydesktop/files/recordmydesktop/0.3.8.1/recordmydesktop-0.3.8.1.tar.gz
recordproto               1.14.2       01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/recordproto-1.14.2.tar.bz2
recutils                  1.9          17 April 2022 https://ftp.gnu.org/pub/gnu/recutils/recutils-1.9.tar.gz
redcloth                  4.3.2        21 September 2017 https://rubygems.org/downloads/RedCloth-4.3.2.gem
redis                     5.0.7        14 October 2023 https://rubygems.org/downloads/redis-5.0.7.gem
redland                   1.0.17       01 August 2015 http://download.librdf.org/source/redland-1.0.17.tar.gz
redmine                   3.4.10       23 April 2019 http://www.redmine.org/releases/redmine-3.4.10.tar.gz
reft                      0.11         01 June 2014 http://www.rafkind.com/jon/tar/reft-0.11.tar.gz
reiserfsprogs             3.6.27       03 August 2017 https://www.kernel.org/pub/linux/kernel/people/jeffm/reiserfsprogs/v3.6.27/reiserfsprogs-3.6.27.tar.xz
relion                    23.02.2024   20 December 2022 https://github.com/3dem/relion/archive/refs/tags/23.02.2024.tar.gz
rendercheck               1.5          12 June 2015 http://xorg.freedesktop.org/releases/individual/app/rendercheck-1.5.tar.bz2
renderproto               0.11         01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/renderproto-0.11.tar.bz2
reportbuilder             1.9          17 June 2020 https://rubygems.org/downloads/report_builder-1.9.gem
reportlab                 1.20         01 June 2014 http://www.reportlab.org/ftp/ReportLab_1_20.tgz
requests                  2.29.0       28 April 2023 https://files.pythonhosted.org/packages/4c/d2/70fc708727b62d55bc24e43cc85f073039023212d482553d853c44e57bdb/requests-2.29.0.tar.gz
rerun                     0.14.0       02 April 2024 https://rubygems.org/downloads/rerun-0.14.0.gem
resmgr                    1.0          01 June 2014 ftp://ftp.lst.de/pub/people/okir/resmgr/resmgr-1.0.tar.bz2
resourceproto             1.2.0        01 June 2014 http://xorg.freedesktop.org/releases/individual/proto/resourceproto-1.2.0.tar.bz2
rest                      0.9.1        19 June 2022 https://download.gnome.org/sources/rest/0.9/rest-0.9.1.tar.xz
restclient                2.1.0        28 May 2020  https://rubygems.org/downloads/rest-client-2.1.0.gem
retrogtk                  1.0.1        30 November 2020 https://download.gnome.org/sources/retro-gtk/1.0/retro-gtk-1.0.1.tar.xz
rex                       1.4.0        09 March 2016 http://www.cpan.org/authors/id/F/FE/FERKI/Rex-1.4.0.tar.gz
rexml                     3.2.5        05 May 2021  https://rubygems.org/downloads/rexml-3.2.5.gem
rezound                   0.13.1beta   31 October 2017 https://sourceforge.net/projects/rezound/files/ReZound/0.13.1beta/rezound-0.13.1beta.tar.gz
rfkill                    0.5          24 October 2018 https://mirrors.edge.kernel.org/pub/software/network/rfkill/rfkill-0.5.tar.xz
rfpdf                     1.5.3f       01 June 2014 http://zeropluszero.com/software/fpdf/rfpdf153g.tar.gz
rgb                       1.1.0        31 October 2022 https://xorg.freedesktop.org/releases/individual/app/rgb-1.1.0.tar.xz
rhythmbox                 3.4.7        16 April 2023 https://download.gnome.org/sources/rhythmbox/3.4/rhythmbox-3.4.7.tar.xz
rili                      2.0.1        28 May 2015  https://sourceforge.net/projects/ri-li/files/Ri-li%20Linux_Unix/Ri-li%20V2.0.1/Ri-li-2.0.1.tar.bz2
rinruby                   2.1.0        19 August 2018 https://rubygems.org/downloads/rinruby-2.1.0.gem
ripoff                    0.8.3        01 January 2013 https://sourceforge.net/projects/ripoffc/files/RipOff/0.8.3/ripoff-0.8.3.tar.gz
ripperx                   2.7.2        01 June 2014 http://sourceforge.net/projects/ripperx/
rison                     2.1.0        01 December 2017 https://rubygems.org/downloads/rison-2.1.0.gem
ristretto                 0.13.1       17 May 2023  https://archive.xfce.org/src/apps/ristretto/0.13/ristretto-0.13.1.tar.bz2
rkward                    0.7.1        23 February 2020 https://download.kde.org/stable/rkward/0.7.1/src/rkward-0.7.1.tar.gz
rlog                      1.3.7        01 June 2014 http://www.arg0.net/rlog/rlog-1.3.7.tar.gz
rlwrap                    0.37         01 June 2014 http://utopia.knoware.nl/~hlub/uck/rlwrap/rlwrap-0.37.tar.gz
rmagick                   4.2.2        15 April 2021 https://rubygems.org/downloads/rmagick-4.2.2.gem
rman                      3.2          01 June 2014 http://switch.dl.sourceforge.net/sourceforge/polyglotman/rman-3.2.tar.gz
rmovie                    0.5.1        01 December 2017 https://rubygems.org/downloads/rmovie-0.5.1.gem
rnalila                   0.2          26 January 2018 https://github.com/mtw/RNAlila/releases/RNAlila-0.2.tar.xz
rnaz                      2.1          29 June 2017 https://www.tbi.univie.ac.at/software/RNAz/RNAz-2.1.tar.gz
robodoc                   4.99.34      01 May 2014  http://sourceforge.net/projects/robodoc/
rocksndiamonds            3.2.4        01 November 2012 http://www.artsoft.org/rocksndiamonds/download.html
rocs                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/rocs-23.08.5.tar.xz
roo                       2.8.3        28 May 2020  https://rubygems.org/downloads/roo-2.8.3.gem
rope                      0.11.0       24 December 2018 https://files.pythonhosted.org/packages/52/8d/2ebe70e55742a46813952493f8fc86ff2800ccc105e2dfcb25298f7eeb72/rope-0.11.0.tar.gz
rosegarden                20.12        10 January 2021 https://sourceforge.net/projects/rosegarden/files/rosegarden/20.12/rosegarden-20.12.tar.bz2
rouge                     3.26.1       26 September 2021 https://rubygems.org/downloads/rouge-3.26.1.gem
roxclib                   2.1.10       21 February 2016 http://www.kerofin.demon.co.uk/rox/ROX-CLib-2.1.10.tar.gz
roxsession                0.30         01 June 2014 http://sourceforge.net/project/showfiles.php?group_id=7023
roxterm                   3.8.3        04 September 2022 https://github.com/realh/roxterm/archive/3.8.3.tar.gz
rpcbind                   1.2.5        03 September 2018 https://sourceforge.net/projects/rpcbind/files/rpcbind/1.2.5/rpcbind-1.2.5.tar.bz2
rpcsvcproto               1.4.2        01 July 2020 https://github.com/thkukuk/rpcsvc-proto/releases/download/v1.4.2/rpcsvc-proto-1.4.2.tar.xz
rpm                       4.18.0       07 November 2022 http://ftp.rpm.org/releases/rpm-4.18.x/rpm-4.18.0.tar.bz2
rrdtool                   1.2.11       01 June 2014 http://people.ee.ethz.ch/~oetiker/webtools/rrdtool/pub/rrdtool-1.2.11.tar.gz
rspec                     3.10.0       15 April 2021 https://rubygems.org/downloads/rspec-3.10.0.gem
rspeccore                 3.10.1       15 April 2021 https://rubygems.org/downloads/rspec-core-3.10.1.gem
rspecexpectations         3.10.1       15 April 2021 https://rubygems.org/downloads/rspec-expectations-3.10.1.gem
rspecsupport              3.10.2       15 April 2021 https://rubygems.org/downloads/rspec-support-3.10.2.gem
rst2html5                 2.0.1        02 March 2024 https://files.pythonhosted.org/packages/bb/82/a85a9664cced2dce7b9d8895f6cace6c2501072a320342d7edcb6d7ce295/rst2html5-2.0.1.tar.gz
rstart                    1.0.6        04 April 2022 https://www.x.org/releases/individual/app/rstart-1.0.6.tar.xz
rsync                     3.3.0        07 April 2024 https://rsync.samba.org/ftp/rsync/rsync-3.3.0.tar.gz
rtorrent                  01.10.2017   30 September 2017 https://github.com/rakshasa/rtorrent-01.10.2017
rtranscoder               0.1.3        01 December 2017 https://rubygems.org/downloads/rtranscoder-0.1.3.gem
ruamelyaml                0.17.9       13 June 2021 https://files.pythonhosted.org/packages/ea/7f/4bcd7276603b4324ac12839a949b3e58f03cda1d87218c89a8a1efe31c1a/ruamel.yaml-0.17.9.tar.gz
rubberband                1.8.1        17 April 2018 https://github.com/falkTX/rubberband/archive/v1.8.1.tar.gz
rubinius                  5.0          24 April 2021 https://github.com/rubinius/rubinius/releases/download/v5.0/rubinius-5.0.tar.bz2
rubocop                   1.13.0       24 April 2021 https://rubygems.org/downloads/rubocop-1.13.0.gem
ruby                      3.3.0        07 March 2024 https://cache.ruby-lang.org/pub/ruby/3.3/ruby-3.3.0.tar.xz
ruby2d                    0.9.2        21 February 2022 https://rubygems.org/downloads/ruby2d-0.9.2.gem
ruby2js                   4.1.7        05 October 2021 https://rubygems.org/downloads/ruby2js-4.1.7.gem
rubygame                  2.6.4        01 December 2017 https://rubygems.org/downloads/rubygame-2.6.4.gem
rubygems                  3.5.7        24 March 2024 https://rubygems.org/rubygems/rubygems-3.5.7.tgz
rubygnome                 3.4.7        01 August 2021 https://github.com/ruby-gnome/ruby-gnome/archive/refs/tags/3.4.7.tar.gz
rubygr                    0.0.26       15 April 2021 https://rubygems.org/downloads/ruby-gr-0.0.26.gem
rubygraphviz              1.2.5        28 May 2020  https://rubygems.org/downloads/ruby-graphviz-1.2.5.gem
rubyinline                3.12.5       28 May 2020  https://rubygems.org/downloads/RubyInline-3.12.5.gem
rubyjs                    0.8.0        01 December 2017 https://rubygems.org/downloads/rubyjs-0.8.0.gem
rubyprogressbar           1.11.0       15 April 2021 https://rubygems.org/downloads/ruby-progressbar-1.11.0.gem
rubypwsh                  0.8.0        15 April 2021 https://rubygems.org/downloads/ruby-pwsh-0.8.0.gem
rubyrc4                   0.1.5        22 July 2020 https://rubygems.org/downloads/ruby-rc4-0.1.5.gem
rubystats                 0.3.0        26 November 2019 https://rubygems.org/downloads/rubystats-0.3.0.gem
rubytorrent               0.3          02 December 2017 https://rubygems.org/downloads/rubytorrent-0.3.gem
rubyxosd                  1.1.0        01 May 2014  https://rubyforge.org/projects/ruby-xosd/
rubyzip                   2.3.0        28 May 2020  https://rubygems.org/downloads/rubyzip-2.3.0.gem
rungetty                  1.2          01 June 2014 http://packages.debian.org/testing/admin/rungetty.html
runit                     2.1.2        19 October 2019 http://smarden.org/runit/runit-2.1.2.tar.gz
ruport                    1.7.1        01 December 2017 https://rubygems.org/downloads/ruport-1.7.1.gem
rust                      1.77.1       08 April 2024 https://github.com/rust-lang/rust
ruvi                      0.4.12       01 June 2014 https://rubygems.org/downloads/ruvi-0.4.12.gem
rxvt                      2.7.10       01 May 2014  https://sourceforge.net/projects/rxvt/files/rxvt-dev/2.7.10/rxvt-2.7.10.tar.gz
rxvtunicode               9.31         05 January 2023 http://dist.schmorp.de/rxvt-unicode/rxvt-unicode-9.31.tar.bz2
rygel                     0.42.2       01 April 2023 https://download.gnome.org/sources/rygel/0.42/rygel-0.42.2.tar.xz
sakura                    3.8.7        02 April 2024 https://launchpad.net/sakura/trunk/3.8.7/+download/sakura-3.8.7.tar.gz
samba                     4.20.0       27 March 2024 https://us1.samba.org/samba/ftp/stable/samba-4.20.0.tar.gz
samtools                  1.19.2       05 February 2024 https://sourceforge.net/projects/samtools/files/samtools/1.19.2/samtools-1.19.2.tar.bz2
sanebackends              1.2.1        19 May 2023  https://gitlab.com/sane-project/backends/uploads/110fc43336d0fb5e514f1fdc7360dd87/sane-backends-1.2.1.tar.gz
sanefrontends             1.0.14       25 August 2020 https://gitlab.com/sane-project/frontends/uploads/14e5c5a9205b10bd3df04501852eab28/sane-frontends-1.0.14.tar.gz
sash                      3.7          01 May 2014  http://members.tip.net.au/~dbell/programs/sash-3.7.tar.gz
sass                      3.7.4        03 May 2019  https://rubygems.org/downloads/sass-3.7.4.gem
sassrails                 6.0.0        28 May 2020  https://rubygems.org/downloads/sass-rails-6.0.0.gem
sawfish                   1.12.0       27 December 2021 https://download.tuxfamily.org/sawfish/sawfish_1.12.0.tar.xz
sbc                       1.5          10 December 2020 https://mirrors.edge.kernel.org/pub/linux/bluetooth/sbc-1.5.tar.xz
schroedinger              1.0.11       19 January 2016 https://launchpad.net/schroedinger/trunk/1.0.11/+download/schroedinger-1.0.11.tar.gz
scim                      1.4.18       19 March 2019 https://github.com/scim-im/scim/archive/1.4.18.tar.gz
scintilla                 414          10 October 2018 https://www.scintilla.org/scintilla414.tgz
scipy                     1.0.0        26 October 2017 https://github.com/scipy/scipy/releases/download/v1.0.0/scipy-1.0.0.tar.xz
scite                     4.1.4        10 March 2019 https://www.scintilla.org/scite414.tgz
scons                     4.7.0        20 March 2024 https://downloads.sourceforge.net/scons/SCons-4.7.0.tar.gz
scourge                   0.15         01 December 2012 http://scourge.svn.sourceforge.net/viewvc/scourge/scourge2.tar.gz
screen                    4.9.1        18 August 2023 https://ftp.gnu.org/pub/gnu/screen/screen-4.9.1.tar.gz
screengrab                2.4.0        30 August 2022 https://github.com/lxqt/screengrab/releases/download/2.4.0/screengrab-2.4.0.tar.xz
scribus                   1.6.1        07 January 2024 https://downloads.sourceforge.net/scribus/scribus-1.6.1.tar.xz
scripts                   1.0.1        01 May 2014  http://xorg.freedesktop.org/releases/individual/app/scripts-1.0.1.tar.bz2
scrnsaverproto            1.2.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/proto/scrnsaverproto-1.2.2.tar.bz2
scrollkeeper              0.3.14       01 March 2014 ftp://ftp.gnome.org/pub/GNOME/sources/scrollkeeper/0.3/scrollkeeper-0.3.14.tar.bz2
scrot                     0.8          01 May 2014  http://linuxbrit.co.uk/downloads/scrot-0.8.tar.gz
scruffy                   0.2.6        02 December 2017 https://rubygems.org/downloads/scruffy-0.2.6.gem
scummvm                   2.8.1        01 April 2024 https://downloads.scummvm.org/frs/scummvm/2.8.1/scummvm-2.8.1.tar.xz
sddm                      0.21.0       27 February 2024 https://github.com/sddm/sddm/releases/download/v0.21.0/sddm-0.21.0.tar.xz
sddmkcm                   5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/sddm-kcm-5.27.9.tar.xz
sdl                       1.2.15       01 June 2013 https://www.libsdl.org/release/SDL-1.2.15.tar.gz
sdl12compatrelease        1.2.68       28 March 2024 https://github.com/libsdl-org/sdl12-compat/archive/refs/tags/release-1.2.68/sdl12-compat-release-1.2.68.tar.gz
sdl2                      2.30.2       04 April 2024 https://github.com/libsdl-org/SDL/releases/download/release-2.30.2/SDL2-2.30.2.tar.gz
sdl2gfx                   1.0.4        01 November 2018 https://sourceforge.net/projects/sdl2gfx/files/SDL2_gfx-1.0.4.tar.gz
sdl2image                 2.6.3        08 February 2023 https://www.libsdl.org/projects/SDL_image/release/SDL2_image-2.6.3.tar.gz
sdl2mixer                 2.8.0        25 February 2024 https://github.com/libsdl-org/SDL_mixer/releases/download/release-2.8.0/SDL2_mixer-2.8.0.tar.gz
sdl2net                   2.2.0        20 September 2022 https://www.libsdl.org/projects/SDL_net/release/SDL2_net-2.2.0.tar.gz
sdl2ttf                   2.20.2       09 February 2023 https://github.com/libsdl-org/SDL_ttf/releases/download/release-2.20.2/SDL2_ttf-2.20.2.tar.gz
sdlgfx                    2.0.22       01 May 2014  http://www.ferzkopp.net/Software/SDL_gfx-2.0/SDL_gfx-2.0.22.tar.gz
sdlimage                  1.2.12       01 May 2014  http://www.libsdl.org/projects/SDL_image/release/SDL_image-1.2.12.tar.gz
sdlmixer                  1.2.12       01 December 2012 https://www.libsdl.org/projects/SDL_mixer/release/SDL_mixer-1.2.12.tar.gz
sdlmm                     0.1.8        05 April 2024 https://sourceforge.net/projects/sdlmm/files/SDLmm/0.1.8/SDLmm-0.1.8.tar.bz2
sdlnet                    1.2.8        01 November 2012 https://www.libsdl.org/projects/SDL_net/release/SDL_net-1.2.8.tar.gz
sdlpango                  0.1.2        01 November 2012 http://sourceforge.net/projects/sdlpango/
sdlperl                   2.2.0        16 July 2016 http://backpan.perl.org/authors/id/D/DG/DGOEHRIG/SDL_Perl-2.2.0.tar.gz
sdlpop                    18.06.2018   16 June 2018 https://github.com/NagyD/SDLPoP
sdltty                    05.04.2024   05 April 2024 https://github.com/Grumbel/SDL_tty/SDL_tty-05.04.2024.tar.xz
sdoc                      2.1.0        15 April 2021 https://rubygems.org/downloads/sdoc-2.1.0.gem
sdparm                    1.11         23 April 2021 http://sg.danny.cz/sg/p/sdparm-1.11.tar.xz
seaborn                   0.8.1        28 June 2018 https://files.pythonhosted.org/packages/10/01/dd1c7838cde3b69b247aaeb61016e238cafd8188a276e366d36aa6bcdab4/seaborn-0.8.1.tar.gz
seahorse                  42.0         23 May 2022  https://download.gnome.org/sources/seahorse/42/seahorse-42.0.tar.xz
seahorsenautilus          3.11.92      01 March 2014 http://ftp.gnome.org/pub/GNOME/sources/seahorse-nautilus/3.11/seahorse-nautilus-3.11.92.tar.xz
seamonkey                 2.53.1       28 February 2020 https://ftp.mozilla.org/pub/seamonkey/releases/2.53.1/source/seamonkey-2.53.1.source.tar.xz
seatd                     21.02.2024   20 February 2024 https://github.com/kennylevinsen/seatd/releases/download/3.2.2/seatd-21.02.2024.tar.xz
seatris                   0.0.14       01 May 2014  http://www.earth.li/projectpurple/files/seatris-0.0.14.tar.gz
sed                       4.9          06 November 2022 https://ftp.gnu.org/gnu/sed/sed-4.9.tar.xz
segatex                   8.650        05 April 2024 https://sourceforge.net/projects/segatex/files/segatex/8.650/segatex-8.650.tar.gz
semanticpuppet            1.0.3        15 April 2021 https://rubygems.org/downloads/semantic_puppet-1.0.3.gem
semantik                  1.0.3        15 June 2018 https://waf.io/semantik-1.0.3.tar.bz2
sendmail                  8.17.1       17 August 2021 ftp://ftp.sendmail.org/pub/sendmail/sendmail.8.17.1.tar.gz
sensorsapplet             3.0.0        19 February 2024 http://downloads.sourceforge.net/sensors-applet/sensors-applet-3.0.0.tar.gz
seqtk                     1.3          02 January 2020 https://github.com/lh3/seqtk/archive/v1.3.tar.gz
sequel                    5.52.0       13 January 2022 https://rubygems.org/downloads/sequel-5.52.0.gem
serf                      1.3.9        03 January 2019 https://archive.apache.org/dist/serf/serf-1.3.9.tar.bz2
sessreg                   1.1.3        31 October 2022 https://xorg.freedesktop.org/releases/individual/app/sessreg-1.1.3.tar.xz
setconf                   0.7.6        24 December 2018 https://files.pythonhosted.org/packages/e2/13/e3d15834bdbbfcfff4a93639541817be2db36263bfb92868187e2db35df2/setconf-0.7.6.tar.gz
setuptools                69.5.1       14 April 2024 https://files.pythonhosted.org/packages/d6/4f/b10f707e14ef7de524fe1f8988a294fb262a29c9b5b12275c7e188864aed/setuptools-69.5.1.tar.gz
setxkbmap                 1.3.4        20 May 2023  https://www.x.org/releases/individual/app/setxkbmap-1.3.4.tar.xz
sg3utils                  1.47         17 November 2021 http://sg.danny.cz/sg/p/sg3_utils-1.47.tar.xz
sgmlcommon                0.6.3        10 July 2015 ftp://sources.redhat.com/pub/docbook-tools/new-trials/SOURCES/sgml-common-0.6.3.tgz
shaderc                   15.03.2024   15 March 2024 shaderc-15.03.2024
shadow                    4.15.1       26 March 2024 https://github.com/shadow-maint/shadow/releases/download/4.15.1/shadow-4.15.1.tar.xz
shapelib                  1.3.0        01 November 2013 http://download.osgeo.org/shapelib/shapelib-1.3.0.tar.gz
shareddesktopontologies   0.11.0       01 October 2013 http://sourceforge.net/projects/oscaf/files/shared-desktop-ontologies/0.11.0/shared-desktop-ontologies-0.11.0.tar.bz2
sharedmimeinfo            2.4          11 February 2024 https://gitlab.freedesktop.org/xdg/shared-mime-info/-/archive/2.4/shared-mime-info-2.4.tar.gz
sharutils                 4.15.2       21 June 2020 https://ftp.gnu.org/gnu/sharutils/sharutils-4.15.2.tar.xz
shed                      1.15         01 May 2014  https://sourceforge.net/projects/shed/files/shed/shed%201.15/shed-1.15.tar.gz
shepherd                  0.9.2        12 September 2022 https://ftp.gnu.org/pub/gnu/shepherd/shepherd-0.9.2.tar.gz
shim                      15.8         22 January 2024 https://github.com/rhboot/shim/releases/download/15.8/shim-15.8.tar.bz2
shindo                    0.3.10       15 April 2021 https://rubygems.org/downloads/shindo-0.3.10.gem
shine                     21.05.2015   20 May 2015  shine-21.05.2015
shipping                  1.6.0        01 December 2017 https://rubygems.org/downloads/shipping-1.6.0.gem
shishi                    1.0.3        09 August 2022 https://ftp.gnu.org/pub/gnu/shishi/shishi-1.0.3.tar.gz
shmux                     1.0.2        01 November 2012 http://web.taranis.org/shmux/dist/shmux-1.0.2.tgz
shntool                   3.0.7        01 May 2014  http://www.etree.org/shnutils/shntool/dist/src/shntool-3.0.7.tar.gz
shorturl                  1.0.0        01 May 2014  https://rubygems.org/downloads/shorturl-1.0.0.gem
shotcut                   18.12.23     18 January 2019 https://github.com/mltframework/shotcut/archive/shotcut-18.12.23.tar.gz
shotgun                   0.9.2        02 August 2017 https://rubygems.org/downloads/shotgun-0.9.2.gem
shotwell                  0.32.3       16 November 2023 https://download.gnome.org/sources/shotwell/0.32/shotwell-0.32.3.tar.xz
showfont                  1.0.6        01 September 2022 https://www.x.org/releases/individual/app/showfont-1.0.6.tar.xz
sickle                    1.33         02 Feb 2020  https://github.com/najoshi/sickle/archive/v1.33.tar.gz
sidekiq                   6.2.1        15 April 2021 https://rubygems.org/downloads/sidekiq-6.2.1.gem
signonkwalletextension    23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/signon-kwallet-extension-23.08.5.tar.xz
sigopt                    1.3.0        04 April 2016 https://pypi.python.org/packages/source/s/sigopt/sigopt-1.3.0.tar.gz#md5=ccd67d5c514c1a20659f6217686f0782
silk                      3.10.1       08 March 2015 https://tools.netsa.cert.org/releases/silk-3.10.1.tar.gz
simplescan                44.0         19 May 2023  https://download.gnome.org/sources/simple-scan/44/simple-scan-44.0.tar.xz
simsoup                   0.3          01 May 2014  http://www.simsoup.info/SimSoup-0.3.tar.gz
sinatra                   2.1.0        01 February 2021 https://rubygems.org/downloads/sinatra-2.1.0.gem
sinatraactiverecord       2.0.22       15 April 2021 https://rubygems.org/downloads/sinatra-activerecord-2.0.22.gem
sinatracontrib            2.1.0        15 April 2021 https://rubygems.org/downloads/sinatra-contrib-2.1.0.gem
sinatrareloader           1.0          26 December 2018 https://rubygems.org/downloads/sinatra-reloader-1.0.gem
sip                       6.8.3        03 March 2024 https://files.pythonhosted.org/packages/99/85/261c41cc709f65d5b87669f42e502d05cc544c24884121bc594ab0329d8e/sip-6.8.3.tar.gz
sipwitch                  1.9.1        01 May 2014  http://ftp.gnu.org/gnu/sipwitch/sipwitch-1.9.1.tar.gz
sisiya                    0.4-21       01 May 2014  http://ovh.dl.sourceforge.net/sourceforge/sisiya/sisiya-0.4-21.tar.gz
sitemapgenerator          6.1.2        17 June 2020 https://rubygems.org/downloads/sitemap_generator-6.1.2.gem
sithwm                    1.2.3        01 May 2014  http://sithwm.darkside.no/sn/sithwm-1.2.3.tgz
six                       1.16.0       06 May 2021  https://files.pythonhosted.org/packages/71/39/171f1c67cd00715f190ba0b100d606d440a28c93c7714febeca8b79af85e/six-1.16.0.tar.gz
skanlite                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/skanlite-23.08.5.tar.xz
skanpage                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/skanpage-23.08.5.tar.xz
skijump                   0.2.0        01 May 2014  http://prdownloads.sourceforge.net/skijump/skijump-0.2.0.tar.gz
slang                     2.3.3        28 November 2022 https://www.jedsoft.org/releases/slang/slang-2.3.3.tar.bz2
slaptget                  0.10.2f      01 May 2014  http://software.jaos.org/source/slapt-get/slapt-get-0.10.2f.tar.gz
slave                     0.2.0        01 May 2014  http://www.codeforpeople.com/lib/ruby/slave/slave-0.2.0.tgz
sleepypenguin             3.5.2        28 May 2020  https://rubygems.org/downloads/sleepy_penguin-3.5.2.gem
slib                      3b5          16 December 2018 http://groups.csail.mit.edu/mac/ftpdir/scm/slib-3b5.tar.gz
slideshow                 0.1.0        01 May 2014  https://github.com/ext/slideshow
slim                      4.1.0        28 May 2020  https://rubygems.org/downloads/slim-4.1.0.gem
slocate                   3.1          01 January 2014 http://slocate.trakker.ca/files/slocate-3.1.tar.gz
sloccount                 2.26         01 May 2014  http://sourceforge.net/projects/sloccount/files/sloccount-2.26.tar.gz
slop                      4.8.2        15 April 2021 https://rubygems.org/downloads/slop-4.8.2.gem
slurp                     1.1.0        22 February 2019 https://github.com/emersion/slurp/archive/v1.1.0.tar.gz
smake                     1.2.5        07 February 2016 http://sourceforge.net/projects/s-make/files/smake-1.2.5.tar.gz
smalltalk                 3.2.5        01 May 2023  https://ftp.gnu.org/gnu/smalltalk/smalltalk-3.2.5.tar.xz
smartmontools             7.3          07 March 2022 https://downloads.sourceforge.net/smartmontools/smartmontools-7.3.tar.gz
smc                       1.9          01 December 2012 http://downloads.sourceforge.net/smclone/smc-1.9.tar.bz2
smf                       0.15.15      26 November 2019 https://rubygems.org/downloads/smf-0.15.15.gem
smokeqt                   4.14.3       15 July 2015 ftp://gd.tuwien.ac.at/kde/stable/4.14.3/src/smokeqt-4.14.3.tar.xz
smpeg                     18.11.2011   01 March 2013 http://www.3ddownloads.com/linuxgames/loki/open-source/smpeg/smpeg-18.11.2011.tar.gz
smplayer                  21.1.0       17 January 2021 https://downloads.sourceforge.net/smplayer/smplayer-21.1.0.tar.bz2
smproxy                   1.0.7        16 October 2022 https://www.x.org/releases/individual/app/smproxy-1.0.7.tar.xz
smuxi                     0.8.11       01 May 2014  https://www.smuxi.org/jaws/data/files/smuxi-0.8.11.tar.gz
snack                     2.2.10       01 September 2013 http://www.speech.kth.se/snack/dist/snack2.2.10.tar.gz
snake3d                   0.7          01 May 2014  http://surfnet.dl.sourceforge.net/sourceforge/worms3d/snake3d-0.7.tgz
snappy                    1.0          01 April 2014 http://ftp.gnome.org/pub/gnome/sources/snappy/1.0/snappy-1.0.tar.xz
snapscreenshot            1.0.14.3     01 March 2014 http://bisqwit.iki.fi/src/arch/snapscreenshot-1.0.14.3.tar.bz2
snd                       19.8         27 November 2019 https://ccrma.stanford.edu/software/snd/snd-19.8.tar.gz
snes9x                    1.53         08 September 2017 http://files.ipherswipsite.com/snes9x/snes9x-1.53.tar.bz2
snogray                   20.04.2008   01 May 2014  http://download.savannah.gnu.org/releases/snogray/snogray-20.04.2008.tar.gz
snort                     2.9.17       19 November 2020 https://www.snort.org/downloads/snort/snort-2.9.17.tar.gz
soappy                    0.12.22      02 August 2017 https://pypi.python.org/packages/78/1b/29cbe26b2b98804d65e934925ced9810883bdda9eacba3f993ad60bfe271/SOAPpy-0.12.22.zip
solfege                   3.8.3        01 May 2014  http://www.solfege.org/Solfege/Download
solid                     5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/solid-5.115.0.tar.xz
solseek                   1127043      01 May 2014  https://www.gnome-look.org/p/1127043/
sonik                     1.0.0        01 May 2014  http://prdownloads.sourceforge.net/sonik/sonik-1.0.0.tar.gz
sonnet                    5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/sonnet-5.115.0.tar.xz
soprano                   2.9.4        01 December 2013 http://sourceforge.net/projects/soprano/files/Soprano/2.9.4/soprano-2.9.4.tar.bz2
sortversions              1.5          26 August 2017 http://search.cpan.org/CPAN/authors/id/E/ED/EDAVIS/Sort-Versions-1.5.tar.gz
soundconverter            2.1.4        20 December 2014 https://launchpad.net/soundconverter/trunk/2.1.4/+download/soundconverter-2.1.4.tar.xz
soundjuicer               3.40.0       19 June 2023 https://download.gnome.org/sources/sound-juicer/3.40/sound-juicer-3.40.0.tar.xz
soundtouch                2.3.3        02 April 2024 https://www.surina.net/soundtouch/soundtouch-2.3.3.tar.gz
sourceinstall             2.5rc2       01 May 2014  ftp://ftp.gnu.org/gnu/sourceinstall/sourceinstall-2.5rc2.tar.gz
sox                       14.4.2       12 April 2015 https://sourceforge.net/projects/sox/files/sox/14.4.2/sox-14.4.2.tar.gz
spdf                      0.2          01 May 2014  http://users.tkk.fi/~jitulkki/spdf/spdf-0.2.tar.gz
spectacle                 23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/spectacle-23.08.5.tar.xz
spectrographic            0.9.3        28 December 2019 https://files.pythonhosted.org/packages/6c/cd/5ef7c8e1d53b1d0df1a6507b267ca3bbca889bcb83395d5ddb72d6b7080e/spectrographic-0.9.3.tar.gz
speechd                   26.11.2013   01 November 2013 http://git.freebsoft.org/?p=speechd.git/speechd-26.11.2013.tar.gz
speedcrunch               0.10.1       01 May 2014  http://www.kde-apps.org/content/show.php/SpeedCrunch?content=16696
speex                     1.2.0        16 February 2017 https://downloads.xiph.org/releases/speex/speex-1.2.0.tar.gz
speexdsp                  1.2.0        10 June 2019 https://ftp.osuosl.org/pub/xiph/releases/speex/speexdsp-1.2.0.tar.gz
sphinx                    2.2.0        15 October 2019 https://files.pythonhosted.org/packages/76/42/a4465a0080e545cd152f7d3f16229d5e1300183fcb1067e4ec7e639b8605/Sphinx-2.2.0.tar.gz
spice                     0.12.8       08 August 2016 http://www.spice-space.org/download/releases/spice-0.12.8.tar.bz2
spiceprotocol             0.12.12      08 August 2016 http://spice-space.org/download/releases/spice-protocol-0.12.12.tar.bz2
spidermonkey              08.01.2007   01 June 2013 spidermonkey-08.01.2007
spirvheaders              1.3.280.0    22 March 2024 https://github.com/KhronosGroup/SPIRV-Headers/archive/refs/tags/vulkan-sdk-1.3.280.0/SPIRV-Headers-1.3.280.0.tar.gz
spirvtools                1.3.280.0    25 March 2024 https://github.com/KhronosGroup/SPIRV-Tools/archive/refs/tags/vulkan-sdk-1.3.280.0/SPIRV-Tools-1.3.280.0.tar.gz
spkg                      1.0rc9       01 May 2014  http://spkg.megous.com/dl/releases/?C=M;O=D
splint                    3.1.1        01 May 2014  http://www.splint.org/downloads/splint-3.1.1tgz
splitvt                   1.6.5        01 May 2014  http://www.devolution.com/~slouken/projects/splitvt/splitvt-1.6.5.tar.gz
spreadsheet               1.3.1        07 April 2024 https://rubygems.org/downloads/spreadsheet-1.3.1.gem
spring                    2.1.1        15 April 2021 https://rubygems.org/downloads/spring-2.1.1.gem
sprockets                 4.0.2        17 June 2020 https://rubygems.org/downloads/sprockets-4.0.2.gem
sprocketsrails            3.2.2        15 April 2021 https://rubygems.org/downloads/sprockets-rails-3.2.2.gem
spyc                      0.3beta      01 May 2014  http://spyc.sourceforge.net/
sqlite3                   1.6.1        06 March 2023 https://rubygems.org/downloads/sqlite3-1.6.1.gem
sqliteautoconf            3450300      15 April 2024 https://www.sqlite.org/2024/sqlite-autoconf-3450300.tar.gz
sqlitebrowser             3.11.0       05 February 2019 https://github.com/sqlitebrowser/sqlitebrowser/archive/sqlitebrowser-3.11.0.tar.gz
sqliteman                 1.0.1        01 May 2014  http://sqliteman.com/
sqliteruby                2.2.3        28 November 2017 https://rubygems.org/downloads/sqlite-ruby-2.2.3.gem
squashfstools             4.6.1        21 March 2022 https://github.com/plougher/squashfs-tools/archive/refs/tags/4.6.1.tar.gz
squid                     6.9          08 April 2024 http://www.squid-cache.org/Versions/v6/squid-6.9.tar.gz
sshfs                     3.7.3        29 May 2022  https://github.com/libfuse/sshfs/releases/download/sshfs-3.7.3/sshfs-3.7.3.tar.xz
sslscan                   1.8.2        01 January 2014 http://downloads.sourceforge.net/project/sslscan/sslscan/sslscan-1.8.2.tgz
ssysm                     0.2.4.3      01 May 2014  http://freshmeat.net/redir/ssysm/65338/url_tgz/ssysm-0.2.4.3.tar.gz
st                        0.8.1        19 September 2018 https://dl.suckless.org/st/st-0.8.1.tar.gz
stager                    2.0.1        01 May 2014  http://software.uninett.no/stager/download/Stager_2.0.1.tar.gz
startupnotification       0.12         01 June 2013 http://www.freedesktop.org/software/startup-notification/releases/startup-notification-0.12.tar.gz
statifier                 1.7.1        01 May 2014  http://sourceforge.net/projects/statifier/files/statifier/1.7.1/statifier-1.7.1.tar.gz
stax                      1.37         01 November 2012 http://www.gamblin.ca/staxpc/
stella                    3.7.2        01 May 2014  http://sourceforge.net/projects/stella/files/stella/3.7.2/stella-3.7.2.tar.gz
step                      23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/step-23.08.5.tar.xz
stfl                      0.23         03 October 2017 http://www.clifford.at/stfl/stfl-0.23.tar.gz
stlport                   5.2.1        24 May 2020  https://sourceforge.net/projects/stlport/files/STLport/STLport-5.2.1/STLport-5.2.1.tar.bz2
stow                      2.3.0        30 June 2019 http://ftp.gnu.org/pub/gnu/stow/stow-2.3.0.tar.gz
strace                    6.8          21 March 2024 https://github.com/strace/strace/releases/download/v6.8/strace-6.8.tar.xz
strasheela                0.8          01 March 2013 http://heanet.dl.sourceforge.net/sourceforge/strasheela/strasheela-0.8.tar.gz
stratagus                 2.2.5.5      01 November 2012 http://launchpad.net/stratagus/trunk/2.2.5.5/+download/stratagus_2.2.5.5.orig.tar.gz
streamripper              1.64.6       01 May 2014  http://sourceforge.net/projects/streamripper/files/streamripper%20%28current%29/1.64.6/streamripper-1.64.6.tar.gz
streamtuner               0.99.99      01 April 2014 http://savannah.nongnu.org/download/streamtuner/streamtuner-0.99.99.tar.gz
strigi                    0.7.8        01 January 2014 http://www.vandenoever.info/software/strigi/strigi-0.7.8.tar.bz2
strongswan                4.6.4        01 June 2012 http://download.strongswan.org/strongswan-4.6.4.tar.bz2
stunnel                   5.71         26 September 2023 https://www.stunnel.org/downloads/stunnel-5.71.tar.gz
sublib                    0.9          01 May 2014  http://sourceforge.net/projects/sublib/files/sublib/0.9/
subtitlecomposer          05.04.2024   10 October 2017 https://github.com/maxrd2/subtitlecomposer/subtitlecomposer-05.04.2024.tar.xz
subtitleeditor            0.40.0       01 May 2014  http://download.gna.org/subtitleeditor/0.40/subtitleeditor-0.40.0.tar.gz
subtle                    0.11.3224-xi 01 November 2012 https://subforge.org/attachments/download/81/subtle-0.11.3224-xi.tbz2
subversion                1.14.3       31 December 2023 https://www.apache.org/dist/subversion/subversion-1.14.3.tar.bz2
sudo                      1.9.13       16 February 2023 https://www.sudo.ws/dist/sudo-1.9.13.tar.gz
supertux                  0.6.1        15 December 2019 https://github.com/SuperTux/supertux/releases/download/v0.6.1/SuperTux-v0.6.1-Source.tar.gz
supybot                   0.83.1       01 May 2014  https://surfnet.dl.sourceforge.net/sourceforge/supybot/Supybot-0.83.1.tar.bz2
sushi                     46.0         06 April 2024 https://download.gnome.org/sources/sushi/46/sushi-46.0.tar.xz
suspendutils              1.0          01 September 2013 http://sourceforge.net/projects/suspend/files/suspend/suspend-1.0/suspend-utils-1.0.tar.bz2
sussen                    0.90         01 May 2014  http://dev.mmgsecurity.com/projects/sussen/
svgalib                   1.9.25       01 August 2013 http://www.svgalib.org/svgalib-1.9.25.tar.gz
svgpart                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/svgpart-23.08.5.tar.xz
sway                      1.8.1        16 March 2023 https://github.com/swaywm/sway/releases/download/1.8.1/sway-1.8.1.tar.gz
swbis                     1.13.1       06 November 2018 https://ftp.gnu.org/pub/gnu/swbis/swbis-1.13.1.tar.gz
sweep                     0.9.1        01 May 2014  http://www.metadecks.org/software/sweep/download/sweep-0.9.1.tar.bz2
sweeper                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/sweeper-23.08.5.tar.xz
swellfoop                 46.0         16 March 2024 https://download.gnome.org/sources/swell-foop/46/swell-foop-46.0.tar.xz
swig                      4.2.1        27 February 2024 https://prdownloads.sourceforge.net/swig/swig-4.2.1.tar.gz
swinput                   0.7.4        04 May 2019  http://download.savannah.nongnu.org/releases/swinput/swinput-0.7.4.tar.gz
swipl                     7.6.0-rc2    30 September 2017 http://www.swi-prolog.org/download/stable/src/swipl-7.6.0-rc2.tar.gz
swpkg                     0.51         01 May 2014  http://web.taranis.org/swpkg/dist/swpkg-0.51.tgz
syck                      1.4.1        22 September 2022 https://rubygems.org/downloads/syck-1.4.1.gem
sylpheed                  3.7.0        01 February 2018 http://sylpheed.sraoss.jp/sylpheed/v3.7/sylpheed-3.7.0.tar.xz
sympa                     6.1.25       26 November 2017 http://www.sympa.org/distribution/sympa-6.1.25.tar.gz
sympy                     1.8          12 June 2021 https://github.com/sympy/sympy/releases/download/sympy-1.8/sympy-1.8.tar.gz
synaptic                  0.84.2       10 March 2017 http://ftp.debian.org/debian/pool/main/s/synaptic/synaptic_0.84.2.tar.xz
syndication               5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/syndication-5.115.0.tar.xz
synfig                    1.2.1        08 October 2017 https://sourceforge.net/projects/synfig/files/releases/1.2.1/source/synfig-1.2.1.tar.gz
syntax                    1.2.2        01 December 2017 https://rubygems.org/downloads/syntax-1.2.2.gem
syntaxhighlighting        5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/syntax-highlighting-5.115.0.tar.xz
sysdig                    0.18.0       25 September 2017 https://github.com/draios/sysdig/archive/0.18.0.tar.gz
sysklogd                  2.2.0        10 March 2021 https://github.com/troglobit/sysklogd/releases/download/v2.2.0/sysklogd-2.2.0.tar.gz
syslinux                  6.03         16 November 2018 https://mirrors.edge.kernel.org/pub/linux/utils/boot/syslinux/syslinux-6.03.tar.xz
sysprof                   3.48.0       25 October 2023 https://download.gnome.org/sources/sysprof/3.48/sysprof-3.48.0.tar.xz
sysstat                   12.7.2       30 January 2023 http://pagesperso-orange.fr/sebastien.godard/sysstat-12.7.2.tar.xz
systemd                   255          21 January 2024 https://github.com/systemd/systemd/archive/v255/systemd-255.tar.gz
systemsettings            5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/systemsettings-5.27.9.tar.xz
systemtap                 3.2          01 November 2017 https://sourceware.org/systemtap/ftp/releases/systemtap-3.2.tar.gz
systemtoolsbackends       2.10.2       01 February 2014 http://ftp.gnome.org/pub/GNOME/sources/system-tools-backends/2.10/system-tools-backends-2.10.2.tar.gz
systemu                   2.6.5        25 November 2019 https://rubygems.org/downloads/systemu-2.6.5.gem
sysuname                  1.2.1        28 May 2020  https://rubygems.org/downloads/sys-uname-1.2.1.gem
sysvinit                  3.09         25 March 2024 https://github.com/slicer69/sysvinit/releases/download/3.09/sysvinit-3.09.tar.xz
tabbed                    0.6          30 June 2015 http://dl.suckless.org/tools/tabbed-0.6.tar.gz
tabble                    0.45         06 October 2020 http://www.rillion.net/tabble/tabble-0.45.tar.gz
taglib                    2.0.1        13 April 2024 https://taglib.org/releases/taglib-2.0.1.tar.gz
taglibruby                1.1.0        27 January 2021 https://rubygems.org/downloads/taglib-ruby-1.1.0.gem
tali                      40.5         01 February 2022 https://download.gnome.org/sources/tali/40/tali-40.5.tar.xz
talib                     0.4.10       30 July 2017 https://pypi.python.org/packages/c0/13/3d92ed6c09ed585ed58aeab5da6361ff2aeff7757d8224089bd574945716/TA-Lib-0.4.10.tar.gz
talloc                    2.4.0        21 January 2023 https://www.samba.org/ftp/talloc/talloc-2.4.0.tar.gz
tangoicontheme            0.7.2        01 May 2014  http://tango-project.org/releases/tango-icon-theme-0.7.2.tar.gz
tar                       1.35         21 January 2024 https://ftp.gnu.org/gnu/tar/tar-1.35.tar.xz
tartan                    0.2.1        01 November 2012 https://rubygems.org/downloads/tartan-0.2.1.gem
tasks                     3.3.90       01 November 2013 http://ftp.gnome.org/pub/GNOME/sources/tasks/3.3/tasks-3.3.90.tar.xz
tasque                    0.1.12       24 September 2014 http://ftp.gnome.org/pub/GNOME/sources/tasque/0.1/tasque-0.1.12.tar.xz
tcc                       0.9.26       01 August 2013 http://download.savannah.gnu.org/releases/tinycc/tcc-0.9.26.tar.bz2
tcl                       8.6.14       29 February 2024 https://downloads.sourceforge.net/tcl/tcl8.6.14.tar.gz
tcpdump                   4.99.4       08 April 2023 https://www.tcpdump.org/release/tcpdump-4.99.4.tar.gz
tcsh                      6.24.12      06 April 2024 https://astron.com/pub/tcsh/tcsh-6.24.12.tar.gz
tdb                       1.4.8        15 March 2023 https://www.samba.org/ftp/tdb/tdb-1.4.8.tar.gz
tea                       44.1.0       18 July 2017 http://semiletov.org/tea/dloads/tea-44.1.0.tar.bz2
ted                       2.21         01 May 2014  ftp://ftp.nluug.nl/pub/editors/ted/ted-2.21tar.gz
telegnome                 0.3.6        30 August 2021 https://download.gnome.org/sources/telegnome/0.3/telegnome-0.3.6.tar.xz
telepathyglib             0.24.1       16 September 2014 http://telepathy.freedesktop.org/releases/telepathy-glib/telepathy-glib-0.24.1.tar.gz
telepathylogger           0.8.0        01 October 2013 http://telepathy.freedesktop.org/releases/telepathy-logger/telepathy-logger-0.8.0.tar.bz2
telepathymissioncontrol   5.16.6       12 February 2022 https://telepathy.freedesktop.org/releases/telepathy-mission-control/telepathy-mission-control-5.16.6.tar.gz
telepathyqt               0.9.8        30 May 2020  https://github.com/TelepathyIM/telepathy-qt/releases/download/telepathy-qt-0.9.8/telepathy-qt-0.9.8.tar.gz
tellico                   3.4.4        19 February 2022 https://tellico-project.org/files/tellico-3.4.4.tar.xz
tellyskout                23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/telly-skout-23.08.5.tar.xz
templateglib              3.36.2       14 March 2024 https://download.gnome.org/sources/template-glib/3.36/template-glib-3.36.2.tar.xz
temple                    0.8.2        28 May 2020  https://rubygems.org/downloads/temple-0.8.2.gem
tepl                      6.9.0        19 February 2024 https://download.gnome.org/sources/tepl/6.9/tepl-6.9.0.tar.xz
termanimation             2.6          13 October 2018 https://cpan.metacpan.org/authors/id/K/KB/KBAUCOM/Term-Animation-2.6.tar.gz
termansicolor             1.7.1        18 February 2019 https://rubygems.org/downloads/term-ansicolor-1.7.1.gem
termcap                   1.3.1        01 May 2014  ftp://ftp.gnu.org/gnu/termcap/termcap-1.3.1.tar.gz
terminator                2.1.1        11 May 2021  https://github.com/gnome-terminator/terminator/releases/download/v2.1.1/terminator-2.1.1.tar.gz
terminology               1.13.0       14 April 2024 https://download.enlightenment.org/rel/apps/terminology/terminology-1.13.0.tar.xz
termit                    3.9.0        11 September 2017 https://rubygems.org/downloads/termit-3.9.0.gem
termreadkey               2.38         28 June 2021 https://cpan.metacpan.org/authors/id/J/JS/JSTOWE/TermReadKey-2.38.tar.gz
tesseract                 5.3.4        31 January 2024 https://github.com/tesseract-ocr/tesseract/archive/refs/tags/5.3.4.tar.gz
testdifferences           0.66         03 September 2018 https://cpan.metacpan.org/authors/id/D/DC/DCANTRELL/Test-Differences-0.66.tar.gz
testdisk                  6.11.3       01 May 2014  http://www.cgsecurity.org/testdisk-6.11.3.tar.bz2
testunit                  3.3.6        17 June 2020 https://rubygems.org/downloads/test-unit-3.3.6.gem
tetex                     3.0          01 May 2014  ftp://tug.ctan.org/tex-archive/systems/unix/teTeX/3.0/distrib/tetex-3.0.tar.gz
tevent                    0.16.0       19 October 2023 https://www.samba.org/ftp/tevent/tevent-0.16.0.tar.gz
texi2html                 1.82         01 January 2013 http://savannah.inetbridge.net/texi2html/texi2html-1.82.tar.bz2
texinfo                   7.1          19 October 2023 https://ftp.gnu.org/gnu/texinfo/texinfo-7.1.tar.xz
texmaker                  5.0.3        02 November 2018 http://www.xm1math.net/texmaker/texmaker-5.0.3.tar.bz2
textbibtex                0.88         19 April 2021 https://cpan.metacpan.org/authors/id/A/AM/AMBS/Text-BibTeX-0.88.tar.gz
textcsv                   2.00         12 May 2019  https://cpan.metacpan.org/authors/id/I/IS/ISHIGAKI/Text-CSV-2.00.tar.gz
thesilversearcher         2.2.0        13 September 2018 http://geoff.greer.fm/ag/releases/the_silver_searcher-2.2.0.tar.gz
thin                      1.7.2        31 July 2017 https://rubygems.org/downloads/thin-1.7.2.gem
thoggen                   0.7.1        01 April 2014 http://prdownloads.sourceforge.net/thoggen/thoggen-0.7.1.tar.gz
thor                      1.1.0        25 April 2021 https://rubygems.org/downloads/thor-1.1.0.gem
threadsafe                0.3.6        07 December 2017 https://rubygems.org/downloads/thread_safe-0.3.6.gem
threadweaver              5.115.0      20 February 2024 https://download.kde.org/stable/frameworks/5.115/threadweaver-5.115.0.tar.xz
thunar                    4.18.8       27 October 2023 https://archive.xfce.org/src/xfce/thunar/4.18/thunar-4.18.8.tar.bz2
thunarvolman              4.15.0       25 August 2020 https://archive.xfce.org/src/xfce/thunar-volman/4.15/thunar-volman-4.15.0.tar.bz2
tidy                      1.1.2        05 March 2017 https://rubygems.org/downloads/tidy-1.1.2.gem
tiff                      4.6.0        16 March 2024 https://download.osgeo.org/libtiff/tiff-4.6.0.tar.gz
tightvnc                  1.3.10       01 May 2014  https://sourceforge.net/projects/vnc-tight/files/TightVNC-unix/1.3.10/tightvnc-1.3.10_unixsrc.tar.bz2
tilda                     14.01.2018   14 January 2018 https://github.com/lanoxx/tilda/tilda-14.01.2018
tilt                      2.0.10       28 May 2020  https://rubygems.org/downloads/tilt-2.0.10.gem
timelimit                 1.9.0        18 September 2018 https://devel.ringlet.net/files/sys/timelimit/timelimit-1.9.0.tar.xz
timidity++                2.14.0       01 May 2014  https://sourceforge.net/projects/timidity/files/TiMidity++/TiMidity++-2.14.0/TiMidity++-2.14.0.tar.xz
tintin                    2.02.20      07 December 2022 https://github.com/scandum/tintin/releases/download/2.02.20/tintin-2.02.20.tar.gz
tf                        50b8         01 February 2013 https://sourceforge.net/projects/tinyfugue/files/tinyfugue/5.0%20beta%208/tf-50b8.tar.gz
tinyvm                    03.07.2011   01 May 2014  https://github.com/GenTiradentes/tinyvm/tinyvm-03.07.2011
tinyxml                   2.6.2        01 May 2014  http://sourceforge.net/projects/tinyxml/files/tinyxml/2.6.2/tinyxml_2_6_2.tar.gz
tioga                     1.19.1       10 February 2016 https://rubygems.org/downloads/tioga-1.19.1.gem
tk                        8.6.14       02 March 2024 https://sourceforge.net/projects/tcl/files/Tcl/8.6.14/tk8.6.14.tar.gz
tmux                      3.4          13 February 2024 https://github.com/tmux/tmux/releases/download/3.4/tmux-3.4.tar.gz
tmuxinator                2.0.1        28 May 2020  https://rubygems.org/downloads/tmuxinator-2.0.1.gem
tokodon                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/tokodon-23.08.5.tar.xz
tomboy                    1.15.9       16 July 2017 http://ftp.gnome.org/pub/gnome/sources/tomboy/1.15/tomboy-1.15.9.tar.xz
toml                      0.10.2       02 December 2021 https://files.pythonhosted.org/packages/be/ba/1f744cdc819428fc6b5084ec34d9b30660f6f9daaf70eead706e3203ec3c/toml-0.10.2.tar.gz
toppler                   1.1.6        12 December 2015 http://sourceforge.net/projects/toppler/files/toppler/1.1.6/toppler-1.1.6.tar.gz
torsmo                    0.18         01 May 2014  https://sourceforge.net/projects/torsmo/files/torsmo/torsmo%200.18/torsmo-0.18.tar.gz
totem                     42.0         17 July 2022 https://download.gnome.org/sources/totem/42/totem-42.0.tar.xz
totemplparser             3.26.6       26 June 2021 https://download.gnome.org/sources/totem-pl-parser/3.26/totem-pl-parser-3.26.6.tar.xz
toybox                    0.7.7        13 October 2018 https://landley.net/toybox/downloads/toybox-0.7.7.tar.gz
toycars                   0.3.10       01 December 2012 http://sourceforge.net/projects/toycars/files/toycars/0.3.10/toycars-0.3.10.tar.gz
trac                      1.4.3        11 November 2022 https://download.edgewall.org/trac/Trac-1.4.3.tar.gz
traceroute                2.1.2        15 February 2023 https://sourceforge.net/projects/traceroute/files/traceroute/traceroute-2.1.2/traceroute-2.1.2.tar.gz
trackballs                1.1.4        03 April 2016 https://sourceforge.net/projects/trackballs/files/trackballs/1.1.4/trackballs-1.1.4.tar.gz
tracker                   3.7.1        27 March 2024 https://download.gnome.org/sources/tracker/3.7/tracker-3.7.1.tar.xz
trackerminers             3.7.1        27 March 2024 https://download.gnome.org/sources/tracker-miners/3.7/tracker-miners-3.7.1.tar.xz
trackfs                   0.0.7        01 May 2014  http://www.mr511.de/software/trackfs-0.0.7.tar.gz
tramp                     2.5.4        02 December 2022 https://ftp.gnu.org/pub/gnu/tramp/tramp-2.5.4.tar.gz
translateshell            0.9.7.1      21 March 2023 translate-shell-0.9.7.1
transmission              4.0.4        07 December 2023 https://github.com/transmission/transmission/releases/download/4.0.4/transmission-4.0.4.tar.xz
transset                  1.0.3        04 December 2022 https://www.x.org/releases/individual/app/transset-1.0.3.tar.xz
tree                      2.0.1        05 January 2022 ftp://mama.indstate.edu/linux/tree/tree-2.0.1.tgz
treetop                   1.6.12       04 March 2023 https://rubygems.org/downloads/treetop-1.6.12.gem
triehash                  3            11 July 2020 https://github.com/julian-klode/triehash/archive/debian/0.3-3.tar.gz
trimines                  1.3.0        01 May 2014  http://www.freewebs.com/trimines/trimines-1.3.0.tar.gz
tripwire                  2.4.3.7      07 October 2017 https://github.com/Tripwire/tripwire-open-source/archive/2.4.3.7.tar.gz
trix                      0.93         01 May 2014  http://www.kde-apps.org/content/show.php/trix?content=49417/trix-0.93
trtl                      0.0.2        07 October 2017 https://rubygems.org/downloads/trtl-0.0.2.gem
tslib                     1.22         06 March 2023 https://github.com/libts/tslib/releases/download/1.22/tslib-1.22.tar.xz
tsombie                   1.1.2        01 December 2012 http://mathias-kettner.com/download/tsombie-1.1.2.tar.gz
ttfunk                    1.6.2.1      28 May 2020  https://rubygems.org/downloads/ttfunk-1.6.2.1.gem
ttycolor                  0.5.1        28 May 2020  https://rubygems.org/downloads/tty-color-0.5.1.gem
ttycursor                 0.7.1        28 May 2020  https://rubygems.org/downloads/tty-cursor-0.7.1.gem
ttyprogressbar            0.17.0       28 May 2020  https://rubygems.org/downloads/tty-progressbar-0.17.0.gem
ttyscreen                 0.8.0        17 June 2020 https://rubygems.org/downloads/tty-screen-0.8.0.gem
tulip                     3.0.0        01 May 2014  http://downloads.sourceforge.net/auber/tulip-3.0.0B6.tar.bz2?modtime=1184356395&big_mirror=0
tumbler                   4.18.2       03 December 2023 https://archive.xfce.org/src/xfce/tumbler/4.18/tumbler-4.18.2.tar.bz2
tunapie                   2.1.19       27 November 2019 https://sourceforge.net/projects/tunapie/files/tunapie/2.1/tunapie-2.1.19.tar.gz
tunnel                    1.2.1        01 May 2014  http://tspiteri.org/tunnel/download/
turbolinks                5.2.1        28 May 2020  https://rubygems.org/downloads/turbolinks-5.2.1.gem
turbovnc                  1.2.1        01 July 2014 http://sourceforge.net/projects/turbovnc/files/1.2.1/turbovnc-1.2.1.tar.gz
tuxrip                    0996         01 May 2014  http://tuxrip.free.fr/tuxrip/tuxrip099beta6.tar.bz2
tv                        0.5.1        24 November 2017 http://darwin.zoology.gla.ac.uk/~rpage/treeviewx/download/0.5/tv-0.5.1.tar.gz
tvtime                    1.0.1        01 May 2014  http://prdownloads.sourceforge.net/tvtime/tvtime-1.0.1.tar.gz
twilioruby                5.37.0       17 June 2020 https://rubygems.org/downloads/twilio-ruby-5.37.0.gem
twind                     1.1.0        01 May 2014  http://puzzle.dl.sourceforge.net/sourceforge/twind/twind-1.1.0.tar.gz
twisted                   18.9.0       18 October 2018 https://files.pythonhosted.org/packages/5d/0e/a72d85a55761c2c3ff1cb968143a2fd5f360220779ed90e0fadf4106d4f2/Twisted-18.9.0.tar.bz2
twitux                    0.69         29 July 2016 https://sourceforge.net/projects/twitux/files/twitux/0.69/twitux-0.69.tar.bz2
twm                       1.0.12       04 April 2022 https://www.x.org/releases/individual/app/twm-1.0.12.tar.xz
twolame                   0.4.0        25 September 2022 https://sourceforge.net/projects/twolame/files/twolame/0.4.0/twolame-0.4.0.tar.gz
txr                       206          18 January 2019 http://www.kylheku.com/cgit/txr/snapshot/txr-206.tar.bz2
typespeed                 0.6.5        27 March 2017 http://typespeed.sourceforge.net/typespeed-0.6.5.tar.gz
tzinfo                    2.0.2        28 May 2020  https://rubygems.org/downloads/tzinfo-2.0.2.gem
uchardet                  0.0.8        12 December 2022 https://www.freedesktop.org/software/uchardet/releases/uchardet-0.0.8.tar.xz
uclibc                    0.9.32       01 May 2014  http://www.uclibc.org/downloads/uClibc-0.9.32.tar.bz2
ucview                    0.16         01 May 2014  http://www.unicap-imaging.org/downloads/ucview-0.16.tar.gz
udev                      182          01 August 2013 http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev-182.tar.xz
udftools                  1.0.0b3      01 May 2014  http://downloads.sourceforge.net/linux-udf/udftools-1.0.0b3.tar.gz
udisks                    2.9.4        24 October 2021 https://github.com/storaged-project/udisks/releases/download/udisks-2.9.4/udisks-2.9.4.tar.bz2
ufoai                     2.5          09 August 2015 http://sourceforge.net/projects/ufoai/files/UFO_AI%202.x/2.5/ufoai-2.5-source.tar.bz2
uglifier                  4.2.0        28 May 2020  https://rubygems.org/downloads/uglifier-4.2.0.gem
uhttpmock                 0.10.0       08 March 2024 https://tecnocode.co.uk/downloads/uhttpmock/uhttpmock-0.10.0.tar.xz
uim                       1.5.4        01 May 2014  http://uim.googlecode.com/files/uim-1.5.4.tar.bz2
umbrello                  23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/umbrello-23.08.5.tar.xz
umockdev                  0.18.0       08 March 2024 https://github.com/martinpitt/umockdev/releases/download/0.18.0/umockdev-0.18.0.tar.xz
unbound                   1.19.3       16 March 2024 https://nlnetlabs.nl/downloads/unbound/unbound-1.19.3.tar.gz
uncrustify                0.65         02 August 2017 https://sourceforge.net/projects/uncrustify/files/uncrustify/uncrustify-0.65/uncrustify-0.65.tar.gz
unf                       0.1.4        21 September 2017 https://rubygems.org/downloads/unf-0.1.4.gem
unfext                    0.0.8        25 January 2023 https://rubygems.org/downloads/unf_ext-0.0.8.2.gem
unhash                    0.7          01 May 2014  http://www.geocities.com/dxp2532/
unicodecollate            1.28         24 September 2020 http://search.cpan.org/CPAN/authors/id/S/SA/SADAHIRO/Unicode-Collate-1.28.tar.gz
unicorn                   6.1.0        26 August 2022 https://rubygems.org/downloads/unicorn-6.1.0.gem
unieject                  6            01 May 2014  http://prdownloads.sourceforge.net/unieject/unieject-6.tar.bz2
unifdef                   2.12         18 March 2023 https://dotat.at/prog/unifdef/unifdef-2.12.tar.xz
union                     1.0.6        06 November 2018 https://rubygems.org/downloads/union-1.0.6.gem
unionfsfuse               0.25         01 May 2014  http://podgorny.cz/unionfs-fuse/releases/unionfs-fuse-0.25.tar.bz2
units                     2.22         06 September 2022 https://ftp.gnu.org/pub/gnu/units/units-2.22.tar.gz
unity                     7.4.0        20 November 2019 https://launchpad.net/unity/7.4/7.4.0/+download/unity-7.4.0.tar.bz2
unixodbc                  2.3.7        07 November 2019 ftp://ftp.unixodbc.org/pub/unixODBC/unixODBC-2.3.7.tar.gz
unoconv                   0.7          15 January 2019 http://dag.wieers.com/home-made/unoconv/unoconv-0.7.tar.gz
unotools                  0.3.3        10 January 2020 https://files.pythonhosted.org/packages/12/35/443632cfa43f82efd363bc8104b3ae67a887a248c6c6baec34c7b9edbcb5/unotools-0.3.3.tar.gz
unrtf                     0.21.10      25 November 2018 http://ftp.gnu.org/pub/gnu/unrtf/unrtf-0.21.10.tar.gz
unzip                     6.0          17 December 2015 http://downloads.sourceforge.net/infozip/unzip60.tar.gz
upower                    v1.90.0      23 July 2022 https://gitlab.freedesktop.org/upower/upower/-/archive/v1.90.0/upower-v1.90.0.tar.bz2
upstart                   1.6.1        01 January 2013 http://upstart.ubuntu.com/download/1.6.1/upstart-1.6.1.tar.gz
uri                       5.28         29 March 2024 https://www.cpan.org/authors/id/O/OA/OALDERS/URI-5.28.tar.gz
uriparser                 0.9.4        12 November 2020 https://sourceforge.net/projects/uriparser/files/Sources/0.9.4/uriparser-0.9.4.tar.xz
urlgrabber                4.0.0        27 November 2019 http://urlgrabber.baseurl.org/download/urlgrabber-4.0.0.tar.gz
urllib3                   1.26.8       13 January 2022 https://files.pythonhosted.org/packages/b0/b1/7bbf5181f8e3258efae31702f5eab87d8a74a72a0aa78bc8c08c1466e243/urllib3-1.26.8.tar.gz
urpkg                     1.4          01 May 2014  http://www.svasey.org/urpkg/urpkg-1.4.tar.bz2
usbutils                  016          25 October 2023 https://mirrors.edge.kernel.org/pub/linux/utils/usb/usbutils/usbutils-016.tar.xz
usermanager               5.18.6       29 September 2020 https://download.kde.org/stable/plasma/5.18.6/user-manager-5.18.6.tar.xz
userspacercu              0.12.1       12 August 2020 https://lttng.org/files/urcu/userspace-rcu-0.12.1.tar.bz2
utf8proc                  2.6.0        25 November 2020 https://github.com/JuliaStrings/utf8proc/archive/v2.6.0.tar.gz
utfcpp                    10.03.2024   10 March 2024 https://github.com/nemtrif/utfcpp/utfcpp-10.03.2024
utillinux                 2.40         27 March 2024 https://www.kernel.org/pub/linux/utils/util-linux/v2.40/util-linux-2.40.tar.xz
utilmacros                1.20.0       14 February 2023 https://www.x.org/releases/individual/util/util-macros-1.20.0.tar.xz
uuid                      1.6.2        01 July 2013 ftp://ftp.ossp.org/pkg/lib/uuid/uuid-1.6.2.tar.gz
v4lutils                  1.26.1       17 March 2024 https://www.linuxtv.org/downloads/v4l-utils/v4l-utils-1.26.1.tar.xz
vala                      0.56.16      14 March 2024 https://download.gnome.org/sources/vala/0.56/vala-0.56.16.tar.xz
valadoc                   0.36.2       04 March 2019 http://ftp.gnome.org/pub/gnome/sources/valadoc/0.36/valadoc-0.36.2.tar.xz
valencia                  0.8.0        01 August 2014 http://ftp.gnome.org/pub/GNOME/sources/valencia/0.8/valencia-0.8.0.tar.xz
valgrind                  3.22.0       13 April 2024 https://sourceware.org/pub/valgrind/valgrind-3.22.0.tar.bz2
valknut                   0.3.23       01 November 2017 https://sourceforge.net/projects/wxdcgui/files/valknut/0.3.23/valknut-0.3.23.tar.bz2
valkyrie                  2.0.0        17 December 2017 http://valgrind.org/downloads/valkyrie-2.0.0.tar.bz2
vapoursynth               R65          19 February 2024 https://github.com/vapoursynth/vapoursynth/archive/refs/tags/R65.tar.gz
vc                        0.7.3        09 August 2015 http://code.compeng.uni-frankfurt.de/attachments/download/174/Vc-0.7.3.tar.gz
vcinit                    1.2          01 May 2014  http://www.dervishd.net/Projects/VCinit-1.2.tar.gz
vdr                       1.6.0        01 May 2014  http://www.cadsoft.de/vdr/download.htm
veejay                    1.5.51       21 April 2019 https://sourceforge.net/projects/veejay/files/veejay-1.5/veejay-1.5.51.tar.bz2
vera                      1.23         10 February 2016 http://ftp.gnu.org/pub/gnu/vera/vera-1.23.tar.gz
vertris                   0.3.2        01 May 2014  http://vertris.googlecode.com/files/vertris-0.3.2.zip
vice                      1.19         01 May 2014  http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/vice-1.19.tar.gz
videocut                  0.2.0        01 May 2014  http://www.kde-apps.org/content/show.php/VideoCut?content=60826
videoproto                2.3.3        12 March 2016 http://xorg.freedesktop.org/releases/individual/proto/videoproto-2.3.3.tar.gz
videotrans                1.6.1        01 May 2014  http://sourceforge.net/projects/videotrans/files/videotrans/1.6.1/videotrans-1.6.1.tar.bz2
viennarna                 2.6.4        03 November 2023 https://www.tbi.univie.ac.at/RNA/download/sourcecode/2_6_x/ViennaRNA-2.6.4.tar.gz
viewres                   1.0.7        16 October 2022 https://www.x.org/releases/individual/app/viewres-1.0.7.tar.xz
viewvc                    1.1.15       01 May 2014  http://viewvc.tigris.org/files/documents/3330/49223/viewvc-1.1.15.tar.gz
vim                       9.0          28 June 2022 http://ftp.vim.org/pub/vim/unix/vim-9.0.tar.bz2
vino                      3.22.0       20 November 2019 http://ftp.gnome.org/pub/GNOME/sources/vino/3.22/vino-3.22.0.tar.xz
virtualenv                20.17.1      21 January 2023 https://files.pythonhosted.org/packages/7b/19/65f13cff26c8cc11fdfcb0499cd8f13388dd7b35a79a376755f152b42d86/virtualenv-20.17.1.tar.gz
vitetris                  0.57         01 November 2012 http://www.victornils.net/tetris/vitetris-0.57.tar.gz
vlc                       3.0.20       30 October 2023 https://download.videolan.org/pub/videolan/vlc/3.0.20/vlc-3.0.20.tar.xz
vlock                     2.1          01 May 2014  http://cthulhu.c3d2.de/~toidinamai/vlock/vlock-2.1.tar.gz
vmd                       1.9.3        16 June 2017 https://www.ks.uiuc.edu/Research/vmd/vmd-1.9.3/files/final/vmd-1.9.3tar.gz
vnstat                    2.2          30 April 2019 https://humdi.net/vnstat/vnstat-2.2.tar.gz
vobcopy                   1.1.0        01 May 2014  http://vobcopy.org/download/vobcopy-1.1.0.tar.bz2
volleyball                0.82         01 May 2014  http://www.losersjuegos.com.ar/juegos/volleyball/descargas/volleyball-0.82.tar.gz
volumekey                 0.3.12       12 October 2018 https://releases.pagure.org/volume_key/volume_key-0.3.12.tar.xz
vor                       0.5.6        11 June 2023 https://qualdan.com/vor/vor-0.5.6.tar.bz2
vorbistools               1.4.2        26 January 2021 https://downloads.xiph.org/releases/vorbis/vorbis-tools-1.4.2.tar.gz
vpnc                      0.5.3        01 May 2013  https://www.unix-ag.uni-kl.de/~massar/vpnc/vpnc-0.5.3.tar.gz
vrpe                      0.31         01 May 2014  http://vrpe.sytes.net/VRPE/VRPE-0.31.tar.bz2
vsftpd                    3.0.5        09 August 2021 https://security.appspot.com/downloads/vsftpd-3.0.5.tar.gz
vte                       0.76.0       20 March 2024 https://download.gnome.org/sources/vte/0.76/vte-0.76.0.tar.xz
vulkanheaders             1.3.277      26 March 2024 https://github.com/KhronosGroup/Vulkan-Headers/archive/refs/tags/v1.3.277/Vulkan-Headers-1.3.277.tar.gz
vulkanloader              1.3.281      27 March 2024 https://github.com/KhronosGroup/Vulkan-Loader/archive/refs/tags/v1.3.281/Vulkan-Loader-1.3.281.tar.gz
w3m                       0.5.3        30 December 2018 https://sourceforge.net/projects/w3m/files/w3m/w3m-0.5.3/w3m-0.5.3.tar.gz
waf                       2.0.22       26 April 2021 https://waf.io/waf-2.0.22.tar.bz2
waon                      0.10         01 March 2014 https://sourceforge.net/projects/waon/files/waon/0.10/waon-0.10.tar.gz
warden                    1.2.8        30 April 2019 https://rubygems.org/downloads/warden-1.2.8.gem
warmux                    11.04.1      01 July 2014 http://sourceforge.net/projects/warmux/files/warmux-11.04.1.tar.bz2
warzone2100               3.1.2        26 July 2015 http://sourceforge.net/projects/warzone2100/files/releases/3.1.2/warzone2100-3.1.2.tar.xz
watir                     6.17.0       28 October 2020 https://rubygems.org/downloads/watir-6.17.0.gem
wavbreaker                0.12         21 November 2019 http://downloads.sourceforge.net/wavbreaker/wavbreaker-0.12.tar.gz
wavpack                   5.7.0        02 March 2024 https://github.com/dbry/WavPack/releases/download/5.7.0/wavpack-5.7.0.tar.xz
wayland                   1.22.0       04 April 2023 https://gitlab.freedesktop.org/wayland/wayland/-/releases/1.22.0/downloads/wayland-1.22.0.tar.xz
waylandprotocols          1.34         21 March 2024 https://gitlab.freedesktop.org/wayland/wayland-protocols/-/releases/1.34/downloads/wayland-protocols-1.34.tar.xz
wcd                       6.0.1-beta3  08 August 2017 https://waterlan.home.xs4all.nl/wcd/wcd-6.0.1-beta3.tar.gz
wdiff                     1.2.2        05 March 2021 https://ftp.gnu.org/gnu/wdiff/wdiff-1.2.2.tar.gz
webkit                    r189384      22 December 2015 http://builds.nightly.webkit.org/files/trunk/src/WebKit-r189384.tar.bz2
webkitgtk                 2.44.1       13 April 2024 https://webkitgtk.org/releases/webkitgtk-2.44.1.tar.xz
webmin                    2.021        22 March 2023 https://downloads.sourceforge.net/webadmin/webmin-2.021.tar.gz
webrick                   1.8.1        13 March 2023 https://rubygems.org/downloads/webrick-1.8.1.gem
websocketdriver           0.7.2        28 May 2020  https://rubygems.org/downloads/websocket-driver-0.7.2.gem
weechat                   3.1          02 June 2021 https://weechat.org/files/src/weechat-3.1.tar.xz
weggli                    19.02.2024   19 February 2023 https://github.com/weggli-rs/weggli
wesnoth                   1.16.12      04 April 2024 https://sourceforge.net/projects/wesnoth/files/wesnoth-1.16/wesnoth-1.16.12/wesnoth-1.16.12.tar.bz2
weston                    12.0.3       30 January 2024 https://gitlab.freedesktop.org/wayland/weston/-/releases/12.0.3/downloads/weston-12.0.3.tar.xz
wget                      1.24.5       12 March 2024 https://ftp.gnu.org/pub/gnu/wget/wget-1.24.5.tar.gz
wget2                     2.1.0        31 August 2023 https://ftp.gnu.org/gnu/wget/wget2-2.1.0.tar.gz
wheel                     0.43.0       14 March 2024 https://files.pythonhosted.org/packages/b8/d6/ac9cd92ea2ad502ff7c1ab683806a9deb34711a1e2bd8a59814e8fc27e69/wheel-0.43.0.tar.gz
whenever                  1.0.0        22 May 2020  https://rubygems.org/downloads/whenever-1.0.0.gem
which                     2.21         17 June 2015 http://ftp.gnu.org/gnu/which/which-2.21.tar.gz
whitedune                 0.29beta670  01 May 2014  http://vrml.cip.ica.uni-stuttgart.de/dune/down.html
whois                     5.5.7        06 October 2020 http://ftp.debian.org/debian/pool/main/w/whois/whois_5.5.7.tar.xz
wicd                      1.7.4        25 January 2016 https://launchpad.net/wicd/1.7/1.7.4/+download/wicd-1.7.4.tar.gz
wimlib                    1.14.4       15 March 2024 https://wimlib.net/downloads/wimlib-1.14.4.tar.gz
windowmaker               0.96.0       07 August 2023 https://github.com/window-maker/wmaker/releases/download/wmaker-0.96.0/WindowMaker-0.96.0.tar.gz
windowswmproto            1.0.3        01 May 2014  https://www.x.org/releases/individual/proto/windowswmproto-1.0.3.tar.bz2
wine                      8.4          20 March 2023 https://dl.winehq.org/wine/source/8.x/wine-8.4.tar.xz
wings                     2.2.6.1      28 May 2020  https://sourceforge.net/projects/wings/files/wings/2.2.6.1/wings-2.2.6.1.tar.bz2
winzig                    1.73         01 May 2014  http://freshmeat.net/redir/winzig/20777/url_tgz/winzig.1.73.tar.gz
wirble                    0.1.3        23 March 2017 https://rubygems.org/downloads/wirble-0.1.3.gem
wiredtiger                11.0.0       29 August 2022 https://github.com/wiredtiger/wiredtiger/archive/refs/tags/11.0.0.tar.gz
wireguard                 0.0.20170918 19 September 2017 https://git.zx2c4.com/WireGuard/snapshot/WireGuard-0.0.20170918.tar.xz
wirelesstools             .29          01 May 2014  http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/wireless_tools.29.tar.gz
wireshark                 4.2.4        31 March 2024 https://www.wireshark.org/download/src/all-versions/wireshark-4.2.4.tar.xz
wkhtmltox                 0.12.5       12 May 2019  https://github.com/wkhtmltopdf/wkhtmltopdf/archive/0.12.5.tar.gz
wlassistant               0.5.7        01 May 2014  http://wlassistant.sourceforge.net/
wmctrl                    1.07         01 May 2014  http://www.sweb.cz/tripie/utils/wmctrl/dist/wmctrl-1.07.tar.gz
wmii                      20071003     01 May 2014  http://www.suckless.org/snaps/wmii-20071003.tgz
woff2                     1.0.2        22 December 2021 https://github.com/google/woff2/archive/v1.0.2/woff2-1.0.2.tar.gz
wordpress                 6.5          03 April 2024 https://wordpress.org/wordpress-6.5.tar.gz
worker                    4.7.0        10 March 2021 http://www.boomerangsworld.de/cms/worker/downloads/worker-4.7.0.tar.bz2
wpasupplicant             2.10         11 October 2022 https://w1.fi/releases/wpa_supplicant-2.10.tar.gz
wpebackendfdo             1.14.2       03 April 2023 https://wpewebkit.org/releases/wpebackend-fdo-1.14.2.tar.xz
wput                      0.6.1        01 May 2014  http://prdownloads.sourceforge.net/wput/wput-0.6.1.tgz
writeexcel                1.0.5        12 August 2017 https://rubygems.org/downloads/writeexcel-1.0.5.gem
wv                        1.2.9        01 August 2013 http://www.abisource.com/downloads/wv/1.2.9/wv-1.2.9.tar.gz
wv2                       0.4.2        01 May 2014  https://sourceforge.net/projects/wvware/files/wv2-0.4.2.tar.bz2
wxgtk                     2.6.3        01 May 2014  http://mesh.dl.sourceforge.net/sourceforge/wxwindows/wxGTK-2.6.3.tar.bz2
wxpython                  4.1.0        25 November 2020 https://files.pythonhosted.org/packages/cb/4f/1e21d3c079c973ba862a18f3be73c2bbe2e6bc25c96d94df605b5cbb494d/wxPython-4.1.0.tar.gz
wxsvg                     1.1.2        01 May 2014  http://sourceforge.net/projects/wxsvg/files/wxsvg/1.1.2/wxsvg-1.1.2.tar.bz2
wxwidgets                 3.2.4        21 December 2023 https://github.com/wxWidgets/wxWidgets/releases/download/v3.2.4/wxWidgets-3.2.4.tar.bz2
x11perf                   1.6.1        17 March 2019 https://www.x.org/releases/individual/app/x11perf-1.6.1.tar.gz
x264                      20220819     18 September 2022 https://anduin.linuxfromscratch.org/BLFS/x264/x264-20220819.tar.xz
x265                      20240216     18 March 2024 https://anduin.linuxfromscratch.org/BLFS/x265/x265-20240216.tar.xz
x86info                   1.30         01 May 2014  http://codemonkey.org.uk/projects/x86info/x86info-1.30.tgz
xapianbindings            1.4.22       05 February 2023 https://oligarchy.co.uk/xapian/1.4.22/xapian-bindings-1.4.22.tar.xz
xapiancore                1.4.25       10 March 2024 https://oligarchy.co.uk/xapian/1.4.25/xapian-core-1.4.25.tar.xz
xapianomega               1.4.9        11 January 2019 https://oligarchy.co.uk/xapian/1.4.9/xapian-omega-1.4.9.tar.xz
xarchiver                 0.5.4.23     03 March 2024 https://github.com/ib/xarchiver/archive/0.5.4.23/xarchiver-0.5.4.23.tar.gz
xaric                     0.13.7       06 December 2015 http://xaric.org/software/xaric/releases/xaric-0.13.7.tar.gz
xaudio                    0.6.1        01 April 2014 http://www.chaoticmind.net/~hcb/murx/xaudio/xaudio-0.6.1.tar.gz
xauth                     1.1.3        04 March 2024 https://www.x.org/releases/individual/app/xauth-1.1.3.tar.gz
xautomation               1.02         01 May 2014  http://hoopajoo.net/static/projects/xautomation-1.02.tar.gz
xawtv                     3.95         01 May 2014  http://dl.bytesex.org/releases/xawtv/xawtv-3.95.tar.gz
xbacklight                1.2.3        16 July 2019 http://xorg.freedesktop.org/releases/individual/app/xbacklight-1.2.3.tar.bz2
xbak                      0.1.5        01 May 2014  http://sourceforge.net/projects/xbak/files/xbak/xbak-0.1.5/xbak-0.1.5.tar.bz2
xbiff                     1.0.5        01 February 2024 https://www.x.org/releases/individual/app/xbiff-1.0.5.tar.xz
xbindkeys                 1.8.5        01 May 2014  http://www.nongnu.org/xbindkeys/xbindkeys-1.8.5.tar.gz
xbitmaps                  1.1.3        03 March 2023 https://www.x.org/releases/individual/data/xbitmaps-1.1.3.tar.xz
xboard                    4.9.1        08 August 2016 http://ftp.gnu.org/gnu/xboard/xboard-4.9.1.tar.gz
xcalc                     1.1.2        06 May 2023  https://www.x.org/releases/individual/app/xcalc-1.1.2.tar.xz
xcbproto                  1.17.0       16 April 2024 https://xcb.freedesktop.org/dist/xcb-proto-1.17.0.tar.xz
xcbutil                   0.4.1        23 January 2023 https://xcb.freedesktop.org/dist/xcb-util-0.4.1.tar.xz
xcbutilcursor             0.1.5        18 November 2023 https://www.x.org/releases/individual/lib/xcb-util-cursor-0.1.5.tar.xz
xcbutilerrors             1.0.1        19 October 2022 https://www.x.org/releases/individual/lib/xcb-util-errors-1.0.1.tar.xz
xcbutilimage              0.4.1        19 October 2022 https://www.x.org/releases/individual/lib/xcb-util-image-0.4.1.tar.xz
xcbutilkeysyms            0.4.1        19 October 2022 https://www.x.org/releases/individual/lib/xcb-util-keysyms-0.4.1.tar.xz
xcbutilrenderutil         0.3.10       19 October 2022 https://www.x.org/releases/individual/lib/xcb-util-renderutil-0.3.10.tar.xz
xcbutilwm                 0.4.2        19 October 2022 https://www.x.org/releases/individual/lib/xcb-util-wm-0.4.2.tar.xz
xcbutilxrm                1.0          22 November 2016 https://github.com/Airblader/xcb-util-xrm/releases/download/v1.0/xcb-util-xrm-1.0.tar.bz2
xchat                     2.8.8        01 April 2014 http://xchat.org/files/source/2.8/xchat-2.8.8.tar.bz2
xchm                      1.27         22 March 2019 https://github.com/rzvncj/xCHM/releases/download/1.27/xchm-1.27.tar.gz
xclip                     10.03.2023   01 May 2014  https://downloads.sourceforge.net/project/xclip/xclip/0.12/xclip-10.03.2023.tar.xz
xclipboard                1.1.4        12 July 2022 https://www.x.org/releases/individual/app/xclipboard-1.1.4.tar.xz
xclock                    1.1.0        05 April 2022 https://www.x.org/pub/individual/app/xclock-1.1.0.tar.xz
xcm                       0.5.3        01 May 2014  https://sourceforge.net/projects/oyranos/files/Xcm/xcm-0.5.3.tar.bz2
xcmiscproto               1.2.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/proto/xcmiscproto-1.2.2.tar.bz2
xcmsdb                    1.0.6        12 July 2022 https://www.x.org/releases/individual/app/xcmsdb-1.0.6.tar.xz
xcompmgr                  1.1.8        26 March 2019 https://www.x.org/releases/individual/app/xcompmgr-1.1.8.tar.gz
xconsole                  1.0.8        12 July 2022 https://www.x.org/releases/individual/app/xconsole-1.0.8.tar.xz
xcursorgen                1.0.8        04 December 2022 https://www.x.org/releases/individual/app/xcursorgen-1.0.8.tar.xz
xcursorthemes             1.0.6        16 February 2019 https://www.x.org/releases/individual/data/xcursor-themes-1.0.6.tar.bz2
xdbedizzy                 1.0.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/app/xdbedizzy-1.0.2.tar.bz2
xdg                       4.1.0        28 May 2020  https://rubygems.org/downloads/xdg-4.1.0.gem
xdgdbusproxy              0.1.5        20 January 2024 https://github.com/flatpak/xdg-dbus-proxy/releases/download/0.1.5/xdg-dbus-proxy-0.1.5.tar.xz
xdgdesktopportal          1.14.5       25 July 2022 https://github.com/flatpak/xdg-desktop-portal/releases/download/1.14.5/xdg-desktop-portal-1.14.5.tar.xz
xdgdesktopportalgnome     46.0         27 March 2024 https://download.gnome.org/sources/xdg-desktop-portal-gnome/46/xdg-desktop-portal-gnome-46.0.tar.xz
xdgdesktopportalkde       5.27.9       24 October 2023 https://download.kde.org/stable/plasma/5.27.9/xdg-desktop-portal-kde-5.27.9.tar.xz
xdguserdirs               0.17         20 March 2018 https://user-dirs.freedesktop.org/releases/xdg-user-dirs-0.17.tar.gz
xdguserdirsgtk            0.11         14 October 2022 https://download.gnome.org/sources/xdg-user-dirs-gtk/0.11/xdg-user-dirs-gtk-0.11.tar.xz
xdgutils                  1.1.3        26 January 2019 https://portland.freedesktop.org/download/xdg-utils-1.1.3.tar.gz
xdialog                   2.3.1        01 May 2014  http://xdialog.free.fr/Xdialog-2.3.1.tar.bz2
xditview                  1.0.7        20 February 2024 https://www.x.org/releases/individual/app/xditview-1.0.7.tar.xz
xdm                       1.1.16       05 April 2024 https://www.x.org/releases/individual/app/xdm-1.1.16.tar.xz
xdotool                   3.20210903.1 17 October 2021 https://github.com/jordansissel/xdotool/releases/download/v3.20210903.1/xdotool-3.20210903.1.tar.gz
xdpyinfo                  1.3.4        29 April 2023 https://www.x.org/releases/individual/app/xdpyinfo-1.3.4.tar.xz
xdriinfo                  1.0.5        18 April 2015 https://xorg.freedesktop.org/releases/individual/app/xdriinfo-1.0.5.tar.gz
xdtv                      2.4.0        31 August 2017 https://sourceforge.net/projects/xawdecode/files/01%20-%20XdTV/2.4.0/xdtv-2.4.0.tar.gz
xedit                     1.2.4        25 March 2024 https://www.x.org/releases/individual/app/xedit-1.2.4.tar.xz
xemacs                    21.5.35      01 April 2024 http://ftp.xemacs.org/pub/xemacs/xemacs-21.5/xemacs-21.5.35.tar.gz
xercesc                   3.2.3        23 July 2020 http://www-us.apache.org/dist//xerces/c/3/sources/xerces-c-3.2.3.tar.xz
xev                       1.2.6        05 March 2024 https://www.x.org/releases/individual/app/xev-1.2.6.tar.xz
xextproto                 7.2.99.901   01 November 2013 https://xorg.freedesktop.org/releases/individual/proto/xextproto-7.2.99.901.tar.bz2
xf86bigfontproto          1.2.0        01 May 2014  http://xorg.freedesktop.org/releases/individual/proto/xf86bigfontproto-1.2.0.tar.bz2
xf86dga                   1.0.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/app/xf86dga-1.0.2.tar.bz2
xf86dgaproto              2.1          01 January 2013 http://xorg.freedesktop.org/releases/individual/proto/xf86dgaproto-2.1.tar.bz2
xf86driproto              2.1.1        01 May 2014  http://xorg.freedesktop.org/releases/individual/proto/xf86driproto-2.1.1.tar.bz2
xf86inputaiptek           1.0.0.5      01 May 2014  https://www.x.org/releases/individual/driver/xf86-input-aiptek-1.0.0.5.tar.bz2
xf86inputelographics      1.4.4        01 March 2024 https://www.x.org/releases/individual/driver/xf86-input-elographics-1.4.4.tar.xz
xf86inputevdev            2.10.6       30 May 2018  https://www.x.org/releases/individual/driver/xf86-input-evdev-2.10.6.tar.gz
xf86inputevtouch          0.8.8        01 May 2012  http://www.conan.de/touchscreen/xf86-input-evtouch-0.8.8.tar.bz2
xf86inputfpit             1.4.0        22 December 2015 https://www.x.org/releases/individual/driver/xf86-input-fpit-1.4.0.tar.gz
xf86inputhyperpen         1.4.1        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-input-hyperpen-1.4.1.tar.bz2
xf86inputjoystick         1.6.3        24 November 2016 https://www.x.org/releases/individual/driver/xf86-input-joystick-1.6.3.tar.bz2
xf86inputkeyboard         2.0.0        19 August 2022 https://www.x.org/releases/individual/driver/xf86-input-keyboard-2.0.0.tar.xz
xf86inputlibinput         1.3.0        05 April 2023 https://www.x.org/releases/individual/driver/xf86-input-libinput-1.3.0.tar.gz
xf86inputmouse            1.9.3        02 July 2018 https://www.x.org/releases/individual/driver/xf86-input-mouse-1.9.3.tar.gz
xf86inputmutouch          1.2.1        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-input-mutouch-1.2.1.tar.bz2
xf86inputpenmount         1.4.0        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-input-penmount-1.4.0.tar.bz2
xf86inputsynaptics        1.9.1        30 May 2018  https://xorg.freedesktop.org/releases/individual/driver/xf86-input-synaptics-1.9.1.tar.gz
xf86inputvmmouse          13.2.0       16 October 2022 http://xorg.freedesktop.org/releases/individual/driver/xf86-input-vmmouse-13.2.0.tar.gz
xf86inputvoid             1.4.1        14 December 2018 https://www.x.org/releases/individual/driver/xf86-input-void-1.4.1.tar.bz2
xf86inputwacom            1.2.2        16 April 2024 https://github.com/linuxwacom/xf86-input-wacom/releases/download/xf86-input-wacom-1.2.2/xf86-input-wacom-1.2.2.tar.bz2
xf86miscproto             0.9.3        01 May 2014  http://xorg.freedesktop.org/releases/individual/proto/xf86miscproto-0.9.3.tar.bz2
xf86rushproto             1.1.2        01 May 2014  https://www.x.org/releases/individual/proto/xf86rushproto-1.1.2.tar.bz2
xf86videoamd              2.7.7.7      13 March 2008 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-amd-2.7.7.7.tar.bz2
xf86videoamdgpu           23.0.0       26 February 2023 https://www.x.org/releases/individual/driver/xf86-video-amdgpu-23.0.0.tar.xz
xf86videoapm              1.3.0        08 February 2019 https://www.x.org/releases/individual/driver/xf86-video-apm-1.3.0.tar.bz2
xf86videoark              0.7.4        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ark-0.7.4.tar.bz2
xf86videoast              1.1.5        22 August 2015 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ast-1.1.5.tar.bz2
xf86videoati              13.09.2022   15 October 2019 https://www.x.org/releases/individual/driver/xf86-video-ati-19.1.0.tar.gz
xf86videochips            1.5.0        25 March 2024 https://www.x.org/releases/individual/driver/xf86-video-chips-1.5.0.tar.xz
xf86videocirrus           1.6.0        20 August 2022 https://www.x.org/releases/individual/driver/xf86-video-cirrus-1.6.0.tar.xz
xf86videodummy            0.4.0        20 August 2022 https://www.x.org/releases/individual/driver/xf86-video-dummy-0.4.0.tar.xz
xf86videofbdev            0.5.0        01 June 2018 ftp://ftp.x.org/pub/individual/driver/xf86-video-fbdev-0.5.0.tar.bz2
xf86videofreedreno        1.4.0        12 October 2015 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-freedreno-1.4.0.tar.bz2
xf86videogeode            2.11.20      22 September 2019 https://www.x.org/releases/individual/driver/xf86-video-geode-2.11.20.tar.gz
xf86videoglide            1.2.2        02 April 2019 ftp://ftp.x.org/pub/individual/driver/xf86-video-glide-1.2.2.tar.gz
xf86videoi128             1.4.0        01 May 2014  https://www.x.org/releases/individual/driver/xf86-video-i128-1.4.0.tar.gz
xf86videoi740             1.4.0        01 May 2014  https://www.x.org/releases/individual/driver/xf86-video-i740-1.4.0.tar.gz
xf86videoi810             1.7.4        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-i810-1.7.4.tar.bz2
xf86videointel            2.99.917     11 April 2015 ftp://ftp.x.org/pub/individual/driver/xf86-video-intel-2.99.917.tar.bz2
xf86videomach64           6.9.7        20 August 2022 https://www.x.org/releases/individual/driver/xf86-video-mach64-6.9.7.tar.xz
xf86videomga              2.0.1        19 August 2022 https://www.x.org/releases/individual/driver/xf86-video-mga-2.0.1.tar.xz
xf86videomodesetting      0.9.0        01 June 2014 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-modesetting-0.9.0.tar.gz
xf86videoneomagic         1.3.0        27 December 2018 https://www.x.org/releases/individual/driver/xf86-video-neomagic-1.3.0.tar.gz
xf86videonewport          0.2.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-newport-0.2.2.tar.bz2
xf86videonouveau          1.0.17       17 April 2021 https://www.x.org/releases/individual/driver/xf86-video-nouveau-1.0.17.tar.bz2
xf86videonv               2.1.23       25 March 2024 https://www.x.org/releases/individual/driver/xf86-video-nv-2.1.23.tar.xz
xf86videoomap             0.4.5        24 May 2020  https://www.x.org/releases/individual/driver/xf86-video-omap-0.4.5.tar.gz
xf86videoopenchrome       0.6.0        08 March 2017 https://www.x.org/releases/individual/driver/xf86-video-openchrome-0.6.0.tar.bz2
xf86videoopentegra        0.7.0        01 July 2014 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-opentegra-0.7.0.tar.xz
xf86videoqxl              0.1.5        31 December 2016 https://www.x.org/releases/individual/driver/xf86-video-qxl-0.1.5.tar.bz2
xf86videoradeonhd         1.3.0        01 November 2017 https://www.x.org/releases/individual/driver/xf86-video-radeonhd-1.3.0.tar.bz2
xf86videorendition        4.2.7        23 May 2018  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-rendition-4.2.7.tar.gz
xf86videos3               0.7.0        27 July 2019 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-s3-0.7.0.tar.bz2
xf86videos3virge          1.11.0       09 February 2019 https://www.x.org/releases/individual/driver/xf86-video-s3virge-1.11.0.tar.gz
xf86videosavage           2.4.1        25 March 2024 https://www.x.org/releases/individual/driver/xf86-video-savage-2.4.1.tar.xz
xf86videosiliconmotion    1.7.0        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-siliconmotion-1.7.0.tar.bz2
xf86videosis              0.12.0       04 December 2019 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sis-0.12.0.tar.bz2
xf86videosisusb           0.9.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sisusb-0.9.2.tar.bz2
xf86videotdfx             1.5.0        17 February 2019 https://www.x.org/releases/individual/driver/xf86-video-tdfx-1.5.0.tar.bz2
xf86videotga              1.2.1        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-tga-1.2.1.tar.bz2
xf86videotrident          1.4.0        27 October 2016 https://xorg.freedesktop.org/archive/individual/driver/xf86-video-trident-1.4.0.tar.xz
xf86videotseng            1.2.5        05 April 2024 https://www.x.org/releases/individual/driver/xf86-video-tseng-1.2.5.tar.gz
xf86videov4l              0.3.0        16 August 2018 https://www.x.org/releases/individual/driver/xf86-video-v4l-0.3.0.tar.gz
xf86videovboxvideo        1.0.1        25 March 2024 https://www.x.org/releases/individual/driver/xf86-video-vboxvideo-1.0.1.tar.xz
xf86videovesa             2.6.0        12 December 2022 https://www.x.org/releases/individual/driver/xf86-video-vesa-2.6.0.tar.xz
xf86videovia              0.2.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-via-0.2.2.tar.bz2
xf86videovmware           13.4.0       29 January 2023 https://www.x.org/releases/individual/driver/xf86-video-vmware-13.4.0.tar.gz
xf86videovoodoo           1.2.2        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-voodoo-1.2.2.tar.bz2
xf86videowsfb             0.4.0        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-wsfb-0.4.0.tar.bz2
xf86videoxgi              1.6.1        22 August 2015 http://xorg.freedesktop.org/releases/individual/driver/xf86-video-xgi-1.6.1.tar.bz2
xf86videoxgixp            1.8.0        01 May 2014  http://xorg.freedesktop.org/releases/individual/driver/xf86-video-xgixp-1.8.0.tar.bz2
xfburn                    0.7.0        07 March 2023 https://archive.xfce.org/src/apps/xfburn/0.7/xfburn-0.7.0.tar.bz2
xfce4appfinder            4.16.1       26 April 2021 https://archive.xfce.org/src/xfce/xfce4-appfinder/4.16/xfce4-appfinder-4.16.1.tar.bz2
xfce4clipmanplugin        1.6.2        05 May 2021  https://archive.xfce.org/src/panel-plugins/xfce4-clipman-plugin/1.6/xfce4-clipman-plugin-1.6.2.tar.bz2
xfce4cpufreqplugin        1.2.0        19 September 2018 http://archive.xfce.org/src/panel-plugins/xfce4-cpufreq-plugin/1.2/xfce4-cpufreq-plugin-1.2.0.tar.bz2
xfce4devtools             4.18.0       19 October 2023 http://archive.xfce.org/src/xfce/xfce4-dev-tools/4.18/xfce4-dev-tools-4.18.0.tar.bz2
xfce4eyesplugin           4.5.0        25 September 2017 http://archive.xfce.org/src/panel-plugins/xfce4-eyes-plugin/4.5/xfce4-eyes-plugin-4.5.0.tar.bz2
xfce4genmonplugin         4.0.0        26 September 2017 http://archive.xfce.org/src/panel-plugins/xfce4-genmon-plugin/4.0/xfce4-genmon-plugin-4.0.0.tar.bz2
xfce4mpcplugin            0.5.0        30 August 2017 http://archive.xfce.org/src/panel-plugins/xfce4-mpc-plugin/0.5/xfce4-mpc-plugin-0.5.0.tar.bz2
xfce4notifyd              0.8.2        03 March 2023 https://archive.xfce.org/src/apps/xfce4-notifyd/0.8/xfce4-notifyd-0.8.2.tar.bz2
xfce4panel                4.18.6       01 March 2024 https://archive.xfce.org/src/xfce/xfce4-panel/4.18/xfce4-panel-4.18.6.tar.bz2
xfce4panelprofiles        1.0.10       06 February 2020 https://archive.xfce.org/src/apps/xfce4-panel-profiles/1.0/xfce4-panel-profiles-1.0.10.tar.bz2
xfce4powermanager         4.18.3       03 December 2023 https://archive.xfce.org/src/xfce/xfce4-power-manager/4.18/xfce4-power-manager-4.18.3.tar.bz2
xfce4pulseaudioplugin     0.4.7        03 June 2023 https://archive.xfce.org/src/panel-plugins/xfce4-pulseaudio-plugin/0.4/xfce4-pulseaudio-plugin-0.4.7.tar.bz2
xfce4sampleplugin         0.1.2        25 September 2017 http://archive.xfce.org/src/panel-plugins/xfce4-sample-plugin/0.1/xfce4-sample-plugin-0.1.2.tar.gz
xfce4screensaver          4.18.3       06 March 2024 https://archive.xfce.org/src/apps/xfce4-screensaver/4.18/xfce4-screensaver-4.18.3.tar.bz2
xfce4screenshooter        1.9.8        13 March 2022 http://archive.xfce.org/src/apps/xfce4-screenshooter/1.9/xfce4-screenshooter-1.9.8.tar.bz2
xfce4session              4.18.2       29 March 2023 https://archive.xfce.org/src/xfce/xfce4-session/4.18/xfce4-session-4.18.2.tar.bz2
xfce4settings             4.18.4       01 December 2023 https://archive.xfce.org/src/xfce/xfce4-settings/4.18/xfce4-settings-4.18.4.tar.bz2
xfce4statusnotifierplugin 0.2.0        26 September 2017 http://archive.xfce.org/src/panel-plugins/xfce4-statusnotifier-plugin/0.2/xfce4-statusnotifier-plugin-0.2.0.tar.bz2
xfce4systemloadplugin     1.2.3        18 August 2019 https://archive.xfce.org/src/panel-plugins/xfce4-systemload-plugin/1.2/xfce4-systemload-plugin-1.2.3.tar.bz2
xfce4taskmanager          1.4.0        30 December 2020 https://git.xfce.org/apps/xfce4-taskmanager/snapshot/xfce4-taskmanager-1.4.0.tar.gz
xfce4terminal             1.1.3        01 March 2024 https://archive.xfce.org/src/apps/xfce4-terminal/1.1/xfce4-terminal-1.1.3.tar.bz2
xfce4whiskermenuplugin    2.6.2        16 November 2021 https://archive.xfce.org/src/panel-plugins/xfce4-whiskermenu-plugin/2.6/xfce4-whiskermenu-plugin-2.6.2.tar.bz2
xfce4xkbplugin            0.8.1        26 September 2017 http://archive.xfce.org/src/panel-plugins/xfce4-xkb-plugin/0.8/xfce4-xkb-plugin-0.8.1.tar.bz2
xfconf                    4.18.2       19 October 2023 https://archive.xfce.org/src/xfce/xfconf/4.18/xfconf-4.18.2.tar.bz2
xfd                       1.1.3        11 March 2019 https://xorg.freedesktop.org/releases/individual/app/xfd-1.1.3.tar.bz2
xfdesktop                 4.18.1       23 January 2023 https://archive.xfce.org/src/xfce/xfdesktop/4.18/xfdesktop-4.18.1.tar.bz2
xfe                       1.33         01 May 2014  http://sourceforge.net/projects/xfe/files/xfe/1.33/xfe-1.33.tar.gz
xfig                      3.2.8        01 April 2023 https://sourceforge.net/projects/mcj/files/xfig-3.2.8.tar.xz
xfindproxy                1.0.4        18 April 2015 https://xorg.freedesktop.org/releases/individual/app/xfindproxy-1.0.4.tar.gz
xfmedia                   0.9.2        30 July 2022 https://www.spurint.org/files/xfmedia/xfmedia-0.9.2.tar.bz2
xfontsel                  1.1.1        05 March 2024 https://www.x.org/releases/individual/app/xfontsel-1.1.1.tar.xz
xforge                    0.2.2        01 May 2014  http://users.tkk.fi/~phonkane/xforge/xforge-0.2.2.tar.gz
xfs                       1.2.1        12 July 2022 https://www.x.org/releases/individual/app/xfs-1.2.1.tar.xz
xfsdump                   3.1.12       14 June 2023 https://mirrors.edge.kernel.org/pub/linux/utils/fs/xfs/xfsdump/xfsdump-3.1.12.tar.xz
xfsinfo                   1.0.7        24 October 2022 https://www.x.org/releases/individual/app/xfsinfo-1.0.7.tar.xz
xfsprogs                  6.6.0        05 February 2024 https://www.kernel.org/pub/linux/utils/fs/xfs/xfsprogs/xfsprogs-6.6.0.tar.xz
xft                       2.1.2        01 December 2012 http://xlibs.freedesktop.org/release/xft-2.1.2.tar.gz
xfwm4                     4.18.0       11 January 2023 https://archive.xfce.org/src/xfce/xfwm4/4.18/xfwm4-4.18.0.tar.bz2
xfwp                      1.0.3        01 May 2014  https://xorg.freedesktop.org/releases/individual/app/xfwp-1.0.3.tar.bz2
xgamma                    1.0.7        01 April 2023 https://xorg.freedesktop.org/releases/individual/app/xgamma-1.0.7.tar.xz
xgc                       1.0.6        16 October 2022 https://xorg.freedesktop.org/releases/individual/app/xgc-1.0.6.tar.gz
xhost                     1.0.9        15 December 2022 https://www.x.org/releases/individual/app/xhost1.0.9.tar.xz
xinelib                   1.2.13       30 May 2023  https://sourceforge.net/projects/xine/files/xine-lib/1.2.13/xine-lib-1.2.13.tar.xz
xinetd                    2.3.15       01 May 2014  http://www.xinetd.org/xinetd-2.3.15.tar.gz
xineui                    0.99.14      11 January 2023 https://sourceforge.net/projects/xine/files/xine-ui/0.99.14/xine-ui-0.99.14.tar.xz
xinit                     1.4.2        04 December 2022 https://www.x.org/releases/individual/app/xinit-1.4.2.tar.xz
xinput                    1.6.4        29 April 2023 https://xorg.freedesktop.org/releases/individual/app/xinput-1.6.4.tar.xz
xisxwayland               2            01 September 2022 https://www.x.org/releases/individual/app/xisxwayland-2.tar.xz
xkbcomp                   1.4.7        20 February 2024 https://www.x.org/releases/individual/app/xkbcomp-1.4.7.tar.xz
xkbdata                   1.0.1        01 May 2014  https://www.x.org/releases/individual/data/xkbdata-1.0.1.tar.gz
xkbevd                    1.1.5        16 November 2022 https://www.x.org/releases/individual/app/xkbevd-1.1.5.tar.xz
xkbprint                  1.0.6        16 October 2022 https://www.x.org/releases/individual/app/xkbprint-1.0.6.tar.xz
xkbutils                  1.0.6        20 February 2024 https://www.x.org/releases/individual/app/xkbutils-1.0.6.tar.xz
xkeyboardconfig           2.39         14 June 2023 https://www.x.org/pub/individual/data/xkeyboard-config/xkeyboard-config-2.39.tar.xz
xkill                     1.0.6        16 November 2022 https://www.x.org/releases/individual/app/xkill-1.0.6.tar.xz
xload                     1.2.0        25 March 2024 https://www.x.org/releases/individual/app/xload-1.2.0.tar.xz
xlogo                     1.0.6        16 November 2022 https://www.x.org/releases/individual/app/xlogo-1.0.6.tar.gz
xlsatoms                  1.1.3        21 February 2019 http://xorg.freedesktop.org/releases/individual/app/xlsatoms-1.1.3.tar.gz
xlsclients                1.1.5        16 November 2022 https://www.x.org/releases/individual/app/xlsclients-1.1.5.tar.xz
xlsfonts                  1.0.8        04 March 2024 https://www.x.org/releases/individual/app/xlsfonts-1.0.8.tar.xz
xmag                      1.0.7        28 July 2022 https://www.x.org/releases/individual/app/xmag-1.0.7.tar.xz
xmahjongg                 3.7          01 May 2014  http://www.lcdf.org/xmahjongg/xmahjongg-3.7.tar.gz
xman                      1.2.0        25 March 2024 https://www.x.org/releases/individual/app/xman-1.2.0.tar.xz
xmedcon                   0.21.0       05 April 2021 https://prdownloads.sourceforge.net/xmedcon/xmedcon-0.21.0.tar.bz2
xmessage                  1.0.7        05 March 2024 https://www.x.org/releases/individual/app/xmessage-1.0.7.tar.xz
xmh                       1.0.5        23 March 2024 https://xorg.freedesktop.org/releases/individual/app/xmh-1.0.5.tar.xz
xmlcopyeditor             1.0.7.7      01 May 2014  http://puzzle.dl.sourceforge.net/sourceforge/xml-copy-editor/xmlcopyeditor-1.0.7.7.tar.gz
xmldom                    1.44         01 May 2014  http://search.cpan.org/CPAN/authors/id/T/TJ/TJMATHER/XML-DOM-1.44.tar.gz
xmllibxmlsimple           1.01         17 January 2020 https://cpan.metacpan.org/authors/id/M/MA/MARKOV/XML-LibXML-Simple-1.01.tar.gz
xmlnamespacesupport       1.12         14 February 2019 https://cpan.metacpan.org/authors/id/P/PE/PERIGRIN/XML-NamespaceSupport-1.12.tar.gz
xmlparser                 2.47         21 January 2024 https://cpan.metacpan.org/authors/id/T/TO/TODDR/XML-Parser-2.47.tar.gz
xmlsax                    1.02         23 June 2020 https://cpan.metacpan.org/authors/id/G/GR/GRANTM/XML-SAX-1.02.tar.gz
xmlsaxbase                1.09         28 December 2017 http://search.cpan.org/CPAN/authors/id/G/GR/GRANTM/XML-SAX-Base-1.09.tar.gz
xmlsec1                   1.3.3        23 February 2024 https://www.aleksey.com/xmlsec/download/xmlsec1-1.3.3.tar.gz
xmlsimple                 2.25         26 March 2018 http://www.cpan.org/authors/id/G/GR/GRANTM/XML-Simple-2.25.tar.gz
xmlsmart                  1.78         12 April 2019 https://cpan.metacpan.org/authors/id/T/TM/TMHARISH/XML-Smart-1.78.tar.gz
xmlto                     0.0.28       11 August 2016 https://releases.pagure.org/xmlto/xmlto-0.0.28.tar.bz2
xmltv                     0.5.70       28 June 2021 https://sourceforge.net/projects/xmltv/files/xmltv/0.5.70/xmltv-0.5.70.tar.bz2
xmodmap                   1.0.11       12 July 2022 https://www.x.org/releases/individual/app/xmodmap-1.0.11.tar.xz
xmore                     1.0.4        20 February 2024 https://www.x.org/releases/individual/app/xmore-1.0.4.tar.xz
xmp                       4.1.0        28 July 2018 https://sourceforge.net/projects/xmp/files/xmp/4.1.0/xmp-4.1.0.tar.gz
xorgcffiles               1.0.6        25 December 2015 https://xorg.freedesktop.org/releases/individual/util/xorg-cf-files-1.0.6.tar.gz
xorgproto                 2024.1       27 March 2024 https://www.x.org/releases/individual/proto/xorgproto-2024.1.tar.xz
xorgserver                21.1.13      13 April 2024 https://www.x.org/archive/individual/xserver/xorg-server-21.1.13.tar.xz
xorgsetup                 0.9.7        22 December 2015 ftp://ftp.slackware.org.uk/slacky/slackware-12.1/hardware/x.org-setup/0.9.7/src/xorgsetup-0.9.7.tar.bz2
xorgsgmldoctools          1.12         03 February 2024 https://www.x.org/archive//individual/doc/xorg-sgml-doctools-1.12.tar.gz
xorriso                   1.5.6        14 June 2023 https://ftp.gnu.org/pub/gnu/xorriso/xorriso-1.5.6.tar.gz
xosd                      2.2.14       01 December 2013 https://sourceforge.net/projects/libxosd/files/libxosd/xosd-2.2.14/xosd-2.2.14.tar.gz
xournal                   0.4.8.2016   08 August 2020 https://sourceforge.net/projects/xournal/files/xournal/0.4.8.2016/xournal-0.4.8.2016.tar.gz
xournalpp                 19.02.2024   19 February 2024 https://github.com/xournalpp/xournalpp/releases
xpad                      4.5.0        22 April 2015 https://launchpad.net/xpad/trunk/4.5/+download/xpad-4.5.0.tar.bz2
xpaint                    3.1.4        08 October 2021 https://sourceforge.net/projects/sf-xpaint/files/sf-xpaint/xpaint-3.1.4/xpaint-3.1.4.tar.bz2
xpdf                      4.04         04 December 2023 https://dl.xpdfreader.com/xpdf-4.04.tar.gz
xphelloworld              1.0.1        01 May 2014  https://xorg.freedesktop.org/releases/individual/app/xphelloworld-1.0.1.tar.bz2
xplsprinters              1.0.1        01 May 2014  https://xorg.freedesktop.org/releases/individual/app/xplsprinters-1.0.1.tar.bz2
xpr                       1.2.0        05 March 2024 https://www.x.org/releases/individual/app/xpr-1.2.0.tar.xz
xpra                      2.3.3        24 August 2018 https://www.xpra.org/src/xpra-2.3.3.tar.xz
xprehashprinterlist       1.0.1        01 May 2014  https://xorg.freedesktop.org/releases/individual/app/xprehashprinterlist-1.0.1.tar.bz2
xprop                     1.2.7        20 February 2024 https://www.x.org/releases/individual/app/xprop-1.2.7.tar.xz
xproto                    7.0.31       08 October 2016 https://www.x.org/releases/individual/proto/xproto-7.0.31.tar.gz
xpyb                      1.3.1        09 January 2018 https://xcb.freedesktop.org/dist/xpyb-1.3.1.tar.gz
xrandr                    1.5.2        04 December 2022 https://www.x.org/releases/individual/app/xrandr-1.5.2.tar.xz
xrdb                      1.2.2        05 June 2023 https://www.x.org/releases/individual/app/xrdb-1.2.2.tar.xz
xrefresh                  1.1.0        05 March 2024 https://www.x.org/releases/individual/app/xrefresh-1.1.0.tar.xz
xrender                   0.8.3        01 November 2012 http://freeware.sgi.com/source/xrender/xrender-0.8.3.tar.bz2
xrick                     021212       01 May 2014  http://www.bigorno.net/xrick/xrick-021212.tgz
xrx                       1.0.4        16 April 2019 https://www.x.org/releases/individual/app/xrx-1.0.4.tar.gz
xsane                     0.999        28 December 2017 http://anduin.linuxfromscratch.org/BLFS/xsane/xsane-0.999.tar.gz
xscope                    1.4.4        05 June 2023 https://www.x.org/releases/individual/app/xscope-1.4.4.tar.xz
xscreensaver              6.08         24 February 2024 https://www.jwz.org/xscreensaver/xscreensaver-6.08.tar.gz
xsel                      15.03.2024   15 March 2024 http://www.vergenet.net/~conrad/software/xsel/download/xsel-1.2.0.tar.gz
xset                      1.2.5        04 December 2022 https://www.x.org/releases/individual/app/xset-1.2.5.tar.xz
xsetmode                  1.0.0        01 January 2014 https://www.x.org/releases/individual/app/xsetmode-1.0.0.tar.bz2
xsetpointer               1.0.0        01 May 2014  https://xorg.freedesktop.org/releases/individual/app/xsetpointer-1.0.0.tar.bz2
xsetroot                  1.1.3        31 October 2022 https://xorg.freedesktop.org/releases/individual/app/xsetroot-1.1.3.tar.xz
xsm                       1.0.6        07 March 2024 https://www.x.org/releases/individual/app/xsm-1.0.6.tar.xz
xstdcmap                  1.0.5        04 December 2022 https://www.x.org/releases/individual/app/xstdcmap-1.0.5.tar.xz
xterm                     390          22 February 2024 https://invisible-mirror.net/archives/xterm/xterm-390.tgz
xtermcontrol              3.7          28 March 2019 http://thrysoee.dk/xtermcontrol/xtermcontrol-3.7.tar.gz
xtrace                    1.3.1        01 May 2014  https://alioth.debian.org/frs/download.php/file/3733/xtrace_1.3.1.orig.tar.gz
xtrans                    1.5.0        05 June 2023 https://www.x.org/releases/individual/lib/xtrans-1.5.0.tar.xz
xtrap                     1.0.3        18 April 2018 https://www.x.org/releases/individual/app/xtrap-1.0.3.tar.bz2
xu4                       1.0beta3     01 October 2013 http://xu4.sourceforge.net/xu4-1.0beta3.tar.bz2
xulrunner                 41.0b9       05 January 2016 http://ftp.mozilla.org/pub/xulrunner/releases/41.0b9/source/xulrunner-41.0b9.source.tar.xz
xvidcap                   1.1.7        01 October 2013 https://sourceforge.net/projects/xvidcap/files/xvidcap/1.1.7/xvidcap-1.1.7.tar.gz
xvidcore                  1.3.7        01 January 2020 http://downloads.xvid.com/downloads/xvidcore-1.3.7.tar.gz
xvidtune                  1.0.4        06 February 2023 https://www.x.org/releases/individual/app/xvidtune-1.0.4.tar.xz
xvinfo                    1.1.5        04 December 2022 https://xorg.freedesktop.org/releases/individual/app/xvinfo-1.1.5.tar.xz
xvoice                    0.9.6        01 April 2014 http://prdownloads.sourceforge.net/xvoice/xvoice-0.9.6.tar.gz
xwallpaper                0.6.2        09 July 2019 https://github.com/stoeckmann/xwallpaper/releases/download/v0.6.2/xwallpaper-0.6.2.tar.xz
xwayland                  23.2.6       09 April 2024 https://www.x.org/releases/individual/xserver/xwayland-23.2.6.tar.xz
xwd                       1.0.9        05 June 2023 https://www.x.org/releases/individual/app/xwd-1.0.9.tar.xz
xwininfo                  1.1.6        12 April 2023 https://xorg.freedesktop.org/releases/individual/app/xwininfo-1.1.6.tar.gz
xwud                      1.0.6        12 July 2022 https://www.x.org/releases/individual/app/xwud-1.0.6.tar.xz
xxhash                    09.06.2023   09 June 2023 https://github.com/Cyan4973/xxHash/archive/refs/tags/v0.8.1.tar.gz
xz                        5.6.1        09 March 2024 https://github.com/tukaani-project/xz/releases/download/v5.6.1/xz-5.6.1.tar.gz
yabause                   0.9.14       17 February 2017 https://sourceforge.net/projects/yabause/files/yabause/0.9.14/yabause-0.9.14.tar.gz
yaf                       2.12.2       01 May 2014  https://tools.netsa.cert.org/releases/yaf-2.12.2.tar.gz
yafc                      1.3.7        14 September 2017 http://www.yafc-ftp.com/downloads/yafc-1.3.7.tar.xz
yakuake                   3.0.5        22 September 2018 https://download.kde.org/stable/yakuake/3.0.5/src/yakuake-3.0.5.tar.xz
yaml                      0.2.5        02 June 2020 https://pyyaml.org/download/libyaml/yaml-0.2.5.tar.gz
yamlnetparser             07.02.2008   01 February 2013 https://sourceforge.net/projects/yaml-net-parser/files/yaml-net-parser/
yard                      0.9.26       26 July 2021 https://rubygems.org/downloads/yard-0.9.26.gem
yasm                      1.3.0        06 September 2014 http://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz
yaz                       5.27.1       12 February 2019 http://ftp.indexdata.dk/pub/yaz/yaz-5.27.1.tar.gz
yelp                      42.2         29 December 2022 https://download.gnome.org/sources/yelp/42/yelp-42.2.tar.xz
yelptools                 42.1         31 October 2022 https://download.gnome.org/sources/yelp-tools/42/yelp-tools-42.1.tar.xz
yelpxsl                   42.1         23 February 2024 https://download.gnome.org/sources/yelp-xsl/42/yelp-xsl-42.1.tar.xz
youtubedl                 2021.12.17   22 December 2021 https://github.com/ytdl-org/youtube-dl/releases/download/2021.12.17/youtube-dl-2021.12.17.tar.gz
ypserv                    2.19         01 May 2014  ftp://ftp.kernel.org/pub/linux/utils/net/NIS/ypserv-2.19.tar.bz2
yptools                   4.2.2        06 December 2017 http://www.linux-nis.org/download/yp-tools/yp-tools-4.2.2.tar.bz2
ytdlp                     17.02.2023   16 September 2022 https://github.com/yt-dlp/yt-dlp/archive/refs/tags/2023.02.17.tar.gz
yum                       3.4.3        15 November 2019 http://yum.baseurl.org/download/3.4/yum-3.4.3.tar.gz
z3                        4.8.8        19 June 2020 https://github.com/Z3Prover/z3/archive/z3-4.8.8.tar.gz
zabbix                    4.4.7        06 March 2021 https://sourceforge.net/projects/zabbix/files/ZABBIX%20Latest%20Stable/4.4.7/zabbix-4.4.7.tar.gz
zanshin                   23.08.5      21 February 2024 https://download.kde.org/stable/release-service/23.08.5/src/zanshin-23.08.5.tar.xz
zatacka                   0.1.8_       01 May 2014  https://sourceforge.net/projects/zatacka/files/zatacka/0.1.8/zatacka-0.1.8_src.tar.gz
zathura                   0.4.7        18 April 2021 https://pwmt.org/projects/zathura/download/zathura-0.4.7.tar.xz
zbar                      0.23.93      07 April 2024 https://github.com/mchehab/zbar/archive/refs/tags/0.23.93.tar.gz
zee                       0.6          01 May 2014  https://sourceforge.net/projects/zee/files/zee/0.6/zee-0.6.tar.gz
zenity                    4.0.1        26 March 2024 https://download.gnome.org/sources/zenity/4.0/zenity-4.0.1.tar.xz
zeroconfioslave           22.04.3      07 July 2022 https://download.kde.org/stable/release-service/22.04.3/src/zeroconf-ioslave-22.04.3.tar.xz
zeromq                    4.3.4        02 February 2021 https://github.com/zeromq/libzmq/releases/download/v4.3.4/zeromq-4.3.4.tar.gz
zfs                       2.2.3        23 February 2024 https://github.com/openzfs/zfs/releases/download/zfs-2.2.3/zfs-2.2.3.tar.gz
zile                      2.6.2        06 May 2021  https://ftp.gnu.org/pub/gnu/zile/zile-2.6.2.tar.gz
zim                       0.70         13 April 2019 https://zim-wiki.org/downloads/zim-0.70.tar.gz
zimg                      3.0.4        10 February 2023 https://github.com/sekrit-twc/zimg/archive/release-3.0.4.tar.gz
zip                       3.0          15 February 2023 https://downloads.sourceforge.net/infozip/zip-3.0.tar.gz
zipruby                   0.3.6        03 December 2017 https://rubygems.org/downloads/zipruby-0.3.6.gem
zix                       07.04.2024   07 April 2024 https://download.kde.org/stable/zix-07.04.2024.tar.xz
zlib                      1.3.1        23 January 2024 https://www.zlib.net/zlib-1.3.1.tar.xz
zope                      4.4.2        22 May 2020  https://files.pythonhosted.org/packages/04/e6/288b653d2e42dd5608093a14b954164d1d85f742577330e973c756ec4864/Zope-4.4.2.tar.gz
zopeinterface             6.1          28 October 2023 https://files.pythonhosted.org/packages/87/03/6b85c1df2dca1b9acca38b423d1e226d8ffdf30ebd78bcb398c511de8b54/zope.interface-6.1.tar.gz
zsh                       5.9          07 April 2024 https://www.zsh.org/pub/zsh-5.9.tar.xz
zstd                      1.5.6        28 March 2024 https://github.com/facebook/zstd/releases/download/v1.5.6/zstd-1.5.6.tar.gz
zsync                     0.6.2        26 January 2019 http://zsync.moria.org.uk/download/zsync-0.6.2.tar.bz2
zutils                    1.10         06 March 2021 http://download.savannah.gnu.org/releases/zutils/zutils-1.10.tar.lz
zvbi                      0.2.35       28 September 2015 https://sourceforge.net/projects/zapping/files/zvbi/0.2.35/zvbi-0.2.35.tar.bz2
zxingcpp                  2.0.0        10 February 2023 https://github.com/zxing-cpp/zxing-cpp/archive/refs/tags/v2.0.0.tar.gz
zziplib                   0.13.68      18 March 2024 https://sourceforge.net/projects/zziplib/files/zziplib13/0.13.68/zziplib-0.13.68.tar.bz2

</pre>


Currently this project does not accept donations, but
in the future this may be subject to change, including
more information in how folks could support the project,
if they would like to.

Of course **documentation**, **patches**, **bug fixes** and so
forth are **always** appreciated.

## Feedback wanted and appreciated, as well as contributions to the RBT project

<b>Feedback</b> about rbt will be considered, in particular to make working
with it easier and better. Suggestions to improve the project are also welcome,
in particular if it comes to smaller changes, as they are easier to implement.

New ideas about new or missing features and functionality are appreciated as
well.

Code contribution of all sorts are also accepted. Please try to adhere to
the coding standard(s) though - at the least document any new code
that is to be added extensively, so that other users (as well as I)
understand what the code does. I may add a github project tracker for
ideas pertaining this.


## Contact information and mandatory 2FA (no longer) coming up in 2022 / 2023

If your creative mind has ideas and specific suggestions to make this gem
more useful in general, feel free to drop me an email at any time, via:

    shevy@inbox.lt

Before that email I used an email account at Google gmail, but in **2021** I
decided to slowly abandon gmail, for various reasons. In order to limit the
explanation here, allow me to just briefly state that I do not feel as if I
want to promote any Google service anymore when the user becomes the end
product (such as via data collection by upstream services, including other
proxy-services). My feeling is that this is a hugely flawed business model
to begin with, and I no longer wish to support this in any way, even if
only indirectly so, such as by using services of companies that try to
promote this flawed model.

In regards to responding to emails: please keep in mind that responding 
may take some time, depending on the amount of work I may have at that
moment. So it is not that emails are ignored; it is more that I have not
(yet) found the time to read and reply. This means there may be a delay
of days, weeks and in some instances also months. There is, unfortunately,
not much I can do when I need to prioritise my time investment, but I try
to consider <b>all</b> feedback as an opportunity to improve my projects
nonetheless.

In <b>2022</b> rubygems.org decided to make 2FA mandatory for every
gem owner eventually:

see
https://blog.rubygems.org/2022/06/13/making-packages-more-secure.html

However had, that has been reverted again, so I decided to shorten
this paragraph. Mandatory 2FA may exclude users who do not have a 
smartphone device or other means to 'identify'. I do not feel it is
a fair assumption by others to be made that non-identified people may
not contribute code, which is why I reject it. Mandatory 2FA would mean
an end to all my projects on rubygems.org, so let's hope it will never
happen. (Keep in mind that I refer to mandatory 2FA; I have no qualms
for people who use 2FA on their own, but this carrot-and-stick strategy
by those who control the rubygems infrastructure is a very bad one to
pursue.
