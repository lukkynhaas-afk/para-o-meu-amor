<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="theme-color" content="#090b18">
    <title>Minhas Férias 🏖️</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            background: radial-gradient(
                ellipse at top,
                #29215e 0%,
                #111329 45%,
                #080a13 100%
            );
            color: white;
            font-family: Arial, sans-serif;
        }

        .card {
            width: 100%;
            max-width: 500px;
            text-align: center;
            padding: 30px 20px;
            border: 1px solid #ffffff25;
            border-radius: 28px;
            background: #ffffff0c;
            box-shadow: 0 20px 70px #0006;
        }

        .emoji {
            font-size: 65px;
            animation: flutuar 3s ease-in-out infinite;
        }

        h1 {
            font-size: 32px;
            line-height: 1.2;
            margin: 15px 0;
            background: linear-gradient(
                90deg,
                #ffffff,
                #c5b8ff,
                #71e6ff
            );
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .mensagem {
            color: #c5c8df;
            font-size: 15px;
            line-height: 1.6;
        }

        .contador {
            display: grid;
            grid-template-columns: repeat(4, minmax(0, 1fr));
            gap: 8px;
            margin: 30px 0;
        }

        .unidade {
            padding: 18px 3px;
            border: 1px solid #ffffff18;
            border-radius: 16px;
            background: #ffffff0d;
        }

        .numero {
            font-size: clamp(25px, 7vw, 38px);
            font-weight: bold;
            font-variant-numeric: tabular-nums;
            color: #a99aff;
        }

        .legenda {
            margin-top: 8px;
            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #c5c8df;
        }

        .data {
            margin-top: 20px;
            padding: 15px 10px;
            border-radius: 15px;
            background: #a99aff15;
            color: #ddd7ff;
            font-size: 14px;
            line-height: 1.6;
        }

        .rodape {
            margin-top: 22px;
            color: #9297b8;
            font-size: 12px;
        }

        @keyframes flutuar {
            0%, 100% {
                transform: translateY(0);
            }

            50% {
                transform: translateY(-9px);
            }
        }

        @media (max-width: 360px) {
            .contador {
                gap: 5px;
            }

            .unidade {
                padding: 14px 2px;
            }

            .legenda {
                font-size: 9px;
                letter-spacing: 0;
            }
        }
    </style>
</head>

<body>

    <main class="card">

        <div class="emoji" id="emoji">🏖️</div>

        <h1 id="titulo">Contagem para as férias!</h1>

        <p class="mensagem" id="mensagem">
            A liberdade está chegando...
            Cada segundo conta! 😎
        </p>

        <div class="contador" id="contador">

            <div class="unidade">
                <div class="numero" id="dias">000</div>
                <div class="legenda">Dias</div>
            </div>

            <div class="unidade">
                <div class="numero" id="horas">00</div>
                <div class="legenda">Horas</div>
            </div>

            <div class="unidade">
                <div class="numero" id="minutos">00</div>
                <div class="legenda">Minutos</div>
            </div>

            <div class="unidade">
                <div class="numero" id="segundos">00</div>
                <div class="legenda">Segundos</div>
            </div>

        </div>

        <div class="data" id="data">
            📅 2 de dezembro de 2026
        </div>

        <div class="rodape">
            ✨ Seu descanso tem data marcada ✨
        </div>

    </main>

    <script>
        // DATA DE INÍCIO DAS FÉRIAS
        // Dezembro é o mês 11 no JavaScript.
        const inicioFerias = new Date(2026, 11, 2, 0, 0, 0);

        // DATA DE TÉRMINO DAS FÉRIAS
        const fimFerias = new Date(2027, 0, 2, 0, 0, 0);

        function atualizarContador() {

            const agora = new Date();

            const emoji = document.getElementById("emoji");
            const titulo = document.getElementById("titulo");
            const mensagem = document.getElementById("mensagem");
            const contador = document.getElementById("contador");
            const data = document.getElementById("data");

            let destino;

            if (agora < inicioFerias) {

                destino = inicioFerias;

                emoji.textContent = "🏖️";
                titulo.textContent = "Contagem para as férias!";
                mensagem.textContent =
                    "A liberdade está chegando... Cada segundo conta! 😎";

                data.textContent =
                    "📅 Suas férias começam em 2 de dezembro de 2026";

                contador.style.display = "grid";

            } else if (agora < fimFerias) {

                destino = fimFerias;

                emoji.textContent = "🌴";
                titulo.textContent = "FÉRIAS ATIVADAS! 🎉";
                mensagem.textContent =
                    "Nada de trabalho! Aproveite seu merecido descanso! 😎";

                data.textContent =
                    "☀️ Suas férias vão até 2 de janeiro de 2027";

                contador.style.display = "grid";

            } else {

                emoji.textContent = "💪";
                titulo.textContent = "Até as próximas férias!";
                mensagem.textContent =
                    "Essa acabou, mas já pode sonhar com a próxima! 😂";

                contador.style.display = "none";

                data.textContent =
                    "✨ Que venham os próximos dias de descanso!";

                return;
            }

            // Calcula o tempo real restante em milissegundos.
            const restante = Math.max(
                0,
                destino.getTime() - agora.getTime()
            );

            const dias = Math.floor(
                restante / (1000 * 60 * 60 * 24)
            );

            const horas = Math.floor(
                (restante / (1000 * 60 * 60)) % 24
            );

            const minutos = Math.floor(
                (restante / (1000 * 60)) % 60
            );

            const segundos = Math.floor(
                (restante / 1000) % 60
            );

            // Atualiza os números na página.
            document.getElementById("dias").textContent =
                String(dias).padStart(3, "0");

            document.getElementById("horas").textContent =
                String(horas).padStart(2, "0");

            document.getElementById("minutos").textContent =
                String(minutos).padStart(2, "0");

            document.getElementById("segundos").textContent =
                String(segundos).padStart(2, "0");
        }

        // Atualiza imediatamente ao abrir o site.
        atualizarContador();

        // Atualiza a contagem a cada segundo.
        setInterval(atualizarContador, 1000);
    </script>

</body>
</html>
