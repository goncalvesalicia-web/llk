function calcularIMC() {
    // Busca os elementos do DOM
    const peso = parseFloat(document.getElementById('peso').value);
    const altura = parseFloat(document.getElementById('altura').value);
    const divResultado = document.getElementById('resultado');

    // Validação simples
    if (isNaN(peso) || isNaN(altura) || altura <= 0) {
        divResultado.innerHTML = "Por favor, insira valores válidos.";
        divResultado.style.color = "red";
        return;
    }

    // Cálculo do IMC: peso / (altura * altura)
    const imc = peso / (altura * altura);
    let classificacao = "";

    // Lógica de classificação
    if (imc < 18.5) {
        classificacao = "Abaixo do peso";
    } else if (imc < 25) {
        classificacao = "Peso normal";
    } else if (imc < 30) {
        classificacao = "Sobrepeso";
    } else {
        classificacao = "Obesidade";
    }

    // Exibe o resultado formatado
    divResultado.style.color = "#333";
    divResultado.innerHTML = `Seu IMC é ${imc.toFixed(2)}<br>(${classificacao})`;
}
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de IMC</title>
    <style>
        body { font-family: Arial, sans-serif; display: flex; justify-content: center; padding: 50px; background-color: #f4f4f9; }
        .card { background: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); width: 300px; }
        input { width: 100%; padding: 10px; margin: 10px 0; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; }
        button { width: 100%; padding: 10px; background-color: #28a745; color: white; border: none; border-radius: 4px; cursor: pointer; }
        button:hover { background-color: #218838; }
        #resultado { margin-top: 20px; font-weight: bold; text-align: center; }
    </style>
</head>
<body>

    <div class="card">
        <h2>Calculadora de IMC</h2>
        <label for="peso">Peso (kg):</label>
        <input type="number" id="peso" placeholder="Ex: 70.5" step="0.1">
        
        <label for="altura">Altura (m):</label>
        <input type="number" id="altura" placeholder="Ex: 1.75" step="0.01">
        
        <button onclick="calcularIMC()">Calcular</button>

        <div id="resultado"></div>
    </div>

    <script src="script.js"></script>
</body>
</html>
