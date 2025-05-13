<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Maki Web - Proposal</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Helvetica, Arial, sans-serif;
      background: url('background.jpg') no-repeat center center fixed;
      background-size: cover;
    }

    .container {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .login-box {
      background: white;
      padding: 30px;
      width: 380px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      border-radius: 8px;
      text-align: center;
    }

    .login-box h1 {
      color: #1877f2;
      font-size: 36px;
      margin-bottom: 20px;
    }

    .login-box p {
      font-size: 20px;
      margin-bottom: 30px;
    }

    .login-box input {
      width: 100%;
      padding: 14px;
      margin: 8px 0;
      border: 1px solid #ddd;
      border-radius: 6px;
      font-size: 16px;
    }

    .login-box button {
      width: 100%;
      background: #1877f2;
      color: white;
      font-weight: bold;
      padding: 14px;
      border: none;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 10px;
    }

    .login-box button:hover {
      background: #165cdb;
    }

    .proposal-container {
      display: none;
      padding: 60px 20px;
      text-align: center;
      color: #ff4081;
      font-size: 24px;
      font-weight: bold;
      background-color: rgba(255,255,255,0.9);
      min-height: 100vh;
    }

    #proposalText {
      animation: fadeIn 2s ease-in-out forwards;
      opacity: 0;
      max-width: 700px;
      margin: 0 auto;
      white-space: pre-wrap;
    }

    button.proposal-btn {
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      font-size: 18px;
      cursor: pointer;
      margin-top: 30px;
      background-color: #28a745;
      color: white;
      box-shadow: 0 0 15px rgba(255, 0, 0, 0.5);
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }
  </style>
</head>
<body>

<!-- Background Music -->
<audio autoplay loop id="bgMusic">
  <source src="where-were-going.mp3" type="audio/mp3">
  Your browser does not support the audio tag.
</audio>

<!-- Login Page -->
<div class="container" id="loginPage">
  <div class="login-box">
    <h1>Maki Web</h1>
    <p>Log in to continue</p>
    <input type="text" id="username" placeholder="Username" />
    <input type="password" id="password" placeholder="Password" />
    <button onclick="login()">Log In</button>
  </div>
</div>

<!-- Proposal Page -->
<div class="proposal-container" id="proposalPage">
  <div id="proposalText"></div>
  <button class="proposal-btn" onclick="sayYes()">Yes 💍</button>
</div>

<script>
  const users = {
    "Tyri": "0452",
    "Maki": "112621",
    "Sample": "0000",
    "Pam": "0000"
  };

  const message = `I've loved you since I can't remember when,
and I'm gonna love you till I can't forget how.

Will you marry me?`;

  let i = 0;
  const speed = 40;

  function typeProposal() {
    const textBox = document.getElementById("proposalText");
    if (i < message.length) {
      textBox.innerHTML += message.charAt(i);
      i++;
      setTimeout(typeProposal, speed);
    }
  }

  function login() {
    const user = document.getElementById("username").value.trim();
    const pass = document.getElementById("password").value.trim();

    if (users[user] && users[user] === pass) {
      document.getElementById("loginPage").style.display = "none";
      document.getElementById("proposalPage").style.display = "block";
      typeProposal();
      document.getElementById("bgMusic").play();
    } else {
      alert("Incorrect username or password.");
    }
  }

  function sayYes() {
    alert("💖 She said YES! 💍💖");
  }
</script>

</body>
</html>
