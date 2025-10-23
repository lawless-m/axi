# Axi C# - Turtle Graphics Library for .NET

A C# port of the [axi Python library](https://github.com/fogleman/axi) for creating drawings using Logo-style turtle graphics. This version includes an Avalonia desktop application for interactive drawing.

## Projects

### Axi.Drawing
Core library implementing turtle graphics and drawing primitives.

**Features:**
- Logo-style turtle graphics (forward, backward, left, right)
- Pen control (pen up, pen down)
- Built-in shapes (box, square, circle)
- Path-based drawing representation
- SVG export
- Transformations (translate, scale, rotate)

### Axi.Avalonia
Desktop application with an interactive Logo command interface.

**Features:**
- Real-time turtle graphics visualization
- Command-line style input
- Visual turtle indicator showing position and heading
- Color-coded pen state (red = down, green = up)

## Getting Started

### Prerequisites
- .NET 8.0 SDK or later

### Building

```bash
cd axi-csharp
dotnet restore
dotnet build
```

### Running the Avalonia App

```bash
cd Axi.Avalonia
dotnet run
```

## Logo Commands

The application supports the following Logo-style commands:

### Movement
- `forward [distance]` or `fd [distance]` - Move forward
- `backward [distance]` or `bk [distance]` - Move backward

### Turning
- `right [angle]` or `rt [angle]` - Turn right in degrees
- `left [angle]` or `lt [angle]` - Turn left in degrees

### Pen Control
- `penup` or `pu` - Lift pen (stop drawing)
- `pendown` or `pd` - Lower pen (start drawing)

### Shapes
- `box [width] [height]` - Draw a rectangle
- `square [size]` - Draw a square
- `circle [radius]` - Draw a circle

### Other
- `home` - Return to origin (0, 0) facing up
- `clear` - Clear the drawing

### Examples

Draw a square:
```
box 100 100
```

Draw a simple house:
```
box 100 100, penup, forward 100, right 90, forward 100, left 90, pendown, forward 50, left 120, forward 58, left 120, forward 58, left 120
```

Draw a circle:
```
circle 50
```

Multiple commands (separated by commas or semicolons):
```
forward 100, right 90, forward 100, right 90, forward 100, right 90, forward 100
```

## Programming API

You can also use the library programmatically:

```csharp
using Axi.Drawing;

var turtle = new Turtle();

// Draw a box
turtle.Forward(100);
turtle.Right(90);
turtle.Forward(50);
turtle.Right(90);
turtle.Forward(100);
turtle.Right(90);
turtle.Forward(50);

// Or use the built-in method
turtle.Box(100, 50);

// Get the drawing
var drawing = turtle.GetDrawing();

// Export to SVG
var svg = drawing.ToSvg(800, 600);
File.WriteAllText("output.svg", svg);
```

## Architecture

### Point
Immutable struct representing a 2D point with double precision.

### Drawing
Container for paths (collections of points). Supports transformations and SVG export.

### Turtle
Implements Logo-style turtle graphics:
- Maintains position, heading, and pen state
- Generates paths as the turtle moves
- Provides high-level drawing primitives

## Differences from Python Version

This C# port focuses on the core turtle graphics functionality:
- ✅ Turtle graphics API
- ✅ Drawing and path management
- ✅ Basic transformations
- ✅ SVG export
- ✅ Interactive GUI (Avalonia)
- ❌ Device control (AxiDraw hardware)
- ❌ Motion planning
- ❌ Advanced path optimization

## Future Enhancements

Potential additions:
- More Logo commands (repeat, setxy, etc.)
- Saved drawing files
- Undo/redo
- Export to other formats
- Color support
- Fill operations
- More advanced shapes

## License

This project is based on the original [axi library by Michael Fogleman](https://github.com/fogleman/axi).
