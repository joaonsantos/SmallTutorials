## Add Branch Information to Prompt

### Purpose
Version Control Tools like git are very useful 
to work in a shared environment with multiple teammates.

Sometimes you have lots of branches and you simply 
need some information in your terminal prompt to 
avoid using the git command and being able to 
see this information at a glance.

### Introduction
If you run a debian-based system then your home folder (~)
probably has a '.bashrc' file. This file houses many
configurations to tailor your bash experience.

We will customize this file to modify the variable 'PS1'
that customizes your default prompt in the bash shell.

### Requirements

- Git version control tool

### Add Branch Information to Prompt, if in a Git Repository

1. Use your favourite editor to open the '.bashrc' in your 
home folder.

2. Find the line where the 'PS1' variable is assigned a 
value.

3. Outside of the function paste this function that 
outputs the branch information to stdout.
```
git_branch() {
  git branch 2>/dev/null | grep '^*' | colrm 1 2
}
```

4. Add this function to your prompt variable, with a yellow color, for example:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \[\033[0;33m\]$(git_branch)\[\033[00m\]$ '
```

5. Save the file.

6. Source the '.bashrc' file.
```
source .bashrc
```

You should now have a terminal prompt with a yellow color branch information.
