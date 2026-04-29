---
date: '2026-04-22'
title: 'Bye bye Powerpoint'
summary: "Writing your presentations in AsciiDoc"
author: ["Wilbert van Dolleweerd"]
draft: false
categories: ["blog"]
tags: ["AsciiDoc", "AsciiDoctor", "revealjs"]
ShowToc: false
---
I don't like creating presentations in Powerpoint. When presented with a blank slate or 
our company template, I don't know where to start. I tend to fiddle around a lot with diagrams and pictures. 
I would prefer if I could focus on the message that I'm trying to get across.

Why not use a language like Markdown or AsciiDoc which would allow me to put it into a Git repository and do versioning on it?

Since I'm already using [AsciiDoc](https://asciidoc.org/) for my architecture documentation using [Arc42](https://arc42.org/), 
I started looking if someone else had already solved this.

# Asciidoctor reveal.js
Enter [Asciidoctor reveal.js](https://docs.asciidoctor.org/reveal.js-converter/latest/). This is a converter that will 
convert AsciiDoc into a HTML5 presentation designed to be run within the [reveal.js](https://revealjs.com/) presentation framework.

## Setup
You can download a standalone executable but AsciiDoctor also comes with a lot of plugins like [PlantUml](https://plantuml.com/) support. 
It is actually easier to use a [Docker container](https://github.com/asciidoctor/docker-asciidoctor) that will contain all the plugins that you can use. I am writing down the necessary steps here 
just as a reminder for me whenever I want to start a new presentation. 

So this blog post is just for me so I can just offload these steps to my external memory (this blog).

## The steps needed to start a new presentation

1. Create a folder on your system where you want to create your presentation. For these steps I'm going to use `E:\Personal\Presentation`.

2. Go to that folder and clone the appropriate version of Reveal.js there. The repository for Reveal.js can be found at [https://github.com/hakimel/reveal.js](https://github.com/hakimel/reveal.js).
   Have a look at the [compatibility matrix](https://docs.asciidoctor.org/reveal.js-converter/latest/setup/compatibility-matrix/) for AsciiDoctor reveal.js to see which version of Reveal.js you should clone.
   For now, I'm using version 4.12.
   
   `git clone -b 4.1.2 --depth 1 https://github.com/hakimel/reveal.js.git` 
   
4. If you want to use images in your presentation, I recommend creating an `E:\Personal\presentation\images` folder to store these.

5. Start your Docker container and point it to the folder where your presentation files will be stored, `E:\Personal\Presentation`.

   `docker run -it -v E:\Personal\Presentation:/documents/ asciidoctor/docker-asciidoctor`
   
   Or if using Podman:
   
   `podman run -it -v E:\Personal\Presentation:/documents/ docker.io/asciidoctor/docker-asciidoctor`

6. The Docker image will be downloaded and started and you will be presented with a prompt that can now be used to convert your presentation. 

7. Start creating your AsciiDoc presentation files in `E:\Personal\Presentation`. Documentation can be found [here.](https://docs.asciidoctor.org/reveal.js-converter/latest/) 

8. When ready, convert your AsciiDoc file to Reveal.js using the command below. This will create a corresponding `sample-slides.html` file that you can launch with a browser.

   `asciidoctor-revealjs sample-slides.adoc`
   
   Optionally, if you are using PlantUml diagrams in your AsciiDoc, use:
   
   `asciidoctor-revealjs -r asciidoctor-kroki sample-slides.adoc`
   
9. When done, enter `exit` in the container prompt to stop the container.

10. You can now copy the `E:\Personal\Presentation` folder somewhere else to run your presentation. Stick it in a Git repository or copy it to a USB stick.
   Be sure that you include the `revealjs` folder in your own copy as well.

11. Optionally, at the end the Docker container can be removed (it can simpy be downloaded again for a new presentation).

## Example repository
If you want a more complete example, you can see the end result of the presentation on my [Github account.](https://github.com/WilbertOnGithub/lightningtalk_postgresql)


## Useful Reveal.js configuration
Reveal.js can be configured by setting configuration options in your root document (start of your presentation). 
I list my options that I use. 

```
:revealjs_theme: league
:source-highlighter: highlight.js
:revealjsdir: reveal.js
:imagesdir: images
:revealjs_history: true
:revealjs_center: true
:revealjs_heigth: "90%"
:revealjs_width: "80%"
:revealjs_progress: true
:revealjs_transition: convex
:revealjs_controlsLayout: bottom-right
:revealjs_showSlideNumber: all
:revealjs_slideNumber: c
:revealjs_autoPlayMedia: true
:revealjs_minScale: 0.2
:revealjs_maxScale: 2.0
:revealjs_totalTime: 300
```