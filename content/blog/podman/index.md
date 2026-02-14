---
date: '2026-02-07T15:12:00+02:00'
title: 'Podman'
summary: "Podman as a drop in replacement for Docker Desktop"
author: ["Wilbert van Dolleweerd"]
draft: false
categories: ["blog"]
tags: ["Docker", "Podman"]
ShowToc: false
---
# Replacing Docker Desktop with Podman
For software development, I used [Docker Desktop](https://www.docker.com/products/docker-desktop/) quite a lot. 
During development, I have a lot of dependencies that I don't want to install permanently on my machine. 
Database servers are a prime example, I might have to work with either an Oracle, Microsoft SQL Server or 
PostgreSQL database for any given project. Running that dependency in Docker is really helpful.

I prefer open source tools and I heard good things about [Podman](https://podman.io/) so I decided to give it a shot. 
I'm writing down how I installed and configured it so this article might be of use for someone else.

## Installing Podman Desktop

You can download a binary installer on the Podman website. I prefer using [Winget](https://winget.run/).
You can use the following command to install.

```
winget install -e --id RedHat.Podman-Desktop
``` 

## Configuring Podman Desktop

After installation of Podman Desktop, Podman still needs to be set up. When starting Podman Desktop simply follow 
the instructions. It will first want to install Podman itself. Typically, you want to run Podman using Windows Linux Subsystem (WSL v2). 
This is the default selection.

After Podman is installed, Podman Desktop will want to setup a Podman machine for you. Again, simply use the 
default selection offered.  

I recommend going to the *Settings* and *Preferences* and enabling *Docker compatibility*. This sets a Docker-compatible environment
allowing all your tools that access Docker to use Podman.

Finally, make sure that the extension *Compose extension* is enabled and activated.  This installs a Compose binary to work with Podman meaning 
that you can use a Docker Compose command that will work with Docker Compose files.

After this part, Podman Desktop and Podman is installed and ready for use.

## Using existing Docker compose files

For my development, I already have a set of Docker Compose files that I use to setup different dependencies.
See the example below that I use to setup Microsoft SQL Server 2022 with a separate datavolume so my databases
are not lost when shutting down Docker.

```yaml
name: SQL_server_2022
services:  
    
    sqlserver:
        container_name: sqlserver_container
        image: mcr.microsoft.com/mssql/server:2022-latest
        environment:
            ACCEPT_EULA: Y
            SA_PASSWORD: addyourownpasswordhere
            MSSQL_AGENT_ENABLED: true
        volumes:
            - sql2022datavolume:/var/opt/mssql
        ports:
            - "1433:1433"

volumes:
    sql2022datavolume:
```

Podman is API compatible with Docker, so you can use ```podman compose up``` to start 
running that Docker Compose file.

However, if you prefer to keep on using Docker commands (maybe you have existing scripting you don't feel like changing), you can create an alias. 
Since I use Powershell in my terminal, I simply added the line below to my startup profile. 

```ps
Set-Alias -Name docker -Value podman 
```

{{< callout >}}
  If you don't know where your PowerShell startup profile is located, use ```$Profile``` to display its location.
{{< /callout >}}

Now you can use ```docker compose up``` which will be rerouted to Podman.

## The result 

Now you can uninstall Docker Desktop and start on using Podman to run your containers. 

{{< callout type="warning" >}}
  Podman claims to be fully compatible with Docker Compose files but the hivemind of the internet has different opinions. 
  Basic compose functionality seems to work fine but advanced scenarios with complex requirements might run into issues.
  
  Having said that, for now I did not (yet) encounter this. Will update this post when necessary.
{{< /callout >}}



