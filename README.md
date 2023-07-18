# RangeSlider 2023.07.2

Range selection widget for Python Tkinter GUI developement in slider widget structure with two handles.
<!--    
***Add-on files***
+ An ipython notebook is provided to illustrate the basic usage of tool. -->

***Updates and Fixes in v2023.07.2 w.r.t v2023.07.1***
+ Updated: Documentation, included padX and padY in widget calls to avoid confusion with errors. However, the values needs to be updated in case of non-suitability depending on system and used font size, handle size etc.

***Updates and Fixes in v2023.07.1 w.r.t v2022.12.1***
+ Fixed: Error in updation of UI in absence of step markers.
+ Fixed: Error in initialisation of handle values. (Closing the issue: https://github.com/harshvinay752/RangeSlider/issues/7#issue-1806570927)
+ Added: Complimentary check for correct [step_size] parameter in case of usage of step markers.
+ Fixed: Updated example code in documentation.

***Updates and Fixes in v2022.12.1 w.r.t. v2021.7.4***
+ Added option to change font color of label (Merged from: https://github.com/RWitak)
+ Improved and added option to set initial value of handles. (Merged from: https://github.com/sebasj13)

Note: In order to set the initial values -- declare initial value to the handle variable, if undeclared both handles will be set to min_val. See example in Usage section.
+ Added option to set step size. (Closing the issue: https://github.com/harshvinay752/RangeSlider/issues/4#issue-1451264874)
+ Added option to display step points on the bar, with added color option.
+ Added option to (dis)allow the handles to cross each other.
+ Added option to force(or set) handle value. (Both by value or normalised position). (Closing the issue: https://github.com/harshvinay752/RangeSlider/issues/1#issue-1050521371)

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
[![](/image.PNG)](https://raw.githubusercontent.com/harshvinay752/RangeSlider/main/image.PNG)

## Usage

***Importing required sliders***

For horizontal RangeSlider:
```
from RangeSlider.RangeSlider import RangeSliderH 
```

For vertical RangeSlider:
```
from RangeSlider.RangeSlider import RangeSliderV
```

For both horizontal and vertical RangeSlider:
```
from RangeSlider.RangeSlider import RangeSliderH, RangeSliderV
```

***Creating Simple RangeSlider widget:***
```
from tkinter.ttk import *
import tkinter as tk
 
root = tk.Tk()
 
hLeft = tk.DoubleVar(value = 0.2)  #left handle variable initialised to value 0.2
hRight = tk.DoubleVar(value = 0.85)  #right handle variable initialised to value 0.85
hSlider = RangeSliderH( root , [hLeft, hRight] , padX = 12)   #horizontal slider, [padX] value might be needed to be different depending on system, font and handle size. Usually [padX] = 12 serves,
                                                              #otherwise a recommended value will be shown through an error message
hSlider.pack()   # or grid or place method could be used

vBottom = tk.DoubleVar(value = 0)   #bottom handle variable
vTop = tk.DoubleVar(value = 1)   #top handle variable
vSlider = RangeSliderV( root, [vBottom, vTop] , padY = 12)    #vertical slider, [padY] value might be needed to be different depending on system, font and handle size. Usually [padY] = 12 serves,
                                                              #otherwise a recommended value will be shown through an error message
vSlider.pack()  # or grid or place method could be used

root.mainloop()
```

***Getting current value***
```
print ( hSlider.getValues() )  #return type list of format [ left handle value, right handle value ]
print ( vSlider.getValues() )  #return type list of format [ bottom handle value, top handle value ]
```

***Force value***
```
hSlider.forceValues([0.2, 0.67])  #returns None
vSlider.forceValues([0.62, 0.85])  #returns None
```

***Callback on value change***
``` 
def doSomething():
    print ('I was called.')

hLeft.trace_add('w', doSomething)
hRight.trace_add('w', doSomething)
vBottom.trace_add('w', doSomething)
vTop.trace_add('w', doSomething)
```
***Attributes***

*For RangeSliderH*:

|Attribute|Default Value|Acceptable Value(s) or Description|Release Comment|
|--|--|--|--|
|master| N/A | parent like Tk instance, TopLevel, or Frame etc.|v2021.7.4|
|variables| N/A | list of DoubleVar of length two in order of left handle and right handle|v2021.7.4|
|Width| 400 | width of widget in px |v2021.7.4|
|Height| 80 | height of widget in px |v2021.7.4|
|min_val| 0 | minimum value |v2021.7.4|
|max_val| 1 | maximum value |v2021.7.4|
|padX| 3 | padding from both left and right in px |v2021.7.4|
|image_anchorR| CENTER |anchor value for right handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |v2021.7.4|
|image_anchorL| CENTER |anchor value for left handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |v2021.7.4|
|imageL| None | PhotoImage instance for imaged left handle |v2021.7.4|
|imageR| None | PhotoImage instance for imaged right handle |v2021.7.4|
|auto| True | True for automatic circular colored handle, False for imaged handle |v2021.7.4|
|line_width| 3 | width of widget track in px |v2021.7.4|
|bar_radius| 10 | radius of outer circle of handle |v2021.7.4|
|bar_color_inner| '#5c8a8a' | hex value of color for inner circle in string format |v2021.7.4|
|bar_color_outer| '#c2d6d6' | hex value of color for inner circle in string format |v2021.7.4|
|line_s_color| '#0a50ff' | hex value of color for selected portion for widget track in string format |v2021.7.4|
|line_color| '#476b6b' | hex value of color for unselected portion for widget track in string format|v2021.7.4|
|bgColor| '#ffffff' | hex value of color for background of widget in string format |v2021.7.4|
|step_marker_color| '#ffffff' | hex value of color in string format for steps marked on widget bar|__v2022.12.1__|
|font_color| '#000000' | hex value of color for font of widget in string format |__v2022.12.1__|
|show_value| True | True if current value of handle are intended; otherwise False |v2021.7.4|
|digit_precision| '.1f' | precision format for shown value |v2021.7.4|
|valueSide| 'TOP' | 'TOP' if shown value intended above the handle or 'BOTTOM' if shown value intended below the handle |v2021.7.4|
|font_family| 'Times' | font family ( all font families supported by tkinter are acceptable )|v2021.7.4|
|font_size| 16 | font size in pt |v2021.7.4|
|suffix| "" | suffix for shown value |v2021.7.4|
|step_size| 0 | step size of handle movement, step_size equal to 0 implies continuous movement subject to system architecture floating point resolution |__v2022.12.1__|
|step_marker| False | True if to display step markers on bar; otherwise False |__v2022.12.1__|
|cross_each_other| False | True if handles can cross each other |__v2022.12.1__|

*For RangeSliderV:*

|Attribute|Default Value|Acceptable Value(s)|Release Comment|
|--|--|--|--|
|master| N/A | parent like Tk instance, TopLevel, or Frame etc.|v2021.7.4|
|variables| N/A | list of DoubleVar of length two in order of lower handle and upper handle|v2021.7.4|
|Width| 80 | width of widget in px |v2021.7.4|
|Height| 400 | height of widget in px |v2021.7.4|
|min_val| 0 | minimum value |v2021.7.4|
|max_val| 1 | maximum value |v2021.7.4|
|padY| 3 | padding from both top and bottom in px |v2021.7.4|
|image_anchorU| CENTER |anchor value for upper handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |v2021.7.4|
|image_anchorL| CENTER |anchor value for lower handle if image is used as handle  -  N, NE, E, SE, S, SW, W, NW, CENTER |v2021.7.4|
|imageL| None | PhotoImage instance for imaged lower handle |v2021.7.4|
|imageU| None | PhotoImage instance for imaged upper handle |v2021.7.4|
|auto| True | True for automatic circular colored handle, False for imaged handle |v2021.7.4|
|line_width| 3 | width of widget track in px |v2021.7.4|
|bar_radius| 10 | radius of outer circle of handle |v2021.7.4|
|bar_color_inner| '#5c8a8a' | hex value of color for inner circle in string format |v2021.7.4|
|bar_color_outer| '#c2d6d6' | hex value of color for inner circle in string format |v2021.7.4|
|line_s_color| '#0a50ff' | hex value of color for selected portion for widget track in string format |v2021.7.4|
|line_color| '#476b6b' | hex value of color for unselected portion for widget track in string format|v2021.7.4|
|bgColor| '#ffffff' | hex value of color for background of widget in string format |v2021.7.4|
|step_marker_color| '#ffffff' | hex value of color in string format for steps marked on widget bar|__v2022.12.1__|
|font_color| '#000000' | hex value of color for font of widget in string format |__v2022.12.1__|
|show_value| True | True if current value of handle are intended; otherwise False |v2021.7.4|
|digit_precision| '.1f' | precision format for shown value |v2021.7.4|
|valueSide| 'TOP' | 'TOP' if shown value intended above the handle or 'BOTTOM' if shown value intended below the handle |v2021.7.4|
|font_family| 'Times' | font family ( all font families supported by tkinter are acceptable )|v2021.7.4|
|font_size| 16 | font size in pt |v2021.7.4|
|suffix| "" | suffix for shown value |v2021.7.4|
|step_size| 0 | step size of handle movement, step_size equal to 0 implies continuous movement subject to system architecture floating point resolution |__v2022.12.1__|
|step_marker| False | True if to display step markers on bar; otherwise False |__v2022.12.1__|
|cross_each_other| False | True if handles can cross each other |__v2022.12.1__|

***Additional Notes for attributes***
+ if show_value is False, digit_precision, valueSide, font_family, font_size and suffix have no effect
+ if auto is True, imageL, imageU, image_anchorL, image_anchorR and image_anchorU have no effect
+ if auto is False, bar_radius, bar_color_inner, bar_color_outer have no effect
+ if step_size is zero, step_marker will not be made

***Exceptions raised***
|Condition|Exception|
|--|--|
|if auto is True and either imageL or imageU or imageR or combination out of three is also given | Exception raised: "Can't decide if to use auto shape or images!" |
| if auto is False and one of the image handles is missing | Exception raised: "Handle for one image missing." |
| if auto is False and dimensions for both handles provided are not same | Exception raised : "Image dimensions incompatible, both handles should have same height and width respectively." |
| if Width or Height or padX or padY are not sufficient to render the widget with all features visible safely | Exception raised : $dimension$ not suitable with suggestions to avoid it |

***Functions***

|Function|Arguments|Output Format|
|--|--|--|
|getValues()|NIL|value of handle variables in list format in the same order as given in object definition, returned values lie between min_val and max_val|
|getPos()|NIL|normalised value of handle variables in list format in the same order as given in object definition, returned values lie between 0 and 1|
|forceValues(values)|values : a list of two values each indicating value of handle, values must be between min_val and max_val|return None|
|forcePos(pos)|pos : a list of two normalised values each indicating value of handle, values must be between 0 and 1|return None|

Note: The relation between value ($v_i$) and normalised value ($n_i$) of $i^{th}$ handle defined for a slider with max_val of $v_<$ and min_val of $v_>$ is given by:

$\begin{equation}
n_i = \frac{v_i - v_>}{v_<-v_>}
\end{equation}$


# Words of Developer

This is the second version of this library. It is one of its kind widget for tkinter. When I was developing a tool for my college project I found that at the time no inbuilt or external tool is available for tkinter allowing range selection. However, range selection is a high demand tool specially for applications dealing with data visualizations. I would appreciate any developer from any community who wants to contribute to this project.

I thank RWitak and Sebastian for contributing to this project.

