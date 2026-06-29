# FIT-CONTROL
PAGINA ESPECIALIZADA PARA VER TU PROGRESO EN EL GYM
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>FIT CONTROL</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; background: #f4f4f4; }
    h1 { text-align: center; color: #007bff; margin-bottom: 5px; }
    h3 { text-align: center; color: #555; font-size: 14px; margin-top: 0; }
    section { background: #fff; padding: 20px; margin-bottom: 20px; border-radius: 8px; }
    label { display: block; margin-top: 10px; }
    input, select, textarea { width: 100%; padding: 8px; margin-top: 5px; }
    button { margin-top: 15px; padding: 10px 20px; background: #007bff; color: #fff; border: none; border-radius: 5px; cursor: pointer; }
    button:hover { background: #0056b3; }
    .resultado { margin-top: 10px; font-weight: bold; }
    .ejercicios { margin-top: 15px; }
    .dia { margin-bottom: 10px; }
    canvas { margin-top: 20px; }
  </style>
</head>
<body>
  <h1>FIT CONTROL</h1>
  <h3>entrena, mide, progresa</h3>

  <!-- Login / Registro -->
  <section>
    <h2>Login / Registro</h2>
    <label for="usuario">Usuario:</label>
    <input type="text" id="usuario">
    <label for="clave">Contraseña:</label>
    <input type="password" id="clave">
    <button onclick="registrar()">Registrar</button>
    <button onclick="login()">Login</button>
    <div id="mensajeLogin"></div>
  </section>

  <!-- Sección IMC -->
  <section>
    <h2>Calculadora de IMC</h2>
    <label for="peso">Peso (kg):</label>
    <input type="number" id="peso" placeholder="Ej: 70">
    <label for="altura">Altura (cm):</label>
    <input type="number" id="altura" placeholder="Ej: 175">
    <button onclick="calcularIMC()">Calcular IMC</button>
    <div class="resultado" id="resultadoIMC"></div>
    <canvas id="graficaIMC" width="400" height="200"></canvas>
  </section>

  <!-- Sección Ejercicios -->
  <section>
    <h2>Registro de Ejercicios</h2>
    <label for="dia">Día:</label>
    <select id="dia">
      <option>Lunes</option>
      <option>Martes</option>
      <option>Miércoles</option>
      <option>Jueves</option>
      <option>Viernes</option>
      <option>Sábado</option>
      <option>Domingo</option>
    </select>
    <label for="ejercicio">Ejercicio:</label>
    <input type="text" id="ejercicio" placeholder="Ej: Press banca">
    <label for="detalle">Detalles (series, repeticiones, peso):</label>
    <textarea id="detalle"></textarea>
    <button onclick="guardarEjercicio()">Guardar Ejercicio</button>
    <div class="ejercicios" id="listaEjercicios"></div>
  </section>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // Login básico con localStorage
    function registrar(){
      let usuario = document.getElementById("usuario").value;
      let clave = document.getElementById("clave").value;
      localStorage.setItem(usuario, clave);
      document.getElementById("mensajeLogin").innerText = "Usuario registrado!";
    }
    function login(){
      let usuario = document.getElementById("usuario").value;
      let clave = document.getElementById("clave").value;
      let guardado = localStorage.getItem(usuario);
      if(guardado === clave){
        document.getElementById("mensajeLogin").innerText = "Login exitoso!";
      } else {
        document.getElementById("mensajeLogin").innerText = "Usuario o clave incorrecta.";
      }
    }

    // IMC + Gráfica
    let historialIMC = [];
    let ctx = document.getElementById('graficaIMC').getContext('2d');
    let graficaIMC = new Chart(ctx, {
      type: 'line',
      data: {
        labels: [],
        datasets: [{
          label: 'IMC',
          data: [],
          borderColor: 'blue',
          fill: false
        }]
      }
    });

    function calcularIMC() {
      let peso = document.getElementById("peso").value;
      let altura = document.getElementById("altura").value / 100;
      if(peso > 0 && altura > 0){
        let imc = (peso / (altura * altura)).toFixed(2);
        document.getElementById("resultadoIMC").innerText = "Tu IMC es: " + imc;
        historialIMC.push(imc);
        graficaIMC.data.labels.push("Medición " + historialIMC.length);
        graficaIMC.data.datasets[0].data.push(imc);
        graficaIMC.update();
      } else {
        alert("Por favor ingresa valores válidos.");
      }
    }

    // Registro de ejercicios
    function guardarEjercicio() {
      let dia = document.getElementById("dia").value;
      let ejercicio = document.getElementById("ejercicio").value;
      let detalle = document.getElementById("detalle").value;
      if(ejercicio.trim() !== ""){
        let lista = document.getElementById("listaEjercicios");
        let div = document.createElement("div");
        div.classList.add("dia");
        div.innerHTML = "<strong>" + dia + ":</strong> " + ejercicio + " - " + detalle;
        lista.appendChild(div);
        document.getElementById("ejercicio").value = "";
        document.getElementById("detalle").value = "";
      } else {
        alert("Agrega un nombre de ejercicio.");
      }
    }
  </script>
</body>
</html>
