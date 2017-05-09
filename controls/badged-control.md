---
layout: no-sidebar
title: Badged Control
---

Renders a badge overlay on a control.

Examples:

```xml
<Controls:Badged Badge="{Binding Path=BadgeValue}">
  <!-- Control to wrap goes here -->
  <Button Content="Notifications" />
</Controls:Badged>
```

![]({{site.baseurl}}/images/badged-control-button.png)

```xml
<Controls:Badged Badge="{Binding Path=BadgeValue}" BadgePlacementMode="BottomRight">
  <!-- Control to wrap goes here -->
  <Button>
    <iconPacks:PackIconFontAwesome Kind="CommentOutline"/>
  </Button>
</Controls:Badged>
```

![]({{site.baseurl}}/images/badged-control-button-icon.png)