---
layout: no-sidebar
title: Slider
---

This control has several styles in MahApps.Metro:

### BasicStyle
![]({{site.baseurl}}/images/slider_standard.png) 
Its the basic style for Slider. It applies automatically if you don`t use your custom style.
If you want to base your custom style on that style, you need to add ```BasedOn="{StaticResource MetroSlider}"```

### FlatSlider style
![]({{site.baseurl}}/images/slider_cube.png) 
To use that style you need to load resource dictionary
```<ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/FlatSlider.xaml" />```
and explicitly set style to slider ```Style="{DynamicResource FlatSlider}"```

This style could be dynamically changed to:
![]({{site.baseurl}}/images/slider_tick.png)
For that you need just to change TickPlacement property from None to any other.
