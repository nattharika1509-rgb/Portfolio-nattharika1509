---
name: threejs-sprite-designer
description: Expert skill for creating and animating 3D Sprites (Billboards) in Three.js. Handles spritesheet animation, flipbook effects, and performance optimization for thousands of 2D elements in a 3D scene.
---

# Three.js Sprite Designer

This skill focuses on integrating 2D "Sprites" into 3D environments, a technique common in high-end interactive websites and retro-modern games.

## Core Concepts

### 1. The Sprite Object
A Sprite is a 2D plane that always faces the camera.

```javascript
const map = new THREE.TextureLoader().load( 'sprite.png' );
const material = new THREE.SpriteMaterial( { map: map, color: 0xffffff } );
const sprite = new THREE.Sprite( material );
scene.add( sprite );
```

### 2. Spritesheet Animation (Flipbook)
To animate a sprite, you shift the `offset` of the texture.

```javascript
// Texture setup
map.wrapS = map.wrapT = THREE.RepeatWrapping;
map.repeat.set(1 / horizontalTiles, 1 / verticalTiles);

// Update function
function updateSpriteAnimation(texture, horizontalTiles, verticalTiles, currentFrame) {
  const h = currentFrame % horizontalTiles;
  const v = Math.floor(currentFrame / horizontalTiles);
  texture.offset.x = h / horizontalTiles;
  texture.offset.y = (verticalTiles - 1 - v) / verticalTiles;
}
```

## Advanced Patterns

### Billboard Modes
- **Screen-facing**: Always faces camera regardless of rotation.
- **Y-Axis Restricted**: Only rotates on the Y axis (useful for characters on a floor).

### Instanced Sprites
For rendering thousands of sprites, use `InstancedMesh` with a specialized shader to handle billboard rotation in the vertex shader for maximum performance.

## Best Practices
1. **Power of Two Textures**: Ensure spritesheets are 512x512, 1024x1024 etc.
2. **Alpha Testing**: Use `alphaTest: 0.5` in `SpriteMaterial` to prevent depth-sorting issues with transparent edges.
3. **Distance Scaling**: Set `sizeAttenuation: true` to make sprites smaller when far away.
