# Interactive Voronoi Diagram Generator

This is a powerful, interactive web-based tool for generating and visualizing Voronoi diagrams. Built with vanilla JavaScript, HTML, and Tailwind CSS, it allows for dynamic creation and manipulation of Voronoi sites directly in the browser.

### [View the Live Demo](https://raw.githack.com/USERNAME/REPOSITORY/main/index.html)
*(Replace `USERNAME/REPOSITORY` with your GitHub username and repository name)*



## Features

- **Fully Interactive Canvas**: Smoothly pan and zoom with the mouse to navigate your diagram.
- **Multiple Edit Modes**: Switch between modes for point editing, panning, and generating complex shapes.
- **Advanced Point Generators**:
  - **Circles**: Create concentric rings of points with adjustable radii and spacing.
  - **Grids**: Generate rotatable grids with configurable dimensions.
  - **Polygons**: Draw custom polygons to generate sites.
- **Specialized Polygon Generation**:
  - **Ring Mode**: Automatically creates a three-layer "wall" of points along polygon edges, perfect for corridors and boundaries, with intelligent clipping at corners.
  - **Vertex Mode**: Generates points based on the geometry of the polygon's corners.
  - **Edge Splitting**: Adds intermediate points on long edges for more stable Voronoi structures.
- **Rich Display Options**:
  - Toggle the visibility of cell fills, edges, and the generating sites.
  - View the **Delaunay triangulation**, the dual graph of the Voronoi diagram.
  - Enable a **Heatmap** to visualize the density of points.
- **Powerful Tools**:
  - **Voxelize**: Snaps the generated diagram to a grid, creating a pixelated effect.
  - **Cull Redundant**: Intelligently removes points that are fully surrounded by neighbors of the same material, optimizing the diagram.
- **History Management**: Unlimited undo and redo capabilities for worry-free editing.
- **Custom Materials**: Assign up to 8 different materials (colors) to points to create distinct regions.
- **Import & Export**: Save your work as a JSON file and load it back in later.

## How to Use

1.  **Select a Mode**: Use the **Mode** dropdown to choose an action.
    - **Pan & Zoom (Default)**: Drag to pan, use the mouse wheel to zoom.
    - **Edit Points**:
        - **Drag** a point to move it.
        - **Double-click** on the canvas to add a new point.
        - **Single-click** a point to change it to the currently selected material.
        - **`Alt` + Click** a point to delete it.
    - **Add Shape (Circle, Grid, Polygon)**: A preview of the shape will follow your cursor.
        - **Click** to place the shape and generate the points.
        - Use the **`Arrow Keys`** while previewing to adjust shape parameters in real-time.

2.  **Polygon Creation**:
    - In **Add Polygon** mode, **left-click** to place vertices.
    - A line will preview the next segment.
    - To finish, **click near the first vertex** to close the shape.
    - **Right-click** at any time to cancel the current polygon.

3.  **Generator Parameters**:
    - When a shape mode is selected, a panel appears for fine-tuning.
    - **Overwrite Existing**: Removes points from the existing diagram that fall within the new shape's area.
    - **Generate as Ring (Polygon)**: Toggles the advanced "wall" generation mode.

4.  **Manage Your Diagram**:
    - Use the buttons on the toolbar to **Undo**, **Redo**, **Clear All**, or **Cull Redundant** points.
    - **Export** your point data as a JSON file or **Import** a previously saved file.

## Technical Details

- The Voronoi diagram is calculated from first principles using the half-plane intersection method. Each cell is constructed by clipping a bounding box with the perpendicular bisectors between its site and all other sites.
- The polygon clipping logic is an implementation of the **Sutherland-Hodgman algorithm**.
- The application is written entirely in **vanilla JavaScript (ES6)** with no external dependencies aside from Tailwind CSS for styling.
