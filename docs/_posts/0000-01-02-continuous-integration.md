# Continuous Integration

-[+] What is it?
-[+] Why is it important?
-[+] How do we do it?

Note: Ask people what their understand is  

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

