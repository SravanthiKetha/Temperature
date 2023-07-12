# Temperature
<!DOCTYPE html>
<html>
<head>
  <title>Temperature Converter</title>
  <style>
    .container {
      margin: 20px;
    }
    label {
      display: block;
      margin-bottom: 10px;
    }
    input[type="text"] {
      padding: 5px;
      width: 150px;
    }
    select {
      padding: 5px;
      width: 150px;
    }
    button {
      padding: 5px 10px;
    }
    #result {
      margin-top: 10px;
      font-weight: bold;
    }
  </style>
  <script>
    function convertTemperature() {
      var temperatureInput = document.getElementById("temperature").value;
      var unitSelect = document.getElementById("unit");
      var selectedUnit = unitSelect.options[unitSelect.selectedIndex].value;

      if (!isNumeric(temperatureInput)) {
        alert("Invalid temperature input. Please enter a number.");
        return;
      }

      var temperature = parseFloat(temperatureInput);
      var convertedTemp;
      var convertedUnit;

      if (selectedUnit === "celsius") {
        convertedTemp = (temperature - 32) * 5 / 9;
        convertedUnit = "°C";
      } else if (selectedUnit === "fahrenheit") {
        convertedTemp = (temperature * 9 / 5) + 32;
        convertedUnit = "°F";
      } else if (selectedUnit === "kelvin") {
        convertedTemp = temperature + 273.15;
        convertedUnit = "K";
      }

      var resultDisplay = document.getElementById("result");
      resultDisplay.textContent = "Converted Temperature: " + convertedTemp.toFixed(2) + " " + convertedUnit;
    }

    function isNumeric(value) {
      return !isNaN(parseFloat(value)) && isFinite(value);
    }
  </script>
</head>
<body>
  <div class="container">
    <h2>Temperature Converter</h2>
    <label>Temperature:</label>
    <input type="text" id="temperature" placeholder="Enter temperature" required>
    <label>Unit:</label>
    <select id="unit">
      <option value="celsius">Celsius</option>
      <option value="fahrenheit">Fahrenheit</option>
      <option value="kelvin">Kelvin</option>
    </select>
    <button onclick="convertTemperature()">Convert</button>
    <div id="result"></div>
  </div>
</body>
</html>
