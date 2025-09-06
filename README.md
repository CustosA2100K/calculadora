<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Calculadora Rojo, Azul y Blanco</title>
    <style>
        body {
            background: #fff;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .calculadora {
            background: #fff;
            border: 3px solid #0074D9;
            border-radius: 12px;
            box-shadow: 0 4px 16px rgba(0,0,0,0.1);
            padding: 24px;
            width: 320px;
        }
        .pantalla {
            background: #fff;
            color: #0074D9;
            border: 2px solid #FF4136;
            border-radius: 6px;
            font-size: 2em;
            padding: 12px;
            margin-bottom: 16px;
            text-align: right;
            width: 100%;
            box-sizing: border-box;
        }
        .botones {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        button {
            font-size: 1.2em;
            padding: 16px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: background 0.2s;
        }
        .rojo { background: #FF4136; color: #fff; }
        .azul { background: #0074D9; color: #fff; }
        .blanco { background: #fff; color: #0074D9; border: 2px solid #0074D9; }
        button:active { opacity: 0.8; }
    </style>
</head>
<body>
    <div class="calculadora">
        <input type="text" class="pantalla" id="pantalla" value="0" disabled>
        <div class="botones">
            <button class="blanco" onclick="agregar('7')">7</button>
            <button class="blanco" onclick="agregar('8')">8</button>
            <button class="blanco" onclick="agregar('9')">9</button>
            <button class="azul" onclick="agregar('/')">÷</button>
            <button class="blanco" onclick="agregar('4')">4</button>
            <button class="blanco" onclick="agregar('5')">5</button>
            <button class="blanco" onclick="agregar('6')">6</button>
            <button class="azul" onclick="agregar('*')">×</button>
            <button class="blanco" onclick="agregar('1')">1</button>
            <button class="blanco" onclick="agregar('2')">2</button>
            <button class="blanco" onclick="agregar('3')">3</button>
            <button class="azul" onclick="agregar('-')">−</button>
            <button class="blanco" onclick="agregar('0')">0</button>
            <button class="blanco" onclick="agregar('.')">.</button>
            <button class="rojo" onclick="limpiar()">C</button>
            <button class="azul" onclick="agregar('+')">+</button>
            <button class="rojo" style="grid-column: span 4;" onclick="calcular()">=</button>
        </div>
    </div>
    <script>
        let pantalla = document.getElementById('pantalla');
        let operacion = '';

        function agregar(valor) {
            if (pantalla.value === '0' && valor !== '.') {
                pantalla.value = valor;
            } else {
                pantalla.value += valor;
            }
            operacion = pantalla.value;
        }

        function limpiar() {
            pantalla.value = '0';
            operacion = '';
        }

        function calcular() {
            try {
                let resultado = eval(pantalla.value.replace(/÷/g, '/').replace(/×/g, '*').replace(/−/g, '-'));
                pantalla.value = resultado;
                operacion = resultado;
            } catch {
                pantalla.value = 'Error';
                operacion = '';
            }
        }
    </script>
</body>
</html>
