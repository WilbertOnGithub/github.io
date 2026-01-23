---
date: '2025-07-30T08:57:26+02:00'
title: 'Details matter'
summary: "Or: 'the file contained different line endings than formatting it would result in.'"
author: ["Wilbert van Dolleweerd"]
draft: false
categories: ["blog"]
tags: ["Blazor"]
ShowToc: false
---
Computers are not unlike petulant, whiny little children. If they come across something not to their liking, they throw their 
hands up in the air, stop working and loudly announce their discontent to everyone. 

I'm always reminded of this when I forget some little detail and stuff simply does not work anymore. 

Last week, I encountered one of these situations and decided to write it down. Maybe 
this will save some time for someone else who also runs into this.

# The project
I'm working on a small hobby project where we want to compare energy usage between homes 
in our neighborhood. I wanted to present some collected data as an interactive graph hosted 
on the web where everyone can access it. Like I said, this is a hobby project so I did not 
want to use a complicated hosting solution.

So I decided to write this using [Blazor](https://dotnet.microsoft.com/en-us/apps/aspnet/web-apps/blazor) and 
specifically [Webassembly](https://webassembly.org/). This would allow me to build something that I can 
simply host on a static site. Something like Github pages.

I developed this on Windows and when I had something that I wanted to share, I wrote a [Github action](https://github.com/WilbertOnGithub/EnergieVergelijking/blob/main/.github/workflows/gh-pages.yml) 
to build and publish it onto a Github page. This way I could easily update it locally, push it onto Github and 
build and deployment would be automated.

## 'The file contained different line endings than formatting it would result in.'
During compilation on Github however, the process stopped with the above error message. Unexpected, compilation 
works fine locally. The message mentions something about line endings.

[Windows and Linux use different line-endings.](https://stackoverflow.com/questions/419291/historical-reason-behind-different-line-ending-at-different-platforms) 
Windows uses `CRLF` (Carriage Return, Line Feed). Linux uses `LF` only.

I develop locally on my Windows desktop (`CRLF`) and the Github action compiles using an Ubuntu Linux distribution (`LF`). 
It looked like my files still contained the Windows style line-endings during the compilation process on Linux.

But why? Normally this stuff is [handled for you by Git](https://docs.github.com/en/get-started/git-basics/configuring-git-to-handle-line-endings) 
 using the `core.autocrlf` setting. This ensures that in the Git repository line endings are stored in Unix style but when checking out they are converted 
to the correct setting for the platform.

## The solution
Finally, I decided to have a look at everything in my project that could contain global configuration. Eventually, 
I looked at my `.editorconfig` and found this:

```
end_of_line = crlf
```

During compilation on Ubuntu, this setting **forces** line-endings to be converted to `CRLF` resulting in the earlier 
mentioned error message. Removing this line solved the problem.

To be honest, I have no idea why I had put this in the configuration file. I suspect that I simply copied an existing 
`.editorconfig` file from another project.

Lesson learned: understand what each setting does and don't blindly copy from other projects.

## The result
Now i could finally deploy the project succesfully. You can see the end result [here](https://wilbertvandolleweerd.com/EnergieVergelijking/).

Use the code `n5lvbv` to get access.