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
value, in the color enabled prompt, for example.

![PS1 Location](https://raw.githubusercontent.com/joaonsantos/SmallTutorials/master/add_branch_to_terminal_prompt/imgs/ps1location.png)

3. Paste this function in the file. The function outputs 
the branch information to stdout, in the place seen in the image.
```
git_branch() {
  git branch 2>/dev/null | grep '^*' | colrm 1 2
}
```

4. Replace the PS1 variable definition line, with the
   definition below.<br/>
   The 'git_branch' function output is added to the 
   prompt and is color coded yellow *( \[\033[0;33m\] )*.
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \[\033[0;33m\]$(git_branch)\[\033[00m\]$ '
```

5. Customize with different color codes and tailor bash prompt
   to your liking.<br/>
   More info on this here -> 
   ![Bash Color Codes](https://unix.stackexchange.com/questions/124407/what-color-codes-can-i-use-in-my-ps1-prompt)

5. Save the file.

6. Source the '.bashrc' file.
```
source .bashrc
```

You should now have a terminal prompt with colored branch information.
