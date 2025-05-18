<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Number Predictor</title>
</head>
<body>
<h2>Number Sequence Predictor</h2>
<p>Enter a sequence of numbers separated by commas (e.g., 2, 4, 6):</p>
<input type="text" id="numberInput" placeholder="Enter numbers">
<button onclick="predictNext()">Predict Next Number</button>
<h3 id="result"></h3>

<script>
function predictNext() {
const input = document.getElementById("numberInput").value;
const numbers = input.split(',').map(num => parseFloat(num.trim()));

if (numbers.length < 2 || numbers.some(isNaN)) {
document.getElementById("result").innerText = "Please enter at least two valid numbers.";
return;
}

// Try to detect a pattern (assumes arithmetic sequence)
const diffs = [];
for (let i = 1; i < numbers.length; i++) {
diffs.push(numbers[i] - numbers[i - 1]);
}

const avgDiff = diffs.reduce((a, b) => a + b, 0) / diffs.length;
const next = numbers[numbers.length - 1] + avgDiff;

document.getElementById("result").innerText = `Predicted next number: ${next}`;
}
</script>
</body>
</html>
