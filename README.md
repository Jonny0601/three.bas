# THREE.BAS
THREE Buffer Animation System is an extension for [THREE.js](https://github.com/mrdoob/three.js/). It simplifies the workflow of extending the built-in THREE.js materials to include animation logic in the vertex shader. For an overview of this approach, check out [this tutorial series](https://medium.com/@Zadvorsky/into-vertex-shaders-594e6d8cd804).

The standard way of animating objects in THREE.js is to change the values of position, rotation and scale on the CPU and upload the results to the GPU as a transformation matrix. As the number of objects increases, the volume of data sent to the GPU each frame becomes a bottleneck. THREE.BAS works around this issue by storing additional information on the GPU when the geometry is created (using attributes). The animation state is then determined in the vertex shader based on a small number of uniform values.

The two building blocks of this approach are THREE.BufferGeometry and THREE.ShaderMaterial. The geometry is used to store additional attributes. The material contains animation logic inside the shader. In stead of using ShaderMaterial directly, THREE.BAS provides subclasses that duplicate the behavior of THREE.js materials (MeshBasic, MeshPhong and MeshStandard) and an API to inject (animation) logic in specific locations. This way you can make full use of features such as lighting.

While this approach is more cumbersome to work with, it provides a significant performance boost both on desktop and mobile. It has been used in award winning projects such as [Cavalier Challenge](https://cavalierchallenge.com/) and [DS Signature Art](https://ds-signatureart.com/).

See [examples](http://three-bas-examples.surge.sh/), [documentation](http://three-bas-examples.surge.sh/docs/) and the wiki for more information.

There is also a tutorial [here](https://medium.com/@Zadvorsky/into-vertex-shaders-594e6d8cd804) that goes through the basics of vertex shaders, and the approach of BAS. Part 4 in particular focusses on using this extension. 

## Compatibility
Tested with THREE.js r105. Because the animation materials inject code into the built in materials, BAS may not work with earlier versions of three.

## Usage
Include `dist/bas.js` or `dist/bas.min.js` in your project. An npm package is also available:

    $ npm install three-bas
    
## ES6 imports
```js
import * as BAS from 'three-bas'
// or
import {
  PrefabBufferGeometry,
  StandardAnimationMaterial,
  // etc
} from 'three-bas'
```

## Development
This project relies or [npm](https://www.npmjs.com/) and [rollup](https://rollupjs.org/) for building the source.

Run `$ npm install` to install dependencies and `npm run dev` to start building.
