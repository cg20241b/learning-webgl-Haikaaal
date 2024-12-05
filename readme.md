# WebGL Cube with Texture

This project demonstrates how to create a rotating 3D cube with a texture using WebGL.

## Overview

The code initializes a WebGL context, defines the geometry and colors of a cube, and applies a texture to it. The cube is then animated to rotate continuously.

## Key Components

1. **Canvas Initialization**: 
   - The canvas is set to full screen by matching the window's inner width and height.
   - WebGL context is obtained from the canvas.

2. **Geometry Definition**:
   - Vertices, colors, and indices for the cube are defined.
   - Texture coordinates are specified for each face of the cube.

3. **Buffers Creation**:
   - Vertex, color, index, and texture coordinate buffers are created and data is stored in them.

4. **Shaders**:
   - Vertex and fragment shaders are defined and compiled.
   - The shaders are linked to create a shader program.

5. **Matrix Setup**:
   - Projection, view, and model matrices are set up to handle the 3D transformations.

6. **Texture Loading**:
   - An image is loaded and used as a texture for the cube.
   - Texture parameters are set to handle wrapping and filtering.

7. **Animation**:
   - The cube is continuously rotated around the X, Y, and Z axes.
   - The scene is rendered in each frame using `requestAnimationFrame`.

## How to Run

1. Ensure you have the image file `monsieur.png` in the same directory as the HTML file.
2. Open the HTML file in a web browser to see the rotating textured cube.

## Prompting

Im using copilot to help me when doing this webgl

how do i add image into the side of the cube

To add an image to the side of the cube, you need to use textures in WebGL. Here are the steps to modify your existing code to include a texture on one side of the cube.

index.html
Load the texture image.
Modify the vertex shader to include texture coordinates.
Modify the fragment shader to use the texture.
Update the vertex data to include texture coordinates.
Bind the texture and set up the texture parameters.
index.html
Replace 'path/to/your/image.png' with the actual path to your image file. This code will map the texture to the front face of the cube. You can adjust the textureCoords array to map the texture to other faces as needed.


## Code Structure

```html
<!doctype html>
<html>
   <body>
      <canvas id="my_Canvas"></canvas>
      <script>
         // Canvas and WebGL context initialization
         var canvas = document.getElementById('my_Canvas');
         canvas.width = window.innerWidth;
         canvas.height = window.innerHeight;
         gl = canvas.getContext('experimental-webgl');

         // Geometry and buffers setup
         var vertices = [...];
         var colors = [...];
         var indices = [...];
         var textureCoords = [...];

         var vertex_buffer = gl.createBuffer();
         var color_buffer = gl.createBuffer();
         var index_buffer = gl.createBuffer();
         var textureCoordBuffer = gl.createBuffer();

         // Shaders setup
         var vertCode = '...';
         var fragCode = '...';
         var vertShader = gl.createShader(gl.VERTEX_SHADER);
         var fragShader = gl.createShader(gl.FRAGMENT_SHADER);
         var shaderProgram = gl.createProgram();

         // Matrix setup
         function get_projection(angle, a, zMin, zMax) { ... }
         var proj_matrix = get_projection(40, canvas.width/canvas.height, 1, 100);
         var mov_matrix = [...];
         var view_matrix = [...];

         // Texture loading
         var texture = gl.createTexture();
         var image = new Image();
         image.onload = function() { ... }
         image.src = 'monsieur.png';

         // Animation and drawing
         var time_old = 0;
         var animate = function(time) { ... }
         animate(0);

         // Handle window resize
         window.addEventListener('resize', function() { ... });
      </script>
   </body>
</html>