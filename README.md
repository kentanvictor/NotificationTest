# 通知进阶

* NotificationCompat.Builder中提供的丰富的API
 * setsound()

 ```java
 setsound(Uri.fromFile(new File("system/media/audio/ringtones/Luna.ogg")))
 ```
 * setsound()方法中接收一个Uri参数，所以在指定音频文件的时候还需要先获取到音频文件对应的API。
