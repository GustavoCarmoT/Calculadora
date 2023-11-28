# Calculadora
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora</title>
  <style>
    input, button {
      margin: 5px;
      padding: 10px;
      font-size: 16px;
    }
  </style>
</head>
<body>

  <h2>Calculadora</h2>

  <input type="text" id="display" disabled>

  <br>

  <button onclick="appendToDisplay('1')">1</button>
  <button onclick="appendToDisplay('2')">2</button>
  <button onclick="appendToDisplay('3')">3</button>
  <button onclick="setOperation('+')">+</button>

  <br>

  <button onclick="appendToDisplay('4')">4</button>
  <button onclick="appendToDisplay('5')">5</button>
  <button onclick="appendToDisplay('6')">6</button>
  <button onclick="setOperation('-')">-</button>

  <br>

  <button onclick="appendToDisplay('7')">7</button>
  <button onclick="appendToDisplay('8')">8</button>
  <button onclick="appendToDisplay('9')">9</button>
  <button onclick="setOperation('*')">*</button>

  <br>

  <button onclick="appendToDisplay('0')">0</button>
  <button onclick="clearDisplay()">C</button>
  <button onclick="calculateResult()">=</button>
  <button onclick="setOperation('/')">/</button>

  <script>
    let display = document.getElementById('display');
    let currentInput = '';
    let currentOperation = '';
    let firstOperand = '';

    function appendToDisplay(value) {
      currentInput += value;
      display.value = currentInput;
    }

    function clearDisplay() {
      currentInput = '';
      display.value = '';
    }

    function setOperation(operation) {
      currentOperation = operation;
      firstOperand = currentInput;
      currentInput = '';
    }

    function calculateResult() {
      let result;
      const secondOperand = currentInput;

      switch (currentOperation) {
        case '+':
          result = parseFloat(firstOperand) + parseFloat(secondOperand);
          break;
        case '-':
          result = parseFloat(firstOperand) - parseFloat(secondOperand);
          break;
        case '*':
          result = parseFloat(firstOperand) * parseFloat(secondOperand);
          break;
        case '/':
          result = parseFloat(firstOperand) / parseFloat(secondOperand);
          break;
        default:
          result = 'Error';
      }

      display.value = result;
      currentInput = result.toString();
      currentOperation = '';
    }
  </script>

</body>
</html>
