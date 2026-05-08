#Processingを用いて制作したリズムゲーム風のミニゲームです。
スペースキーでタイミングよくノーツを入力すると、入力タイミングに応じて判定結果が表示される仕様になっています。音楽ゲームが好きで、タイミング判定やキー入力処理がどのように実装されているのか興味を持ったことをきっかけに制作しました。制作では、入力タイミングによって判定を分岐させる処理や、複数ノーツの動きを管理する部分に特に苦労しました。
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
