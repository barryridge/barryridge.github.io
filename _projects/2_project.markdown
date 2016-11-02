---
layout: post
title: ACat ADT Tools
description: Action data table manipulation tools for the ACat project.
img: /assets/img/acat_adt_editor.png
---

# [ACat ADT Tools](https://github.com/barryridge/acat-adt-tools): A suite of tools for creating and manipulating ADTs (Action Data Tables) for the [EU FP7 ACat project](http://www.acat-project.eu/).

***

The ACat ADT Tools suite is a Matlab library for creating and manipulating ADTs (Action Data Tables) for the EU FP7 ACat project, consisting of:

1. adttool:
    A tool that generates new, or populates existing, ADT XML files using ROS bag recordings.

2. adteditor:
    A GUI editor that acts as an interface to adttool in order to make certain tasks easier.


<center>
<img src="{{ site.baseurl }}/assets/img/acat_adt_editor.png" width="80%" alt="" title="ACat ADT GUI editor."/>
</center>
<div class="col three caption">
	ACat ADT GUI editor
</div>

The GUI editor allows for ROS bag files to be opened in Matlab and examined with a
'video editor' type of interface, where the recorded data trajectories may be displayed on a timeline
accompanied by visualisations of RGB and depth data in separate windows.
This is not too dissimilar to the `rqt_bag` tool that comes bundled with ROS,
but it adds additional types of functionality that were specific to the needs of our project.
The trajectory data may be broken into 'action chunks' using a simple click-and-drag interface.
The action chunks may be subsequently labelled depending on what task the recorded robot
was engaged in at the time, e.g. "Approach hole" or "Insert peg".
After the data has been chunked, a [*semantic event chain (SEC)*](https://scholar.google.de/citations?user=2xCdZQcAAAAJ&hl=en)
may be specified using dynamically generated checkboxes (see bottom-right of figure).
Finally, an action data table may be exported to an XML file that contains all of the
relevant information regarding the action chunks, timings, SEC table, etc.
