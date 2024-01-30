---
layout: post
title: "Screenplay Editor and Viewer Application"
featured: "/assets/screenplay/screenplay-editor.webp"
categories: project
---

Created for an online video production organisation to streamline the writing and execution of screenplay scripts.

![Screenshot of the Screenplay Editor application](/assets/screenplay/screenplay-editor.webp)
_Screenshot of the Screenplay Editor application_

Parses raw text input and converts into an interactive, formatted screenplay script through a script viewer component. Features text manipulation functionalities. Interprets scene and stage directions to determine styling and alignment.

<video width="100%" height="auto" controls>
  <source src="/assets/screenplay/screenplay-demo.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
_Demo of the screenplay editor_

The organisation used the 'machinima' technique to produce their videos, a process that necessiated efficiency in relaying dialogue virtually, directly from the scripts. This application solved this problem by enabling actors to copy their lines directly from the script by interacting with the screenplay viewer component; Clicking on their line would copy their specific dialogue to their clipboard, allowing them to quickly copy to the in-game chatbox during filming.

<video width="100%" height="auto" controls>
  <source src="/assets/screenplay/screenplay-tools.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
_Demo of the text manipulation tools_

The 'Share Script' button appends the content of the script to the URL, allowing users to bookmark the script or share the script within the viewer.

Developed with HTML, JavaScript, and CSS.

Demo: <https://mingbl.com/screenplay-editor>

Source code: <https://github.com/mingbl/screenplay-editor>
