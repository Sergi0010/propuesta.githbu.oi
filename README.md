<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Quieres ser mi novia?</title>
    <style>
        /* Estilos básicos */
        body {
            background-image: url('fondo-bosque.png');
            background-size: cover;
            background-position: center;
            color: #4a235a;
            font-family: 'Poppins', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: auto;
            background-attachment: fixed;
        }

        /* Contenedor principal */
        .container {
            text-align: center;
            padding: 40px;
            border-radius: 20px;
            background: rgba(255, 255, 255, 0.85);
            width: 90%;
            max-width: 600px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        /* Encabezado */
        h1 {
            font-size: 2.5em;
            color: #2c3e50;
            font-weight: bold;
            margin-bottom: 20px;
            text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
        }

        /* Botones */
        .button {
            background-color: #e3a1ff;
            color: white;
            border: none;
            padding: 15px 25px;
            font-size: 1.2em;
            cursor: pointer;
            border-radius: 30px;
            margin-top: 20px;
            transition: all 0.4s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
        }

        .button:hover {
            background-color: #bd84e6;
            transform: scale(1.1);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
        }

        /* Input de respuesta */
        .input-field {
            padding: 12px;
            margin-top: 20px;
            font-size: 1.2em;
            width: 80%;
            border-radius: 20px;
            border: 2px solid #e3a1ff;
            outline: none;
            transition: border-color 0.3s ease;
        }

        .input-field:focus {
            border-color: #bd84e6;
        }

        /* Estilo para las imágenes */
        .character-img {
            width: 120px;
            border-radius: 15px;
            margin: 15px 0;
        }

        /* Estilo para la carta */
        .card {
            background-color: #f8f1f1;
            border-radius: 20px;
            padding: 25px;
            max-width: 600px;
            margin: 20px auto;
            text-align: center;
            box-shadow: 0 6px 18px rgba(0, 0, 0, 0.15);
            animation: fadeIn 1s ease-out;
        }

        .card h2 {
            color: #e74c3c;
            font-size: 2em;
            margin-bottom: 20px;
            text-shadow: 1px 1px 5px rgba(0, 0, 0, 0.2);
        }

        .card p {
            font-size: 1.2em;
            line-height: 1.6;
            color: #333;
            margin-bottom: 20px;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Transición de fondo */
        .container {
            transition: background-color 0.5s ease;
        }

        .container.active {
            background-color: rgba(255, 228, 228, 0.8);
        }

        /* Animación de botones */
        .button:active {
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div class="container" id="content">
        <h1>Bienvenida al bosque encantado 🌲✨</h1>
        <p>Para descubrir la pregunta mágica, resuelve las pistas de este bosque encantado.</p>
        <button class="button" onclick="nextHint()">Comenzar aventura</button>
    </div>

    <script>
        const hints = [
            { question: "¿Cuál es mi película favorita?", answer: "spiderman" },
            { question: "Esta es nuestra fecha especial. ¿La recuerdas? 📅", answer: "07/12/24" },
            { question: "Programa que veiamos cuando pequeño.", answer: "jorge el curioso" },
            { question: "Canción que nos identifique. PISTA: Te la dedique en un concierto", answer: "te vi" },
            { question: "Tu comida favorita", answer: "pollo" }
        ];

        let currentHint = 0;

        function nextHint() {
            const content = document.getElementById('content');
            if (currentHint < hints.length) {
                content.innerHTML = `
                    <h2>Pista ${currentHint + 1}</h2>
                    <p>${hints[currentHint].question}</p>
                    <input type="text" id="answerInput" class="input-field" placeholder="Escribe tu respuesta aquí">
                    <button class="button" onclick="checkAnswer()">Siguiente pista</button>
                    <p id="responseMessage" class="response"></p>
                `;
                content.classList.add("active");
            } else {
                showFinalQuestion();
            }
        }

        function checkAnswer() {
            const userAnswer = document.getElementById('answerInput').value.trim().toLowerCase();
            const responseMessage = document.getElementById('responseMessage');
            const correctAnswer = hints[currentHint].answer;

            if (userAnswer === correctAnswer) {
                responseMessage.textContent = "¡Respuesta correcta! 🎉";
                currentHint++;
                if (currentHint < hints.length) {
                    nextHint(); // Siguiente pista
                } else {
                    showFinalQuestion();
                }
            } else {
                responseMessage.textContent = "¡Ups! Respuesta incorrecta, intenta de nuevo.";
            }
        }

        function showFinalQuestion() {
            const content = document.getElementById('content');
            content.innerHTML = `
                <h1>¿Quieres ser mi novia? 🌹</h1>
                <p>Rapunzel te ha guiado hasta aquí con su magia ✨</p>
                <button class="button" id="yesButton" onclick="showMessage('yes')">Sí</button>
                <button class="button" id="noButton" onclick="showMessage('no')">No</button>
                <div id="messageArea"></div>
            `;
        }

        let cardIndex = 0;
const yesMessages = [
    { text: "Eres mi luz y mi inspiración. No hay día que no agradezca tenerte en mi vida. 💖 Cada momento contigo es un tesoro, y prometo cuidarlo siempre. ¡Te amo infinitamente!", img1: "cero1.jpeg", img2: "cero2.jpeg", img3: "cero3.jpeg" },
    { text: "Eres mi luz y mi inspiración. No hay día que no agradezca tenerte en mi vida. 💖 Cada momento contigo es un tesoro, y prometo cuidarlo siempre. ¡Te amo infinitamente!", img1: "uno1.jpeg", img2: "uno2.jpeg", img3: "uno3.jpeg" },
    { text: "Amarte ha sido lo más maravilloso que me ha pasado. Eres la persona que me hace querer ser mejor cada día. 💕 Gracias por existir y hacerme tan feliz.", img1: "dos1.jpeg", img2: "dos2.jpeg", img3: "dos3.jpeg" },
    { text: "A tu lado, todo es más hermoso. No necesito nada más que tu amor para sentirme completo. 💖 Gracias por ser mi persona favorita en este mundo.", img1: "tres1.jpeg", img2: "tres2.jpeg", img3: "tres3.jpeg" },
    { text: "Cada día a tu lado es un regalo. No importa lo que pase, siempre estaré aquí para ti. 💫 Te amo con todo mi corazón, y más allá.", img1: "cuatro1.jpeg", img2: "cuatro2.jpeg", img3: "cuatro3.jpeg" },
    { text: "Tus abrazos son mi refugio, tu sonrisa mi motivación. Siempre que pienso en el futuro, me imagino contigo a mi lado. 💞", img1: "cinco1.jpeg", img2: "cinco2.jpeg", img3: "cinco3.jpeg" },
    { text: "Lo que siento por ti no tiene palabras. Eres todo lo que siempre soñé, y mucho más. 💖 Gracias por hacer mi vida perfecta.", img1: "seis1.jpeg", img2: "seis2.jpeg", img3: "seis3.jpeg" },
    { text: "Con cada día que pasa, mi amor por ti crece más. Eres mi razón para sonreír, y siempre serás lo mejor que me ha pasado. 🌸", img1: "siete1.jpeg", img2: "siete2.jpeg", img3: "siete3.jpeg" },
    { text: "Cada momento contigo es un capítulo más en nuestra historia de amor. Mi corazón late por ti, y solo por ti. 💕", img1: "ocho1.jpeg", img2: "ocho2.jpeg", img3: "ocho3.jpeg" },
    { text: "Desde que llegaste a mi vida, todo ha cambiado para mejor. Eres el sol que ilumina mis días. 🌞", img1: "nueve1.jpeg", img2: "nueve2.jpeg", img3: "nueve3.jpeg" },
    { text: "El amor que siento por ti es eterno, y aunque el tiempo pase, siempre te amaré más. Gracias por ser mi todo. 💖", img1: "diez1.jpeg", img2: "diez2.jpeg", img3: "diez3.jpeg" },
    { text: "No hay nada que desee más en este mundo que estar contigo para siempre. Eres la razón de mi felicidad. 😍", img1: "once1.jpeg", img2: "once2.jpeg", img3: "once3.jpeg" }
];

        const noMessages = [
            { text: "¡¿Pero por qué no?!", img: "triste.jpg" },
            { text: "¡No me quieres :((!", img: "quince1.png" },
            { text: "Me rompes el corazón 💔", img: "once.jpeg" },
            { text: "Dime qué hice mal 😭", img: "triste2.jpg" }
        ];

        function showMessage(choice) {
            const messageArea = document.getElementById("messageArea");
            const message = choice === "yes" ? yesMessages[cardIndex] : noMessages[cardIndex];
            messageArea.innerHTML = `
                <div class="card">
                    <h2>${message.text}</h2>
                    ${message.img1 ? `<img src="${message.img1}" class="character-img">` : ""}
                    ${message.img2 ? `<img src="${message.img2}" class="character-img">` : ""}
                    ${message.img3 ? `<img src="${message.img3}" class="character-img">` : ""}
                </div>
            `;

            if (choice === "yes") {
                messageArea.innerHTML += `
                    <button class="button" onclick="nextHint()">Siguiente</button>
                `;
            }

            cardIndex = (cardIndex + 1) % (choice === "yes" ? yesMessages.length : noMessages.length);
        }
    </script>
</body>
</html>