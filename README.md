This is a **WIP** fork of [lewster32/phaser-plugin-isometric](https://github.com/lewster32/phaser-plugin-isometric) & [sebashwa/phaser3-plugin-isometric](https://github.com/sebashwa/phaser3-plugin-isometric/issues) to make it work with Phaser 3.70.0+

## Description

Phaser Isometric is a comprehensive axonometric plugin for Phaser which provides an API for handling axonometric projection of assets in 3D space to the screen.
The goal has been to mimic as closely as possible the existing APIs provided by Phaser for standard orthogonal 2D projection, but add a third dimension.
Also included is an Arcade-based 3D AABB physics engine, which again is closely equivalent in functionality and its API.

## Install
Install using NPM
```
$ npm i phaser3-plugin-isometric3.5
```
and include it in your phaser game js file by importing, setting sceneConfig, and loading the plugin in your `preload()` function:
```
import IsoPlugin, { IsoPhysics } from '../../isometric-plugin/IsoPlugin';

 class playGame extends Phaser.Scene {
  constructor() {
    const sceneConfig = {
      key: 'PlayGame',
      mapAdd: { isoPlugin: 'iso', isoPhysics: 'isoPhysics' }
    };

    super(sceneConfig);
  }

  preload() {
    this.load.image('cube', '/images/player/cube.png');
    this.load.scenePlugin({
      key: 'IsoPlugin',
      url: IsoPlugin,
      sceneKey: 'iso'
    });

    this.load.scenePlugin({
      key: 'IsoPhysics',
      url: IsoPhysics,
      sceneKey: 'isoPhysics'
    });
  }

  ...
  ```
## Features

-  Familiar Phaser API - if you've grasped the basics of Phaser, you can use this!
-  3D geometry helpers in the form of Point3 and Cube
-  Adjustable axonometric projection angle to allow for classic 2:1 pixel dimetric, true 120° isometric or any angle you like via `scene.isometric.projectionAngle`
-  Simple x+y (with z fudging)
-  Arcade Physics derived 3D physics engine (**Working, but needs refactoring!**)
-  Familiar factory methods added to GameObjectFactory and GameObjectCreator so you can do `scene.add.isoSprite`
-  Helpful debug utilities (**Not fully working yet!**)
   
   
For Debug boxes, create a graphics object in the `create()` function:

```
this.graphics = this.add.graphics({ x: 0, y: 0 })
```
and call `debugRender(this.graphics)` in the `update()` function:
```
this.graphics.clear();
objectName.body.debugRender(this.graphics);

```
or for members of a group

```
this.graphics.clear();
this.groupName.children.each((child)=>{child.body.debugRender(this.graphics);})

```


## Examples

Check out the [docs](https://github.com/sebashwa/phaser3-plugin-isometric/tree/master/docs) folder and the [github-page](https://sebashwa.github.io/phaser3-plugin-isometric/)
