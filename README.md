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
