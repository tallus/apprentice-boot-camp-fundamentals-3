## The case for branching…

--

## Branches

+ Protect the main code-base from incomplete changes
+ Enable parallel streams of development
+ Make the history more legible

--

## Feature Branch Workflow

> “… all feature development should take place in a dedicated branch instead of the master branch. … makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch will never contain broken code …”
> —[Git Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

--

## How do feature branches enable CD?

+ Nobody works on the master branch
    + thus master is always releaseable
+ Any feature-based changes made on a feature branch
+ Some Continuous Integration systems only run on master...


Note:
Mention that some people consider that not running against master isn't true CI.

--

## Example *

### Mary begins a new feature

<img src="https://wac-cdn.atlassian.com/dam/jcr:223f5106-2191-4450-8916-e5c80d7d907a/02.svg?cdnVersion=ks">

```
git checkout -b marys-feature master
```

`*` Shamelessly borrowed from [Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

--

### Mary goes to lunch

<img src="https://wac-cdn.atlassian.com/dam/jcr:e2c88c1b-fb28-46a3-93be-c1c45f86bd1c/03%20(1).svg?cdnVersion=ks">

```
git push -u origin marys-feature
```

--

### Mary finishes her feature

<img src="https://wac-cdn.atlassian.com/dam/jcr:d0c471b4-61c8-4005-86bc-904d894e391b/04.svg?cdnVersion=ks">

```
git push
```

--

### Bill receives the pull request

<img src="https://wac-cdn.atlassian.com/dam/jcr:2119c2a3-7dff-43ad-bf98-77672d93242f/05%20(1).svg?cdnVersion=ks">

--

### Mary publishes her feature

<img src="https://wac-cdn.atlassian.com/dam/jcr:09308632-38a3-4637-bba2-af2110629d56/07.svg?cdnVersion=ks">

```
git checkout master
git pull
git pull origin marys-feature
git push
```

--

## Afterwards

Delete the branch… done.

---

<img height="500" src="https://upload.wikimedia.org/wikipedia/commons/0/01/LinuxCon_Europe_Linus_Torvalds_03_%28cropped%29.jpg">

+ Linus Torvalds

--

<img src="http://upload.wikimedia.org/wikipedia/commons/a/af/Tux.png"/>

+ Father of the Linux kernel
+ Creator of git
+ Mother of...

--

> What the #*?!, guys?
> This piece-of-$#?! commit is marked for stable, but you clearly never
> even test-compiled it, did you?

> There aren't enough swear-words in the English language, so now I'll
> have to call you perkeleen vittupää just to express my disgust and
> frustration with this crap.
 
> Linus [LKML.ORG 2013](https://lkml.org/lkml/2013/7/13/132)

Note:
Allegedly he has attempted to clean up his act since

--

## Why is Linux a good example?

[gitstats for Linux kernel end of 2019](https://phoronix.com/misc/linux-eoy2019/lines.html)

+ It's not just Linux

[<img src="https://opensource.org/files/osi_keyhole_300X300_90ppi_0.png">](https://www.opensource.org)

--

> The normal git workflow involves the use of a lot of branches.
> Each line of development can be separated into a separate “topic branch” and maintained independently.
> Branches in git are cheap, there is no reason to not make free use of them.

[A Guide to the Kernel Development Process](https://www.kernel.org/doc/html/latest/process/7.AdvancedTopics.html) 

--

> ...Git is “expressly designed to make you feel less intelligent than you thought you were.” What’s your response to this?

> Torvalds: So I think it used to be true but isn’t any more. There is a few reasons people feel that way, but I think only one of them remains. The one that remains is fairly simple: “you can do things so many ways.”

[10 Years of Git](https://www.linuxfoundation.org/blog/2015/04/10-years-of-git-an-interview-with-git-creator-linus-torvalds)

--

## A prophecy...

<iframe src="https://player.vimeo.com/video/60788996" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/60788996">GIT IS HARD</a> from <a href="https://vimeo.com/owltastic">Meagan Fisher</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

Note:
This video probably needs a bit of context setting - it's a developer having some issues with git which perplexes the whole team.
This situation is not uncommon ;-)
We're going to do some exercises involving branching, git is a very powerful tool, it's possible to get things VERY wrong.

--

<img style="border:0;box-shadow:none;background-color:transparent" src="images/aliens.png">

Note:
I'm increasingly of the opinion that there is only one real explanation for how git works, and that is that it is alien technology ;-)

--

<img width="500px" src="images/guitar_hero.png">

Note:
Branches can easily get out of control, they should be few in number and short-lived - you have been warned.

--

### Git guidelines

+ Use a small set of commands:
    + clone
    + commit
    + push
    + pull
+ Use a consistent workflow
+ Branches should be short-lived
+ The number of branches should be small

--

## Merging

<img src="https://wac-cdn.atlassian.com/dam/jcr:09308632-38a3-4637-bba2-af2110629d56/07.svg?cdnVersion=ks">


Note:
What is a merge
Sometimes it's easy
And sometimes it's hard

--

<backgroundimage>images/traffic_merge.svg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

+ Git is actually good at merging
+ Some merges are simple
+ Some merges are not
+ Keeping your branches short-lived decreases the risk of complicated merges
    

--


## Different kinds of merge

+ Simple
    + Different files
    + Same file, different lines
    + Same file, same lines
+ Complicated

Note:
Whiteboard what might be simple and complex merges with the group

--

## Diverging branches

<img src="images/diverging_branches.svg">

+ The problem gets worse with distance and time


Note:
It's not just the change itself that determines the complexity of the merge, they get worse with distance and time.
You can end up with separate bits of software.
Like straddling two diverging canoes.


--

## A simple merge

<img src="images/green_merge.png">

+ Be a little wary

Note:
Worth pointing out that just because a merge can be completed automatically, does not guarantee the functionality is
correct.

--


## A complicated merge

<img src="images/merge_hell.png">

Note:
A salutary tale - whilst working on the slides I failed to follow my own advice and ended up with conflicts.
Explain the merge view, our changes on the left, base version in the middle, other developer's version on the right.

--

## Conflicts

```
<<<<<<< HEAD:file.txt
Conflicts
=======
What conflicts?
>>>>>>> 77976da35a11db4580b80ae27e8d65caf5208086:file.txt
```

+ Must be resolved manually
+ _**BE AFRAID!**_


Note:
What are they  
What do they look like  
What is the effect  
How do you resolve them  
