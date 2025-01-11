<!DOCTYPE html>
<html>
<head>
  <title>AI Smart Calculator</title>
  <style>
    #calculator {
      width: 400px;
      padding: 20px;
      background-color: #f1f1f1;
      border-radius: 10px;
      font-family: Arial, sans-serif;
    }
    #calculator input, #calculator button {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      font-size: 16px;
    }
    #result {
      font-size: 24px;
      font-weight: bold;
      text-align: right;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <h1>AI Smart Calculator</h1>
  <div id="calculator">
    <input type="text" id="equation" placeholder="Enter an equation">
    <button onclick="calculateEquation()">Calculate</button>
    <div id="result"></div>
  </div>

  <script>
    function calculateEquation() {
      const equationInput = document.getElementById('equation');
      const equation = equationInput.value.trim();

      if (equation) {
        try {
          const result = evaluate(equation);
          document.getElementById('result').textContent = result;
        } catch (error) {
          document.getElementById('result').textContent = 'Error: Invalid equation';
        }
      } else {
        document.getElementById('result').textContent = '';
      }
    }

    function evaluate(equation) {
      // Use a math.js-like library to evaluate the equation
      const math = {
        add: (a, b) => a + b,
        subtract: (a, b) => a - b,
        multiply: (a, b) => a * b,
        divide: (a, b) => a / b,
        pow: (a, b) => a ** b,
        sqrt: Math.sqrt,
        sin: Math.sin,
        cos: Math.cos,
        tan: Math.tan,
        // Add more math functions as needed
      };

      // Use the math object to evaluate the equation
      return Function(`'use strict'; return (${equation});`).call(math);
    }
  </script>
</body>
</html>
