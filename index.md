---
title: 1. Single file
description: test website
---

<input id="text-input" type="text" placeholder="Enter your text">
<button onclick="submitText()">Submit</button>
<div id="results"></div>

<script>
  async function submitText() {
    const input = document.getElementById("text-input").value;

    const response = await fetch("https://tilschmittulms-minimal.hf.space/api/predict", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ data: [input] })
    });

    const json = await response.json();
    const result = json.data[0]; // Assuming the output is a single string
    document.getElementById("results").innerHTML = `<p>Result: ${result}</p>`;
  }
</script>
