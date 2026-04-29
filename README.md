<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Logic Simulator</title>

<style>
body {
    font-family: Arial;
    background: #f0f2f5;
    text-align: center;
}

.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    padding: 20px;
}

.card {
    background: white;
    padding: 20px;
    border-radius: 15px;
    width: 280px;
    box-shadow: 0 5px 10px rgba(0,0,0,0.1);
}

button {
    padding: 10px;
    margin: 5px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
}

.led {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin: 10px auto;
    background: gray;
}

.on { background: limegreen; }
.off { background: gray; }

.and { border-top: 5px solid green; }
.or { border-top: 5px solid blue; }
.not { border-top: 5px solid purple; }

</style>
</head>

<body>

<h1>⚡ Mantiqiy elementlar simulatori</h1>

<div class="container">

<!-- AND -->
<div class="card and">
<h2>AND (VA)</h2>
<button onclick="toggle('andA')">A</button>
<button onclick="toggle('andB')">B</button>

<div id="andLED" class="led off"></div>
</div>

<!-- OR -->
<div class="card or">
<h2>OR (YOKI)</h2>
<button onclick="toggle('orA')">A</button>
<button onclick="toggle('orB')">B</button>

<div id="orLED" class="led off"></div>
</div>

<!-- NOT -->
<div class="card not">
<h2>NOT (INKOR)</h2>
<button onclick="toggle('notA')">Sensor</button>

<div id="notLED" class="led on"></div>
</div>

</div>

<script>
let state = {
    andA: 0, andB: 0,
    orA: 0, orB: 0,
    notA: 1
};

function toggle(key) {
    state[key] = state[key] ? 0 : 1;
    update();
}

function update() {
    // AND
    let andOut = state.andA && state.andB;
    setLED("andLED", andOut);

    // OR
    let orOut = state.orA || state.orB;
    setLED("orLED", orOut);

    // NOT
    let notOut = !state.notA;
    setLED("notLED", notOut);
}

function setLED(id, value) {
    let el = document.getElementById(id);
    el.className = "led " + (value ? "on" : "off");
}

// initial update
update();
</script>

</body>
</html>
