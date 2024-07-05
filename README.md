# 请不要随便扫描不明二维码——————正在窃取信息，将以短信的形式发送至特定手机
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Code Rain</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: black;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <canvas id="canvas"></canvas>
    <script>
        var c = document.getElementById("canvas");
        var ctx = c.getContext("2d");

        c.height = window.innerHeight;
        c.width = window.innerWidth;

        var matrix = "ABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%+-/~{[|`]}";
        matrix = matrix.split("");

        var font_size = 10;
        var columns = c.width / font_size;
        var drops = [];
        for (var x = 0; x < columns; x++)
            drops[x] = 1;

        function draw() {
            ctx.fillStyle = "rgba(0, 0, 0, 0.04)";
            ctx.fillRect(0, 0, c.width, c.height);

            ctx.fillStyle = "#0F0";
            ctx.font = font_size + "px arial";

            for (var i = 0; i < drops.length; i++) {
                var text = matrix[Math.floor(Math.random() * matrix.length)];
                ctx.fillText(text, i * font_size, drops[i] * font_size);

                if (drops[i] * font_size > c.height && Math.random() > 0.975)
                    drops[i] = 0;

                drops[i]++;
            }
        }

        setInterval(draw, 35);
    </script>
</body>
</html>
