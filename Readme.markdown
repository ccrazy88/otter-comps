# Otter Comps!  And learning (a little bit) about git, perhaps!
**Authors**: Chrisna Aing, Sarah Halls, and Kiva Oken  

There will be a first draft of this paper here by Thursday, February 25, 2010!
Otherwise, we will all be dead.  A presentation should also appear at some point
and it will also be written in LaTeX, obv.  

[George] says that throwing this on both of you will be next to impossible and I
want to prove him wrong, even though I sort of agree with him.  Please help me
out here!  And take a look at his terrific face.  Really, unless we are going to
type the entire thing together, this will be a godsend.

## Git

### Installation:

**3rd CMC (OS X)**:

1. Open the Terminal application.
2. Enter the command `emacs .bash_profile`.  A text file should show up.
3. In the line that begins `PATH=$PATH:`, add `:/opt/local/git/bin` to the end.
4. Press `Ctrl-x Ctrl-s` to save and then `Ctrl-x Ctrl-c` to exit.
5. Close and reopen the Terminal application and try executing the command 
   `git`.  If you see a long list of commands, it is installed.
6. [Generate] and add a new SSH key.
7. [Set] your username, e-mail, and GitHub token.
8. Enter the command `git config --global core.autocrlf input`.
9. You should be ready to get going!

**Mac OS X**:

1. [Download] and install git.
2. Follow Steps 6-9 of the 3rd CMC installation guide.

**Windows**:

1. See me.  I'll do it for you -- it will be much less painful (for you) this
   way.

### Tutorials:

1. [Read this first].  You will want to skip to the point about cloning an
   existing repository.  The existing repository will be this one, the link to
   which can be found near the top of the page!  The tutorial will teach you the
   basics you will need to know, which I hope is all we need to get this thing
   done.  And then you will be able to show this to all of your friends!
2. [Working with the repository].  This is an overview of the commands you will
   use to interact with the online version of our paper and presentation.
3. More are on the way?

### Strategy:

**Master**: Contains final or close-to-final portions of our paper.  
**Branches**: We will each take multiple branches out, each of which will
correspond to a piece of the paper that we are currently working on.  Once they
are finished to our liking, they will then be merged to the master.

## LaTeX

### Some useful rules of thumb:

1. Split long sentences into several lines so that each line has at most 80
   characters.  **This is VERY important, since git works line-by-line.  Switch
   to a monospaced font and make sure your window is 80 characters wide!**
2. Turn off automatic line wrapping of your LaTeX editor.
3. Do not change line breaks without good reason.
4. Verify that your code can be compiled flawlessly before committing your
   modifications to the repository.
5. Add a meaningful and descriptive comment when committing your modifications
   to the repository.
6. Put only those files under version control that are directly modified by the
   user.  **This has already been done by me (or rather, .gitignore).**

Goodbye!

[George]: http://drp.ly/pzye4+
[Generate]: http://help.github.com/mac-key-setup/
[Set]: http://help.github.com/git-email-settings/
[Download]: http://tinyurl.com/ydyjqva
[Read this first]: http://learn.github.com/p/setup.html
[Working with the repository]: http://help.github.com/remotes
