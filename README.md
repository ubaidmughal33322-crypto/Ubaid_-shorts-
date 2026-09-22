index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, initial-scale=1.0">
  <title>Ubaid Shorts</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      background: #000;
      color: white;
      font-family: Arial, sans-serif;
    }

    .video-box {
      height: 100vh;
      width: 100%;
      position: relative;
      overflow: hidden;
      background: #111;
    }

    video {
      width: 100%;
      height: 100%;
      object-fit: contain;
    }

    .info {
      position: absolute;
      bottom: 90px;
      left: 15px;
      text-shadow: 1px 1px 4px black;
    }

    .buttons {
      position: absolute;
      right: 15px;
      bottom: 120px;
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    button, .upload {
      color: white;
      background: #252525;
      border: 0;
      border-radius: 10px;
      padding: 12px;
      font-size: 16px;
      cursor: pointer;
    }

    .upload {
      display: inline-block;
      margin-top: 8px;
    }

    #videoUpload {
      display: none;
    }

    .nav {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 60px;
      background: #111;
      display: flex;
      justify-content: space-around;
      align-items: center;
    }
  </style>
</head>

<body>

  <div class="video-box">

    <video id="myVideo" controls loop playsinline>
      <source
        src="https://www.w3schools.com/html/mov_bbb.mp4"
        type="video/mp4">
    </video>

    <div class="info">
      <h2>🎬 Ubaid Shorts</h2>
      <p>@Ubaid</p>
      <p>My first short video</p>

      <label for="videoUpload" class="upload">
        ➕ Upload Short
      </label>

      <input
        type="file"
        id="videoUpload"
        accept="video/*">
    </div>

    <div class="buttons">
      <button id="likeBtn">❤️ Like 0</button>
      <button onclick="alert('Comment feature coming soon!')">
        💬 Comment
      </button>
      <button onclick="shareVideo()">↗️ Share</button>
    </div>

    <div class="nav">
      <span>🏠 Home</span>
      <span>🔍 Search</span>
      <span>➕ Upload</span>
      <span>👤 Profile</span>
    </div>

  </div>

  <script>
    const video = document.getElementById("myVideo");
    const fileInput = document.getElementById("videoUpload");
    const likeBtn = document.getElementById("likeBtn");

    let likes = 0;

    fileInput.addEventListener("change", function () {
      const file = this.files[0];

      if (file) {
        video.src = URL.createObjectURL(file);
        video.load();
        video.play();
      }
    });

    likeBtn.addEventListener("click", function () {
      likes++;
      likeBtn.textContent = "❤️ Like " + likes;
    });

    function shareVideo() {
      if (navigator.share) {
        navigator.share({
          title: "Ubaid Shorts",
          text: "Check out my short video!"
        });
      } else {
        alert("Share option is not available in this browser.");
      }
    }
  </script>

</body>
</html>
