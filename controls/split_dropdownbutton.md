layout: no-sidebar
title: SplitButton and DropDownButton

###SplitButton

![]({{site.baseurl}}/images/splitButton_1.png)  

This controls is like button with dropdownlist, but content of the button changed when selected item changed.

###Events
SplitButton has SelectionChanged and Click events


###SelectedItem and SelectedIndex
This properties usage is just like in Listbox or ComboBox. When one of this properties changed, Content of the button will also changed.

###Binding to ObservableCollection<T> or Dictionary<TK, TV>
To correctly bind ObservableCollection or Dictionary to SplitButton you need to use ItemsSource and DisplayMemberPath
For ex, ```ItemsSource="{Binding Albums}" DisplayMemberPath="Title"```
In case if you bind simple types like enum or int32, you don`t need to use DisplayMemberPath property, only ItemsSource.

###Orientation
SplitButton supports orientation changing as you can see on the screenshot.

###Button commands
You can use button commands for SplitButton

###Icon property
You can add separate icon to SplitButton to display it independently from its content.
It could be bitmap image or vector icon.
```Icon="{DynamicResource appbar_alert}"```

###Example
```<Controls:SplitButton Icon="{DynamicResource appbar_alert}"
                                HorizontalContentAlignment="Left"
                                HorizontalAlignment="Center"
                                VerticalContentAlignment="Center"
                                Width="120"
                                SelectedIndex="2"
                                ItemsSource="{Binding Albums}"
                                DisplayMemberPath="Title"
                                VerticalAlignment="Center"  />```
								
result will be:
![]({{site.baseurl}}/images/splitButton_2.png)



###DropDownButton

![]({{site.baseurl}}/images/dropDownButton_1.png)  

This control almost the same as splitbutton with few differences:
it has no selectedItem and SelectedIndex properties and also has no Selectionchanged event.
Content of the button also not changing. Its static. DropDoenList is context menu, instead of Listbox in SplitButton.
Otherwise its identical to SplitButton.

###Example
```<Controls:DropDownButton  VerticalContentAlignment="Center"
                                     Width="120"
                                     Content="Test"
                                     DisplayMemberPath="Title"
                                     Icon="{DynamicResource appbar_music}"
                                     ItemsSource="{Binding Albums}">
            </Controls:DropDownButton>```
			
result:
![]({{site.baseurl}}/images/dropDownButton_2.png)  
			
