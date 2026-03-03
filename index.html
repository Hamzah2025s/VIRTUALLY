<!DOCTYPE html>
<html>
<head>
  <title>virtually</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@4.10.0"></script>
  <script src="https://cdn.jsdelivr.net/npm/@tensorflow-models/body-pix"></script>
  <script src="https://cdn.jsdelivr.net/npm/@tensorflow-models/pose-detection"></script>

  <style>
    body { font-family: Arial; background:#111; color:white; text-align:center; margin:0; }
    header { padding:20px; font-size:28px; font-weight:bold;
             background:linear-gradient(90deg,#6a11cb,#2575fc); }
    canvas { max-width:95%; border:2px solid #444; margin-top:20px; }
    input, button { margin:10px; padding:10px; border-radius:6px; border:none; }
    button { background:#2575fc; color:white; font-weight:bold; cursor:pointer; }
  </style>
</head>
<body>

<header>virtually</header>

<input type="file" id="bodyUpload" accept="image/*">
<input type="file" id="clothingUpload" accept="image/*">
<br>
<button onclick="runAI()">Auto Fit Clothing</button>
<button onclick="downloadImage()">Download Look</button>

<br>
<canvas id="canvas"></canvas>

<script>
let bodyImage = new Image();
let clothingImage = new Image();
let canvas = document.getElementById("canvas");
let ctx = canvas.getContext("2d");

let detector;

async function loadModels(){
  await tf.setBackend("webgl");
  detector = await poseDetection.createDetector(
    poseDetection.SupportedModels.MoveNet
  );
}
loadModels();

document.getElementById("bodyUpload").onchange = e => {
  const reader = new FileReader();
  reader.onload = ev => bodyImage.src = ev.target.result;
  reader.readAsDataURL(e.target.files[0]);
};

document.getElementById("clothingUpload").onchange = e => {
  const reader = new FileReader();
  reader.onload = ev => clothingImage.src = ev.target.result;
  reader.readAsDataURL(e.target.files[0]);
};

async function runAI(){
  canvas.width = bodyImage.width;
  canvas.height = bodyImage.height;
  ctx.drawImage(bodyImage,0,0);

  const poses = await detector.estimatePoses(bodyImage);
  if(!poses.length) return;

  const keypoints = poses[0].keypoints;

  const leftShoulder = keypoints.find(k => k.name==="left_shoulder");
  const rightShoulder = keypoints.find(k => k.name==="right_shoulder");
  const leftHip = keypoints.find(k => k.name==="left_hip");

  if(!leftShoulder || !rightShoulder || !leftHip) return;

  const shoulderWidth = Math.abs(rightShoulder.x - leftShoulder.x);
  const torsoHeight = Math.abs(leftHip.y - leftShoulder.y);

  const clothingWidth = shoulderWidth * 1.4;
  const clothingHeight = torsoHeight * 1.4;

  const centerX = (leftShoulder.x + rightShoulder.x) / 2;
  const topY = leftShoulder.y;

  ctx.drawImage(
    clothingImage,
    centerX - clothingWidth/2,
    topY - 20,
    clothingWidth,
    clothingHeight
  );
}

function downloadImage(){
  const link = document.createElement("a");
  link.download = "virtually-look.png";
  link.href = canvas.toDataURL();
  link.click();
}
</script>

</body>
</html>
