<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Student Portal - Prediction App</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #eef2f7;
            margin: 0;
        }

        header {
            background: #2563eb;
            color: white;
            text-align: center;
            padding: 20px;
        }

        .container {
            width: 400px;
            background: white;
            margin: 40px auto;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.15);
        }

        h2 {
            text-align: center;
            color: #2563eb;
        }

        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }

        input, select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            width: 100%;
            margin-top: 25px;
            padding: 12px;
            background: #2563eb;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }

        button:hover {
            background: #1d4ed8;
        }

        #result {
            margin-top: 20px;
            padding: 15px;
            text-align: center;
            font-size: 18px;
            font-weight: bold;
            border-radius: 5px;
        }
    </style>
</head>

<body>

<header>
    <h1>Student Portal</h1>
    <p>Student Performance Prediction</p>
</header>

<div class="container">

    <h2>Prediction Form</h2>

    <label>Student Name</label>
    <input type="text" id="name" placeholder="Enter student name">

    <label>Attendance (%)</label>
    <input type="number" id="attendance" placeholder="Example: 80">

    <label>Study Hours per Day</label>
    <input type="number" id="study" placeholder="Example: 4">

    <label>Previous Marks (%)</label>
    <input type="number" id="marks" placeholder="Example: 65">

    <button onclick="predict()">Predict Result</button>

    <div id="result"></div>

</div>

<script>

function predict() {

    let name = document.getElementById("name").value;
    let attendance = Number(document.getElementById("attendance").value);
    let study = Number(document.getElementById("study").value);
    let marks = Number(document.getElementById("marks").value);

    if (name === "" || attendance === 0 || study === 0 || marks === 0) {
        document.getElementById("result").innerHTML =
            "Please enter all details.";
        return;
    }

    let score = 0;

    // Attendance prediction
    if (attendance >= 75) {
        score++;
    }

    // Study hours prediction
    if (study >= 3) {
        score++;
    }

    // Previous marks prediction
    if (marks >= 40) {
        score++;
    }

    let result = document.getElementById("result");

    if (score >= 2) {

        result.style.background = "#dcfce7";
        result.style.color = "#166534";

        result.innerHTML =
            "Hello " + name +
            "!<br>Prediction: Likely to Pass ✅";

    } else {

        result.style.background = "#fee2e2";
        result.style.color = "#991b1b";

        result.innerHTML =
            "Hello " + name +
            "!<br>Prediction: Needs Improvement ⚠️";
    }
}

</script>

</body>
</html>D
