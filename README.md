# San-Valent-n-<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>San Valentín Interactivo 💖</title>
    <style>
        /* Fondo romántico */
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background: linear-gradient(to bottom, #ffdde9, #b0e0e6);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            font-family: 'Arial', sans-serif;
        }

        /* Mensaje con efecto de escritura */
        .typing {
            font-size: 2rem;
            color: #d6006c;
            border-right: 2px solid #d6006c;
            white-space: nowrap;
            overflow: hidden;
            width: 0;
            animation: typing 3s steps(30, end) forwards, blink 0.75s step-end infinite;
            text-align: center;
            z-index: 1;
            position: relative;
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 25ch; }
        }

        @keyframes blink {
            50% { border-color: transparent; }
        }

        /* Contenedor de corazones */
        .hearts-container {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            transform: rotate(-45deg);
            pointer-events: none;
            animation: fall linear forwards;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
        }

        .heart::before {
            top: -10px;
            left: 0;
        }

        .heart::after {
            left: 10px;
            top: 0;
        }

        @keyframes fall {
            0% {
                transform: translateY(0) rotate(-45deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(-45deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <h1 class="typing">¿Quieres ser mi San Valentín? 💌</h1>

    <div class="hearts-container"></div>

    <script>
        const container = document.querySelector('.hearts-container');

        // Crear un corazón en la posición del mouse
        document.addEventListener('mousemove', (e) => {
            const heart = document.createElement('div');
            heart.classList.add('heart');

            // Posición inicial
            heart.style.left = `${e.clientX - 10}px`;
            heart.style.top = `${e.clientY - 10}px`;

            // Duración y velocidad aleatoria
            const duration = Math.random() * 3 + 2; // 2 a 5 segundos
            heart.style.animationDuration = `${duration}s`;

            // Escala aleatoria
            const scale = Math.random() * 0.7 + 0.3;
            heart.style.transform += ` scale(${scale})`;

            // Color aleatorio
            const colors = ['#ff4d6d','#ff85a2','#ffb6c1','#ff69b4','#d6006c'];
            heart.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
            heart.querySelectorAll('::before, ::after'); // no es necesario, ya usan el mismo color

            container.appendChild(heart);

            // Eliminar corazón después de la animación
            setTimeout(() => {
                heart.remove();
            }, duration * 1000);
        });
    </script>
</body>
</html>
