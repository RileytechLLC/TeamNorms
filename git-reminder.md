# These serve as a reminder - if you don't know what you're doing, update your resume before you do any of these. And maybe call some references just incase.

In this, I want to go over what I do with git and how I work my branches. Your mileage will vary, but this is the best I've found. Yes there are faster ways to do it with combining commands and such, but this is a REMINDER.

### Concept : spawn points, denoted with --> :godmode: 
this is something I made up to explain a way to do things safely. If you create a spawn point, you can ALWAYS get back to a good state. Yes you could do it all on local, but I use the tool to save me from myself. Save spawn points often. If you do get stuck and completely mess up your local, a remote reset will give you whatever is out on remote.
```bash
git reset origin/$branch --hard
```


## Rebasing
Assumptions :
- master is ...um ...master
- origin is ...um ...origin
- feature-of-awesome is your feature branch.
- feature-of-awesome has been pushed --meaning local and remote match. AKA :godmode: 
- no one else is working on your branch

you start with a :godmode: 
```bash
git checkout master
git pull
git checkout feature-of-awesome
git rebase origin/master
#deal with conflicts if any
gitk #review
```

```bash
git push origin feature-of-awesome --force-with-lease
```
:godmode: new spawn point created

```bash
git checkout master
git merge feature-of-awesome --no-ff
# give it a commit message (or just save it as-is, that's what I do 99.9% of the time)
```
:godmode: new spawn point created
