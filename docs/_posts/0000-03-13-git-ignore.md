## Git Ignore

+ In general we only commit things we write
+ Some things are generated
    + IDE settings
    + Downloaded dependencies (e.g. node modules)
    + Compiled files
    + Minified HTML / CSS / JS
+ Do not commit these
    + Avoids conflicts
    + Avoids bloat

--

## .gitignore to the rescue

+ The `.gitignore` file controls what files should be ignored
+ Makes `git add . ` safe(r)
+ Versioned itself

--

## Easy to copy

+ [gitignore.io](https://www.gitignore.io/) will generate based on the technology you use
+ It will be very verbose
+ Easy to write shorter version yourself

--

## Example .gitignore

```
# C-sharp/vscode ignores
.vscode
bin
obj

**/.idea
*.iml

docs/_site
docs/Gemfile.lock

exercises/java/out
exercises/java/.gradle
exercises/java/build/

*.pyc
```