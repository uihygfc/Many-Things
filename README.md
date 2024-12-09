let shapes = [];

function setup() {
  createCanvas(800, 600);
  for (let i = 0; i < 10; i++) {
    shapes.push({
      x: random(width),
      y: random(height),
      size: random(20, 50),
      xSpeed: random(2, 5),
      ySpeed: random(2, 5),
      r: random(255),
      g: random(255),
      b: random(255)
    });
  }
}

function draw() {
  background(0);
  for (let shape of shapes) {
    fill(shape.r, shape.g, shape.b);
    ellipse(shape.x, shape.y, shape.size);
    shape.x += shape.xSpeed;
    shape.y += shape.ySpeed;
    shape.size += sin(frameCount * 0.05) * 2;
    if (shape.x > width || shape.x < 0) shape.xSpeed *= -1;
    if (shape.y > height || shape.y < 0) shape.ySpeed *= -1;
    if (shape.r < 255) shape.r += 1;
    if (shape.g > 0) shape.g -= 1;
    shape.b = (shape.b + 1) % 255;
  }
}

