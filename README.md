# Fruit Demo App

A simple mobile application built with .NET MAUI that demonstrates fruit data visualization and management.

## 📱 Features

- Display a list of fruits with their details
- Visual progress indicators for fruit statistics
- Responsive layout that works across different devices
- Modern UI with MVVM architecture

## 🛠 Technologies Used

- .NET MAUI
- C#
- XAML
- MVVM Pattern

## 🚀 Getting Started

### Prerequisites

- Visual Studio 2022 (17.4 or later) with .NET MAUI workload
- JetBrain Rider
- .NET 8.0 SDK


## 📂 Project Structure

```
FruitDemo/
├── Models/
│   └── FruitInformation.cs
├── Views/
│   └── MainPage.xaml
│   └── MainPage.xaml.cs
├── MauiProgram.cs/
├── Resources/
│   └── Fonts
│         └── Roboto-Bold.ttf
│         └── Roboto-Regular.ttf
```

## 🎯 Usage

The app provides a user-friendly interface to:
- View fruit information
- See percentage-based statistics
- Interact with a responsive UI

## 📝 Nuget Package
- AcrylicView.Maui

---
# Overview
![Screenshot 2024-11-08 at 8 22 30 PM](https://github.com/user-attachments/assets/1e2d61a8-ba88-419a-abf8-240880a0918d)

# ⭐️ Analysis of MainPage.xaml File

## Introduction

The `MainPage.xaml` file provided is part of a .NET MAUI (Multi-platform App UI) application, specifically designed for displaying information about a fruit named "Papaya." This XAML file defines the UI layout and elements for a mobile or desktop application page using XAML (eXtensible Application Markup Language). This language is commonly used for creating user interfaces in .NET-based applications.

## Key Features of MainPage.xaml

### 1. **Page Definition and Namespaces**
The file begins by defining a `ContentPage` named `FruitDemo.MainPage`. Several namespaces are imported:
- **`xmlns="http://schemas.microsoft.com/dotnet/2021/maui"`**: This is the standard namespace for .NET MAUI components.
- **`xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"`**: This is used for XAML features such as x:Class, which specifies the backing C# class.
- **`xmlns:acrylic="clr-namespace:Xe.AcrylicView;assembly=Xe.AcrylicView"`**: This custom namespace includes the `AcrylicView` element, which provides a frosted glass effect for UI elements.

### 2. **Background Styling**
The page's background is set using a `LinearGradientBrush`, which creates a gradient effect that transitions from a light yellow color (`#FFCC33`) to a slightly darker yellow (`#FCBC03`). This gives the page a visually appealing, dynamic background that fits well with the tropical theme of the fruit.

#### Example:
```xml
<ContentPage.Background>
    <LinearGradientBrush EndPoint="0,1">
        <GradientStop Offset="0.1" Color="#FFCC33" />
        <GradientStop Offset="1.0" Color="#FCBC03" />
    </LinearGradientBrush>
</ContentPage.Background>
```

### 3. **Grid Layout**
The main layout is built using a `Grid` element, which has three rows defined in a proportion of `.2*, .4*, .4*`. This layout provides structure to organize the page content, including an image, descriptive labels, and a detailed view of nutrient information.

- **Grid Properties**:
  - The `Grid` uses a margin of `25` to provide spacing between its edges and the parent container.

### 4. **Image Element**
An `Image` element is included to represent the papaya. It is centered both horizontally and vertically and spans across all three rows of the grid.

#### Example:
```xml
<Image
    Aspect="Center"
    Grid.RowSpan="3"
    HorizontalOptions="Center"
    Source="papaya.png"
    VerticalOptions="Center" />
```
- **Attributes**:
  - `Aspect="Center"`: Ensures the image is centered within its container.
  - `Source="papaya.png"`: Specifies the image to be displayed.

### 5. **VerticalStackLayout for Fruit Information**
A `VerticalStackLayout` is used to display information about the fruit. It contains two labels:
- **Fruit Name ("PAPAYA")**: Displayed with a larger font size (`45`).
- **Serving Size ("100 grams")**: Displayed with a smaller, bold font (`20`).

### 6. **AcrylicView for Nutrient Information**
The `AcrylicView` element from the `Xe.AcrylicView` namespace is used to create a translucent card-like container for displaying detailed nutrient information about the papaya.
- **Attributes**:
  - `CornerRadius="20"`: Gives the acrylic view rounded corners.
  - `TintColor="#FCE7A7"`: Sets a light yellow tint.
  - `TintOpacity=".2"`: Controls the transparency of the tint.

Inside the `AcrylicView`, a `VerticalStackLayout` is used to bind the `PapayaInfo` data, which contains micronutrient details like `Micronutrient` and `Percentage`.

#### Example:
```xml
<acrylic:AcrylicView
    Grid.Row="2"
    CornerRadius="20"
    EffectStyle="Custom"
    TintColor="#FCE7A7"
    TintOpacity=".2"
    VerticalOptions="Center">

    <VerticalStackLayout
        Padding="35"
        BindableLayout.ItemsSource="{Binding PapayaInfo}"
        VerticalOptions="Center">
        <BindableLayout.ItemTemplate>
            <DataTemplate>
                <Grid Margin="0,10,0,0"
                      ColumnDefinitions=".6*,.4*">
                    <Label FontFamily="Bold"
                           FontSize="20"
                           Text="{Binding Micronutrient}"/>
                    <Label Grid.Column="1"
                           FontFamily="Regular"
                           FontSize="20"
                           HorizontalOptions="End"
                           Text="{Binding Percentage, StringFormat='{0} %'}" />
                </Grid>
            </DataTemplate>
        </BindableLayout.ItemTemplate>
    </VerticalStackLayout>

</acrylic:AcrylicView>
```

### Key Features Summary
- **Visual Appeal**: Uses gradients, images, and rounded acrylic effects to create an attractive UI.
- **Data Binding**: Utilizes MAUI's data binding to dynamically populate information.
- **Responsive Layout**: Utilizes `Grid` and `VerticalStackLayout` to arrange elements adaptively.

## Resources for Further Reference
Here are some useful resources for understanding the concepts used in this layout:
1. [Microsoft MAUI Documentation](https://learn.microsoft.com/en-us/dotnet/maui/what-is-maui) - Official documentation for learning about MAUI.
2. [XAML Layouts in MAUI](https://learn.microsoft.com/en-us/dotnet/maui/user-interface/layouts/) - Information on different layouts available in MAUI.
3. [AcrylicView Effect in MAUI](https://github.com/sswi/AcrylicView.MAUI) - Documentation on the custom `AcrylicView` used for frosted glass effects.
4. [Bindable Layouts in MAUI](https://learn.microsoft.com/en-us/dotnet/maui/user-interface/layouts/bindablelayout?view=net-maui-8.0) - Useful for understanding how to bind dynamic collections to the UI.
---
# ⭐️ Analysis of MainPage.xaml.cs File

## Introduction

The `MainPage.xaml.cs` file provided is a code-behind file for a .NET MAUI application page. It is written in C# and is directly associated with `MainPage.xaml`. The code-behind file is primarily responsible for initializing data and managing UI bindings for the `MainPage`, where the XAML file is responsible for defining the UI layout. This is a common approach used in MVVM (Model-View-ViewModel) patterns to separate logic from UI definitions.

## Key Features of MainPage.xaml.cs

### 1. **Namespace and Class Definition**
The code belongs to the namespace `FruitDemo`, which indicates it is part of a larger application dealing with fruits, possibly a nutrition or educational application. The primary class is `MainPage`, which extends `ContentPage`. This class contains properties and methods that interact with the XAML UI defined in `MainPage.xaml`.

```csharp
namespace FruitDemo
{
    public partial class MainPage : ContentPage
    {
        // Code continues...
    }
}
```

- **`MainPage : ContentPage`**: The class inherits from `ContentPage`, which is a base class for defining pages in MAUI. This means the `MainPage` will have all the functionalities of a typical mobile or desktop page, such as displaying UI elements and handling user interactions.

### 2. **PapayaInfo Property**
A property named `PapayaInfo` is defined as a `List<FruitInformation>`. This property holds detailed nutritional information about the fruit "Papaya."

```csharp
public List<FruitInformation> PapayaInfo { get; set; }
```
- **Purpose**: The `PapayaInfo` property serves as a collection that provides detailed information about different micronutrients found in Papaya. This property is used for data binding in `MainPage.xaml` to display nutritional information in a UI-friendly manner.

### 3. **Constructor - MainPage()**
The `MainPage` constructor initializes the `PapayaInfo` list with specific details about Papaya's nutrients. Additionally, the constructor sets the `BindingContext` to `this` to allow for easy data binding within the XAML.

```csharp
public MainPage()
{
    InitializeComponent();
    PapayaInfo = new List<FruitInformation>
    {
        new FruitInformation
        {
            Micronutrient = "Vitamin C",
            Percentage = 101
        },
        new FruitInformation
        {
            Micronutrient = "Vitamin A",
            Percentage = 19
        },
        new FruitInformation
        {
            Micronutrient = "Calcium",
            Percentage = 2
        },
        new FruitInformation
        {
            Micronutrient = "Magnesium",
            Percentage = 5
        },
        new FruitInformation
        {
            Micronutrient = "Potassium",
            Percentage = 5
        },
    };
    this.BindingContext = this;
}
```
- **`InitializeComponent()`**: This method initializes the components of the page, linking the XAML definitions to the C# code.
- **`PapayaInfo` Initialization**: A list of `FruitInformation` objects is created, each containing a micronutrient and its respective percentage. Examples include Vitamin C (101%), Vitamin A (19%), Calcium (2%), Magnesium (5%), and Potassium (5%).
- **`BindingContext`**: Setting the `BindingContext` to `this` allows the XAML UI to directly bind to properties defined in the code-behind file, making data binding straightforward and consistent.

### 4. **The FruitInformation Model**
While not directly included in the provided file, it is evident that `FruitInformation` is a model class, likely defined elsewhere in the application. It contains at least two properties:
- **`Micronutrient`** (type: `string`): Represents the name of the nutrient (e.g., Vitamin C).
- **`Percentage`** (type: `int`): Represents the percentage of the daily value of that nutrient.

### Key Concepts Explained
1. **Data Binding**: The code uses `BindingContext` to enable data binding between the `PapayaInfo` list and UI elements defined in the XAML (`MainPage.xaml`). This allows the UI to automatically reflect the values provided in the `PapayaInfo` collection without manually updating each UI element.

2. **Initialization of Data**: The constructor's initialization of `PapayaInfo` with hardcoded nutrient values is a simple example of how data can be made available to the view. In a more complex scenario, this data might come from a database, an API, or user input.

3. **Partial Class and XAML Code-Behind**: The use of `partial class` means the C# file is part of a complete class that includes both the XAML and the C# logic. The XAML handles the visual representation, while the C# code handles the logic and data management.

---
# ⭐️ Analysis of FruitInformation.cs File

## Introduction
The `FruitInformation.cs` file defines a simple model class called `FruitInformation` within the namespace `FruitDemo.Models`. In the context of the MVVM (Model-View-ViewModel) pattern, this model represents data related to a particular fruit's nutritional components, such as micronutrients and their respective percentages. This class is part of a .NET MAUI application, and it is primarily used to store and transfer data between different parts of the application.

## Key Features of FruitInformation.cs

### 1. **Namespace and Class Definition**
The class `FruitInformation` is defined under the namespace `FruitDemo.Models`, which indicates it is part of the data layer of an application that likely deals with fruits and nutrition information.

```csharp
namespace FruitDemo.Models;

public class FruitInformation
{
    // Class contents...
}
```
- **Namespace**: `FruitDemo.Models` suggests that this file belongs to a broader application, and placing it in the `Models` folder adheres to the MVVM structure.
- **Class Purpose**: This class serves as a **model** for storing information about a fruit's nutritional properties.

### 2. **Properties of the FruitInformation Class**
The `FruitInformation` class has two public properties:

```csharp
public string Micronutrient { get; set; }
public int Percentage { get; set; }
```
- **`Micronutrient` (type: `string`)**: This property holds the name of the micronutrient (e.g., "Vitamin C", "Vitamin A").
  - **Usage**: Represents a specific nutrient found in the fruit.
  - **Example**: If the nutrient is "Vitamin C," this property will be set as `Micronutrient = "Vitamin C"`.

- **`Percentage` (type: `int`)**: This property holds the percentage value of the nutrient based on its recommended daily value.
  - **Usage**: Represents the percentage of the daily value provided by the nutrient.
  - **Example**: If the nutrient provides 101% of the daily value, this property will be `Percentage = 101`.

### Key Concepts Explained
1. **Properties in Models**: The properties `Micronutrient` and `Percentage` encapsulate the data points that are relevant to the application. They follow the standard getter and setter pattern, which makes them easy to bind to user interface components in XAML or other parts of the application.

2. **Simplicity and Extensibility**: The model is kept simple for easy usage, but it could be extended if needed to add more properties, such as `UnitOfMeasure` or `RecommendedDailyIntake`, depending on application requirements.

3. **Data Binding**: This model is an example of a **data entity** that can be directly bound to front-end components via a `BindingContext`. For instance, the `PapayaInfo` list in the `MainPage` binds directly to UI elements that iterate over the collection and display the nutrient details.

## Resources for Further Reference
Here are some useful resources for understanding the concepts used in this model file:

1. [Creating Models in MVVM](https://learn.microsoft.com/en-us/xamarin/xamarin-forms/enterprise-application-patterns/mvvm) - Learn about the role of models within the MVVM pattern.
2. [Data Binding in MAUI](https://learn.microsoft.com/en-us/dotnet/maui/xaml/fundamentals/mvvm?view=net-maui-8.0) - Official documentation for how data binding works in .NET MAUI.
3. [Model-View-ViewModel (MVVM) Design Pattern](https://www.tutorialspoint.com/mvvm/mvvm_introduction.htm) - Introduction to the MVVM pattern, including its benefits and how to implement it in .NET applications.


