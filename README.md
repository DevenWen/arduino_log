# arduino_log

## 2022-08-08
买了一块 maker uno 的板子，发现 arduino 原生驱动并不支持。需要在 https://www.cytron.io/p-maker-uno-simplifying-arduino-for-education 下载一个驱动，并且在*连线*的时候安装。最后安装成功。

从 arduino 的 IDE 中可以识别到 tool-port 的 COM? 的端口。Done

```
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
