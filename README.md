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
 <br/>
 * setDefaults()
 >如果不想要那么多繁杂的设置，直接就可以使用默认的效果<br/>
 ```java
 setDefaults(NotificationCompat.DEFAULT_ALL)
 ```
 <br/>
 * setStyle()
 >在setStyle方法中创建了一个NotificationCompat.BigTextStyle对象，这个对象就是用于封装长文字信息的<br/>当然，还可以添加图片<br/>在setStyle方法中创建一个NotificationCompat.BigPictureStyle对象<br/>然后调用bigPicture()方法将图片传入<br/>通过BitmapFactory的decodeResource()方法将图片解析成Bitmap对象再传入到bigPicture()方法中<br/>
 ```java
 setStyle(new NotificationCompat.BigTextStyle().bigText("Learn how to build notifications, send and sync data, and use voice actions. Get the official Android IDE and developer tools to build apps for Android."))
 ```
 <br/>
 * setPriority()
 >用于设置通知的重要程度</br>5个常量可以选择<br/>PRIORITY_DEFAULT：表示默认的重要程度。<em><strong>和不设置效果是一样的</strong></em></br>PRIORITY_MIN表示最低的重要程度。<em><strong>统可能只会在特定的场景才显示这条通知，比如用户下拉状态栏的时候</strong></em></br>PRIORITY_LOW表示较低的重要程度。<em><strong>系统可能会将这类通知缩小，或改变其显示的顺序，将其排在更重要的通知之后</strong></em><br/>PRIORITY_HIGH表示较高的重要程度。<em><strong>系统可能会将这类通知放大，或改变其显示顺序，将其排在比较靠前的位置</strong></em><br/>PRIORITY_MAX表示最高的重要程度。<em><strong>这类通知消息必须要让用户立刻看到，甚至需要用户做出相应操作。</strong></em></br>
 ```java
 setPriority(NotificationCompat.PRIORITY_MAX)
 ```
