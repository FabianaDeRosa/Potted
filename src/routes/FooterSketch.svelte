<script>
  import P5 from 'p5-svelte';

  const sketch = (p5) => {
  let balls = [];

  p5.setup = () => {
    p5.createCanvas(window.innerWidth, 400).id('myCanvas');
    p5.clear();

    for (let i = 0; i < 9; i++) {
      balls.push(new Ball(p5.width / 2, 0, p5));
    }
  }

  p5.draw = () => {
    for (let i = balls.length - 1; i >= 0; i--) {
      balls[i].show(p5);
      balls[i].move(p5);

      if (balls[i].radius < 0) {
        balls.splice(i, 1);
      }
    }
  }

  class Ball {
    constructor(mX, mY, p5) {
      this.location = p5.createVector(mX, mY);
      this.radius = p5.random(4, 8);

      this.xOff = 0.0;
      this.yOff = 0.0;
    }

    move() {
      this.radius -= p5.random(0.0001);

      this.xOff += p5.random(-0.5, 0.5);
      this.yOff += p5.random(0, 0.5);

      this.nX = p5.noise(this.location.x) * this.xOff;
      this.nY = p5.noise(this.location.y);

      this.location.x += this.nX;
      this.location.y += this.nY;
    }

    show() {
      p5.noStroke();
      p5.fill(152, 87, 68, 150);
      p5.ellipse(this.location.x, this.location.y, this.radius / 4, this.radius / 4);
    }
  }
}
</script>

<P5 {sketch} />

