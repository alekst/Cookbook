
#Problem

``{ 
dyld: Library not loaded: @executable_path/../.Python
  Referenced from: /Users/aleks/.virtualenvs/my_virtual_env/bin/python3.7
  Reason: image not found
 }``

#Explanation

 "When you upgrade Python using Homebrew and then run `brew` cleanup, the symlinks in the virtualenv point to paths that no longer exist (because Homebrew deleted them)."[1]

#Solution

* Check symlinks
```find ~/.virtualenvs/my-virtual-env/ -type l```

* Remove the existing symlinks and recreate them. 
``{
find ~/.virtualenvs/my-virtual-env/ -type l -delete
virtualenv ~/.virtualenvs/my-virtual-env
} ``

[1]: https://stackoverflow.com/questions/23233252/broken-references-in-virtualenvs