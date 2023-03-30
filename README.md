# cronometroJavascriptHTMLCSS
code of a cronometer on javascript/código de um cronômetro em javascript

//HTML PART/parte do HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    
    <link rel="stylesheet" href="assets/styles.css">

</head>
<body>
    <div class="container">
        <h1 id="watch">00:00:00</h1>
        <button class="inicio-btn" onclick="inicio()">Inicio</button>
        <button class="pausa-btn" onclick="pause()">Pausa</button>
        <button class="zerar-btn" onclick="clearAll()">Zerar</button>
    </div>

    <script src="assets/script.js"></script>
    
</body>
</html>

//JAVASCRIPT PART/parte do javascript
const watchDocument = document.querySelector("#watch");

let seconds = 0;
let minutes = 0;
let hours = 0;
let interval;

function inicio () {
    watch();
    interval = setInterval(watch, 100);
}

const pause = () => {
    clearInterval(interval)
}

const clearAll = () => {
    clearInterval(interval);
    seconds = 0;
    minutes = 0;
    hours = 0;
    watchDocument.innerHTML = "00:00:00";
}

const digitZero = (digit) => {
    if (digit < 10) {
        return "0" + digit;
    } else{
        return digit;
    }
}

function watch() {

    seconds ++;
    
    if (seconds === 60) {
        minutes ++;
        seconds = 0;
    } 

    if (minutes === 60) {
        minutes = 0;
        hours ++;
    } 

    watchDocument.innerHTML = digitZero(hours) + ":" + digitZero(minutes) + ":" + digitZero(seconds);

}

//CSS PART/parte do css
body{
    background: gainsboro;
    color: black;
}

.container {
    margin: 0 auto;
    text-align: center;
    max-width: 1000px;

}

button {
    height: 2.3em;
    width: 5.5em;
    border: none;
    color: black;
    border: 1px solid gray;
    cursor: pointer;
}

.inicio-btn {
    background-color: greenyellow;
}
.pausa-btn {
    background-color: lightskyblue;
}
.zerar-btn {
    background-color: lightcoral;
}

//FIM
