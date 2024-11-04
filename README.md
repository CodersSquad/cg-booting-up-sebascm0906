[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/swKMSSMl)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=16850947&assignment_repo_type=AssignmentRepo)
# Computer Graphics Booting Up

## Let's start with ModernGL

This lab stands to prepare the moderngl development environment. Below the steps and requirements for initial coding tasks. Please make sure to edit the python provided files; for dependencies, you can add the files you need.

1. Install moderngl and its dependencies
2. Make sure that the following programs run
    - [`01_hello_world.py`](./01_hello_world.py)
    - [`06_multiple_objects.py`](./06_multiple_objects.py)
    - [`09_models_and_images.py`](./09_models_and_images.py)
        - _Modify this program to change the box's texture to a correctly aligned TEC logo_
3. Document how to execute the 3 programs in the section below.

* For documentation and missing dependencies, follow these links:
    - https://github.com/moderngl/moderngl
    - https://moderngl.readthedocs.io/

## How to run your program

```
# Update this section with instructions on how to run your programs. 

# Consider that these instructions will be executed 
in a completely new linux-based machine (Ubuntu 22.04),
so, instructions for dependencies installation must be added.

# It's highly recommended to use python virtual envs. 
You may take a look on:
https://docs.python.org/3/library/venv.html
```

## Grading Policy

- 25% - `01_hello_world.py` is running with no errors
- 25% - `06_multiple_objects.py` is running with no errors
- 25% - `09_models_and_images.py` is running with the requested change (TEC logo texture)
- 25% - Documentation on how to run your programs


# Python Graphics Project with moderngl and pygame

This repository contains a series of Python scripts that demonstrate the use of `moderngl` and `pygame` to create simple graphical scenes. Below is an explanation of the functionality of each available script.

## Files

### 01_hello_world.py

This script is a basic demonstration that uses `moderngl` and `pygame` to create a window in which the background color changes continuously and smoothly.

#### Functionality

- **Window Initialization**: An 800x800 pixel window is set up using `pygame`, with support for OpenGL and double buffering (`pygame.OPENGL | pygame.DOUBLEBUF`).
- **Background Color Change**: In each frame, the background color changes based on sine functions (`math.sin`). This creates a color transition effect that continuously updates.
  - The red (R), green (G), and blue (B) color components are calculated based on the elapsed time (`now`), which varies as the program runs.
  - Each color component has a phase offset (0, 2.1, and 4.2), ensuring that the three colors change asynchronously, producing a visually appealing color cycle.
- **Rendering**: The `render()` method in the `Scene` class is called in each frame of the main loop to update the background color in the window.
- **Application Exit**: The script listens for a close event (`pygame.QUIT`) to properly close the window.

#### Dependencies

- **moderngl**: A library that simplifies the use of OpenGL in Python.
- **pygame**: A library providing tools for creating games and graphical applications, used here to handle the window and event loop.

### Execution

To run the `01_hello_world.py` script, make sure the dependencies are installed and execute the following command:

```bash
python 01_hello_world.py 
```

### 06_models_and_images.py

This script demonstrates how to render triangles in a 3D scene using `moderngl`, `pygame`, and `numpy`. It uses vertex and fragment shaders to manipulate and render the triangles on the screen.

#### Functionality

- **Window Initialization**: Similar to the first script, it creates an 800x800 pixel window using `pygame`, configured to use OpenGL.
- **Triangle Geometry Definition**: The `TriangleGeometry` class defines a basic triangle with three vertices. These vertices are stored in a Vertex Buffer Object (VBO) that is sent to the GPU for graphical processing.
- **Vertex and Fragment Shaders**:
  - **Vertex Shader**: Transforms the positions of the triangle vertices by applying scaling and translation based on the camera position.
  - **Fragment Shader**: Defines the color of each rendered triangle.
- **Rendering Multiple Triangles**: In the `render()` method of the `Scene` class, three triangles are rendered in different positions and with distinct colors (red, green, blue). This is achieved by passing different position, color, and scale values in each `render()` call.
- **Camera Movement**: The camera rotates around the triangles, calculated using perspective and view functions with `glm`.

#### Dependencies

- **moderngl**: For handling the creation and rendering of buffers and shaders in OpenGL.
- **pygame**: For creating the window and handling events.
- **numpy**: For efficiently handling the triangle vertex data.
- **glm**: For handling camera operations and projection matrices.

### Execution

To run the `06_models_and_images.py` script, make sure the dependencies are installed and execute the following command:

```bash
python 06_models_and_images.py
```


### 09_models_and_images.py

This script loads 3D models and textures to render them in a 3D scene. It uses `moderngl`, `pygame`, `Pillow`, and `glm` to handle texture creation, model loading, and camera transformations.

#### Functionality

- **Image Textures**: The `ImageTexture` class loads an image (`j.jpg`) using `Pillow`, converts it to a compatible format (`RGBA`), and creates a texture that can be applied to models in the scene.
- **3D Model Geometry**: The `ModelGeometry` class loads a 3D model from an `.OBJ` file using `Obj`, converting it into a Vertex Buffer Object (VBO) to render in the scene.
- **Vertex and Fragment Shaders**:
  - **Vertex Shader**: Computes the final positions of the model vertices based on position and scale.
  - **Fragment Shader**: Controls whether to use a texture or a simple color for rendering.
- **Rendering Multiple Models**: The `Scene` class instantiates and renders two models:
  - One without texture (using a simple color).
  - Another with the `j.jpg` image texture applied.
- **Camera Movement**: The camera rotates around the models using `glm.perspective` to create a perspective projection and `glm.lookAt` to simulate the view.

#### Dependencies

- **moderngl**: For managing buffers and shaders in OpenGL.
- **pygame**: For creating the window and handling events.
- **Pillow**: For loading and manipulating image textures.
- **glm**: For camera transformations and projections.

### Execution

To run the `09_models_and_images.py` script, make sure the dependencies are installed and execute the following command:

```bash
python 09_models_and_images.py

