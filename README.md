# 通知进阶

* NotificationCompat.Builder中提供的丰富的API
 * setsound()
 >setsound()方法中接收一个Uri参数，所以在指定音频文件的时候还需要先获取到音频文件对应的API。<br/>
 ```java
 setsound(Uri.fromFile(new File("system/media/audio/ringtones/Luna.ogg")))
 ```

 * setVibrate()
 >使用Vibrate这个属性，长整型数组，用于设置手机静止和振动时长，以毫秒为单位。<br/>下标为0的值表示手机静止的时长，下标为1的值表示手机振动时长，下标为2的值又表示手机静止时长。<br/>以此类推<br/>所以下面的代码表示通知来的时候振动1秒，然后静止1秒，再振动1秒
 ```java
 setVibrate(new long[]{0 , 1000,1000,1000})
 ```
 ><h3>但是，值得注意的是，控制手机振动是需要权限的，所以还需要编辑AndroidManifest.xml文件</h3>
 ```xml
 <uses-permission android:name"android.permission.VIBRATE"/>
 ```
<br/>
 * setLights()
 >控制手机LED灯的显示<br/>当手机有未接电话或者有未读短信的时候手机前置的LED灯就会闪烁<br/>提醒用户去查看<br/>setLights()接收的第一个参数指定LED颜色<br/>第二个参数用于指定LED灯亮起的时长<br/>以毫秒为单位<br/>第三个参数指定的是LED灯暗去的时长<br/>同样也是以毫秒为单位<br/>
 ><h4>下面的代码就是实现LED灯以绿色的光一闪一闪的效果</h4><br/>
 ```java
 setLights(Color.GREEN,1000,1000)
 ```
