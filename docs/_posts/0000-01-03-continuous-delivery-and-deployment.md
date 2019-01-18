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
-[+] Fewer suspects when investigating issues
-[+] Earlier visibility of problems

Note: Kinder to testers—less context to remember.  
  You will always miss things and release defects/have issues in production.  
  Canary deployments are a technique to derisk significant changes to production. 

---

What? ✅  
Why? ✅  
How? …

---

<backgroundimage>https://staticshare.america.gov/uploads/2014/11/canary_art22-1068x479.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

# Canary deployments

-[+] As in the canary in the coal mine
-[+] Feature released to small number of test users
-[+] Provides early warning sign
-[+] Similar to A/B Testing

<small>Image credit [State Department/Doug Thompson](https://share.america.gov/english-idiom-canary-coal-mine/)</small> 

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

# A prophecy...

<iframe src="https://player.vimeo.com/video/60788996" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/60788996">GIT IS HARD</a> from <a href="https://vimeo.com/owltastic">Meagan Fisher</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

Note:
We're going to do some exercises involving branching, git is a very powerful tool, it's possible to get things VERY wrong.

---

<img width="500px" src="images/guitar_hero.png">

Note:
Branches can easily get out of control, they should be few in number and short-lived - you have been warned.

---

<img style="border:0;box-shadow:none;background-color:transparent" src="images/aliens.png">

Note:
I'm increasingly of the opinion that there is only one real explanation for how git works, and that is that it is alien technology ;-)

---

# Exercise
## Make two changes using branches

* Work in pairs - ___***sharing the same git repository***___
* Create two branches based on the same start point
* One person implements Story 2 - Diesel vehicles
* One person implements Story 3 - Alternative fuel vehicles
* Merge them back to master one by one and observe Travis inbetween

Notes:
See branch ```petrol_tax``` for a starting point to this exercise if they haven't completed the previous one.
N.B. don't get them to checkout the branch (git weirdness will ensue), just get them to copy-paste the working code.
There are already test suites for these stories they just need to be enabled so the build runs them.

---

## The case for trunk based development

-[+] Everyone works on ‘master’
-[+] Changes regularly pushed back to origin

---

## Handling multiple changes in progress

Users are shielded from work-in-progress using Feature Toggles

---

# Feature Toggles

AKA Feature Shields/Flags/Switches/Flippers

-[+] Basically conditionals to activate/deactivate bits of code/user interfaces
-[+] May be toggled on and off per environment using configuration
-[+] Prevent features taking action in production environments

(see Further Reading for a good [Feature Toggles article](https://martinfowler.com/articles/feature-toggles.html))

---

## Continuous Integration

-[+] Changes to trunk picked up by CI system
-[+] You *can* toggle features on per environment or per test
-[+] If you do, feature is tested on each push
-[+] Increased complexity—introduces a new code path
-[+] May need to run tests with multiple toggle combinations

Note: It is possible to do CI with branches but few do and there can be issues.
  Features promoted or new builds toggle per environment.  
  Feature branches don’t address complexity—can’t test integrated WIP.

---

## Implementing a Feature Toggle

```javascript
  const features = fetchFeatureTogglesFromSomewhere();

  function generateInvoiceEmail(){
    const baseEmail = buildEmailForInvoice(this.invoice);
    if( features.isEnabled("next-gen-ecomm") ){ 
      return addOrderCancellationContentToEmail(baseEmail);
    }else{
      return baseEmail;
    }
  }
```

Taken from [Feature Toggles (aka Feature Flags)](https://martinfowler.com/articles/feature-toggles.html)

---

# Tidying Up

Code was added to implement feature toggles so we need to tidy this away once functionality fully released

---

# A cautionary tale

[Knightmare: A DevOps Cautionary Tale](https://dougseven.com/2014/04/17/knightmare-a-devops-cautionary-tale/)

-[+] Knight Capital, $365 in assets
-[+] Incomplete deployment
-[+] Reused feature toggle
-[+] Reverted code change but left toggle on
-[+] $460 million loss over in 45 minutes—bankrupt!

Note: Market saw problem in by 09:31—one minute after opening  
  One server (of eight) had failed deployment and was running older code deactivated by now reused toggle  
  No kill switch  
  Back out left resulted in eight bad servers—4 million transactions

---

## Exercise
### Make two changes using trunk based development

* Work in pairs - ___***sharing the same git repository***___
* Implement your own feature toggle
* One person implements Story 4 - After the first year
* One person implements Story 5 - Expensive vehicles after the first year
* Leave your feature toggles off so the built code doesn't apply the new rules yet
* Turn the new features on one at a time

Notes:
See branch ```diesel_and_alternative_tax``` for a starting point to this exercise if they haven't completed the previous one.
N.B. don't get them to checkout the branch (git weirdness will ensue), just get them to copy-paste the working code.
There are already test suites for these stories they just need to be enabled so the build runs them.
There is also an example solution on the ```subsequent_years``` branch.

---

# Checkpoint
## 

---

Summary

---

## Pros of Feature Branching

-[+] Once feature released, clean up as simple as deleting the branch
-[+] If feature abandoned, unused code not left polluting master
-[+] No need to deal with pesky conflicts while developing
-[+] Scales well with large number of features in progress

---

## Pros of Trunk Development

-[+] Changes visible to whole team throughout feature development
-[+] Code review regular rather than large and unpalatable
-[+] Feature can be tested on each push
-[+] Potentially earlier visibility of quality regressions
-[+] No big, scary merge at the end