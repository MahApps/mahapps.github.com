---
layout: no-sidebar
title: Styles
---

### Table of Contents
- [Overview](#overview)

<a name="overview"></a>
### Overview
This guide will introduce you to the many accents and themes that MahApps.Metro has and how to create your own.

All of MahApp.Metro's accents and themes are contained within separate resource dictionaries **(Make sure that all file names are spelled correct. They are Case Sensitive!).**

<a name="how-to-change-the-theme"></a>
### How to change the current theme
You can choose between these available accents:

> "Red", "Green", "Blue", "Purple", "Orange", "Lime", "Emerald", "Teal", "Cyan", "Cobalt", "Indigo", "Violet", "Pink", "Magenta", "Crimson", "Amber", "Yellow", "Brown", "Olive", "Steel", "Mauve", "Taupe", "Sienna"

and these themes:
> "BaseLight", "BaseDark"


#### via App.xaml
The fastest way is to specify the accent and theme resource in App.xaml.

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
![Cobalt and BaseLight theme.](http://jkarger.de/images/mahapps_themes_01.png)

#### via ThemeManager