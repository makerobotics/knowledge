# Git

[Cheat sheet](https://git-scm.com/cheat-sheet)

`git log --follow "filename"`: keeps history of the file commits

Conflict between main and remote origin/main:
```
git switch main
git fetch origin
git merge origin/main
```
Then solve the conflict and commit

# Python

[https\://docs.python.org/3/contents.html](https://docs.python.org/3/contents.html)

An \_\_init\_\_.py file defines a package.

# SSH

Create a private ssh key:  
`ssh-keygen \-t ed25519 \-C "your\_email@example.com"`  
(Will be created in users .ssh folder)

Transfer the public key to the target:  
`ssh-copy-id pi@raspberrypi.local`

Test the connection (no more password necessary):  
`ssh pi@raspberrypi.local`

# UV

[Cheat sheet](https://mathspp.com/blog/uv-cheatsheet)

# Visual Studio code

## Skills
Create the skill file:  
`.github/skills/skillname/SKILL.md`  
Add a yaml header and describe the skill name and description there.  
==> Skill will be automaticially called. Can also be forced by #skill-file in the chat.

## Prompts
Create the prompt file:  
`.github/prompts/create-readme.prompt.md`  
Add a yaml header and describe the prompt name and description there.  
==> Call the prompt by "/create-readme"
