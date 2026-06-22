# test80<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Jump Game</title>
<style>
body {
    margin: 0;
    overflow: hidden;
}

canvas {
    background: skyblue;
    display: block;
}
</style>
</head>
<body>

<canvas id="game"></canvas>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = 800;
canvas.height = 400;

const player = {
    x: 100,
    y: 300,
    width: 40,
    height: 40,
    speed: 5,
    dy: 0,
    jumping: false
};

const gravity = 0.5;

const platforms = [
    {x: 0, y: 350, width: 800, height: 50},
    {x: 250, y: 280, width: 120, height: 20},
    {x: 450, y: 220, width: 120, height: 20}
];

const keys = {};

document.addEventListener("keydown", e => {
    keys[e.key] = true;

    if ((e.key === " " || e.key === "ArrowUp") && !player.jumping) {
        player.dy = -12;
        player.jumping = true;
    }
});

document.addEventListener("keyup", e => {
    keys[e.key] = false;
});

function update() {

    if (keys["ArrowLeft"]) {
        player.x -= player.speed;
    }

    if (keys["ArrowRight"]) {
        player.x += player.speed;
    }

    player.dy += gravity;
    player.y += player.dy;

    player.jumping = true;

    for (let p of platforms) {

        if (
            player.x < p.x + p.width &&
            player.x + player.width > p.x &&
            player.y + player.height > p.y &&
            player.y + player.height < p.y + 20 &&
            player.dy >= 0
        ) {
            player.y = p.y - player.height;
            player.dy = 0;
            player.jumping = false;
        }
    }

    if (player.x < 0) player.x = 0;
    if (player.x > canvas.width - player.width) {
        player.x = canvas.width - player.width;
    }
}

function draw() {

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = "green";
    for (let p of platforms) {
        ctx.fillRect(p.x, p.y, p.width, p.height);
    }

    ctx.fillStyle = "red";
    ctx.fillRect(player.x, player.y, player.width, player.height);

    ctx.fillStyle = "black";
    ctx.font = "20px Arial";
    ctx.fillText("Arrow Keys = Move", 10, 30);
    ctx.fillText("Space = Jump", 10, 60);
}

function gameLoop() {
    update();
    draw();
    requestAnimationFrame(gameLoop);
}

gameLoop();
</script>

</body>
</html>
