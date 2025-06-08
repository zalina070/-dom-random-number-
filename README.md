# -dom-random-number-
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Random Number Generator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      flex-direction: column;
    }

    .container {
      background-color: rgb(207, 125, 152);
      text-align: center;
      border: 1px solid #ccc;
      padding: 70px;
      border-radius: 5px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    }

    .result {
      font-size: 24px;
      margin: 20px 0;
      min-height: 36px;
    }

    .controls {
      margin: 20px 0;
      display: flex;
      flex-direction: column;
      gap: 10px;
      align-items: center;
    }

    .input-group {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    input {
      width: 60px;
      padding: 5px;
    }

    button {
      padding: 8px 15px;
      margin: 0 5px;
      cursor: pointer;
      border: none;
      border-radius: 4px;
    }

    #generate {
      background-color: red;
      color: white;
    }
  </style>
</head>

<body>
  <div class="container">
    <h2>Your random number is:</h2>
    <div class="result" id="result"></div>

    <div class="controls">
      <div class="input-group">
        <label for="lower">Lower limit</label>
        <input type="number" id="lower" value="3" />
      </div>
      <div class="input-group">
        <label for="upper">Upper limit</label>
        <input type="number" id="upper" value="15" />
      </div>
    </div>

    <div class="buttons">
      <button id="generate">Generate</button>
      <button id="clear">Clear</button>
    </div>
  </div>

  <script>
    document.addEventListener('DOMContentLoaded', function () {
      const resultElement = document.getElementById('result');
      const generateButton = document.getElementById('generate');
      const clearButton = document.getElementById('clear');
      const lowerInput = document.getElementById('lower');
      const upperInput = document.getElementById('upper');

      generateButton.addEventListener('click', function () {
        const lower = parseInt(lowerInput.value);
        const upper = parseInt(upperInput.value);

        if (isNaN(lower) || isNaN(upper)) {
          resultElement.textContent = 'Please enter valid numbers';
          return;
        }

        if (lower >= upper) {
          resultElement.textContent = 'Lower limit must be less than upper limit';
          return;
        }

        const randomNumber = Math.floor(Math.random() * (upper - lower + 1)) + lower;
        resultElement.textContent = randomNumber;
      });

      clearButton.addEventListener('click', function () {
        resultElement.textContent = '';
      });
    });
  </script>
</body>

</html>
