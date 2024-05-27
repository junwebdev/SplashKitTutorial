# Getting Started with Splash Kit: A Simple Graphical Application in C#

Welcome to the Splash Kit tutorial! In this guide, we'll walk you through creating a basic graphical application using Splash Kit in C#. We'll cover setting up your development environment, creating a window, drawing shapes, and handling user input.

## Prerequisites

Before we begin, ensure you have the following:

- .NET SDK installed on your system
- Splash Kit installed (follow the installation instructions on the [Splash Kit website](https://www.splashkit.io))

## Step 1: Setting Up Your Project

First, create a new directory for your project and navigate into it:

```sh
mkdir SplashKitProject
cd SplashKitProject
```

Next, create a new .NET console project:

```sh
dotnet new console -n SplashKitProject
cd SplashKitProject
```

Add the Splash Kit NuGet package to your project:

```sh
dotnet add package SplashKitSDK
```

## Step 2: Creating the Main Application File

Open the `Program.cs` file and replace its content with the following code:

```csharp
using System;
using SplashKitSDK;

namespace SplashKitProject
{
    class Program
    {
        static void Main(string[] args)
        {
            Window window = new Window("Splash Kit Example", 800, 600);

            while (!window.CloseRequested)
            {
                SplashKit.ProcessEvents();

                SplashKit.ClearScreen(Color.White);

                SplashKit.FillRectangle(Color.Red, 100, 100, 200, 100);
                SplashKit.DrawText("Hello, Splash Kit!", Color.Black, 100, 250);

                window.Refresh();
            }
        }
    }
}
```

In this code, we:

1. Include the Splash Kit SDK.
2. Create a window titled "Splash Kit Example" with dimensions 800x600.
3. Enter the main event loop that runs until the window is closed.
4. Clear the screen with a white color.
5. Draw a red rectangle and some text.
6. Refresh the window to display the changes.

## Step 3: Building and Running Your Application

To build and run your application, use the following command:

```sh
dotnet run
```

You should see a window with a red rectangle and the text "Hello, Splash Kit!".

## Step 4: Handling User Input

Let's enhance our application by adding some user interaction. Modify your `Program.cs` to include input handling:

```csharp
using System;
using SplashKitSDK;

namespace SplashKitProject
{
    class Program
    {
        static void Main(string[] args)
        {
            Window window = new Window("Splash Kit Example", 800, 600);

            double rectX = 100;
            double rectY = 100;

            while (!window.CloseRequested)
            {
                SplashKit.ProcessEvents();

                // Handle user input
                if (SplashKit.KeyDown(KeyCode.UpKey)) rectY -= 5;
                if (SplashKit.KeyDown(KeyCode.DownKey)) rectY += 5;
                if (SplashKit.KeyDown(KeyCode.LeftKey)) rectX -= 5;
                if (SplashKit.KeyDown(KeyCode.RightKey)) rectX += 5;

                SplashKit.ClearScreen(Color.White);

                SplashKit.FillRectangle(Color.Red, rectX, rectY, 200, 100);
                SplashKit.DrawText("Use arrow keys to move the rectangle", Color.Black, 100, 250);

                window.Refresh();
            }
        }
    }
}
```

In this updated code, we:

1. Declare variables `rectX` and `rectY` to track the rectangle's position.
2. Update the rectangle's position based on arrow key input.
3. Draw the rectangle at its new position on each frame.

## Conclusion

Congratulations! You've created a simple graphical application with Splash Kit in C#. You've learned how to set up a project, create a window, draw shapes, and handle user input. From here, you can explore more features of Splash Kit to create more complex applications and games.

For more information and advanced tutorials, visit the [Splash Kit documentation](https://www.splashkit.io/docs).
