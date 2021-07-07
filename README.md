# RangeSlider 2021.07

Range selection widget for Python Tkinter GUI developement in slider widget structure with two handles.

***Features:***
+ Range selection
+ Vertical as well as horizontal widget
+ Option for showing current value of handle
+ Customizable handle with default circular handle offering color choice or using image as handle
+ Ability to bind a tkinter variable, making it easier to check for slider movement
+ Custom font and position for value text
+ Customizable value precision
+ Custom suffix option
+ Many others...

# Preview
[![N|Solid](https://github.com/harshvinay752/RangeSlider/blob/main/image.PNG?raw=true)](https://nodesource.com/products/nsolid)

## Usage

***Importing required sliders***

For horizontal RangeSlider:
```
from RangeSlider import RangeSliderH 
```

For vertical RangeSlider:
```
from RangeSlider import RangeSliderV
```

For both horizontal and vertical RangeSlider:
```
from RangeSlider import RangeSliderH, RangeSliderV
```

***Creating RangeSlider widget:***
```
from tkinter.ttk import *
from tkinter import as tk
 
root = tk.Tk()
 
hVar1 = DoubleVar()  #left handle variable
hVar2 = DoubleVar()  #right handle variable
rs1 = RangeSliderH( root , [hVar1, hVar2] )   #horizontal
rs1.pack()   # or grid or place method could be used

vVar1 = DoubleVar()   #bottom handle variable
vVar2 = DoubleVar()   #top handle variable
rs2 = RangeSliderV( root, [vVar1, vVar2] )    #vertical
rs2.pack()  # or grid or place method could be used

root.mainloop()
```

***Getting current value***
```
print ( rs1.getValues() )  #return type list of format [ left handle value, right handle value ]
print ( rs2.getValues() )  #return type list of format [ bottom handle value, top handle value ]
```

***Callback on value change***
``` 
def doSomething():
    print ('I was called.')

hVar1.trace_add('w', doSomething)
hVar2.trace_add('w', doSomething)
vVar1.trace_add('w', doSomething)
vVar2.trace_add('w', doSomething)
```
***Attributes***

*For RangeSliderH*:

|Attribute|Default Value|Acceptable Value(s)|
|--|--|--|
|master| N/A | parent like Tk instance, TopLevel, or Frame etc.|
|variables| N/A | list of DoubleVar of length two in order of left handle and right handle|
|Width| 400 | width of widget in px |
|Height| 80 | height of widget in px |
|min_val| 0 | minimum value |
|max_val| 1 | maximum value |
|padX| 3 | padding from both left and right in px |
|image_anchorR| CENTER |anchor value for right handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |
|image_anchorL| CENTER |anchor value for left handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |
|imageL| None | PhotoImage instance for imaged left handle |
|imageR| None | PhotoImage instance for imaged right handle |
|auto| True | True for automatic circular colored handle, False for imaged handle |
|line_width| 3 | width of widget track in px |
|bar_radius| 10 | radius of outer circle of handle |
|bar_color_inner| '#5c8a8a' | hex value of color for inner circle in string format |
|bar_color_outer| '#c2d6d6' | hex value of color for inner circle in string format |
|line_s_color| '#0a50ff' | hex value of color for selected portion for widget track in string format |
|line_color| '#476b6b' | hex value of color for unselected portion for widget track in string format|
|bgColor| '#ffffff' | hex value of color for background of widget in string format |
|show_value| True | True if current value of handle are intended; otherwise False |
|digit_precision| '.1f' | precision format for shown value |
|valueSide| 'TOP' | 'TOP' if shown value intended above the handle or 'BOTTOM' if shown value intended below the handle |
|font_family| 'Times' | font family ( all font families supported by tkinter are acceptable )|
|font_size| 16 | font size in pt |
|suffix| "" | suffix for shown value |

*For RangeSliderV:*

|Attribute|Default Value|Acceptable Value(s)|
|--|--|--|
|master| N/A | parent like Tk instance, TopLevel, or Frame etc.|
|variables| N/A | list of DoubleVar of length two in order of lower handle and upper handle|
|Width| 80 | width of widget in px |
|Height| 400 | height of widget in px |
|min_val| 0 | minimum value |
|max_val| 1 | maximum value |
|padY| 3 | padding from both top and bottom in px |
|image_anchorU| CENTER |anchor value for upper handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |
|image_anchorL| CENTER |anchor value for lower handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |
|imageL| None | PhotoImage instance for imaged lower handle |
|imageU| None | PhotoImage instance for imaged upper handle |
|auto| True | True for automatic circular colored handle, False for imaged handle |
|line_width| 3 | width of widget track in px |
|bar_radius| 10 | radius of outer circle of handle |
|bar_color_inner| '#5c8a8a' | hex value of color for inner circle in string format |
|bar_color_outer| '#c2d6d6' | hex value of color for inner circle in string format |
|line_s_color| '#0a50ff' | hex value of color for selected portion for widget track in string format |
|line_color| '#476b6b' | hex value of color for unselected portion for widget track in string format|
|bgColor| '#ffffff' | hex value of color for background of widget in string format |
|show_value| True | True if current value of handle are intended; otherwise False |
|digit_precision| '.1f' | precision format for shown value |
|valueSide| 'TOP' | 'TOP' if shown value intended above the handle or 'BOTTOM' if shown value intended below the handle |
|font_family| 'Times' | font family ( all font families supported by tkinter are acceptable )|
|font_size| 16 | font size in pt |
|suffix| "" | suffix for shown value |

***Additional Notes for attributes***
+ if show_value is False, digit_precision, valueSide, font_family, font_size and suffix have no effect
+ if auto is True, imageL, imageU, image_anchorL, image_anchorR and image_anchorU have no effect
+ if auto is False, bar_radius, bar_color_inner, bar_color_outer have no effect

***Exceptions raised***
|Condition|Exception|
|--|--|
|if auto is True and either imageL or imageU or imageR or combination out of three is also given | Exception raised: "Can't decide if to use auto shape or images!" |
| if auto is False and one of the image handles is missing | Exception raised: "Handle for one image missing." |
| if auto is False and dimensions for both handles provided are not same | Exception raised : "Image dimensions incompatible, both handles should have same height and width respectively." |
| if Width or Height or padX or padY are not sufficient to render the widget with all features visible safely | Exception raised : $dimension$ not suitable with suggestions to avoid it |

# Words of Developer

This is the first version of this library. It is one of its kind widget for tkinter. When I was developing a tool for my college project I found that at the time no inbuilt or external tool is available for tkinter allowing range selection. However, range selection is a high demand tool specially for applications dealing with data visualizations. I would appreciate any developer from any community who wants to contribute to this project.

Being a graduation student, I am unable to work over it for long. I will try to release next version having more features as soon as possible.



