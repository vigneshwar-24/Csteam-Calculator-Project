# Csteam-Calculator-Project
```
Name: Vigneshwar S
Reg No:212220230058
Dept: AI&DS
```
## HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="cal.css">
    <title>Calculator</title>
</head>
<body>
    <div class="main">
        <input type="text" id="res">
        <div class="btn">
            <input type="button" value='C' onclick="Clear()">
            <input type="button" value='%' onclick="Solve('%')">
            <input type="button" value='←' onclick="Back()">
            <input type="button" value='/' onclick="Solve('/')">
            <br>
            <input type="button" value='7' onclick="Solve('7')">
            <input type="button" value='8' onclick="Solve('8')">
            <input type="button" value='9' onclick="Solve('9')">
            <input type="button" value='*' onclick="Solve('*')">
            <br>
            <input type="button" value='4' onclick="Solve('4')">
            <input type="button" value='5' onclick="Solve('5')">
            <input type="button" value='6' onclick="Solve('6')">
            <input type="button" value='-' onclick="Solve('-')">
            <br>
            <input type="button" value='1' onclick="Solve('1')">
            <input type="button" value='2' onclick="Solve('2')">
            <input type="button" value='3' onclick="Solve('3')">
            <input type="button" value='+' onclick="Solve('+')">
            <br>
            <input type="button" value='0' onclick="Solve('0')">
            <input type="button" value='.' onclick="Solve('.')">
            <input type="button" value='^' onclick="Solve('**')">
            <input type="button" value='=' onclick="Result()">
        </div>
    </div>
    <div class="history">
        <h2>History Of Your Calculation:</h2>
        <textarea id="history" readonly></textarea>
    </div>
    <script src='calculator.js'></script>
</body>
</html>
```
## CSS
```
* {
    padding: 0;
    margin: 0;
    font-family: 'poppins', sans-serif;
}

body {
    background-color: #495250;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
}

.main {
    width: 400px;
    background-color: #FFFFFF;
    border-radius: 6px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

.main input[type='text'] {
    width: 90%;
    height: 80px;
    text-align: right;
    padding: 3px 6px;
    outline: none;
    font-size: 40px;
    border: 1px solid #ccc;
    border-radius: 40px; 
    margin-bottom: 10px;
}

.btn input[type='button'] {
    width: 90px;
    padding: 2px;
    margin: 2px;
    height: 60px;
    cursor: pointer;
    font-size: 18px;
    transition: 0.5s;
    background-color: #495250;
    border: none;
    border-radius: 6px;
    color: white;
}

.btn input[type='button']:hover {
    background-color: black;
}

.history {
    margin-top: 20px;
    text-align: center;
}

.history h2 {
    color: rgb(246, 210, 210);
}

textarea {
    width: 90%;
    height: 150px;
    max-height: 150px; /* Set a maximum height to make it constant size */
    padding: 5px;
    font-size: 14px;
    border-radius: 6px;
    border: 1px solid #FFD700;
    background-color: #f9f9f9;
    resize: none;
    overflow-y: scroll;
}
```
## JAVA SCRIPT
```
let history = [];
let currentExpression = '';

function Solve(val) {
    var v = document.getElementById('res');
    v.value += val;
}

function Result() {
    var num1 = document.getElementById('res').value;
    try {
        var num2 = eval(num1);
        if (isNaN(num2) || !isFinite(num2)) {
            throw new Error("Invalid input");
        }
        history.push(`${num1} = ${num2}`);
        if (history.length > 10) {
            history.shift();
        }
        updateHistoryDisplay();
        document.getElementById('res').value = num2;
    } catch (error) {
        document.getElementById('res').value = 'Error';
    }
}

function Clear() {
    var inp = document.getElementById('res');
    inp.value = '';
}

function Back() {
    var ev = document.getElementById('res');
    ev.value = ev.value.slice(0, -1);
}

function updateHistoryDisplay() {
    document.getElementById('history').value = history.join('\n');
}
```
