---
name: threejs-animation
description: Three.js animation - keyframe animation, skeletal animation, morph targets, animation mixing. Use when animating objects, playing GLTF animations, creating procedural motion, or blending animations.
---

# Three.js Animation

## Quick Start

```javascript
import * as THREE from "three";

const clock = new THREE.Clock();

function animate() {
  const delta = clock.getDelta();
  const elapsed = clock.getElapsedTime();

  mesh.rotation.y += delta;
  mesh.position.y = Math.sin(elapsed) * 0.5;

  requestAnimationFrame(animate);
  renderer.render(scene, camera);
}
animate();
```

## Animation System Overview

1. **AnimationClip** - Container for keyframe data
2. **AnimationMixer** - Plays animations on a root object
3. **AnimationAction** - Controls playback of a clip

## AnimationClip
```javascript
const times = [0, 1, 2];
const values = [0, 1, 0];
const track = new THREE.NumberKeyframeTrack(".position[y]", times, values);
const clip = new THREE.AnimationClip("bounce", 2, [track]);
```

## AnimationMixer
```javascript
const mixer = new THREE.AnimationMixer(model);
const action = mixer.clipAction(clip);
action.play();

function animate() {
  const delta = clock.getDelta();
  mixer.update(delta);
  requestAnimationFrame(animate);
  renderer.render(scene, camera);
}
```

## Loading GLTF Animations
```javascript
loader.load("model.glb", (gltf) => {
  const mixer = new THREE.AnimationMixer(gltf.scene);
  const clips = gltf.animations;
  if (clips.length > 0) {
    mixer.clipAction(clips[0]).play();
  }
});
```

## Performance Tips
1. **Share clips**: Reuse AnimationClips on multiple mixers.
2. **Optimize clips**: Call `clip.optimize()` to remove redundant keyframes.
3. **Disable when off-screen**: Pause animations for non-visible objects.
