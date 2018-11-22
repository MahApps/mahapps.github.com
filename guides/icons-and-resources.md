---
layout: no-sidebar
title: Icons and Resources - MahApps.Metro
---

###Icons

`MahApps.Metro` can use the [MahApps.Metro.IconPacks](https://github.com/MahApps/MahApps.Metro.IconPacks) which contains controls to use these awesome icons in a simple way.

    <Window x:Class="IconPacksTest.App"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:iconPacks="http://metro.mahapps.com/winfx/xaml/iconpacks"
            Title="IconPacks" Height="300" Width="300">

        <Grid>
            <iconPacks:PackIconMaterial Kind="EmoticonCool" VerticalAlignment="Center" HorizontalAlignment="Center" />
        </Grid>

    </Window>

###Modern UI Icons [obsolete]

MahApps.Metro does not embed any icons or "resources" other than control styles. However, there is *[MahApps.Metro.Resources](https://www.nuget.org/packages/MahApps.Metro.Resources/)* package. This allows better discoverability and customisation.

You can install this package using NuGet via Package Manager or Client:

```powershell
PM> Install-Package MahApps.Metro
```

Currently, this consists of [Entypo](http://entypo.com/) and [Temparian's Modern UI Icons](http://modernuiicons.com/).

![](images/6_Resources.png)

## Usage [obsolete]

The resources are simply `Canvas`'s wrapping one or more `Path`s. To use these sorts of elements, you can just use WPF's `VisualBrush`.

```xml
	<Window.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="/Resources/Icons.xaml" />
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Window.Resources>
    
    <Rectangle>
        <Rectangle.Fill>
            <VisualBrush Visual="{StaticResource appbar_add}" />
        </Rectangle.Fill>
    </Rectangle>
```

If you're trying to create "circle" buttons ala Windows Phone 7, the easiest way is to set the `VisualBrush` to be an *`OpacityMask`* on the `Rectangle`. This means you just need to alter the `Rectangle` colours on state change (hover, mouse down, etc)

```xml
	<Rectangle Fill="Black">
		<Rectangle.OpacityMask>
			<VisualBrush Visual="{StaticResource appbar_add}" Stretch="Fill" />
		</Rectangle.OpacityMask>
	</Rectangle>
```
