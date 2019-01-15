# Continuous Integration

-[+] What is it?
-[+] Why is it important?
-[+] How do we do it?

Note: Ask people what they think it means  

---

> “Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.  
>  
> By integrating regularly, you can detect errors quickly, and locate them more easily.”  
> —<cite>[ThoughtWorks](https://www.thoughtworks.com/continuous-integration)</cite>

---

> … integrate code into a shared repository …

Note: Integration of many developers code.  
  Shared repository meaning something like Git.  

---

> … several times a day …

Note: could be every five minutes, could be every two hours.  
  Not every three days.  

---

> … verified by an automated build …

Note: verification may mean running something, testing something, or running tools to do ‘static analysis’.  
  Automated for consistency.  
  Ideally the build process is repeatable.  

---

> … detect errors quickly, and locate them more easily …

Note: Why is it good to detect quickly?  
  Mitigate consequences, minimise context switching.  
  Spend more time building features.  

---

# Common sense?

---

# Why is it important?

> “Works on my machine.”  
> —<cite>Unpopular developer</cite>

Note: Used to be a very common phrase.  

---

# There was a time before automated tests…

We had to wait months for things to be tested

---

# But then…

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Gilfoyle, did you break the build?  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BMTk3NzAyMjY0OF5BMl5BanBnXkFtZTgwNDQ4MTUxNTE@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> No, Dinesh… I did not.  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> [delay]  
> Are you sure? The tests are failing/code doesn’t compile.  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BMTk3NzAyMjY0OF5BMl5BanBnXkFtZTgwNDQ4MTUxNTE@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Yep. Works on my machine. It’s probably user error.  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> [delay]  
> Where is `c:/gilfoylestestdata/`?    
> /    
> Where is `Gilfoyle.java`?  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BMTk3NzAyMjY0OF5BMl5BanBnXkFtZTgwNDQ4MTUxNTE@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> [delay while Gilfoyle eats lunch]
> Try it again.  

---

<backgroundimage>https://m.media-amazon.com/images/M/MV5BN2IzYjhlOTUtMDVmMy00NTk3LTkxNjAtNDZmYjFhNzY3OWJlXkEyXkFqcGdeQXVyNjc5Mjg0NjU@._V1_SY1000_SX1500_AL_.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

> Dammit Gilfoyle.

---

# Integrating code

-[+] Exposes incomplete commits & case sensitive paths
-[+] Makes sure code works in a (hopefully) stable environment
-[+] Provides early/incremental visibility of other developers changes

Note: Windows file systems case insensitive.
  Paths which won’t work on Linux/MacOS.  
  Tests which only work with developer specific incantations.  
  When working in similar areas functional changes sometimes cause conflicting changes.  
  Much easier to address conflicts while they are still small rather than spending days trying to consolidate two directions.  

---

## When the build fails, you want to be confident that the code is broken

Note: Just like the boy who cried wolf…  
  If people don’t trust the build, they ignore it

---

# Important factors

-[+] Time
-[+] Reliability
-[+] Meaningful failures
-[+] Repeatability

---

# Good practices

-[+] Fix broken builds quickly (don’t commit over the top)
  -[+] Be aware of failures—use notifications etc
-[+] Don’t ‘commit & quit’
-[+] You break it, you fix it
-[+] Fix or delete flaky tests (don’t just re-run)
-[+] Make sure your build stays fast
-[+] Keep test environment ‘like production’

Note: Some tests are unreliable—might fail 1% of the time.  
  Fast means 5 minutes or less for some positive feedback.  
  Test environment data is rarely comparible with production.  

---

# Typical Enterprise ‘Pipeline’

* Run fast tests
* Run slow tests and static analysis
* Publish packaged code
* Deploy to dev
* Deploy to test
* Deploy to production

---

What? ✅   
Why? ✅  
How? …

---

# Many options

* Bamboo
* CircleCI
* CruiseControl.NET
* GitLab
* GoCD
* Jenkins
* TravisCI

Note: Moving landscape. GitHub should release their own version soon (Actions).  

---

# Common Features

-[+] GitHub Integration
-[+] Support for performing tasks in parallel
-[+] Publishing / releasing built artifacts
-[+] SCM support: Git / Subversion / CVS / etc.
-[+] Language / build tool support
-[+] Notifications
-[+] Configuration as code

---

# E.g. Travis CI

-[+] Authorise Travis CI to use your github.com account
-[+] Activate Travis CI with your repository
-[+] Add a `travis.yml` file to your repository
-[+] Optional: add build badge to the repository

---

# Then…

-[+] GitHub tells Travis CI each time there is something to fetch and build
-[+] Travis fetches that version of the code
-[+] Travis works out what to run based on repository contents (including `travis.yml`)
-[+] Travis reports status back to GitHub to mark commits with success/failure

---

`travis.yml`:

```yaml
language: java
```

```yaml
language: csharp
solution: solution-name.sln
```

```yaml
language: python
  python:
    - "3.6"
  script:
    - pytest
```

Note: Travis looks at repo to work out how to build once it knows language

---

# Exercise Part 1
## Set up Travis CI

* Fork the example repository
* Log into https://travis-ci.org
* Check that you can see your repository in the list
* Activate Travis CI for your fork

Note: Make sure you have the right Travis CI  
  travis-ci.com is the paid for enterprise version

---

# Exercise Part 2
## Configure your build

* Add a `travis.yml` file to your repo
* Push a change to the README.md file
* Watch Travis clone your project and build it
* Hopefully see your tests pass

---

# Exercise Part 3
## Make it fail

* Find the test which isn’t running
* Make the test run (and fail)
* Push your change
* Watch it fail

---

# Exercise Part 4
## Make it pass

* Implement the code to make the test pass
* Push your change
* Watch it pass 🤞