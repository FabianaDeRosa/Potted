<script> 
  import P5 from 'p5-svelte';
  import data from '/src/lib/JSON/newArrivals.json';

  const sketch = (p5) => {
    let img;
    let balls = [];

    p5.preload = () => {
      const randomImageUrl = data[Math.floor(Math.random() * data.length)].img;
      img = p5.loadImage(randomImageUrl);
    };

    p5.setup = () => {
      p5.createCanvas(img.width, img.height);
      p5.background(253, 248, 241);
    };

    p5.draw = () => {
      for (let i = balls.length - 1; i >= 0; i--) {
        balls[i].draw();
        balls[i].move();
        balls[i].changeColour();

        if (balls[i].radius < 0) {
          balls.splice(i, 1);
        }
      }

      if (p5.mouseIsPressed) {
        for (let i = 0; i < 5; i++) {
          balls.push(
            new Ball(
              p5.mouseX,
              p5.mouseY,
              p5.color(
                img.get(p5.mouseX + p5.random(2), p5.mouseY + p5.random(2))
              )
            )
          );
        }
      }
    };

    class Ball {
      constructor(mX, mY, c) {
        this.location = p5.createVector(mX, mY);
        this.radius = p5.random(0.01, 0.05);
        this.r = p5.red(c);
        this.g = p5.green(c);
        this.b = p5.blue(c);

        this.xOff = 0.0;
        this.yOff = 0.0;
      }

      move() {
        this.radius -= p5.random(0.0001);

        this.xOff += p5.random(-0.5, 0.5);
        this.nX = p5.noise(this.location.x) * this.xOff;

        this.yOff += p5.random(-0.5, 0.5);
        this.nY = p5.noise(this.location.y) * this.yOff;

        this.location.x += this.nX;
        this.location.y += this.nY;
      }

      changeColour() {
        this.c = p5.color(img.get(this.location.x, this.location.y));
        this.r = p5.red(this.c);
        this.g = p5.green(this.c);
        this.b = p5.blue(this.c);
      }

      draw() {
        p5.noStroke();
        p5.fill(this.r, this.g, this.b);
        p5.ellipse(
          this.location.x,
          this.location.y,
          this.radius * 50,
          this.radius * 50
        );
      }
    }
  };
</script>

<P5 {sketch} />