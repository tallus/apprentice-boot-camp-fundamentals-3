## How to do Continuous Integration

--

## Important factors

+ Speed—short feedback loop
+ Reliability
+ Meaningful failures
+ Repeatability

--

## Good practices

+ Fix broken builds quickly (don’t commit over the top)
  + Be aware of failures—use notifications etc
+ Don’t ‘commit & quit’
+ You break it, you fix it
+ Fix or delete flaky tests (don’t just re-run)
+ Make sure your build stays fast
+ Keep test environment ‘like production’

Note: Some tests are unreliable—might fail 1% of the time.  
  Fast means 5 minutes or less for some positive feedback.  
  Test environment data is rarely comparible with production.  

---

## Typical Enterprise ‘Pipeline’

* Run fast tests
* Run slow tests and static analysis
* Publish packaged code
* Deploy to dev
* Deploy to test
* Deploy to production

---

## Many CI solutions

* Bamboo
* CircleCI
* CruiseControl.NET
* GitLab
* GoCD
* Jenkins
* TravisCI
* GitHub Actions

Note: Moving landscape. GitHub should release their own version soon (Actions).  

--

## Common Features

+ GitHub Integration
+ Support for performing tasks in parallel
+ Publishing / releasing built artifacts
+ SCM support: Git / Subversion / CVS / etc.
+ Language / build tool support
+ Notifications
+ Configuration as code

---

## E.g. Travis CI

+ Authorise Travis CI to use your github.com account
+ Activate Travis CI with your repository
+ Add a `.travis.yml` file to your repository
+ Optional: add build badge to the repository

--

## Then…

+ GitHub tells Travis CI each time there is something to fetch and build
+ Travis fetches that version of the code
+ Travis works out what to run based on repository contents (including `.travis.yml`)
+ Travis reports status back to GitHub to mark commits with success/failure

--

## Configuring Travis

* Contents of `.travis.yml` tells Travis what to do
* Specific to each language… e.g.

```yaml
language: java
```

Note: Travis looks at repo to work out how to build once it knows language.  
  One line is enough to build and validate your Java.  

---

## Caution: Git

<img src="https://imgs.xkcd.com/comics/git.png">

