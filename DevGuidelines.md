# General Dev Rules
and yes these can all change whenever we feel it’s necessary.

Make things readable to humans.  Use your best judgement and give some thought to the name(s).  Spend 3 minutes on it and ask someone if you want.

Bad example

`var a = class.Do(i);`

Good example

`var companyCategories = categories.GatherCompanyCategories(companyId);`

If you want to try something crazy, **say something**.  If it seems like a good idea to someone else too -- go for it.  Make a branch. And timebox it.
	if you reach your timebox, check it in anyway -- again, on the branch
	Show the crazy, have a reason why we should do it.

## If you get stuck, ask.  
Don’t pound on a problem for hours, alone.  Ever.

Treat tests as a mandatory.  This means javascript too.  We’ll use Jasmine for that.
Not saying pure TDD (I do like it though) -- but wrap it up in a good set of tests.
Got something else you want to use? let’s hear it

Rebase before checking in.
*If more than one person is in a class, pair up a bit, figure out who’s doing what.

Say no to unplanned work.
* Anyone will tell you their problem is the most important problem, and in their mind it is.  But the team needs to stay focused and always working towards known, well defined work.  Unless the building is literally on fire, then get out fast.

Strangle code that has no tests
* Pick it up some part of it, drop it into a new class, test it relentlessly as is. Then when it’s well covered, write some tests for the new implementation / feature / whatever and replace the old code with calls to the new code.

10 small commits are better than 1 monster commit
* Add your items, in small bits if possible. Stage them then give a message and commit. Note this does not send them to the remote branch


## Git Goodies -- note that only the master branch builds.

also note any git command can be investigated by doing --?, so 

`git --?`

`git branch --?`

`git pull --?`

`git rebase --?`

and so on will all bring up details on those given commands.  Also google is your friend !

## basic git commands and what they do

`git status` show my changes 

`git add .` add everything (careful)

`git add /path/*` add everything in /path

`git gui` bring up git gui

`gitk` show what my branch looks like

`gitk --all` show all branches

`git commit -m “<message>”` make a commit with given message

`git pull --rebase` get changes for my branch and put my changes at the end

`git rebase origin/<branchname>` get a different branch and the branch I’m on, and all my changes at the end

`git merge <branchname>` take the given branchname and merge it onto the current branch, inline.

`git merge <branchname> --no-ff` take the given branch and merge it with a merge commit

`git stash` save off a set of changes not committed

`git stash pop` get the last saved set of stashed changes

`git checkout .` undo tracked changes

`git clean -df` clean out all the untracked changes

`git checkout <BranchName>` I want to switch branches

### More complex stuff

I have changes and want to put them on the remote branch

`git status`

`git gui`


“I have a small change and don’t need a gui”

`git status`

`git add .`

`git commit -m “<message>”`

`git push origin master`

“my branch is done and I’m ready to merge it”
<starting from your branch>

`git pull`

`git rebase origin/master`

`git mergetool`
<fix conflicts if any, install a diff tool if you have to>

`git checkout master`

`git merge <branchname> --no-ff` (this is my personal preference, I like this pattern)

`git push origin master`

“I want to get the latest stuff, but I have changes too”

commit all your changes locally, if you have leftovers that’s fine

`git checkout .` (reset tracked files)

`git clean -df` (clear untracked files)

`git pull --rebase`

`git push origin <BranchName>`

“My merge has went all screwy and I want to start over”

`git merge --abort`

“I have changes leftover but don’t need them after I’ve committed”

`git checkout .`

`git clean -df`

“I want to make a branch” (you can do this with commits pending btw)

`git checkout -b <BranchName>`
`git push origin <BranchName>`

“I have a change I want to keep for a while but not commit it”

`git stash`

<do stuff, damn you John, commit>

`git stash pop`

_note that this only pops the LAST stash you made … so if you do 3 stashes..._
