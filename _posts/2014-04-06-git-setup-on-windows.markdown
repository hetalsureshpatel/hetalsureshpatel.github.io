---
layout: post
title:  "Git Setup On Windows"
date:   2014-04-06 16:02:00
<!-- categries: -->
tags: [git, windows setup]
share: true
comments: true
---

I have been using Git now for nearly a year. In that time I have tried many tools with Visual Studio 2012/21013. What follows is my preferred setup for Git.

1. [Git][git-scm]

   This will install git for windows. It also includes the command line tool as well as git-gui.

2. [Windows Credential Store for Git][git-credential-winstore]

   This will come in handy when you start pushing and pulling from [GitHub][github] repos. This tools uses the Windows Credential Manager with the defined Git credential API.

3. [Conemu-Maximus5][editor]

   This is great tool. As anyone who has used windows and its command-line tools will tell you. Best way to configure this tool is to select  the Developer build, when you open it up for the first time. This will configure all the prompts like cmd, powershell. You can then switch back to the stable version.

4. [Posh-git][posh-git]

   Check out the readme file. It explains it very well. Trust me, you definitely want this if you plan to use git from command-line.

5. [Compare Tool][diffmerge]

   If you do not not have paid tool for comparing files. I recommend Diffmerge, as it is a free tool. I have used this for several years without any issues.


6. Some usefull Git aliases

   * __ahead = log --stat origin/master..HEAD__ : Check what commits have not been pushed to remote branch.
   * __newpush = push -u origin HEAD__: Push a local branch to remote server.
   * __tagpush = push --tag__: Push a newly created tag to remote server.

Would love hear what other people have for using Git on windows.

[git-scm]:    				http://git-scm.com/downloads
[git-credential-winstore]:	http://gitcredentialstore.codeplex.com/
[github]:					http://www.github.com
[editor]:					https://code.google.com/p/conemu-maximus
[posh-git]:					https://github.com/dahlbyk/posh-git
[diffmerge]:				https://sourcegear.com/diffmerge/