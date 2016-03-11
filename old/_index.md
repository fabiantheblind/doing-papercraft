---
layout: default
title: Doing Papercraft
---
Doing Papercraft
================

![images/unfold.gif](images/unfold.gif)  

## Introduction  

This document is a write-down for a workshop @ the University of Applied Sciences Potsdam (Germany) as part of the seminar ["Datenobjekte"](https://incom.org/workspace/6569) (data objects) by [Professor Boris Müller](https://incom.org/profil/99) (a.k.a [@borism](https://twitter.com/borism) on Twitter). We will explore the minimal basics of the 3D application Blender to create primitive shapes which will then be unfolded for laser cutting. _This is still work in progress, there might be_ 🐛_,_ 🐉 _and_ 👾_._  

This document is split into several sub pages for an easier overview.  


{% for item in site.data.meta %}
    - {{item}}
{% endfor %}

<div id="toc-head">Table of Contents</div>
- [Doing Papercraft](#doing-papercraft)
  * [Introduction](#introduction)

- [Prerequisites](#prerequisites)
- [Workflows](#workflows)
  * [Workflow 123DMake](#workflow-123dmake)
  * [Workflow Paperkura](#workflow-paperkura)
  * [Workflow dxf2papercraft](#workflow-dxf2papercraft)
  * [Workflow Processing](#workflow-processing)
- [Application Blender 3D](#application-blender-3d)
  * [Why Blender](#why-blender)
  * [Shortcuts](#shortcuts)
  * [Search Menu](#search-menu)
  * [Interface](#interface)
      - [Customize UI](#customize-ui)
      - [Window content](#window-content)
      - [View areas](#view-areas)
      - [Display methods](#display-methods)
  * [View Navigation](#view-navigation)
  * [Object and Edit Mode](#object-and-edit-mode)
  * [Selection](#selection)
  * [Transformation](#transformation)
      - [Using manipulators](#using-manipulators)
      - [Using hotkeys](#using-hotkeys)
  * [Cursor](#cursor)
  * [Creation](#creation)
      - [Duplication](#duplication)
      - [Add & Delete](#add---delete)
  * [Mesh Manipulation](#mesh-manipulation)
      - [Extrude](#extrude)
      - [Other Manipulations](#other-manipulations)
  * [Modifiers](#modifiers)
      - [Subdivision Surface](#subdivision-surface)
      - [Boolean](#boolean)
      - [Simple Deform](#simple-deform)
      - [Array](#array)
      - [Subdivide and Displace](#subdivide-and-displace)
  * [Add-ons](#add-ons)
      - [Paper Model Add-on](#paper-model-add-on)
  * [Export](#export)
      - [STL STereoLithography](#stl-stereolithography)
    + [OBJ Wavefront](#obj-wavefront)
- [Application Processing 3D](#application-processing-3d)
- [Autodesk 123DMake](#autodesk-123dmake)
  * [Usage Hints](#usage-hints)
  * [Stacked Slices](#stacked-slices)
  * [Interlocked Slices](#interlocked-slices)
  * [Curve](#curve)
  * [Radial Slices](#radial-slices)
  * [Folded Panels](#folded-panels)
    + [Object and Material Settings](#object-and-material-settings)
    + [Joint Types](#joint-types)
      - [Joint Type Tab](#joint-type-tab)
      - [Joint Type Tongue](#joint-type-tongue)
  * [Slices 3D](#slices-3d)
  * [Model Issues](#model-issues)
  * [Get 2D Plans Export](#get-2d-plans-export)

- [Cleaning Plans in Vector Editor](#cleaning-plans-in-vector-editor)
    + [Using Adobe Illustrator](#using-adobe-illustrator)
      - [Usage Hints](#usage-hints)
      - [Plans from 123DMake](#plans-from-123dmake)
      - [Plans from the Blender Paper Model Add-on](#plans-from-the-blender-paper-model-add-on)
      - [Using Inkscape](#using-inkscape)
  * [Export DXF](#export-dxf)
- [Laser](#laser)
  * [Materials](#materials)
- [Links](#links)
  * [References](#references)
  * [Tutorials](#tutorials)
  * [Other experimental papercraft tools](#other-experimental-papercraft-tools)

## Prerequisites  

- a computer
- a 3 button mouse
- Blender (or another 3D application if you already know how to model in 3D)
- 123DMake 
- Vector Editor (Illustrator, Inkscape, Affinity Designer)  
- Processing  

Some of these are optional. Depending on which workflow you are going to use.  

## Workflows  

### Workflow 123DMake  

3D application (modeling) > Export Wavefront (obj) or Binary/ASCII STL (stl) > 123DMake > Export PDF or EPS > 2D application (clean up) > Export DXF R14 (Illustrator/Inkscape)  

### Workflow Paperkura  

3D application (modeling) > Export Metasequoia (mqo), Wavefront (obj), AutoCAD 3D (dxf), 3DS Max (3ds), Lightwave (lwo), Binary/ASCII STL (stl), Google Earth4 (kml, kmz), Collada (dae) > Paperkura > Export PDF/EPS > 2D application (clean up) > Export DXF R14 (Illustrator/Inkscape)  

[www.tamasoft.co.jp/pepakura-en](http://www.tamasoft.co.jp/pepakura-en/productinfo/index.html)

### Workflow dxf2papercraft  

3D application (modeling) >  AutoCAD 3D (dxf) > dxf2papercraft > Export 2D DXF > OpenOffice/Libre Office > Export PDF > 2D application (clean up) > Export DXF R14 (Illustrator/Inkscape)  

- [dxf2papercraft.sourceforge.net](http://dxf2papercraft.sourceforge.net/)  

### Workflow Processing  

Processing > Export OBJ > 3D Application (clean up) > Export Wavefront (obj) or Binary/ASCII STL (stl) > WF 1, 2, 3

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## Application Blender 3D

>Blender is a professional free and open-source 3D computer graphics software product used for creating animated films, visual effects, art, 3D printed models, interactive 3D applications and video games. Blender's features include 3D modeling, UV unwrapping, texturing, raster graphics editing, rigging and skinning, fluid and smoke simulation, particle simulation, soft body simulation, sculpting, animating, match moving, camera tracking, rendering, video editing and compositing. Alongside the modeling features it also has an integrated game engine.  
>[From Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Blender_\(software\)).  

### Why Blender

We mainly use Blender because it is a powerful open source 3D application. If you already familiar with Blender or know other 3D applications you can skip this part and move on to the [Autodesk 123DMake section](#autodesk-123dmake) or export your plans directly from Blender using the [Paper Model Add-on](#paper-model-add-on).

### Shortcuts  

Blender relies heavily on shortcuts. See all shortcuts here [waldobronchart.github.io/ShortcutMapper/#Blender](http://waldobronchart.github.io/ShortcutMapper/#Blender). Some shortcuts depend on the position of the mouse e.g. __x__ for deleting only works when the mouse is over the 3D view.  

### Search Menu  

Another quick way to call actions open panels is the "Search Menu". It gives you quick access to all of Blenders commands by typing. you can open it just by hitting the __space bar__ This is pretty handy if you know a commands name but don't know where to find it. Read more [here.](https://www.blender.org/manual/interface/extended_controls.html)

### Interface  

##### Customize UI

Go to: File > User Preferences… and select the "Input" tab.  

- Change the Mouse selection from right click to left click in the settings > input tab
- "Emulate Numpad" (if you're on a laptop you can use the numbers instead of the numpad)
- adjust UI colors in the theme tab (if you like it more fancy)  

You need to hit __"Save User Settings"__ at the bottom of the window to apply these changes. 

![blender-user-preferences.png](images/blender-user-preferences.png)  

You can add or remove windows by right clicking into the "seam" between two windows to add or join new windows. When adding you toggle horizontal or vertical split by pressing the middle mouse button. You can do the same by clicking and dragging the upper left corner to the left or down. To remove them just join them again. (See the animation below)  

| Mouse                                               | Action                           |
| :---                                                | :---                             |
| Right click window seam                             | split/join windows               |
| Right click window seam select split + middle mouse | toggle horizontal/vertical split |
| click + drag striped corner down/up                 | split horizontally               |
| click + drag striped corner left/right              | split vertically                 |


![images/blender-ui.gif](images/blender-ui.gif)

##### Window content

You can change the content of a window by changing the icon in the header (which is at the bottom of the 3D view).  

![images/blender-change-window-content.png](images/blender-change-window-content.png)  

##### View areas 

Within the 3D view you also have a tool bar on the left and the tool shelf on the right. __t__ shows tool bar and __n__ the tool shelf. On the toolbar you have the most common commands for transformation, editing, creation and many more. On the tool shelf you can access properties for transformations, the view, the 3D cursor and many more. Both of these panels are kind of quick access palettes for properties and action that are essential for editing.  

![images/blender-3d-viewport-tools.png](images/blender-3d-viewport-tools.png)  

##### Display methods  

You can switch the display method on the bottom of the 3D view. For us the only important options are "Solid", "Wireframe" and "Bounding Box".  

![images/viewport-shading.png](images/viewport-shading.png)  

### View Navigation  

The basic navigation in the 3D view is done with the mouse. You can also change the view by using the numpad.  

| Mouse                       | Action                 |
| --------------------------: | ----------             |
| left mouse                  | select                 |
| right mouse                 | set 3D cursor position |
| middle mouse click          | orbit                  |
| middle mouse click + ⇧  | pan                    |
| scroll                      | zoom                   |


_The most useful keys on the numpad are (table also has emulated numpad):_  

| Key Combo (emulated) | View Change                                | Key Combo       |
| ----------:          | :----- ----------------------------------- | :----------     |
| 1                    | Front                                      | Numpad 1        |
| Ctrl + 1             | Back                                       | Numpad Ctrl + 1 |
| 3                    | Right                                      | Numpad 3        |
| Ctrl + 3             | Left                                       | Numpad Ctrl + 3 |
| 7                    | Top                                        | Numpad 7        |
| Ctrl + 7             | Bottom                                     | Numpad Ctrl + 7 |
| 5                    | Toggle orthographic vs perspective mode    | Numpad 5        |
| 0                    | Camera View                                | Numpad 0        |
|                      | **Not so important keys**                  | Numpad          |
| 4                    | Orbit Left                                 | Numpad 4        |
| Ctrl + 4             | Pan Left                                   | Numpad Ctrl + 4 |
| 6                    | Orbit Right                                | Numpad 6        |
| Ctrl + 6             | Pan Right                                  | Numpad Ctrl + 6 |
| 8                    | Orbit Up                                   | Numpad 8        |
| Ctrl + 8             | Pan Up                                     | Numpad Ctrl + 8 |
| 2                    | Oribit Down                                | Numpad 2        |
| Ctrl + 2             | Pan Down                                   | Numpad Ctrl + 2 |
| -                    | Zoom Out                                   | Numpad -        |
|                      | Zoom In (seems not to work)                |                 |



### Object and Edit Mode  

The __"Object Mode"__ is for working with objects in a whole. The __"Edit Mode"__ is for editing vertices, edges or faces of an object. When using [modifiers](#modifiers) you see their effect in object mode. Not in Edit Mode.

### Selection 

To select objects use the left mouse click (if set to left selection. The default is right selection). You can add or remove objects to or from the selection by holding __⇧__. Selected objects are highlighted in orange (default theme). The first in the order of selected objects is a bit brighter. You can also select everything by hitting __a__. In "Edit Mode" there are some extra options for selecting things. You can switch between vertices, edges and faces selection and you can combine them with the buttons on the bar below the 3D view. 

![selection-modes.png](images/selection-modes.png)  

The rectangular (hit __r__ before selecting) or circular (hit __c__) selection by clicking and dragging only applies to the visible objects, vertices, edges and faces by default you can change this if you want. There are more options for selecting. Like Inverting selections and so on. See [the Blender Manual](https://www.blender.org/manual/modeling/meshes/selecting/introduction.html#selection-mode)  


| Action                       | Result                               | Mode             |
| :---                         | :---                                 | :---             |
| Left Mouse                   | select                               | Object/Edit Mode |
| Left Mouse + ⇧           | add/remove                           | Object/Edit Mode |
| a                            | select all                           | Object/Edit Mode |
| Ctrl + i                     | invert the current selection         | Object/Edit Mode |
| Ctrl + Tab                   | selection mode switcher              | Edit Mode        |
| b + left mouse click & drag  | select rectangular area              | Edit Mode        |
| c + left mouse click & drag  | paint selection area                 | Edit Mode        |
| c + left mouse + mouse wheel | paint selection increase or decrease | Edit Mode        |


![blender-ui-sel.gif](images/blender-ui-sel.gif)  


### Transformation  

##### Using manipulators
You can transform objects, groups, vertices, edges and faces (i.e. your selection) by using the 3D manipulators. Change between grab, rotate and scale mode on the bottom of the 3D view. You can combine them or shut them off totally. If you click and drag into the circle at the centre of the manipulator you transform on all axis at once.  

![manipulation.gif](images/manipulation.gif)  

##### Using hotkeys  

Sometimes it is even more convenient to use the hotkeys. When using the hotkeys you can easily constrain the manipulation to an axis. Just hit for example __g + x__ to only move the selection on the global x-axis. If you hit __x__ twice you transform on the objects local axis. The second transformation corresponds with the pull down next to the manipulator buttons on the button of the view. Read some more about the manipulators [here](https://www.blender.org/manual/editors/3dview/transform/transform_control/manipulators.html).   

| Key            | manipulation                                                  |
| :---           | :---                                                          |
| r              | rotate                                                        |
| r + x/y/z      | rotate on one axis only (global)                              |
| r + x/y/z × 2  | rotate on one axis only (selected axis)                       |
| g              | transform (grab)                                              |
| g + x/y/z      | transform (grab) on one axis only (global)                    |
| g + x/y/z × 2  | transform (grab) on one axis only (selected axis)             |
| s              | scale                                                         |
| s  + x/y/z     | scale on one axis only (global)                               |
| s  + x/y/z × 2 | scale on one axis only  (selected axis)                       |
| alt + g        | snaps selection to the center of the scene (Object Mode only) |

![images/manipulation-hotkeys.gif](images/manipulation-hotkeys.gif)  


### Cursor  

The 3D cursor is a pivot point for various features. You can e.g. rotate objects around the cursor (see image below). Newly created objects get created at this position. You can also use the cursor to snap objects to it or the other way around.  

| Key/Action  | Result                                     |
| :---        | :---                                       |
| right click | set 3D cursor position                     |
| ⇧ + c   | reset 3D cursor to the centre of the scene |
| ⇧ + s   | open snap menu (snap to cursor and so on)  |

![images/pivot-menu.png](images/pivot-menu.png)

### Creation  

##### Duplication

To duplicate the current selection (in edit or object mode) just hit __⇧ + d__. This also sets the newly created objects into grab mode so you can set their new position. All the [Transformation](#transformation) rules apply.  

##### Add & Delete

On the tool bar on the left of the 3D view you have various possibilities to add objects.
Use the Create tab an the left to add basic shapes. You can also use the hotkey __⇧ + a__ or use the "Add" menu at the bottom of the 3D view. When you create a new shape you get a new panel at the bottom of the toolbar. There you can set additional settings for the newly created shape e.g. the subdivision of a ICO Sphere or the depth and the radius of a cylinder ad so on. __This is only possible on creation of the shape.__ If the operator panel does not show up just hit __F6__ to show it as a floating panel.  
To delete the selection hit __x__ this applies for Edit- and Object Mode. In Edit Mode you get an additional panel to decide what should be deleted e.g. Vertices, edges, faces and even more options like edge collapse and more. You need to play with it and [read in the manual](https://www.blender.org/manual/modeling/meshes/editing/basics/deleting.html) about it.

| Key/Action   | Result                         |
| :---         | :---                           |
| Toolbar Left | add different type of objects  |
| Add Menu     | add different type of objects  |
| ⇧ + a        | open "Add" floating panel      |
| F6           | open "Operator" floating panel |
| x            | delete selection               |


### Mesh Manipulation

Besides just adding primitive shapes on one another you can also edit the mesh directly. To do this
Go to Edit Mode by hitting the __⇥__ key (TAB). As mentioned before in the [Selection](#selection) section you can select in different way. Vertices only, faces or edges or combine these options. You can now move the selection around as mentioned in the [Transformation](#transformation) section. To manipulate your mesh even further you can now copy and paste your selection. (__⌘  + c__ & __⌘ + v__). Additionally you can use several options on the toolbar to edit your mesh. __Each option has its own operators.__  

##### Extrude  

Extrudes the current selection. [All Transformation](#transformation) and [Selection](#selection) options apply. You can basically differentiate between "extrude region" (hit __e__ or use the button on the toolbar) and "extrude individual". The region extrudes the selection together. The individual extrusion uses each local axis to extrude. See [the manual for further information.](https://www.blender.org/manual/modeling/meshes/editing/duplicating/extrude.html)

![images/extrude.gif](images/extrude.gif)  

| Key/Action | Result             |
| :--        | :--                |
| e          | Extrude Region     |
| ⌥ + e      | Extrude Individual |


##### Other Manipulations  

| Key/Action | Result                    | Description                                        |
| :---       | :---                      | :---                                               |
| f          | Fill                      | Fills the selection with vertices, edges and faces |
| ^ + f      | Face manipulation panel   | Various options to edit faces                      |
| i          | inset face                | Works only with faces                              |
| ^ + b      | bevel                     | Works only with faces                              |
| ^ + e      | Edge manipulation panel   | Various options to edit edges                      |
| ^ + v      | Vertex manipulation panel | Various options to edit vertices                   |
| w          | Specials Panel            | Holds various options                              |


To create new geometry on an existing one you can use the several options. Subdivide, Loop Cut and Slide or the Knife to name just a few. Subdivide for example divides the surface a defined number of times and gives some more options, like smoothness and fractal noise. Loop Cut and Slide allows to subdivide a selection as well by setting a position to cut in by dragging the mouse. the Knife does what it says. Allows to cut the mesh.  

Additionally you will see extra information on some tools on the bottom bar of the 3D view. The Knife for example needs to be confirmed by hitting ↩ (RETURN). Explore the tools by playing with them.  


### Modifiers  

Some modifications can be tedious when done by hand. Fortunately lots of operations have already been pre defined as modifiers. You can access them on the "Properties" window under the little wrench. All modifiers first only affect the selected object. If you want to generate real mesh from them you need to apply them. Also be aware that modifiers work in stack. The order of them define their outcome. You can move them in the stack order by using the up and down arrows on each modifier. We will take a look at some of them that might be useful for our purpose. When you export your form for exchange with the forthcoming applications you don't need to apply these modifiers. An export to Wavefront obj will add all these vertices to the mesh. Read more about modifiers [here.](https://www.blender.org/manual/modeling/modifiers/index.html)  


| Type     | Name                                                 | Short Description                                               |
| :---     | :---                                                 | :---                                                            |
| Generate | [Subdivision Surface Modifier](#subdivision-surface) | Subdivide surface of selected object                            |
| Generate | [Boolean Modifier](#boolean)                         | Intersect, unify or differentiate objects from one another      |
| Deform   | [Simple Deform Modifier](#simple-deform)             | Deform objects by Twisting, bending,tabering or stretching them |
| Generate | [Array Modifier](#array)                             | Create multiple copies of an object                             |
| Generate | [Bevel Modifier](#bevel)                             |                                                                 |   

![images/modifiers.png](images/modifiers.png)  

##### Subdivision Surface

This modifier divides each surface by the number set in the view/render section of it. The difference between view and render should be clear. View is what we see in the 3D view. Render is what will be used in the final render. For our purpose the only thing we need to be concerned about is the view setting. This is what will be exported into our exchange formats. You can also switch between a "Simple" and "Catmull-Clark". To see the result before applying you need to switch the view to Wireframe. See the section [Display methods](#display-methods). You can read more about this modifier [here.](https://www.blender.org/manual/modeling/modifiers/generate/subsurf.html)  

> __"Catmull-Clark"__
> The default option, subdivides and smooths the surfaces. According to [its Wikipedia page](https://en.wikipedia.org/wiki/Catmull%E2%80%93Clark_subdivision_surface), the “arbitrary-looking formula was chosen by Catmull and Clark based on the aesthetic appearance of the resulting surfaces rather than on a mathematical derivation.  

![images/modifier-subdivision-800x500.gif](images/modifier-subdivision-800x500.gif)  


##### Boolean  

The "Boolean Modifier" can be used to create intersection between two objects. When you first apply it you wont see any change. You need to select another object in your scene to be used as the mesh object for the operation. Then you have 3 different methods to apply the modifier. Read more [here.](https://www.blender.org/manual/modeling/modifiers/generate/booleans.html) 

| Methods    | Result                                                |
| :---       | :---                                                  |
| Intersect  | The target mesh is subtracted from the modified mesh. |
| Union      | The target mesh is added to the modified mesh.        |
| Difference | The modified mesh is subtracted from the target mesh. |

![images/modifier-boolean.gif](images/modifier-boolean.gif)  

##### Simple Deform  

> The Simple Deform modifier allows easy application of a simple deformation to an object (meshes, lattices, curves, surfaces and texts are supported).  
> [Simple Deform Modifier](https://www.blender.org/manual/modeling/modifiers/deform/simple_deform.html#simple-deform-modifier)  

| Mode    | Description                                                                                                                           |
| :---    | :---                                                                                                                                  |
| Twist   | Rotates around the Z axis.                                                                                                            |
| Bend    | Bends the mesh over the Z axis.                                                                                                       |
| Taper   | Linearly scales along Z axis.                                                                                                         |
| Stretch | Stretches the object along the Z axis (negative Factor leads to squash), preserving volume by scaling inversely on the X and Y axes.. |

![images/modifier-simple-deform.gif](images/modifier-simple-deform.gif)  

##### Array  

The "Array Modifier" can be used to duplicate elements. You can offset the copies on the 3 axis relative or constantly. You can use an objects transformation to define the offset as well. There are some more options for this modifier. It can be pretty powerful to create multiple copies of an object. Read more [here.](https://www.blender.org/manual/modeling/modifiers/generate/array.html)  

![images/modifier-array.gif](images/modifier-array.gif)  

##### Subdivide and Displace  

To show you what can be done by combining several modifiers the following animation shows how to use the [Subdivision Surface](subdivision-surface) and [Displace](https://www.blender.org/manual/modeling/modifiers/deform/displace.html) modifiers together. The subdivision is done to create more vertices and the displacement to generate some offset on them. The displace modifier uses textures to offset the vertices. You could also use an image or a ramp to displace the vertices. Be creative. This is already rather complex for the starters. Use it as inspiration. There are many more modifiers. To much to explore them all here. Play with some/all of them.  


![images/modifier-subdivide-displace.gif](images/modifier-subdivide-displace.gif)  

### Add-ons  

Additionally to the many build in features of Blender there is a whole ecosystem of [Add-ons](https://www.blender.org/manual/advanced/scripting/python/add_ons.html). There are several Add-ons that are directly distributed with Blender but bot enabled by default. You can browse them in the user preferences an enable those that you like to use. You can also install Add-ons from file. These are Python scripts that are written by members of the community. For our project there are two Add-ons we need to download and install.  

![images/user-prefs-addon.png](images/user-prefs-addon.png)  

1. [Export: Paper Model (.svg) | Export printable net for paper modeling](https://git.blender.org/gitweb/gitweb.cgi/blender-addons-contrib.git/blob_plain/refs/heads/master:/io_export_paper_model.py)  
2. [Autodesk DXF (.dxf) | Export geometry to .DXF file format.](http://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Import-Export/DXF_Exporter)  

##### Paper Model Add-on 
Both are pretty self-explanatory. The Paper Model Add-on adds under File > Export > Paper Model (.svg) the possibility to export a unfolded vector graphic of the selected object. In the export panel ae on the lower left side some export options for the graphic. You can specify the page size, add margins, create tabs for gluing your model and some more options but the default options are pretty good. If the export fails try to scale your model down or increase the size. We will adjust the plans size later on in a vector editor. Read some more about this Add-on [here.](http://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Import-Export/Paper_Model)

![images/paprcraft-export.png](images/paprcraft-export.png)  
![images/papercraft-export-settings.png](images/papercraft-export-settings.png)  

The DXF export Add-on might be useful when working with "dxf2papercraft".

### Export  

To export our data we can use different options. For one we can use the [Paper Model Add-on](#paper-model-add-on). Then we have a vector graphic we just have to clean up and convert to [DXF](https://en.wikipedia.org/wiki/AutoCAD_DXF) to use it for laser cutting. If this is your chosen workflow, move on to [Cleaning Plans in Vector Editor](#cleaning-plans-in-vector-editor). If you want to use 123DMake or Paperkura you need to use an interchange format like [STL](https://en.wikipedia.org/wiki/STL_\(file_format\)) or [OBJ](https://en.wikipedia.org/wiki/Wavefront_.obj_file). You don't need to specify a final scaling. 123DMake and Paperkura both allow to edit the scaling of the Model and the material/paper size.  


##### STL STereoLithography

If you use STL you need to use the ascii format and apply all modifiers when used. It would be better that you don't apply the modifiers from within the Add-on. As already mentioned the modifiers depend on their stack, so applying them by hand gives you a better control over the outcome.  

#### OBJ Wavefront  

You can also use the [Wavefront OBJ](https://en.wikipedia.org/wiki/Wavefront_.obj_file) format. It has some more options for the export but creates a equivalent result. You also should apply the modifiers first as mentioned for the [STL](#stl-stereolithography) export.  ## Application Processing 3D  

> Processing (programming language)
> Processing is an open source programming language and integrated development environment (IDE) built for the electronic arts, new media art, and visual design communities with the purpose of teaching the fundamentals of computer programming in a visual context, and to serve as the foundation for electronic sketchbooks. The project was initiated in 2001 by Casey Reas and Benjamin Fry, both formerly of the Aesthetics and Computation Group at the MIT Media Lab. One of the stated aims of Processing is to act as a tool to get non-programmers started with programming through the instant gratification of visual feedback. The language builds on the Java language, but uses a simplified syntax and graphics programming model. In 2012, they started the Processing Foundation along with Daniel Shiffman, who formally joined as a third project lead.
>[From Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Processing_\(programming_language\))

We wont go in depth into programming with Processing. This here are just some notes on how to export usable 3D data for our purpose. For this we have this simple 3D scene that will create a OBJ file you can use in 123DMake and Paperkura. You should take a look at the output in Blender. There might be some errors or problems with the sizes or centers of these models. But first you need to install the [OBJExport](http://n-e-r-v-o-u-s.com/tools/obj/) library from [Nervous System](http://n-e-r-v-o-u-s.com/index.php). There is a guide on the Processing Wiki on [how to install libraries manually](https://github.com/processing/processing/wiki/How-to-Install-a-Contributed-Library#manual-install). If this worked you can open the Processing IDE, paste the sketch blow into the window and run the sketch. This will create simple scene with a cube and plane and will create the output.obj file next to your Processing sketch. This data can be edited in [Blender](#3d-application-\(blender\))   



```java
/**
 * Simple sketch for doing papercraft
 * uses the OBJExport library from
 * http://n-e-r-v-o-u-s.com/tools/obj/
 *
 * @author Fabian "fabiantheblind" Morón Zirfas
 * @license ISC https://opensource.org/licenses/ISC
 */
import nervoussystem.obj.*; // import the lib

/**
 * the setup runs once.
 * We only set the size of the canvas.
 *
 */
void setup() {
  size(500, 400, P3D);
}
/**
 * This runs all the time. Actually we use the noLoop() statement.
 * it prevents that our scene gets exported each frame.
 *
 */
void draw() {
  background(255);
  // set the position of the camera
  camera(width/10, height/3, -30, width/2, height/2, -250, 0, 1, 0);
  // start the export
  beginRecord("nervoussystem.obj.OBJExport", "output.obj");
  // offset the scene to the center of the canvas.
  // This makes the calculation of the coordiantes easier
  translate(width/2, height/2, -250);
  // make a transformation that only affects the plane
  pushMatrix();
  // rotate by 90 degrees on the x axis
  rotateX(radians(90));
  // start the shape.
  beginShape(QUADS);
  // write the vertices
  vertex(-100, -100, -10);
  vertex(100, -100, -10);
  vertex(100, 100, -10);
  vertex(-100, 100, -10);
  // end the shape
  endShape();
  // reset the matrix of the the sketch so the
  // rotation does not affect the other objects
  popMatrix();
  // we don't want the cube tu be solid
  noFill();
  // start the cube
  beginShape(QUADS);
  vertex(-10, 10, 10);
  vertex( 10, 10, 10);
  vertex( 10, -10, 10);
  vertex(-10, -10, 10);

  vertex( 10, 10, 10);
  vertex( 10, 10, -10);
  vertex( 10, -10, -10);
  vertex( 10, -10, 10);

  vertex( 10, 10, -10);
  vertex(-10, 10, -10);
  vertex(-10, -10, -10);
  vertex( 10, -10, -10);

  vertex(-10, 10, -10);
  vertex(-10, 10, 10);
  vertex(-10, -10, 10);
  vertex(-10, -10, -10);

  vertex(-10, 10, -10);
  vertex( 10, 10, -10);
  vertex( 10, 10, 10);
  vertex(-10, 10, 10);

  vertex(-10, -10, -10);
  vertex( 10, -10, -10);
  vertex( 10, -10, 10);
  vertex(-10, -10, 10);
  // end the cube
  endShape();
  // end the recording
  // this also exports the obj file
  endRecord();
  // we don't want to run the sketch again
  noLoop();
}
```


![images/processing-simple-3d-scene.png](images/processing-simple-3d-scene.png)  

The next sketch is a bit more complex. It creates several boxes and also does the output to a .obj file.  

```java
/**
 * creates a scene with some boxes
 */
import nervoussystem.obj.*; // import the lib

void setup() {
  size(500, 500, P3D);
}

void draw() {
  background(0);
  camera(280, 290, -44, 250, 250, 10, 0, 1, 0);
  beginRecord("nervoussystem.obj.OBJExport", "output.obj");


  for (int r = 0; r <= 360; r+=36) {
    float x = cos(r) * 18;
    float y = sin(r) * -12;
    Box b = new Box(width/2 + x, height/2 + y);
    b.rx = r;
    b.ry = 30;
    b.rz = 42;
    b.draw();
  }
  endRecord();
  noLoop();
}

class Box {
  float d = 10;
  float h = 10;
  float w = 10;
  float x = 0;
  float y = 0;
  float z = 0;
  float rx = 0;
  float ry = 0;
  float rz = 0;
  Box() {
  }
  Box(float x, float y) {
    this.x = x;
    this.y = y;
  }
  Box(float x, float y, float z) {
    this.x = x;
    this.y = y;
    this.z = z;
  }
  Box(float x, float y, float z, float w, float h, float d) {
    this.x = x;
    this.y = y;
    this.z = z;
    this.d = d;
    this.h = h;
    this.w = w;
  }

  void draw() {
    pushMatrix();
    translate(this.x, this.y, this.z);
    rotateX(radians(this.rx));
    rotateY(radians(this.ry));
    rotateZ(radians(this.rz));
    box(this.w, this.h, this.d);
    popMatrix();
  }
}
```


![images/processing-boxen-scene.png](images/processing-boxen-scene.png)  
## Autodesk 123DMake

When you are done with creating a simple 3D object either by using [Blender]({{blender.html | prepend: site.basurl}}) or with [Processing]({{processing.org.html | prepend: site.baseurl}}) you can move on to [Autodesks 123DMake](http://www.123dapp.com/make). Allows creation of low-tech LOM-style (Laminated object manufacturing) solid models. The application has several construction techniques for now we will only focus on creating [Folded Panels](#folded-panels).  

### Usage Hints  

- The default unit is inch. This cannot be set globally you will need to adjust this for each panel where you use units.
- On a German localized computer the application accepts as decimal point the comma even though the numbers are displayed with a dot  
- The application tends to crash sometimes. Save your work often.  
- Pasting into fields wont work. Use the Right Mouse Button and paste from the pop up menu.  
- Splitting the panels can save you a lot of material.  
- On Mac OSX you can extract the Help PDF by opening the application package. In there you'll find the PDF under /Applications/123DMake.app/Contents/Resources/123DMakeHelp.pdf
- You need an Autodesk account for exporting your plans.
- Don't perforate your plan. The marks for the folding lines are enough to. We will cut them with different settings leaving a visual mark where to fold your material.  

### Stacked Slices  

> Cross sections your 3D model, cutting it into slices you can glue and stack on top of one another. Use the Dowels option to make it easier to line up and assemble your model. You can recreate the model using any flat material you can cut.  
> - From 123DMake Help (within Application)  

### Interlocked Slices

> Cuts your 3D model into two stacks of slotted slices. Lock them together in a grid, like when building a 3D puzzle. This uses less material than stacked slices.  
> - From 123DMake Help (within Application)  


### Curve  

>Cuts slices perpendicular to a curve, resembling ribs. Use this for organic shapes, such as for modelling a brontosaurus. Also, use the Navigation tools to help rotate your view to see the 
curve.  
> - From 123DMake Help (within Application)  


### Radial Slices  

>Cuts your 3D model into radiating slices from a central point.  Use this for a round symmetrical object, such as a vase.  
> - From 123DMake Help (within Application)  


### Folded Panels   

> Separates your 3D model into 2D segments of triangular meshes. These segments (panels) are folded multiple times, then attached using one of ten different joint types. Use paper, cardboard, even sheet metal.  
> - From 123DMake Help (within Application)  

#### Object and Material Settings  

When you import your 3D model you first need to set some options. The manufacturing settings allow you to set the size of your material. This can be set to a fairly huge size (the laser cutter at the University of Applied Sciences Potsdam (Germany) has a size of 1200 mm to 900 mm). You can set the "Object Size" when you need a defined size. Another way is adjusting the size based on your material size. if your desired object size exceeds you material size the application will allow you to export several cut sheets.  
What's more important is to set the "Thickness" of your material. This will determine how narrow/wide the holes for tongues and tabs are we are going to produce later on. There is also another setting we need to take in account. The "Slot Offset". This is the amount of material the laser will take away. For cutting grey cardboard around 0.5 to 1.5 mm you can set this to <=1 mm. You can set all of these settings by pressing the little wrench and then adjusting them on the bottom of the application window. You also can save some presets for your material.   


![images/123Dmake-object-material.png](images/123Dmake-object-material.png)  


When you done with setting up your material choose from the Construction Techniques "Folded Panels".  

#####Optimize Panels - Add Remove Seams

If you still want to edit your model you can adjust the count of vertices in these panels or add new seams to your object. You can also split all panels for the final cut plan.  

#### Joint Types  

Here you can select how you want to connect your unfolded object after production. Same are useful for paper, others can be used for sewing or lacing. We are going to focus on the tab and tongue types.  

| Joint Types | Description (taken from 123Dmake Help)                                                                                                                                                                                                                                                                                                 |
| :---        | :---                                                                                                                                                                                                                                                                                                                                   |
| Diamond     | Connect panels by folding and affixing (gluing or welding) the triangular ticks. Change Tick Radius to set the width of the ticks.                                                                                                                                                                                                     |
| Gear        | Connect panels by folding and affixing (gluing or welding) the rectangular ticks. The dark areas of the image need to be cut out. Change Tooth Radius to set the distance from the edge of the sheet for the cutouts. Change Tick Spacing  to set the spacing between the cutouts. Change Tooth Scale  to set the height of the teeth. |
| Laced       | Connect joints by lacing sheets together. Change Hole Radius to make the holes bigger. Change Joint Space to set the spacing between rivets used to connect the joints. Change Tick Radius to set the distance of the rivet holes from the edge of the sheet.                                                                          |
| Multitab    | Connect joint by fixing ticks together. Change Tick Radius to change the height of the ticks. Change Tab Fraction to change the width of the ticks (tabs).                                                                                                                                                                             |
| Puzzle      | Connect joint by fitting pieces together. Change Tick Radius to change the height of the ticks.                                                                                                                                                                                                                                        |
| Rivet       | Connect joint by riveting ticks to one another. Change Hole Radius to make the holes bigger. Change Joint Space to increase or decrease the number of rivets used to connect the joints. Change Tick Radius to set the distance of the rivet holes from the edge of the sheet.                                                         |
| Seam        | Connect joints by sewing them together (like a sewing pattern). Change the Seam Radius to change the width of the seam’s panel border.                                                                                                                                                                                                 |
| Tab         | Connect joints by inserting a tick into slots. Change the Tick Radius to change the width and length of the slots and ticks.                                                                                                                                                                                                           |
| Ticked      | Connect joints by connecting the ticks along the seams Change Tick Space to make the ticks closer to one another or further apart. Change the Seam Radius to change the width of the seam’s panel border.                                                                                                                              |
| Tongue      | Connect joint by inserting a tick into slots. Change Tick Radius to change the tick length and width and slot width.                                                                                                                                                                                                                   |

##### Joint Type Tab  

On the first image below you see the plan for a cube laid out with the "Tab" joint type. The size of the cube is 20 mm × 20 mm × 20 mm on a sheet with the size of 700 mm × 1000 mm × 0.5 mm. The "Tab Joints" are set to have a "Tick Radius" of 10 mm (set it at the bottom of the window). The second one has the same settings but with "Split Panels" enabled.  

![images/123dmake-tab-joint.png](images/123dmake-tab-joint.png)  

![images/123dmake-tab-joint-split-panels.png](images/123dmake-tab-joint-split-panels.png)  


##### Joint Type Tongue

The "Tongue" type is similar to the tab type. We used here the same settings. 
 The size of the cube is 20 mm × 20 mm × 20 mm on a sheet with the size of 700 mm × 1000 mm × 0.5 mm. The "Tongue Joints" are set to have a "Tick Radius" of 10 mm (set it at the bottom of the window). The second one has the same settings but with "Split Panels" enabled.  

![images/123dmake-tongue-joint.png](images/123dmake-tongue-joint.png)  

![images/123dmake-tongue-joint-split-panels.png](images/123dmake-tongue-joint-split-panels.png)  

### Slices 3D
>Cross sections your 3D model, similar to Stacked Slices. Rather than a stepped section for each slice, the section conforms to the surface of the 3D model. 
> - From 123DMake Help (within Application)  


### Model Issues

If the application detects an error with your plan you can see them on the right side under "Model Issues".  

### Get 2D Plans Export  

On the images above you already can see the laid out plans. These can be accessed on the right side after you've selected your construction technique. Just click on them to see them in a larger view. To export them for laser cutting you need to login into your Autodesk account. Then you can go to the "Get Plans" panel and hit the file icon. On the bottom of the window you will see some options for the export. I suggest using the EPS (encapsulated postscript) file format. Then you can export your plan for further cleaning.  


## Cleaning Plans in Vector Editor  

After modeling our object in Blender and exporting it with the [Paper Model Add-on](paper-model-add-on) we have a .svg file. If we did the additional step with 123DMake we have a .eps file. Both can be edited in vector editors. For the best result we need to clean up the data a bit more in vector editing application. We will use Adobe Illustrator (Mac, Win) for this. If you don't have a license for illustrator you can also use Inkscape (Cross Platform) or Affinity Designer (Mac).  


#### Using Adobe Illustrator  

Open your svg or eps, set the units of the document to millimeters (⌘ + ⇧ + p) and set your artboard size to match the size of your material (can be accessed through the Artboard tool or directly from the document settings). To see what the laser will use you should take a look at the "Path View". You can switch back and forth between the visual view and the path view by hitting ⌘ + y on your keyboard. 

##### Usage Hints  

- Using the path view is often much simpler. This is what the Sabeko laser software sees.   
- Different colors produce separated layers in the Sabeko laser software.  
- You can select objects by color using the selection menu.  
- For additional information on your cut plan you can use the [Monoline Text Drawing Script](https://forums.adobe.com/message/4907404)  
- To create real dashed single line paths use [this trick](https://forums.adobe.com/message/3657306) from the Adobe forums.  

##### Plans from 123DMake  

When you used 123DMake you can see you have the some numbers on the plan and, if not splitted into panels, also some folding marks. We can cut those with a low setting to have some visual hints where to fold our model. To do so you need to give them a different color then the outer form we want to cut out. The laser cutter application will detect that and allow us to engrave them with lower power. Release all groups and compound paths if needed. Sort them by color. Remove all unwanted data.  
One important step is to remove the most outer path. This is an outer bound created when exporting the .eps. If we don't do this it will be cutted by the laser. Your final plans should look like the pictures below.  

![images/illustrator-123dmake-normal-view.png](images/illustrator-123dmake-normal-view.png)  

![images/illustrator-123dmake-plan-pathview.png](images/illustrator-123dmake-plan-pathview.png)  

![images/illustrator-123dmake-split-panels-normal-view.png](images/illustrator-123dmake-split-panels-normal-view.png)  
![images/illustrator-123dmake-split-panels-path-view.png](images/illustrator-123dmake-split-panels-path-view.png)  

##### Plans from the Blender Paper Model Add-on  

The size settings from the Paper Model Add-on within Blender are not that intuitive. It is easier export it to something like a A3 paper size and then rescale the model to fit your needs. On the image below you see once the export from blender (the .svg) and on the second and third image the cleaned version in normal and path view. You will need to convert the dotted lines to real paths or it will be a straight cut. Remove all unwanted paths and split them with colors so the laser software can detect them as own layers.  

![images/illustrator-paper-model-add-on-export.png](images/illustrator-paper-model-add-on-export.png)  
![images/illustrator-paper-model-add-on-normal-view.png](images/illustrator-paper-model-add-on-normal-view.png)  
![images/illustrator-paper-model-add-on-path-view.png](images/illustrator-paper-model-add-on-path-view.png)  


##### Using Inkscape  

The same principles as in Illustrator apply to Inkscape.  

- Set the size and units of your document.  
- Rescale your plan to fit your material.  
- Remove all unwanted paths.  
- Separate the paths using colors (if needed).  
- Take a look at the outline view to see the raw paths.  

### Export DXF  

When exporting to .dxf files just you need to watch out for the unit conversion and the DXF version number.  
The laser at the University of Applied Sciences Potsdam (Germany) needs DXF R14 files and the unit scaling should be from one millimeter to one unit. If you already did set your units in the document settings you should be fine. Below you see the export panel from Illustrator and from Inkscape. _Apologize for the localized screenshots._  

![images/illustrator-dxf-export.png](images/illustrator-dxf-export.png)  
![images/inkscape-dxf-export.png](images/inkscape-dxf-export.png)  
## Laser  


### Materials  

This is a list of already tested materials.  

| Materials            | max. (tested) thickness | slot offset | comment                                 |
| :--                  | :---                    | :---        | :--                                     |
| grey cardboard       | 5 mm                    | < 1 mm      |                                         |
| corrugated cardboard | 5 mm                    | < 1 mm      | does not work well for tongues and tabs |
| acrylic              | 10 mm                   | ≈ 2 mm      |                                         |
| MDF                  | 8 mm                    | ≈ 1.5 mm    |                                         |
| HDF                  | 8 mm                    | ≈ 1.5 mm    |                                         |

## Links  

[www.tamasoft.co.jp/pepakura-en](http://www.tamasoft.co.jp/pepakura-en/productinfo/index.html)

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### References

- [www.blender.org/manual](https://www.blender.org/manual/)

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### Tutorials

__Blender__  

- [Blender Basics - 00 - Introduction](https://www.youtube.com/watch?v=zOvawDOWqC4) and following …
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### Other experimental papercraft tools  

- [https://trmm.net/Unfolding_STL](https://trmm.net/Unfolding_STL)

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
