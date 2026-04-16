# customize-group-header-using-mvvm-in-.net-maui-listview

This example demonstrates about how to customize the group header using MVVM in .NET MAUI ListView (SfListView).

## Sample

```xaml
<ContentPage.Resources>
    <ResourceDictionary>
        <DataTemplate x:Name="GroupHeaderTemplate"  x:Key="GroupHeaderTemplate">
            <ViewCell>
                <ViewCell.View>
                    <Grid>
                        <Grid.ColumnDefinitions>
                            <ColumnDefinition Width="30" />
                            <ColumnDefinition Width="*" />
                            <ColumnDefinition Width="40" />
                        </Grid.ColumnDefinitions>
                        <Image x:Name="NormalImage" Grid.Column="0" HorizontalOptions="Center"
                    Source="{Binding IsExpand, Converter={StaticResource BoolToImageConverter}}"
                    VerticalOptions="Center"/>
                        <Label x:Name="label" Text="{Binding Key}" Grid.Column="1" 
                    IsVisible="{Binding Path=BindingContext.IsLabelVisible,
                    Source={x:Reference listView}}"/>
                    </Grid>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </ResourceDictionary>
    </ContentPage.Resources>

<listView:SfListView Grid.Row="1" x:Name="listView" BackgroundColor="AliceBlue" 
                                ItemSpacing="3" ItemSize="70" AllowGroupExpandCollapse="True"
                                GroupHeaderTemplate="{StaticResource GroupHeaderTemplate}"                                   
                                ItemsSource="{Binding Items}">
    <listView:SfListView.DataSource>
        <dataSource:DataSource>
            <dataSource:DataSource.SortDescriptors>
                <dataSource:SortDescriptor PropertyName="ContactName" Direction="Ascending"/>
            </dataSource:DataSource.SortDescriptors>
            <dataSource:DataSource.GroupDescriptors>
                <dataSource:GroupDescriptor PropertyName="DisplayString" />
            </dataSource:DataSource.GroupDescriptors>
        </dataSource:DataSource>
    </listView:SfListView.DataSource>
    <listView:SfListView.ItemTemplate>
        <DataTemplate>
            <ViewCell>
                <ViewCell.View>
                    <Grid x:Name="grid" RowSpacing="1">
                        <Grid.RowDefinitions>
                            <RowDefinition Height="*" />
                            <RowDefinition Height="1" />
                        </Grid.RowDefinitions>
                        <Grid RowSpacing="1">
                            <Grid.ColumnDefinitions>
                                <ColumnDefinition Width="*" />
                                <ColumnDefinition Width="70" />
                            </Grid.ColumnDefinitions>

                            <Grid Grid.Column="0"
                                    RowSpacing="1"
                                    Padding="10,0,0,0"
                                    VerticalOptions="Center">
                                <Grid.RowDefinitions>
                                    <RowDefinition Height="*" />
                                    <RowDefinition Height="*" />
                                </Grid.RowDefinitions>

                                <Label LineBreakMode="WordWrap"
                                        TextColor="#474747"
                                        Text="{Binding ContactName}">
                                </Label>
                                <Label Grid.Row="1"
                                        Grid.Column="0"
                                        TextColor="#474747"
                                        Text="{Binding ContactNumber}">
                                </Label>
                            </Grid>
                        </Grid>
                        <StackLayout Grid.Row="1" BackgroundColor="Gray" HeightRequest="1"/>
                    </Grid>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </listView:SfListView.ItemTemplate>

</listView:SfListView>
```

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
