# Git count lines by file in a project
```bash
git ls-files | xargs wc -l

  8 README.md
  0 docs/.nojekyll
  0 docs/README.md
  9 docs/_sidebar.md
 33 docs/git_change_author_info.md
 26 docs/index.html
 48 docs/python_coroutines.md
231 docs/samsung_debloat.md
  5 docs/settings.js
 29 docs/socat.md
  9 docs/strace.md
398 total
```