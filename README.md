# arduino_log

## 2022-08-10

今天继续玩一下 arduino 的套件，主要是通过 B 站视频关于蜂鸣器的章节，有以下知识点：
1. 了解了有源、无源蜂鸣器的区别，
2. 了解 b10k 的用法；
3. 同时学习从 ANALOG IN 读取外部的电阻值，cool。可以通过外部的电阻值来控制蜂鸣器的开闭。

```c
// 读取 A3 的 analog in 的电平数据，超过 1k 则出发无源蜂鸣
int potVal;
int buzzPin = 8;
int potPin = A3;
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(buzzPin, OUTPUT);
  pinMode(potPin, INPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  potVal = analogRead(potPin);
  Serial.println(potVal);
  while (potVal > 1000) {
    digitalWrite(buzzPin, HIGH);
    potVal = analogRead(potPin);
  }
  digitalWrite(buzzPin, LOW);

}
```

```C
// 持续用有源蜂鸣器
int buzzPin = 8;
int dt1=1;
int dt2=2;
int j;
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(buzzPin, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:

  for (j=1; j<=100; j=j+1){
    digitalWrite(buzzPin, HIGH);
    delay(dt1);
    digitalWrite(buzzPin, LOW);
    delay(dt1);
  }

  for (j=1; j<=100; j=j+1){
    digitalWrite(buzzPin, HIGH);
    delay(dt2);
    digitalWrite(buzzPin, LOW);
    delay(dt2);
  }
}
```

BTW，老伙计非常风趣，老了能够有他那么好的活力还真的非常不错。

## 2022-08-08
买了一块 maker uno 的板子，发现 arduino 原生驱动并不支持。需要在 https://www.cytron.io/p-maker-uno-simplifying-arduino-for-education 下载一个驱动，并且在*连线*的时候安装。最后安装成功。

从 arduino 的 IDE 中可以识别到 tool-port 的 COM? 的端口。Done

```c
void setup() {
  // put your setup code here, to run once:
  pinMode(13, OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:
   digitalWrite(13, HIGH);
   delay(1000);
   digitalWrite(13, LOW);
   delay(1000);
}
```

最后我在 B 站发现了这个还不错的[入门系列视频](https://www.bilibili.com/video/BV1k64y1u75j)，一个国外老伙计的讲解。还不错，成功地让板子上的一个 LED 灯闪烁了起来。

感觉：这个 arduino 的板子玩起来非常简单，基本上是即编写即所得，直接 upload 到板子上就可以见到效果，一个有趣的新玩具，期待它。
