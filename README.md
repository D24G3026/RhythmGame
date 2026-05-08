# RhythmGame
float[] y = new float[7];

String result = "";

void setup() {
  size(500, 800);

  for (int i = 0; i < 7; i++) {
    y[i] = -i * 120;
  }
}

void draw() {

  background(0);

  stroke(255);
  line(0, 500, width, 500);

  // ノーツ表示
  for (int i = 0; i < 7; i++) {

    fill(0, 255, 255);
    rect(150, y[i], 100, 30);

    y[i] += 7;

    if (y[i] > height) {
      y[i] = -200;
    }
  }

  fill(255);
  textSize(40);
  text(result, 200, 200);
}

void keyPressed() {

  if (key == ' ') {

    for (int i = 0; i < 7; i++) {

      if (abs(y[i] - 500) < 25) {

        result = "Nice";
      }

      else if (abs(y[i] - 500) < 60) {

        result = "No";
      }
    }
  }
}
