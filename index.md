---
title: 1. Single file
description: test website
---

<body>
  <h2>Talk to the API</h2>
  <input type="text" id="userInput" placeholder="Enter input here" />
  <button onclick="callAPI()">Submit</button>
  <p id="result">Output will appear here...</p>

  <script>
    async function callAPI() {
      const input = document.getElementById("userInput").value;
      const response = await fetch("https://tilschmittulms-minimal.hf.space/api/predict", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({ data: [input] })
      });

      const json = await response.json();
      const output = json.data?.[0];
      document.getElementById("result").innerText = "Output: " + output;
    }
  </script>
</body>
