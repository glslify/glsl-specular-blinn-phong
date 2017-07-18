# glsl-specular-blinn-phong
Computes the [Blinn-Phong](https://en.wikipedia.org/wiki/Blinn%E2%80%93Phong_shading_model) specular weight for a light source

# Example

```glsl
#pragma glslify: blinnPhongSpec = require(glsl-specular-blinn-phong)

uniform vec3 eyePosition;
uniform vec3 lightPosition;

uniform float shininess;

varying vec3 surfacePosition;
varying vec3 surfaceNormal;

void main() {
  vec3 eyeDirection = normalize(eyePosition - surfacePosition);
  vec3 lightDirection = normalize(lightPosition - surfacePosition);
  vec3 normal = normalize(surfaceNormal);

  float power = blinnPhongSpec(lightDirection, eyeDirection, normal, shininess);

  gl_FragColor = vec4(power,power,power,1.0);
}
```

# Usage

Install with npm:

```
npm install glsl-specular-blinn-phong
```

Then use with [glslify](https://github.com/stackgl/glslify).

# API

```glsl
#pragma glslify: blinnPhong = require(glsl-specular-blinn-phong)
```

##### `float blinnPhong(vec3 lightDir, vec3 eyeDir, vec3 normal, float shininess)`
Computes the specular power in the Blinn-Phong lighting model.

* `lightDir` is a *unit length* `vec3` pointing from the surface point toward the light
* `eyeDir` is a *unit length* `vec3` pointing from the surface point toward the camera
* `normal` is the surface normal at the sample point
* `shininess` is the exponent in the Phong equation (default `20.0`)

**Returns** A `float` representing the power of the Blinn-Phong lighting equation

# License
(c) 2014 Mikola Lysenko. MIT License
