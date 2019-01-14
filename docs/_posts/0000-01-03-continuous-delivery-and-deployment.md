## Continuous Delivery & Deployment
### Structure

-[+] What is it?
-[+] Why is it important?
-[+] How do we do it?

Note: Ask people what they think it means  

---

> “Continuous delivery … is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time and, when releasing the software, doing so manually. It aims at building, testing, and releasing software with greater speed and frequency  
> …

---

> “…  
> The approach helps reduce the cost, time, and risk of delivering changes by allowing for more incremental updates to applications in production. A straightforward and repeatable deployment process is important for continuous delivery.  
> …”

---

> “CD contrasts with continuous deployment, a similar approach in which software is also produced in short cycles but through automated deployments rather than manual ones.”  
> —<cite>[Wikipedia](https://en.wikipedia.org/wiki/Continuous_delivery)</cite>

---

> … teams produce software in short cycles …

Note: Just like our CI definition says several times a day…  
  Could be every five minutes, could be every two hours.  

---

> … ensuring that the software can be reliably released at any time …

Note: At any time means when code is pushed.  
  CI says “verified by an automated build”  
  Automated verification helps with this  
  Further: must be usable/desirable  
  Features should be complete or hidden  
  Going to focus on this  

---

> … when releasing the software, doing so manually …

Note: Manually triggering an automated process vs an automatic process.

---

<img src="images/continous-integration-delivery-deployment.svg">

Note: Explain push from CI to CD

---

# Why is it important?

-[+] Bigger deployments are riskier
-[+] Deploying fixes
-[+] Some changes require coordination
-[+] Unpushed code is risky

Note: Unfinished work can block releasing urgent fixes  
  Sometimes a coordinated release or business activity needs to happen

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BMTk3NzAyMjY0OF5BMl5BanBnXkFtZTgwNDQ4MTUxNTE@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Dinesh, did you deploy?  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Yeah, there were some performance improvements waiting.  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BMTk3NzAyMjY0OF5BMl5BanBnXkFtZTgwNDQ4MTUxNTE@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Did you look at what you were releasing?  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Yeah… you had a commit saying you were making changes to the login process.

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BMTk3NzAyMjY0OF5BMl5BanBnXkFtZTgwNDQ4MTUxNTE@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> That’s right. Making changes. So far all I’ve done is remove the old process.

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Dammit Gilfoyle.

---

# Smaller deployments

-[+] Less to test
-[+] Less suspects when investigating issues
-[+] Earlier visibility of problems

Note: Kinder to testers—less context to remember.  
  You will always miss things and release defects/have issues in production.    

---

What? ✅  
Why? ✅  
How? …


---

# How?
## Trunk vs Branch

-[+] Two different ways to make sure you don’t release incomplete changes
-[+] As usual this is a subjective issue
-[+] Each has pros and cons 

---

# The case for branching

---

# What is a branch?

-[+] Formed when two commits have the same parent
-[+] Commits made against the branch your working copy points to

---

# What is a working copy?

-[+] Your local clone is a working copy
-[+] Working copy ≠ branch
-[+] The copy can consist of multiple branches

---

## Feature Branch Workflow

> “… all feature development should take place in a dedicated branch instead of the master branch. … makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch will never contain broken code …”
> —[Git Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

---

### How do feature branches enable CD?

* Nobody works on the master branch
* Any feature based changes made on a feature branch

---

## Example *

### Mary begins a new feature

<img src="https://wac-cdn.atlassian.com/dam/jcr:223f5106-2191-4450-8916-e5c80d7d907a/02.svg?cdnVersion=ks">

```
git checkout -b marys-feature master
```

`*` Shamelessly borrowed from [Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

---

### Mary goes to lunch

<img src="https://wac-cdn.atlassian.com/dam/jcr:e2c88c1b-fb28-46a3-93be-c1c45f86bd1c/03%20(1).svg?cdnVersion=ks">

```
git push -u origin marys-feature
```

---

### Mary finishes her feature

<img src="https://wac-cdn.atlassian.com/dam/jcr:d0c471b4-61c8-4005-86bc-904d894e391b/04.svg?cdnVersion=ks">

```
git push
```

---

### Bill receives the pull request

<img src="https://wac-cdn.atlassian.com/dam/jcr:2119c2a3-7dff-43ad-bf98-77672d93242f/05%20(1).svg?cdnVersion=ks">

---

### Mary publishes her feature

<img src="https://wac-cdn.atlassian.com/dam/jcr:09308632-38a3-4637-bba2-af2110629d56/07.svg?cdnVersion=ks">

```
git checkout master
git pull
git pull origin marys-feature
git push
```

---

# Afterwards

Delete the branch… done.

---

# Exercise
## Make two changes using branches

---

# The case for trunk based development

---

## Everyone works on `master`

---

## Changes regularly pushed back to origin

---

## WIP protected using feature shields

-[+] Shield prevents feature taking action in production
-[+] Sometimes toggled on and off per environment
-[+] Basically conditionals to activate / deactivate bits of code

---

# Dark deployments 

---

# Tidying Up

* Need to remove feature shields once functionality released

---

# A cautionary tale

(Story about banking incident where feature shield caused massive losses)

---

# Exercise
## Make two changes using trunk based development
