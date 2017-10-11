# Git Primer

~~use Subversion~~

Git is increasingly the source control of choice among both open source enthusiasts and Microsoft developers. While it definitely has its problems and the learning curve is steep, its flexibility allows it to scale all the way from a one-person open source project to a corporate enterprise. In addition, its decentralized nature (more on this in a bit) lends itself very well to community driven projects.

## Caveat Emptor

Something will probably go wrong with your repo at some point. It may or may not be a quick fix when it does. (A lot of professionals still struggle with git, your mentors included.) Nevertheless, one nice thing about git is that it stores *every* change. There's always a way back. It just may take a little time to find.

## Git Terminology

<dl>
<dt>Repo(sitory)</dt>
<dd>A single project managed by git. (This is a generic term for <em>anything</em> git manages, not just the copy on Github.)</dd>
<dt>GitHub</dt>
<dd>A website that hosts open source repositories for free.</dd>
<dt>Working Set / Working Changes</dt>
<dd>Files that have been modified but not commited.</dd>
<dt>Clone</dt>
<dd>Copy a remote (i.e. GitHub) repo to your local computer.</dd>
<dt>Branch</dt>
<dd>Tricky to explain. For now, think of it as a jumping-off point to develop new features without affecting code that works.</dd>
<dt>Checkout</dt>
<dd>Switch between branches. (**Note:** What git calls "clone" is called "checkout" in other source control programs. Yes, this is confusing. No, we don't know why they did it.)
<dt>Push</dt>
<dd>Send the latest version of your code to a linked repo, i.e. GitHub.</dd>
<dt>Pull</dt>
<dd>Request latest version of code from a linked repo.</dd>
<dt>Master / Trunk / Mainline</dt>
<dd>The original, single code branch created at the project's beginning. *All* branches derive from master.</dt>
<dt>Origin</dt>
<dd>A special name given to a *remote* master branch.</dd>
<dt>Merge</dt>
<dd>Fold two series of changes together. Useful when two branches have been worked on in parallel and need to sync up without stepping on each other.</dd>
<dt>Conflict</dt>
<dd>Most of the time, git handles merges automatically using file date/time, etc. Sometimes, though, two conflicting changes will confuse it. These opposing changes are called *conflicts.* Whatever you were doing, it can't be continued until all the conflicts are resolved.</dd>
<dt>Resolve</dt>
<dd>Examine a conflict and choose which of the two changes to apply.</dd>
<dt>Fork</dd>
<dd>Copy another person's project to your own account. (Includes links to the original, of course!)</dd>
<dt>Pull Request</dt>
<dd>Ask a project owner to add your code to theirs. They have to approve it before the merge can take place. Usually used with forks, but it can also be used with branches in some setups.</dd>
<dt>BASH (Shell)</dt>
<dd>A command interpretor often used in linux. Differs wildly from the Windows Command Prompt and requires a different set of commands.</dd>
<dt>Git Bash</dt>
<dd>A Windows-based combination of the BASH shell and git command line.</dd>
<dt>TortoiseGit</dt>
<dd>User friendly(?) Windows GUI which runs the git command line. Integrates seamlessly with Windows as a series of right-click menus.</dd>
</dl>

## Quick Start: Basic usage

1) Create a repo on GitHub
2) `git clone https://github.com/myname/myproject` (replace name and project, of course)
3) Make some changes
4) `git add .`
5) `git commit -am "Make some good notes here. You'll thank yourself later."`
6) Repeat until you're ready to save changes to GitHub
6) `git push`
7) Come back later
8) `git pull`
9) Go to step 3

**Note:** Step 8 is optional *if* you're the only person working on the repo *and* you're only using one computer. Otherwise, do a pull before you start. It'll save you a world of pain.

## Quick Notes: Branching

You shouldn't have to branch for this class. Unless you know what you're doing and are comfortable with the concept, avoid it. Merging a branch is outside the bounds of this document, and if you're just starting out, it's not worth the heartburn.

## How Git Works 

**Nerd stuff ahoy!** Unfortunately, this is actually important, so I recommend reading it. The quick start should be enough to get off the launchpad, though.

There are two core concepts in git: differentials and decentralization.

### Differentials

After the repo is initialized, git tracks *every* change made to the code and stores it in the `.git` folder. To keep from having to make copies of the same file over and over again, git employs a concept called **differentials**. Essentially, git will track *only* the parts of files that change between commits and store those to disk. Git was made to deal with source code, and source changes are often a handful of lines or some new 3kb files, so the tracking is barely noticeable. Differentials are how git can track every change you've ever made without eating up all your disk space.

### Decentralization

Many source control programs use the concept of a "central repository." You have one master copy of the project that sits on a server somewhere, and everyone takes that copy as gospel. You can branch, you can merge back, but there's always *one* version that's official.

Git was built differently. Git is **decentralized,** which means no one repo can claim to be the ultimate source. A local git repo is every bit as valid as the one it was cloned from. It can do everything the remote repo could do. If the original ever goes away, the local repo can keep chugging merrily along. (In fact, it can just upload itself somewhere else!) On top of that, GitHub introduces a concept called **forking,** which allows you to copy other people's projects into a new repo. **Git is a swarm, not a dictatorship.** Understanding this goes a long way towards figuring out Git.

Of course, most people will just use GitHub as a central repository with git---and that's fine. This is the maddening thing about git: the commands are all there, but the usage is up to the individual users/companies. Git can deal with central repositories, multiple forks, feature branches off mainline, per-developer branches, and a hundred more methods even more cryptic than what you just read. Git was made to be extremely flexible, but it doesn't offer much in the way of organization. For better or worse, that's up to the users.

## Some More Complicated Terms

You *probably* won't need these for this class. Still, they're good to know.

<dl>
	<dt>Rebase</dt>
	<dd>Basically, you're picking up all your changes, doing a pull, and then dropping your changes there instead. Tricky, and you can get yourself in a lot of trouble if you do it wrong. But, it can also save you a ton of headaches by avoiding merging and conflicts altogether.</dd>
	<dt>Cherry Pick</dt>
	<dd>Select which differentials to merge. Often used to selectively import code changes without bringing over the entire branch. (Example: You were working on a feature, and it fixed a bug, but you don't want to bring over the new UI until it's fully tested. You can *cherry pick* the changes that fix the bug.)
	<dt>Reset</dt>
	<dd>Roll the codebase back to a specific version. Usually used with `git reset --hard`, which dumps all working changes and returns to the last commit made. Usage beyond that is the kind of stuff *I'm* not all that clear on.</dd>
	<dt>
</dl>

## Merging

Merging is one of the least fun parts of coding. The process is cryptic, your collegue's code is indecypherable, and you have to herd cats just to get answers from him/her. Nevertheless, if you have more than one person on a project, conflicts and merging are inevitable. It used to be so much more difficult when differential source control programs didn't exist.

Take a moment to ponder *that* sobering thought.

Anyway, besides having to track down conflicts, there's also the problem of actually resolving them. Git is text based and doesn't do merging very well on its own. Basically, you're pointed in the right direction with some cryptic marks scrawled in, and that's about it. **A good GUI that works well with git is essential for merging.** TortoiseGit comes with one. Visual Studio, Atom, and (probably?) Brackets can get plugins to provide one. A GUI allows you to see the two versions side by side with conflicts highlighted. After that, you can click one change or the other to resolve.

**For the purposes of this class, you should be doing very little merging, if any.** I strongly advise you only work in master for the entirety of your project.

## I haven't branched! Why is Git asking me to merge?! 

If `git pull` ever yells at you about merging, something has gone wrong. (Most likely, you didn't do a pull before starting work on another computer.) A rebase is probably the fastest way to fix everything. Contact your friendly neighborhood mentor for more details.
