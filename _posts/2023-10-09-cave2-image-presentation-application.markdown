---
layout: post
title: "CAVE2 Image Presentation Application"
featured: "/assets/cave2/cave2-header.jpg"
categories: project
---

A visualisation project created for the University of the Sunshine Coast to promote their CAVE2 facility.

![Picture of the team in front of the CAVE2 display](/assets/cave2/cave2-header.jpg)
_Picture of the team in front of the CAVE2 display_

In 2023, I represented the University of the Sunshine Coast in a presentation for the South Asian delegates from international universities, showcasing a visualisation project I developed as part of a team in which I was also project leader.

The project was created for UniSC to promote their [CAVE2 visualisation facility](https://www.usc.edu.au/study/life-at-unisc/facilities/visualisation-and-simulation/cave2-and-the-community), with the purpose of elevating learning experiences, by uniting the captivating visualisations of galaxies featured in images taken by NASA's James Webb Telescope, with the immersion of the CAVE2 facility's 320 degree ultra high-resolution display.

![Picture of the delegates in front of the CAVE2 display](/assets/cave2/cave2-group.jpg)
_Picture of the delegates in front of the CAVE2 display_

The application fills the panoramic display with images and their respective info taken from NASA’s album of images taken by the James Webb Telescope. An algorithm was developed to mathematically select the best-fitting images based on image aspect ratios and available screen space to reduce the amount of empty space, and resize each image to align with the edges of the screens.

<video width="100%" height="auto" controls>
  <source src="/assets/cave2/cave2-demo.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
_Demo of the application during development_

The images and info are pulled using the Flickr API, and an algorithm was developed to select the image variant closest to the resolution of the CAVE2's display. The application periodically rotates through the album based on a duration specified in the config, which along with other settings such as styling and API keys, can be edited using an adminstrator dashboard that was also developed as part of this project.

The project was developed with Node.JS and Python.

The application runs around-the-clock and is being displayed at the University of the Sunshine Coast's campus in their CAVE2 visualisation facility.

Source code: <https://github.com/mingbl/sage-webb>
