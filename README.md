# jslib-html5-camera-photo

The first objective of this package comes from the need to have a js library that can help me to capture picture from mobile or desktop camera through the browser with the HTML5 video and canvas elements.

Another js camera ? Yes! I found [webcamjs](https://github.com/jhuckaby/webcamjs/) and [jpeg_camera](https://github.com/amw/jpeg_camera) but i need to switch easily from camera `environment` and `user`. You need to build the constraint of getUserMedia()... Another need is to have a `sizeFactor` instead of a fixing 'width' and 'height' that can not fit with the ratio of the resolution that camera can pick.

## supported browsers
[https://caniuse.com/#search=getUserMedia](https://caniuse.com/#search=getUserMedia)
![alt text](./docs/caniuse.png)

## LiveDemo
[https://mabelanger.github.io/jslib-html5-camera-photo/](https://mabelanger.github.io/jslib-html5-camera-photo/)

## Installation

```bash
npm install --save jslib-html5-camera-photo
```

```bash
yarn add jslib-html5-camera-photo
```

Both Yarn and npm download packages from the npm registry.

## API

### Geting started
You can use it with pure JavaScript, Jquery or React.

### Example vanilla Js with HTML

```html
<div id="divId">
  <video id="videoId" autoplay="true"></video>
  <img alt="imgId" id="imgId">
  <button id="takePhotoButtonId">takePhoto</button>
  <button id="stopCameraButtonId">stopCamera</button>
</div>
```

```js
import CameraPhoto from 'lib-html5-camera-photo';

// get videoElement from the dom.
let videoElement = document.getElementById('videoId');
let imgElement = document.getElementById('imgId');
let takePhotoButtonElement = document.getElementById('takePhotoButtonId');
let stopCameraButtonElement = document.getElementById('stopCameraButtonId');

// instantiate CameraPhoto with the videoElement
let cameraPhoto = new CameraPhoto(videoElement);

// start the camera
cameraPhoto.startCamera();


function takePhoto() {
  let dataUri = cameraPhoto.getDataUri();
  imgElement.src = dataUri;
}

function stopCamera() {
  cameraPhoto.stopCamera()
  .then(()=>{
    console.log('Camera stoped!')
  })
  .catch((error)=>{
    console.log('No camera to stop!:', error)
  })
}

takePhotoButtonElement.onclick = takePhoto;
stopCameraButtonElement.onclick = stopCamera;

```



### With React
