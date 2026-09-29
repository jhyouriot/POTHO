<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">

<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0, user-scalable=no"
>

<title>PHOTO EXPERIENCE</title>

<style>

/* ================================
   BASIC
================================ */

* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
}

body {
  background: #08090c;
  color: white;
  font-family:
    Arial,
    "Noto Sans KR",
    sans-serif;

  overflow: hidden;
}

button {
  font: inherit;
  cursor: pointer;
}

.screen {
  display: none;
  width: 100vw;
  height: 100dvh;
}

.screen.active {
  display: flex;
}


/* ================================
   START / THEME SELECT
================================ */

#themeScreen {

  flex-direction: column;
  justify-content: center;
  align-items: center;

  padding: 40px;

  background:
    radial-gradient(
      circle at 50% 0%,
      #1b2533,
      #08090c 60%
    );
}


.eyebrow {

  font-size: 15px;

  letter-spacing: 8px;

  opacity: .5;

  margin-bottom: 15px;
}


h1 {

  margin: 0;

  font-size:
    clamp(38px, 6vw, 76px);

  text-align: center;
}


.subtitle {

  margin-top: 15px;
  margin-bottom: 45px;

  color: #aab0ba;

  font-size: 18px;
}


.themeGrid {

  width: min(1200px, 94vw);

  display: grid;

  grid-template-columns:
    repeat(4, 1fr);

  gap: 18px;
}


.themeCard {

  position: relative;

  aspect-ratio: 3 / 4;

  border: 1px solid
    rgba(255,255,255,.15);

  border-radius: 25px;

  overflow: hidden;

  padding: 0;

  background: #15171c;

  color: white;

  transition: .15s;
}


.themeCard:active {

  transform: scale(.97);

}


.themeCard img {

  width: 100%;
  height: 100%;

  object-fit: cover;
}


.themeCard .themeLabel {

  position: absolute;

  left: 0;
  right: 0;
  bottom: 0;

  padding: 50px 20px 22px;

  text-align: left;

  font-size: 23px;
  font-weight: 800;

  background:
    linear-gradient(
      transparent,
      rgba(0,0,0,.85)
    );
}


/* ================================
   CAMERA
================================ */

#cameraScreen {

  background: black;

}


#cameraStage {

  position: relative;

  width: 100%;
  height: 100%;

  overflow: hidden;

  background: black;
}


#camera {

  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  object-fit: cover;

  transform: scaleX(-1);
}


/* ================================
   IMAGE OVERLAY
================================ */

#imageLayers {

  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  pointer-events: none;

}


.photoLayer {

  position: absolute;

  object-fit: contain;

  pointer-events: none;

  user-select: none;
}


/* ================================
   TOP UI
================================ */

.cameraTop {

  position: absolute;

  top: 30px;
  left: 30px;
  right: 30px;

  z-index: 30;

  display: flex;

  justify-content:
    space-between;

  align-items: center;
}


.themeBadge {

  padding: 13px 22px;

  border-radius: 100px;

  background:
    rgba(0,0,0,.45);

  backdrop-filter:
    blur(12px);

  font-size: 15px;

  letter-spacing: 2px;
}


.changeTheme {

  border: 0;

  color: white;

  padding: 13px 22px;

  border-radius: 100px;

  background:
    rgba(0,0,0,.45);

  backdrop-filter:
    blur(12px);
}


/* ================================
   CAMERA BUTTON
================================ */

.cameraControls {

  position: absolute;

  left: 50%;
  bottom: 35px;

  transform:
    translateX(-50%);

  z-index: 40;
}


.shootButton {

  width: 100px;
  height: 100px;

  border-radius: 50%;

  border: 7px solid
    rgba(255,255,255,.35);

  background: white;

  box-shadow:
    0 0 0 3px white;

}


/* ================================
   COUNTDOWN
================================ */

#countdown {

  position: absolute;

  inset: 0;

  z-index: 50;

  display: none;

  justify-content: center;
  align-items: center;

  font-size:
    clamp(120px,20vw,220px);

  font-weight: 900;

  text-shadow:
    0 8px 40px black;

}


/* ================================
   RESULT
================================ */

#resultScreen {

  flex-direction: column;

  justify-content: center;

  align-items: center;

  padding: 25px;

  background:
    radial-gradient(
      circle at top,
      #1b1f27,
      #08090c 65%
    );
}


.resultTitle {

  font-size: 28px;

  margin-bottom: 20px;

}


#resultCanvas {

  max-height: 70vh;

  max-width: 90vw;

  border-radius: 15px;

  box-shadow:
    0 20px 70px
    rgba(0,0,0,.7);
}


.resultButtons {

  margin-top: 25px;

  display: flex;

  gap: 15px;
}


.resultButtons button {

  border: 0;

  border-radius: 100px;

  padding: 18px 30px;

  font-weight: 700;
}


.primaryButton {

  background: white;

  color: black;
}


.secondaryButton {

  background: #242830;

  color: white;
}


/* ================================
   QR SCREEN
================================ */

#qrScreen {

  flex-direction: column;

  justify-content: center;

  align-items: center;

  text-align: center;

  background:
    radial-gradient(
      circle at top,
      #202733,
      #08090c 65%
    );
}


.qrTitle {

  font-size:
    clamp(32px,5vw,60px);

  margin-bottom: 10px;
}


.qrDescription {

  color: #aab0ba;

  margin-bottom: 30px;

}


.qrBox {

  width: 320px;
  height: 320px;

  padding: 20px;

  background: white;

  border-radius: 25px;

  display: flex;

  justify-content: center;

  align-items: center;
}


#qrImage {

  width: 100%;
  height: 100%;

}


.qrNotice {

  margin-top: 25px;

  color: #7e8794;

  font-size: 14px;
}


.homeButton {

  margin-top: 30px;

  border: 1px solid
    rgba(255,255,255,.2);

  border-radius: 100px;

  background: transparent;

  color: white;

  padding: 16px 28px;

}


/* ================================
   LOADING
================================ */

#loading {

  position: fixed;

  inset: 0;

  z-index: 999;

  display: none;

  justify-content: center;

  align-items: center;

  flex-direction: column;

  background:
    rgba(0,0,0,.88);

  backdrop-filter:
    blur(10px);

}


.loader {

  width: 55px;
  height: 55px;

  border: 5px solid
    rgba(255,255,255,.2);

  border-top-color:
    white;

  border-radius: 50%;

  animation:
    spin .8s linear infinite;

}


@keyframes spin {

  to {
    transform: rotate(360deg);
  }

}


.loadingText {

  margin-top: 20px;

}


/* ================================
   TABLET
================================ */

@media
(max-width: 900px) {

  .themeGrid {

    grid-template-columns:
      repeat(2,1fr);

    max-width: 700px;

  }

  .themeCard {

    aspect-ratio: 4 / 3;

  }

}

</style>
</head>


<body>


<!-- ==================================
     THEME SELECT
=================================== -->

<section
  id="themeScreen"
  class="screen active"
>

  <div class="eyebrow">
    PHOTO EXPERIENCE
  </div>

  <h1>
    CHOOSE YOUR VIBE
  </h1>

  <div class="subtitle">
    원하는 테마를 선택해주세요.
  </div>


  <div class="themeGrid">


    <button
      class="themeCard"
      onclick="selectTheme('faker')"
    >

      <img
        src="./assets/faker/thumbnail.png"
        alt="FAKER"
      >

      <div class="themeLabel">
        FAKER
      </div>

    </button>


    <button
      class="themeCard"
      onclick="selectTheme('kda')"
    >

      <img
        src="./assets/kda/thumbnail.png"
        alt="KDA"
      >

      <div class="themeLabel">
        K/DA
      </div>

    </button>


    <button
      class="themeCard"
      onclick="selectTheme('heartsteel')"
    >

      <img
        src="./assets/heartsteel/thumbnail.png"
        alt="HEARTSTEEL"
      >

      <div class="themeLabel">
        HEARTSTEEL
      </div>

    </button>


    <button
      class="themeCard"
      onclick="selectTheme('pentakill')"
    >

      <img
        src="./assets/pentakill/thumbnail.png"
        alt="PENTAKILL"
      >

      <div class="themeLabel">
        PENTAKILL
      </div>

    </button>


  </div>

</section>



<!-- ==================================
     CAMERA
=================================== -->

<section
  id="cameraScreen"
  class="screen"
>

  <div id="cameraStage">


    <video
      id="camera"
      autoplay
      playsinline
      muted
    ></video>


    <!-- PNG들이 이 안에 생성됨 -->
    <div id="imageLayers"></div>


    <div class="cameraTop">

      <div
        id="themeBadge"
        class="themeBadge"
      >
      </div>

      <button
        class="changeTheme"
        onclick="goHome()"
      >
        ← THEME
      </button>

    </div>


    <div id="countdown">
      3
    </div>


    <div class="cameraControls">

      <button
        class="shootButton"
        onclick="startCountdown()"
        aria-label="사진 촬영"
      >
      </button>

    </div>


  </div>

</section>



<!-- ==================================
     RESULT
=================================== -->

<section
  id="resultScreen"
  class="screen"
>

  <div class="resultTitle">
    사진을 확인해주세요.
  </div>


  <canvas
    id="resultCanvas"
  ></canvas>


  <div class="resultButtons">

    <button
      class="secondaryButton"
      onclick="retake()"
    >
      다시 촬영
    </button>

    <button
      class="primaryButton"
      onclick="uploadPhoto()"
    >
      이 사진 사용
    </button>

  </div>

</section>



<!-- ==================================
     QR
=================================== -->

<section
  id="qrScreen"
  class="screen"
>

  <div class="qrTitle">
    YOUR PHOTO
  </div>

  <div class="qrDescription">
    QR 코드를 스캔하여 사진을 받아가세요.
  </div>


  <div class="qrBox">

    <img
      id="qrImage"
      alt="QR CODE"
    >

  </div>


  <div class="qrNotice">
    사진은 행사 운영 정책에 따라
    일정 시간 후 삭제될 수 있습니다.
  </div>


  <button
    class="homeButton"
    onclick="goHome()"
  >
    처음으로
  </button>

</section>



<!-- ==================================
     LOADING
=================================== -->

<div id="loading">

  <div class="loader"></div>

  <div class="loadingText">
    사진을 준비하고 있습니다...
  </div>

</div>



<!-- ==================================
     QR LIBRARY
=================================== -->

<script
src="https://cdn.jsdelivr.net/npm/qrcode@1.5.4/build/qrcode.min.js">
</script>



<!-- ==================================
     FIREBASE + APP
=================================== -->

<script type="module">


/* =====================================
   FIREBASE
===================================== */

import {
  initializeApp
}
from
"https://www.gstatic.com/firebasejs/12.4.0/firebase-app.js";


import {
  getStorage,
  ref,
  uploadBytes,
  getDownloadURL
}
from
"https://www.gstatic.com/firebasejs/12.4.0/firebase-storage.js";



/*
========================================
여기에 본인의 Firebase 설정을 넣으세요.

Firebase Console
→ Project Settings
→ Your apps
→ Web app
→ firebaseConfig
========================================
*/

const firebaseConfig = {

  apiKey:
    "YOUR_API_KEY",

  authDomain:
    "YOUR_PROJECT.firebaseapp.com",

  projectId:
    "YOUR_PROJECT_ID",

  storageBucket:
    "YOUR_PROJECT_ID.firebasestorage.app",

  messagingSenderId:
    "YOUR_MESSAGING_SENDER_ID",

  appId:
    "YOUR_APP_ID"

};



const firebaseApp =
  initializeApp(firebaseConfig);


const storage =
  getStorage(firebaseApp);



/* =====================================
   THEME SETTINGS

   ★ 여기만 수정하면
   이미지 / 위치 / 크기 변경 가능
===================================== */

const THEMES = {


  /* ============================
     FAKER
  ============================ */

  faker: {

    name:
      "FAKER",

    layers: [

      /*
      전체 프레임
      */

      {
        src:
          "./assets/faker/frame.png",

        x: 0,
        y: 0,

        width: 1,
        height: 1
      },


      /*
      장식 1
      */

      {
        src:
          "./assets/faker/effect01.png",

        x: 0.05,
        y: 0.04,

        width: 0.30
      },


      /*
      장식 2
      */

      {
        src:
          "./assets/faker/effect02.png",

        x: 0.62,
        y: 0.70,

        width: 0.30
      }

    ]

  },



  /* ============================
     KDA
  ============================ */

  kda: {

    name:
      "K/DA",

    layers: [

      {
        src:
          "./assets/kda/frame.png",

        x: 0,
        y: 0,

        width: 1,
        height: 1
      },


      {
        src:
          "./assets/kda/effect01.png",

        x: 0,
        y: 0,

        width: 1
      },


      {
        src:
          "./assets/kda/effect02.png",

        x: 0.65,
        y: 0.08,

        width: 0.25
      }

    ]

  },



  /* ============================
     HEARTSTEEL
  ============================ */

  heartsteel: {

    name:
      "HEARTSTEEL",

    layers: [

      {
        src:
          "./assets/heartsteel/frame.png",

        x: 0,
        y: 0,

        width: 1,
        height: 1
      },


      {
        src:
          "./assets/heartsteel/effect01.png",

        x: 0.03,
        y: 0.10,

        width: 0.25
      },


      {
        src:
          "./assets/heartsteel/effect02.png",

        x: 0.70,
        y: 0.58,

        width: 0.24
      }

    ]

  },



  /* ============================
     PENTAKILL
  ============================ */

  pentakill: {

    name:
      "PENTAKILL",

    layers: [

      {
        src:
          "./assets/pentakill/frame.png",

        x: 0,
        y: 0,

        width: 1,
        height: 1
      },


      {
        src:
          "./assets/pentakill/effect01.png",

        x: 0,
        y: 0.60,

        width: 1
      },


      {
        src:
          "./assets/pentakill/effect02.png",

        x: 0.30,
        y: 0.03,

        width: 0.40
      }

    ]

  }

};



/* =====================================
   VARIABLES
===================================== */

let selectedTheme = null;

let cameraStream = null;

let resetTimer = null;



/* =====================================
   SCREEN
===================================== */

function showScreen(id) {

  document
    .querySelectorAll(".screen")
    .forEach(screen => {

      screen.classList.remove(
        "active"
      );

    });


  document
    .getElementById(id)
    .classList.add(
      "active"
    );

}



/* =====================================
   THEME SELECT
===================================== */

window.selectTheme =
async function(themeKey) {

  selectedTheme =
    themeKey;


  document
    .getElementById(
      "themeBadge"
    )
    .textContent =
      THEMES[themeKey].name;


  loadThemePreview(
    themeKey
  );


  showScreen(
    "cameraScreen"
  );


  await startCamera();

};



/* =====================================
   PREVIEW PNG LAYERS
===================================== */

function loadThemePreview(
  themeKey
) {

  const container =
    document.getElementById(
      "imageLayers"
    );


  container.innerHTML = "";


  const theme =
    THEMES[themeKey];


  theme.layers.forEach(
    (layer, index) => {


      const image =
        document.createElement(
          "img"
        );


      image.src =
        layer.src;


      image.className =
        "photoLayer";


      image.style.left =
        `${layer.x * 100}%`;


      image.style.top =
        `${layer.y * 100}%`;


      image.style.width =
        `${layer.width * 100}%`;


      if (
        layer.height !== undefined
      ) {

        image.style.height =
          `${layer.height * 100}%`;

      }


      image.style.zIndex =
        index + 1;


      container.appendChild(
        image
      );

    }
  );

}



/* =====================================
   CAMERA
===================================== */

async function startCamera() {

  try {


    stopCamera();


    cameraStream =
      await navigator.mediaDevices
        .getUserMedia({

          video: {

            facingMode:
              "user",

            width: {
              ideal: 1920
            },

            height: {
              ideal: 1080
            }

          },

          audio: false

        });


    const video =
      document.getElementById(
        "camera"
      );


    video.srcObject =
      cameraStream;


    await video.play();


  }

  catch(error) {


    console.error(
      error
    );


    alert(
      "카메라를 사용할 수 없습니다.\n브라우저의 카메라 권한을 확인해주세요."
    );


  }

}



function stopCamera() {

  if (!cameraStream) {
    return;
  }


  cameraStream
    .getTracks()
    .forEach(track => {

      track.stop();

    });


  cameraStream = null;

}



/* =====================================
   COUNTDOWN
===================================== */

window.startCountdown =
function() {


  const countdown =
    document.getElementById(
      "countdown"
    );


  countdown.style.display =
    "flex";


  let number = 3;


  countdown.textContent =
    number;


  const timer =
    setInterval(() => {


      number--;


      if (number > 0) {


        countdown.textContent =
          number;


      }

      else {


        clearInterval(
          timer
        );


        countdown.textContent =
          "●";


        setTimeout(
          async () => {


            countdown.style.display =
              "none";


            await capturePhoto();


          },
          250
        );


      }


    }, 1000);

};



/* =====================================
   IMAGE LOADER
===================================== */

function loadImage(src) {

  return new Promise(
    (resolve, reject) => {


      const image =
        new Image();


      image.onload =
        () => resolve(image);


      image.onerror =
        reject;


      image.src =
        src;


    }
  );

}



/* =====================================
   DRAW OVERLAYS TO CANVAS
===================================== */

async function drawThemeLayers(
  ctx,
  canvasWidth,
  canvasHeight
) {


  const theme =
    THEMES[selectedTheme];


  for (
    const layer
    of theme.layers
  ) {


    try {


      const image =
        await loadImage(
          layer.src
        );


      const x =
        layer.x *
        canvasWidth;


      const y =
        layer.y *
        canvasHeight;


      const width =
        layer.width *
        canvasWidth;


      let height;


      if (
        layer.height !== undefined
      ) {


        height =
          layer.height *
          canvasHeight;


      }

      else {


        height =
          width *
          (
            image.naturalHeight /
            image.naturalWidth
          );


      }


      ctx.drawImage(
        image,
        x,
        y,
        width,
        height
      );


    }

    catch(error) {


      console.error(
        "Overlay load error:",
        layer.src,
        error
      );


    }


  }

}



/* =====================================
   CAPTURE PHOTO
===================================== */

async function capturePhoto() {


  const video =
    document.getElementById(
      "camera"
    );


  const canvas =
    document.getElementById(
      "resultCanvas"
    );


  /*
  촬영 결과 해상도
  */

  canvas.width =
    video.videoWidth ||
    1920;


  canvas.height =
    video.videoHeight ||
    1080;


  const ctx =
    canvas.getContext(
      "2d"
    );


  /*
  카메라 사진
  셀카처럼 좌우 반전
  */

  ctx.save();


  ctx.translate(
    canvas.width,
    0
  );


  ctx.scale(
    -1,
    1
  );


  ctx.drawImage(
    video,
    0,
    0,
    canvas.width,
    canvas.height
  );


  ctx.restore();


  /*
  PNG 프레임 합성
  */

  await drawThemeLayers(
    ctx,
    canvas.width,
    canvas.height
  );


  stopCamera();


  showScreen(
    "resultScreen"
  );

}



/* =====================================
   RETAKE
===================================== */

window.retake =
async function() {


  showScreen(
    "cameraScreen"
  );


  await startCamera();

};



/* =====================================
   CANVAS -> BLOB
===================================== */

function canvasToBlob(
  canvas
) {

  return new Promise(
    resolve => {


      canvas.toBlob(

        blob => {

          resolve(blob);

        },

        "image/jpeg",

        0.92

      );


    }
  );

}



/* =====================================
   UNIQUE ID
===================================== */

function createPhotoId() {


  const random =
    crypto.randomUUID();


  return (
    Date.now() +
    "-" +
    random
  );

}



/* =====================================
   FIREBASE UPLOAD
===================================== */

window.uploadPhoto =
async function() {


  const loading =
    document.getElementById(
      "loading"
    );


  loading.style.display =
    "flex";


  try {


    const canvas =
      document.getElementById(
        "resultCanvas"
      );


    const blob =
      await canvasToBlob(
        canvas
      );


    if (!blob) {

      throw new Error(
        "이미지를 생성하지 못했습니다."
      );

    }


    const photoId =
      createPhotoId();


    /*
    Firebase Storage 구조

    photos/
      faker/
      kda/
      heartsteel/
      pentakill/
    */


    const path =

      `photos/${selectedTheme}/${photoId}.jpg`;


    const storageReference =
      ref(
        storage,
        path
      );


    await uploadBytes(

      storageReference,

      blob,

      {

        contentType:
          "image/jpeg",

        customMetadata: {

          theme:
            selectedTheme,

          createdAt:
            new Date()
              .toISOString()

        }

      }

    );


    /*
    Firebase 다운로드 URL
    */

    const downloadURL =
      await getDownloadURL(
        storageReference
      );


    /*
    QR 생성
    */

    await createQRCode(
      downloadURL
    );


    loading.style.display =
      "none";


    showScreen(
      "qrScreen"
    );


    /*
    60초 후 자동 초기화
    */

    clearTimeout(
      resetTimer
    );


    resetTimer =
      setTimeout(
        () => {

          goHome();

        },
        60000
      );


  }

  catch(error) {


    console.error(
      error
    );


    loading.style.display =
      "none";


    alert(
      "사진 업로드 중 오류가 발생했습니다."
    );


  }

};



/* =====================================
   QR CODE
===================================== */

async function createQRCode(
  url
) {


  const qrImage =
    document.getElementById(
      "qrImage"
    );


  try {


    const qrDataURL =
      await QRCode.toDataURL(

        url,

        {

          width: 500,

          margin: 2,

          errorCorrectionLevel:
            "H"

        }

      );


    qrImage.src =
      qrDataURL;


  }

  catch(error) {


    console.error(
      "QR ERROR",
      error
    );


    throw error;


  }

}



/* =====================================
   HOME / RESET
===================================== */

window.goHome =
function() {


  clearTimeout(
    resetTimer
  );


  stopCamera();


  selectedTheme =
    null;


  document
    .getElementById(
      "imageLayers"
    )
    .innerHTML = "";


  document
    .getElementById(
      "qrImage"
    )
    .removeAttribute(
      "src"
    );


  showScreen(
    "themeScreen"
  );

};


</script>

</body>
</html>
