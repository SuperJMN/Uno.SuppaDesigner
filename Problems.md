# Compile-time issues

## ✅ Problem 1
> error CS0260: Missing partial modifier on declaration of type 'ActualSizePropertyProxy'; another partial declaration of this type exists

All classes inheriting from UIElement must have the partial modifier. This is because of the `NativeCtorGenerator`
This is present to avoid random crashes caused by iOS/Android internal behavior

## 💣 Problem 2
>  warning NU1701: Package 'CommonServiceLocator 1.3.0' was restored using '.NETFramework,Version=v4.6.1' instead of the project target framework '.NETStandard,Version=v2.0'. This package may not be fully compatible with your project.

## 💣 Problem 3
### While trying to add Uno.System.Reactive to a Uno Class Library
> Restoring packages for D:\Repos\SuperJMN\Uno.SuppaDesigner\Uno.Zafiro\Uno.Zafiro.csproj...
NU1605: Detected package downgrade: System.Diagnostics.Debug from 4.3.0 to 4.0.11. Reference the package directly from the project to select a different version. 
 Uno.Zafiro -> Uno.System.Reactive 4.0.0-uno.415 -> System.Dynamic.Runtime 4.0.11 -> System.Collections 4.0.11 -> runtime.aot.System.Collections 4.3.0 -> System.Diagnostics.Debug (>= 4.3.0) 
...

This seems to be due to incompatibilities between **Uno.Microsoft.Xaml.Behaviors.Interactivity** and **Uno.System.Reactive** as of 25/05/2019 (latest pre-release versions)

## 💣 Problem 4
The **RichEditBox** is almost unsupported

## 💣 Problem 5
LostFocus isn't defined

## 💣 Problem 6

Although the type is correctly defined, this makes the build fail:

```
<Style TargetType="ctr:HeaderedContentControl" >
        <Setter Property="BorderThickness" Value="1" />
        <!--<Setter Property="BorderBrush" Value="{ThemeResource AccentButtonBackground}" />
        <Setter Property="Background" Value="{ThemeResource AccentButtonBackground}" />-->
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="ctr:HeaderedContentControl">
                    <Border
                        BorderBrush="{TemplateBinding BorderBrush}"
                        BorderThickness="{TemplateBinding BorderThickness}">
                        <Grid>
                            <Grid.RowDefinitions>
                                <RowDefinition Height="Auto" />
                                <RowDefinition />
                            </Grid.RowDefinitions>
                            <Border Background="{TemplateBinding Background}">
                                <TextBlock Text="{TemplateBinding Header}" TextAlignment="Center" FontWeight="Bold" TextWrapping="Wrap" Foreground="{ThemeResource AppBarBorderThemeBrush}"/>
                            </Border>
                            <ContentPresenter Grid.Row="1" />
                        </Grid>
                    </Border>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
```
With this error
> D:\Repos\SuperJMN\Uno.SuppaDesigner\Uno.Zafiro\Themes\Generic.xaml(54,12): XamlCompiler error WMC0110: Unknown target type 'ctr:HeaderedContentControl'

## Unsupported features

## 💣 SymbolIcon doesn't render in the Web head

## 💣 No pickers: There is no way to select a local file. 
For instance, you couldn't upload a file to the server that pretty much limits file processing to URLs of files already uploaded.
