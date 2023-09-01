# 3D EMMERSIVE VIEW

The project uses a HDR 360 degree image for the background of the scene.

!["Immersive view"]("/assets/images/view.png")

```js
import { RGBELoader } from "three/examples/jsm/loaders/RGBELoader";

renderer.toneMapping = THREE.ACESFilmicToneMapping;
renderer.toneMappingExposure = 0.8;

const loader = new RGBELoader();
loader.load("./assets/HDR/background4.hdr", function (texture) {
  texture.mapping = THREE.EquirectangularReflectionMapping;
  scene.background = texture; //make texture background of scene
  scene.environment = texture;

  const sphere = new THREE.Mesh(
    new THREE.SphereGeometry(1, 50, 50),
    new THREE.MeshStandardMaterial({
      roughness: 0,
      metalness: 0.5,
      color: 0xffea00,
    })
  );
  scene.add(sphere);
});
```
