---
layout: no-sidebar
title: FlipView
---

The ```FlipView``` acts as a news banner for your metro applications. It is inspired by Windows 8/WinRT's control of the same name. However, ours was written from the ground-up to support the MahApps.Metro infrastructure. 

### Getting started

The ```FlipView``` is syntatically similar to the regular ```TabControl``` (`Selector`) control. Place your content inside of it's ```Items``` property and it will allow the user to *flip* through them.

The following code was taken from our [MetroDemo](https://github.com/MahApps/MahApps.Metro/tree/master/samples/MetroDemo).

```xml
<Controls:FlipView x:Name="FlipViewTest"
                   Foreground="{DynamicResource WhiteBrush}"
                   Height="200"
                   SelectionChanged="FlipView_SelectionChanged">
    <Controls:FlipView.Items>
        <Grid Background="#2E8DEF">
            <iconPacks:PackIconModern Width="60"
                                      Height="60"
                                      HorizontalAlignment="Center"
                                      VerticalAlignment="Center"
                                      Kind="Cupcake" />
        </Grid>
        <Grid Background="#00A600">
            <iconPacks:PackIconModern Width="60"
                                      Height="60"
                                      HorizontalAlignment="Center"
                                      VerticalAlignment="Center"
                                      Kind="Xbox" />
        </Grid>
        <Grid Background="#BF1E4B">
            <iconPacks:PackIconModern Width="60"
                                      Height="60"
                                      HorizontalAlignment="Center"
                                      VerticalAlignment="Center"
                                      Kind="ChessHorse" />
        </Grid>
    </Controls:FlipView.Items>
</Controls:FlipView>
```

The above code produces the following result.

![flipview](https://user-images.githubusercontent.com/658431/29912993-f366ae1a-8e33-11e7-8073-d43e499775b3.png)

### The Banner

The banner on the bottom of the FlipView can be shown and hidden using the ```IsBannerEnabled``` property. You may change the banner text using the ```BannerText``` property. We use that in code behind to change the banner based on the selected item.

```c#
private void FlipView_SelectionChanged(object sender, SelectionChangedEventArgs e)
{
    var flipview = ((FlipView)sender);
    switch (flipview.SelectedIndex)
    {
        case 0:
            flipview.BannerText = "Cupcakes!";
            break;
        case 1:
            flipview.BannerText = "Xbox!";
            break;
        case 2:
            flipview.BannerText = "Chess!";
            break;
    }
}
```

### The Control Buttons
The *control buttons* (the next and previous buttons) allow the user to flip through the items using their mouse. The buttons can be disabled by calling ```HideControlButtons``` and renabled by calling ```ShowControlButtons```.

The user can also flip through the items using the arrows on their keyboard.

### Automated scrolling (batteries not included)

Disabling the control buttons is useful when you want to provide an automated scrolling experience. This can be implemented by using a timer and by incrementing ```SelectedIndex``` by ```1``` until the index is equal to ```Items.Length - 1```. At that point, you would reset ```SelectedIndex``` to ```0```.
