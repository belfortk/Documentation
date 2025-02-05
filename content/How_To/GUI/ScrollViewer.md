---
PG_TITLE: How To Use the Scroll Viewer
---

# The Scroll Viewer

When you want to keep your user interface small and the information to present large you can use the **ScrollViewer** to contain the information.

![ScrollViewer](/img/gui/scroll1.jpg).

It consists of vertical and horizontal scroll bars and a viewing area. The information you want to present is created as a control that you add to your scroll viewer and is shown in the viewing area. If all the information control fits inside the scroll viewer no scroll bars will be shown.

From Babylon.js version 4.1 onwards it is possible to use an image for the thumb control and in the bars

![ScrollViewer with Image Bars](/img/gui/scroll4.jpg).

## Creating the Scroll Viewer

The scroll viewer base is a rectangle container holding the scroll bars and the viewing area. You create it with or without a name.

```javascript
var myScrollViewer = new BABYLON.GUI.ScrollViewer();
var myScrollViewer = new BABYLON.GUI.ScrollViewer("name");
```
and add it to an advanced texture as usual.

```javascript
var myAdvancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI");
myAdvancedTexture.addControl(myScollViewer);
```
You can then create your control or container of controls to add to the scroll viewer using the **addControl** method.

```javascript
myScrollViewer.addControl(myControl);
```

* [Playground Example - Scroll Viewer](https://www.babylonjs-playground.com/#13CF95#1)

The default setting for width and depth of the scroll viewer is 100% of the parent control.

The following table shows the additional properties of a scroll viewer.

Property|Type|Default|Comments
--------|----|-------|--------
barColor|string|grey|Foreground color of the scroll bar and color of the thumb
barBackground|string|transparent|Background color of the scroll bar and bottom right square
thumbLength|number|0.5|Proportion of thumb compared to scroll bar length (0 to 0.9)
barSize|number|20|Height of scroll bar

**NOTE** All the padding values for the scroll viewer are set as 0. Any padding should be set on the control added to the scroll viewer. 

* [Playground Example - Scroll Viewer of Fixed Size with Grid of Images](https://www.babylonjs-playground.com/#C3RDBS#3)
* [Playground Example - Scroll Viewer of Relative Size with Grid of Images](https://www.babylonjs-playground.com/#C3RDBS#2)

## Scrollbars

Both scrollbars can be reached with:
- horizontalBar
- verticalBar

You can then set the scrollbar position with `scrollViewer.horizontalBar.value`. This value must be between 0 and 1.

## Image Scrollbars

In order to have images in the scroll bar you need to pass a name (can be empty string) and a parameter of true when creating the scroll viewer.

```javascript
var myScrollViewer = new BABYLON.GUI.ScrollViewer("", true);
```
Additional properties are available

Property|Type|Default|Comments
--------|----|-------|--------
thumbImage|GUI Image|none|Image used for the thumb; required for image scroll bars
barImage|GUI Image|none|Image for the scroll bars
thumbHeight|number|1|Proportion of thumb compared to bar height (0 to 1)
barImageHeight|number|1|Proportion of barImage compared to bar height (0 to 1)
scrollBackground|string|grey|background color of scroll bars excluding the bottom right square; useful behind a thin or transparent bar image

You do not have to have a barImage.

* [Playground Example - Image Scroll Bars](https://www.babylonjs-playground.com/#4ZC0G4)
* [Playground Example - Image Scroll Bars in a Grid](https://www.babylonjs-playground.com/#4ZC0G4#1)

## Adding an Adjustable TextBlock Window

When you add a TextBlock of a given size to a scroll viewer both horizontal and vertical scroll bars are shown as needed. 

![Contained TextBlock](/img/gui/scroll3.jpg)

* [Playground Example - Scroll Viewer with Fixed TextBlock](https://www.babylonjs-playground.com/#FX6KVK#3)

However quite often you need to present text fitting the width of the viewing window and scrolling for the height. This is achieved by setting the `textWrapping` and `reSizeToFit` as follows

```javascript
myTextBlock.textWrapping = BABYLON.GUI.TextWrapping.WordWrap;
myTextBlock.resizeToFit = true;
```

![Adjusting TextBlock](/img/gui/scroll2.jpg)

* [Playground Example - Scroll Viewer with Adjusting TextBlock](https://www.babylonjs-playground.com/#3EF49E#5)

## Live-Updating and Child Containers

The ScrollViewer accepts only ONE child control. If that single child is a textBlock, then you can modify its _.text_ property (including \\n linebreaks), to add/remove text content to/from that single textBlock.

The ScrollViewer also accepts a single CONTAINER (such as a stackpanel) for its single child. In that container, you may add/remove any type of control(s). For certain types of containers, you might choose to add ```container.ignoreLayoutWarnings = true;```, and you might need to set a non-percentage _height_ value to certain children within the container(s).

## Further reading

[How To Use the Selection Panel Helper](/how_to/selector)  
[How To Use Babylon GUI](/how_to/gui)  
[How To Use Babylon GUI Xml Loader](/how_to/XmlLoader)  
[How To Use Babylon GUI3D](/how_to/gui3d)


