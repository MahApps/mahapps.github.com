---
layout: no-sidebar
title: Styles
---

### Table of Contents (v1.6.5 and older)
- [Overview](#overview)
- [How to change the current theme... via App.xaml](#app)
- [How to change the current theme... via ThemeManager](#thememanager)
- [How to change the current theme... On a Window different to your Application's MainPage](#window)
- [Creating Custom Accents and Themes](#custom)

### Overview {#overview}

This guide will introduce you to the many accents and themes that `MahApps.Metro` has and how to create your own.

All of `MahApps.Metro`'s accents and themes are contained within separate resource dictionaries **(Make sure that all file names are spelled correct. They are Case Sensitive!).**

## How to change the current theme {#app}

You can choose between these available accents:

> "Red", "Green", "Blue", "Purple", "Orange", "Lime", "Emerald", "Teal", "Cyan", "Cobalt", "Indigo", "Violet", "Pink", "Magenta", "Crimson", "Amber", "Yellow", "Brown", "Olive", "Steel", "Mauve", "Taupe", "Sienna"

and these themes:
> "BaseLight", "BaseDark"


#### via App.xaml

The fastest way is to specify the accent and theme resource in App.xaml.

```xml
<Application x:Class="MahAppsMetroThemesSample.App"
         xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Controls.xaml" />
                <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Fonts.xaml" />
                <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Colors.xaml" />

                <!-- accent resource -->
                <!-- change "Cobalt" to the accent color you want -->

                <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Accents/Cobalt.xaml" />

                <!-- theme resource -->
                <!-- change "BaseLight" to the theme you want -->
                <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Accents/BaseLight.xaml" />
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

![Cobalt and BaseLight theme.](https://jkarger.de/images/mahapps_themes_01.png)

#### via ThemeManager {#thememanager}

`MahApps.Metro` has a `ThemeManager` method that lets you change the accent and theme using the code-behind file. It can be done in 2 lines, like so:

```csharp
public partial class App : Application
{
    protected override void OnStartup(StartupEventArgs e)
    {
        // get the current app style (theme and accent) from the application
        // you can then use the current theme and custom accent instead set a new theme
        Tuple<AppTheme, Accent> appStyle = ThemeManager.DetectAppStyle(Application.Current);

        // now set the Green accent and dark theme
        ThemeManager.ChangeAppStyle(Application.Current,
                                    ThemeManager.GetAccent("Green"),
                                    ThemeManager.GetAppTheme("BaseDark")); // or appStyle.Item1

        base.OnStartup(e);
    }
}
```

### On a Window different to your Application's MainPage {#window}

With `MahApps.Metro` you can have a different accent and theme for a `MetroWindow`. The main window or any other `MetroWindow` will keep the specified accent and theme in the App.xaml.

```xml
<Controls:MetroWindow.Resources>
    <ResourceDictionary>
       <ResourceDictionary.MergedDictionaries>
            <!-- this window should be blue -->
            <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Accents/Blue.xaml" />
            <!-- and should use the light theme -->
            <ResourceDictionary Source="pack://application:,,,/MahApps.Metro;component/Styles/Accents/BaseLight.xaml" />
        </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
</Controls:MetroWindow.Resources>
```

You can also do this with the ThemeManager, like so:

```csharp
public partial class AccentStyleWindow : MetroWindow
{
    public void ChangeAppStyle()
    {
        // set the Red accent and dark theme only to the current window
        ThemeManager.ChangeAppStyle(this,
                                    ThemeManager.GetAccent("Red"),
                                    ThemeManager.GetAppTheme("BaseDark"));
    }
}
```

## Creating Custom Accents and Themes {#custom}

Another nice feature of `MahApps.Metro` `ThemeManager` is to use custom created accents and themes or use a dynamically created accent and theme.

```xml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                    xmlns:options="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
                    mc:Ignorable="options">

    <Color x:Key="HighlightColor">#FF9F0055</Color>

    <Color x:Key="AccentBaseColor">#FFD80073</Color>
    <!--  80%  -->
    <Color x:Key="AccentColor">#CCD80073</Color>
    <!--  60%  -->
    <Color x:Key="AccentColor2">#99D80073</Color>
    <!--  40%  -->
    <Color x:Key="AccentColor3">#66D80073</Color>
    <!--  20%  -->
    <Color x:Key="AccentColor4">#33D80073</Color>

    <!--  re-set brushes too  -->
    <SolidColorBrush x:Key="HighlightBrush" Color="{StaticResource HighlightColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="AccentBaseColorBrush" Color="{StaticResource AccentBaseColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="AccentColorBrush" Color="{StaticResource AccentColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="AccentColorBrush2" Color="{StaticResource AccentColor2}" options:Freeze="True" />
    <SolidColorBrush x:Key="AccentColorBrush3" Color="{StaticResource AccentColor3}" options:Freeze="True" />
    <SolidColorBrush x:Key="AccentColorBrush4" Color="{StaticResource AccentColor4}" options:Freeze="True" />

    <SolidColorBrush x:Key="WindowTitleColorBrush" Color="{StaticResource AccentColor}" options:Freeze="True" />

    <LinearGradientBrush x:Key="ProgressBrush" StartPoint="1.002,0.5" EndPoint="0.001,0.5" options:Freeze="True">
        <GradientStop Offset="0" Color="{StaticResource HighlightColor}" />
        <GradientStop Offset="1" Color="{StaticResource AccentColor3}" />
    </LinearGradientBrush>

    <SolidColorBrush x:Key="CheckmarkFill" Color="{StaticResource AccentColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="RightArrowFill" Color="{StaticResource AccentColor}" options:Freeze="True" />

    <Color x:Key="IdealForegroundColor">White</Color>
    <SolidColorBrush x:Key="IdealForegroundColorBrush" Color="{StaticResource IdealForegroundColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="IdealForegroundDisabledBrush" Opacity="0.4" Color="{StaticResource IdealForegroundColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="AccentSelectedColorBrush" Color="{StaticResource IdealForegroundColor}" options:Freeze="True" />

    <!--  DataGrid brushes  -->
    <SolidColorBrush x:Key="MetroDataGrid.HighlightBrush" Color="{StaticResource AccentColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="MetroDataGrid.HighlightTextBrush" Color="{StaticResource IdealForegroundColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="MetroDataGrid.MouseOverHighlightBrush" Color="{StaticResource AccentColor3}" options:Freeze="True" />
    <SolidColorBrush x:Key="MetroDataGrid.FocusBorderBrush" Color="{StaticResource AccentColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="MetroDataGrid.InactiveSelectionHighlightBrush" Color="{StaticResource AccentColor2}" options:Freeze="True" />
    <SolidColorBrush x:Key="MetroDataGrid.InactiveSelectionHighlightTextBrush" Color="{StaticResource IdealForegroundColor}" options:Freeze="True" />

    <SolidColorBrush x:Key="MahApps.Metro.Brushes.ToggleSwitchButton.OnSwitchBrush.Win10" Color="{StaticResource AccentColor}" options:Freeze="True" />
    <SolidColorBrush x:Key="MahApps.Metro.Brushes.ToggleSwitchButton.OnSwitchMouseOverBrush.Win10" Color="{StaticResource AccentColor2}" options:Freeze="True" />
    <SolidColorBrush x:Key="MahApps.Metro.Brushes.ToggleSwitchButton.ThumbIndicatorCheckedBrush.Win10" Color="{StaticResource IdealForegroundColor}" options:Freeze="True" />
</ResourceDictionary>
```

In order to use this custom accent, you need to add it to the `ThemeManager` first.

```csharp
public partial class App : Application
{
    protected override void OnStartup(StartupEventArgs e)
    {
        // add custom accent and theme resource dictionaries to the ThemeManager
        // you should replace MahAppsMetroThemesSample with your application name
        // and correct place where your custom accent lives
        ThemeManager.AddAccent("CustomAccent1", new Uri("pack://application:,,,/MahAppsMetroThemesSample;component/CustomAccents/CustomAccent1.xaml"));

        // get the current app style (theme and accent) from the application
        Tuple<AppTheme, Accent> theme = ThemeManager.DetectAppStyle(Application.Current);

        // now change app style to the custom accent and current theme
        ThemeManager.ChangeAppStyle(Application.Current,
                                    ThemeManager.GetAccent("CustomAccent1"),
                                    theme.Item1);

        base.OnStartup(e);
    }
}
```

It is also possible to create an accent resource dictionary dynamically by using a specific color.  
Take a look to this complete sample available on [GitHub](https://github.com/punker76/code-samples#mahappsmetro-themes).  

![mahapps_more_colors](https://cloud.githubusercontent.com/assets/658431/13557016/9d7e23a4-e3e7-11e5-839a-177c39977e8e.gif)  
