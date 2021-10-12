# virtual-assistant-
VOICEAPP.HTML
<!DOCTYPE html>
<html>
  <head>
    <title>Voice Recognition</title>
    <link rel="stylesheet" href="light-mode.css" id="styleSheet" />
  </head>

  <body>
    <button id="speakBtn">Speak Now</button>
    <script src="./index.js"></script>
  </body>
</html>

DARK-MODE.CSS

* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  
  body {
    height: 100vh;
    width: 100vw;
    background-color: black;
    color: white;
  }
  
  #speakBtn {
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 0.5rem 1rem;
  }
  
  
  LIGHT-MODE.CSS
  
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  
  body {
    height: 100vh;
    width: 100vw;
    background-color: white;
    color: black;
  }
  
  #speakBtn {
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 0.5rem 1rem;
  }
  
  
  
  
  
  INDEX.JS
  const speakBtn = document.getElementById("speakBtn");
speakBtn.addEventListener("click", speakNow);

const styleSheet = document.getElementById("styleSheet");

// SpeechRecognition

const SpeechRecognition =
  window.SpeechRecognition || window.webkitSpeechRecognition;

const recognition = new SpeechRecognition();

recognition.onstart = function () {
  console.log("Started..");
};

recognition.onresult = function (e) {
  const resultIndex = e.resultIndex;

  const { transcript } = e.results[resultIndex][0];
  console.log(transcript);
  speakOutLoud(transcript);
};

function speakNow() {
  recognition.start();
}

function speakOutLoud(message) {
  let whatToSpeak = message;

  if (whatToSpeak.includes("dark mode")) {
    styleSheet.setAttribute("href", "dark-mode.css");
  } else if (whatToSpeak.includes("light mode")) {
    styleSheet.setAttribute("href", "light-mode.css");
  } else if (whatToSpeak.includes("open YouTube")) {
    window.open("https://youtube.com", "_blank");
  } else if (whatToSpeak.includes("open Google")) {
      window.open("https://google.com", "_blank");
  } else if(whatToSpeak.includes("open Air India")) {
    window.open("https://airindia.in", "_blank");
  } else if(whatToSpeak.includes("open Wikipedia")) {
    window.open("https://wikipedia.org", "_blank");
  }else if(whatToSpeak.includes("play music")) {
    window.open("https://youtube.com/watch?v=q0BVR5jRXxE", "_blank");
  }else if(whatToSpeak.includes(" open tarak mehta  ka ooltah chashma")) {
    window.open("https://youtube.com/results?search_query=taarak+mehta+ka+ulta+chashma", "_blank");
  }
  // The action of saying or expressing something aloud..
  const SpeechSynthesisUtterance =
    window.SpeechSynthesisUtterance || window.webkitSpeechSynthesisUtterance;

  const utterance = new SpeechSynthesisUtterance();

  utterance.volume = 1; // 100%
  utterance.rate = 1;
  utterance.pitch = 1;
  utterance.text = whatToSpeak;

  // Artificial production of human speech
  const speechSynthesis =
    window.speechSynthesis || window.webkitspeechSynthesis;

  speechSynthesis.speak(utterance);
}
