# BMI-CALCULATOR
# BMI Calculator using HTML, CSS and JS
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 400px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
            color: #333;
        }

        label {
            display: block;
            margin: 10px 0 5px;
        }

        input, select {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #218838;
        }

        .result {
            margin-top: 20px;
            text-align: center;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>BMI Calculator</h1>
        <form id="bmiForm">
            <label for="age">Age:</label>
            <input type="number" id="age" required>

            <label for="gender">Gender:</label>
            <select id="gender" required>
                <option value="" disabled selected>Select Gender</option>
                <option value="M">Male</option>
                <option value="F">Female</option>
            </select>

            <label for="weight">Weight (kg):</label>
            <input type="number" id="weight" required>

            <label for="height">Height (cm):</label>
            <input type="number" id="height" required>

            <button type="submit">Calculate BMI</button>
        </form>

        <div id="result" class="result"></div>
    </div>

    <script>
        document.getElementById('bmiForm').addEventListener('submit', function (event) {
            event.preventDefault(); // Prevent form submission

            // Get input values
            const age = parseInt(document.getElementById('age').value);
            const gender = document.getElementById('gender').value;
            const weight = parseFloat(document.getElementById('weight').value);
            const heightCm = parseFloat(document.getElementById('height').value);

            // Convert height from cm to meters
            const heightM = heightCm / 100;

            // Calculate BMI
            const bmi = weight / (heightM ** 2);
            const category = getBMICategory(bmi);

            // Display result
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `Your BMI is: <strong>${bmi.toFixed(2)}</strong><br>You are classified as: <strong>${category}</strong>`;
        });

        // Function to determine BMI category
        function getBMICategory(bmi) {
            if (bmi < 18.5) {
                return "Underweight";
            } else if (bmi < 24.9) {
                return "Normal weight";
            } else if (bmi < 29.9) {
                return "Overweight";
            } else {
                return "Obesity";
            }
        }
    </script>
</body>
</html>
