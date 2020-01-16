## Exercise: Make two changes using branches

* Work in pairs, ___***SHARE THE SAME GIT REPOSITORY***___
* Create two branches based on the same start point
  * `git checkout -b branch_to_create`
* One person implements Story 2 - Diesel vehicles
* One person implements Story 3 - Alternative fuel vehicles
* Add to your TaxCalculator implementation
* Merge branches back to master one by one (observe Travis in between)


Notes:
See branch ```petrol_tax``` for a starting point to this exercise if they haven't completed the previous one.  
N.B. don't get them to checkout the branch (git weirdness will ensue), just get them to copy-paste the working code.  
There are already test suites for these stories they just need to be enabled so the build runs them.  

--

## Reflection

* What happened?
* Did you have any failed builds? If so, why?
* Did your changes conflict?

Note: Laptops closed.  
  These were very small changes.  
  Some changes last days… weeks…

--

<img src="images/merge.png">

Note: Created two branches  
  Merged diesel into master  
  Merged master into alternate  
  Merged alternate into master  

---

<img height="600" src="https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg?cdnVersion=kv">

Note: Git Flow: another branch based workflow  
