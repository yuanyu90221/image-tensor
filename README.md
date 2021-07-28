# image-tensor

## description

使用 tfjs-model 的 [blazeface](https://github.com/tensorflow/tfjs-models/tree/master/blazeface) 做的只呈現臉 背景模糊的應用


## keynote

### canvas

```js===
// get the canvas context
const ctx = document.querySelector("#cvs").getContext("2d");

// Path2D use to draw marked area
const faceArea = new Path2D();
faceArea.ellipse((leftEye[0]+rightEye[0])/2, (leftEye[1]+rightEye[1])/2, size[0]*0.5, size[0]*0.875, 0, 0, 2*Math.PI)
// draw the target
ctx.save();
ctx.clip(faceArea);
ctx.drawImage(img, 0, 0);
ctx.restore();
```

## Path2D
```js===
// Path2D use to draw marked area
const faceArea = new Path2D();
faceArea.ellipse((leftEye[0]+rightEye[0])/2, (leftEye[1]+rightEye[1])/2, size[0]*0.5, size[0]*0.875, 0, 0, 2*Math.PI)
```
## blazemodel
```js===
// load model
let model; 
async function init() {
  // Load the model.
  model = await blazeface.load();
}
// estimateFaces
const returnTensors = false; // Pass in `true` to get tensors back, rather than values.
const predictions = await model.estimateFaces(video, returnTensors);
```
## video mediaDevice
```js===
// 把 video 抓取起來
window.navigator.mediaDevices.getUserMedia({
  audio: false,
  video: true
}).then((stream)=>{
  video.srcObject = stream;
  video.play();
})
```