#jQuery Sash Plugin

##Overview

jQuery Sash Plugin implements so-called sash element: layout with two panels, divided with thin draggable bar. 
Sash can be vertical or horizontal, accurately works with margins, paddings, borders. Nested sash elements are supported.

See [online example here](https://dl.dropboxusercontent.com/u/15089387/js/jquery.sash/example.htm)

##API

###Usage

Simplest usage of jQuery Sash Plugin:

```html
<div id="main">
  <div id="leftPanel">left panel</div>
  <div id="rightPanel">right panel</div>
</div>
...

<script type="text/javascript" src="http://code.jquery.com/jquery-1.10.0.min.js"></script>
<script type="text/javascript" src="http://code.jquery.com/ui/1.10.3/jquery-ui.js"></script>
<script type="text/javascript" src="https://raw.github.com/cowboy/jquery-resize/master/jquery.ba-resize.min.js"></script>
<script type="text/javascript" src="jquery.sash.js"></script>
<script type="text/javascript">
  jQuery(function($) {
    $("#main").sash({ content1: "#leftPanel", content2: "#rightPanel" });
  });
</script>
```

###Options

**orientation** - string, could be "horizontal" or "vertical", default is "horizontal".

**splitterWidth** - positive integer number, default is 5.

**splitterColor** - string, must be css-compatible value for splitter color.

**ratio** - float number, valid range from 0 to 1, default is 0.5.

**minRatio** - float number, valid range from 0 to 1, default is 0.

**maxRatio** - float number, valid range from 0 to 1, default is 1.

**width1** - positive integer number, represents initial width of left/top panel.

**minWidth1** - positive integer number, represents minimal width of left/top panel.

**maxWidth1** - positive integer number, represents maximal width of left/top panel.

**width2** - positive integer number, represents initial width of right/bottom panel.

**minWidth2** - positive integer number, represents minimal width of right/bottom panel.

**maxWidth2** - positive integer number, represents maximal width of right/bottom panel.

**mirror** - boolean, default is false. Represents the behavior on window-resize event. 
See more on [mirror behavior here](#mirror-behavior).

###Functions

```javascript
$("sashDiv").sash("content1")
```
returns the jquery-object for left/top panel

```javascript
$("sashDiv").sash("content2")
```
returns the jquery-object for right/bottom panel

```javascript
$("sashDiv").sash("initialized")
```
returns boolean, true if the specified jquery object was initialized with sash({ ... }) call.

```javascript
$("sashDiv").sash("options")
```
returns the options object, passed during initialization.

```javascript
$("sashDiv").sash("orientation" [, newValue])
```
gets/sets the orientation of sash element. Possible values are "horizontal" or "vertical".

```javascript
$("sashDiv").sash("visible1" [, newValue])
```
gets/sets the visibility of left/top panel. Must be boolean. 
Note that sash shows/hides the splitter automatically, depending on the visibility of it's panels.

```javascript
$("sashDiv").sash("visible2" [, newValue])
```
gets/sets the visibility of right/bottom panel. Must be boolean. 
Note that sash shows/hides the splitter automatically, depending on the visibility of it's panels.

```javascript
$("sashDiv").sash("width1" [, newValue])
```
gets/sets the width of left/top panel. Must be positive integer number. 
Note that sash automatically adjusts the value to minRatio/maxRatio/minWidth1/maxWidth1/minWidth2/maxWidth2.

```javascript
$("sashDiv").sash("width2" [, newValue])
```
gets/sets the width of right/bottom panel. Must be positive integer number. 
Note that sash automatically adjusts the value to minRatio/maxRatio/minWidth1/maxWidth1/minWidth2/maxWidth2.

###Mirror behavior<a id="mirrorBehavior"></a>

jQuery Sash Plugin supports boolean property "mirror". 

When mirror=false (the default), sash behaves "normal": on window-resize event left panel stays fixed, 
right panel adjusts it's size. 

When mirror=true, then the behavior of sash is "mirrored", that means: on window-resize right panel stays fixed 
and left panel adjusts it's size. 

Similar "mirroring" applies to vertical sash. 

This allows to implement (completely complex coding) the following layout:

```
+--------+---------------------+---------+
|        |                     |         |
|        |                     |         |
|        |                     |         |
|        |                     |         |
|        |                     |         |
+--------+---------------------+---------+
```

where, on window-resize, leftmost and rightmost panels "stick" to left and right sides respectively, 
and middle panel fills the rest space.

##Copyright and License

Copyright 2013 (c) Andrey Hihlovskiy

All versions, present and past, of jQuery Sash Plugin are licensed under MIT license:

* [MIT](http://opensource.org/licenses/MIT)
