# 实验2

## 实验2_1 **构建第一个Kotlin应用**

### 1.创建第一个Kotlin应用

step:新建一个项目，选择basic Acitvity，然后在语言中选择kotlin

<img src=".\img\image-20230413214003616.png" alt="image-20230413214003616" style="zoom:33%;" />







<img src="./img/image-20230413214107046.png" alt="image-20230413214107046" style="zoom: 50%;" />



ps. 由于安装过程在实验1中进行了详细说明，这里不再说明，直接进行效果展示，展示如下：

<img src=".\img\image-20230413213648576.png" alt="image-20230413213648576" style="zoom:33%;" />



### 2.**探索界面布局编辑器**

1. 打开 [res下的 fragment_first.xml](..\..\..\MyApplication1\app\src\main\res\layout\fragment_first.xml) ，并且选择designer模式

![image-20230415210344670](./img/image-20230415210344670.png)

2. 可以在attribute中查看各个控件的属性（id、大小、内容等）

   <img src="./img/image-20230415210700042.png" alt="image-20230415210700042" style="zoom:33%;" />



### 3.**向页面添加组件并完成交互代码**

1. 打开 [fragment_first.xml](..\..\..\MyApplication1\app\src\main\res\layout\fragment_first.xml) 并完成相关配置

   + 新增按钮并且增添相关属性（这里以Toast为例）
     
     + 改变各个控件的id
     
       ![image-20230419110559526](./img/image-20230419110559526.png)
     
     + 增加约束：给控件增加左右上下的约束
     
       <img src="./img/image-20230419105624057.png" alt="image-20230419105624057" style="zoom: 50%;" />
     
       
     
     + 改变文字：先改变text
     
     <img src="./img/image-20230419110145929.png" alt="image-20230419110145929" style="zoom:50%;" />
     
     ​	                                                                <img src="./img/image-20230419110300991.png" alt="image-20230419110300991" style="zoom: 50%;" />
     
     
     
     + 改变样式：先在color.xml的颜色，然后在fragment_first中增加
     
       <img src="./img/image-20230419110805616.png" alt="image-20230419110805616" style="zoom: 50%;" />
     
       <img src="./img/image-20230419110929951.png" alt="image-20230419110929951" style="zoom:50%;" />
     
       
     
       

   + 完整代码如下：

     + fragment_first.xml:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
         xmlns:app="http://schemas.android.com/apk/res-auto"
         xmlns:tools="http://schemas.android.com/tools"
         android:layout_width="match_parent"
         android:layout_height="match_parent"
         tools:context=".FirstFragment"
         android:background="@color/screenBackground"
         >
     
     
         <TextView
             android:id="@+id/textview_first"
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:fontFamily="sans-serif-condensed"
             android:text="@string/hello_first_fragment"
             android:textColor="#FFFFFF"
             android:textSize="60sp"
             android:textStyle="bold"
             app:layout_constraintBottom_toBottomOf="parent"
             app:layout_constraintEnd_toEndOf="parent"
             app:layout_constraintStart_toStartOf="parent"
     
     
             app:layout_constraintTop_toTopOf="parent"
             app:layout_constraintVertical_bias="0.3" />
     
         <Button
             android:id="@+id/random_button"
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:text="@string/random_button_text"
             android:textSize="20sp"
             android:backgroundTint="@color/buttonBackground"
             app:layout_constraintBottom_toBottomOf="parent"
             app:layout_constraintEnd_toEndOf="parent"
             app:layout_constraintTop_toBottomOf="@+id/textview_first" />
     
         <Button
             android:id="@+id/toast_button"
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:layout_marginStart="24dp"
             android:text="@string/toast_button_text"
             android:textSize="20sp"
             android:backgroundTint="@color/buttonBackground"
             app:layout_constraintBottom_toBottomOf="parent"
             app:layout_constraintStart_toStartOf="parent"
             app:layout_constraintTop_toBottomOf="@+id/textview_first" />
     
         <Button
             android:id="@+id/count_button"
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:text="@string/count_button_text"
             android:textSize="20sp"
             android:backgroundTint="@color/buttonBackground"
             app:layout_constraintBottom_toBottomOf="parent"
             app:layout_constraintEnd_toStartOf="@+id/random_button"
             app:layout_constraintStart_toEndOf="@+id/toast_button"
     
     
             app:layout_constraintTop_toBottomOf="@+id/textview_first" />
     
     </androidx.constraintlayout.widget.ConstraintLayout>
     ```

     + string.xml

     ```xml
     <resources>
         <string name="app_name">My Application</string>
         <string name="action_settings">Settings</string>
         <!-- Strings used for fragments for navigation -->
         <string name="first_fragment_label">First Fragment</string>
         <string name="second_fragment_label">Second Fragment</string>
         <string name="random_button_text">Random</string>
         <string name="previous">Previous</string>
     
         <string name="hello_first_fragment">0</string>
         <string name="hello_second_fragment">Hello second fragment. Arg: %1$s</string>
         <string name="toast_button_text">Toast</string>
         <string name="count_button_text">Count</string>
     </resources>
     ```

     + colors.xml

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <resources>
         <color name="purple_200">#FFBB86FC</color>
         <color name="purple_500">#FF6200EE</color>
         <color name="purple_700">#FF3700B3</color>
         <color name="teal_200">#FF03DAC5</color>
         <color name="teal_700">#FF018786</color>
         <color name="black">#FF000000</color>
         <color name="white">#FFFFFFFF</color>
         <color name="screenBackground">#2196F3</color>
         <color name="buttonBackground">#BBDEFB</color>
     
     </resources>
     ```

     

   

  2. 在 [FirstFragment.kt](..\..\..\MyApplication1\app\src\main\java\com\jkgg\myapplication\FirstFragment.kt) 实现相关函数
     + 实现点击显示提示文字消息

       + 相关代码如下

       ```kotlin
       view.findViewById<Button>(R.id.toast_button).setOnClickListener {//点击显示消息
                   //创建一个新的消息对象
                   val myToast = Toast.makeText(context, "Hello Toast!", Toast.LENGTH_LONG)
                   // 显示消息
                   myToast.show()
       }
       view.findViewById<Button>(R.id.count_button).setOnClickListener {
           		//执行自增函数
                   countMe(view)
       }
       ```

       ```kotlin
       private fun countMe(view: View) {
               //获取textview_first对象
               val showCountTextView = view.findViewById<TextView>(R.id.textview_first)
       
               // 获取文本内容
               val countString = showCountTextView.text.toString()
       
               
               var count = countString.toInt()
               count++
       
               // 显示增加后的结果
               showCountTextView.text = count.toString()
           }
       ```

3. 打开 [fragment_second.xml](..\..\..\MyApplication1\app\src\main\res\layout\fragment_second.xml) 并完成相关配置

   + 在原有的两个组件上新增一个textview组件用于显示随机数，并且对这几个组件的约束、颜色、位置进行配置

   + 配置文件关键代码如下：

   ```xml
   <TextView
           android:id="@+id/textview_header"
           android:layout_width="0dp"
           android:layout_height="wrap_content"
           android:layout_marginStart="24dp"
           android:layout_marginLeft="24dp"
           android:layout_marginTop="24dp"
           android:layout_marginEnd="24dp"
           android:layout_marginRight="24dp"
           android:fontFamily="sans-serif-condensed"
           android:text="@string/random_heading"
           android:textColor="@color/colorPrimaryDark"
           android:textSize="24sp"
           app:layout_constraintEnd_toEndOf="parent"
           app:layout_constraintStart_toStartOf="parent"
           app:layout_constraintTop_toTopOf="parent" />
   
       <Button
           android:id="@+id/button_second"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="@string/previous"
   
           app:layout_constraintBottom_toBottomOf="parent"
           app:layout_constraintEnd_toEndOf="parent"
           app:layout_constraintStart_toStartOf="parent" />
   
       <TextView
           android:id="@+id/textview_random"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="@string/r_textview_text"
           android:textColor="@android:color/white"
           android:textSize="72sp"
           android:textStyle="bold"
           app:layout_constraintBottom_toTopOf="@+id/button_second"
           app:layout_constraintEnd_toEndOf="parent"
           app:layout_constraintStart_toStartOf="parent"
           app:layout_constraintTop_toBottomOf="@+id/textview_header"
           app:layout_constraintVertical_bias="0.45"
       />
   ```

   


​		目前运行结果如下：

​		

<img src="./img/image-20230419132341281.png" alt="image-20230419132341281" style="zoom:50%;" />



<img src="./img/image-20230419132414091.png" alt="image-20230419132414091" style="zoom:50%;" />

​		从上述结果可以看出页面2还是无法正常显示，所以我们要进行navigation配置

3. 进行navigation配置

   + 打开 [nav_graph.xml](..\..\..\MyApplication1\app\src\main\res\navigation\nav_graph.xml) 向SecondFragment增加Argument**myArg**,类型为**integer**

   <img src="./img/image-20230419132931802.png" alt="image-20230419132931802" style="zoom:50%;" />

   + 打开fragment_first.xml 重新定义一个action，向页面2发送信息，关键代码如下：

   ```kotlin
   val showCountTextView = view.findViewById<TextView>(R.id.textview_first) //获取文本框
   val currentCount = showCountTextView.text.toString().toInt() //获取文本框内容
   val action = FirstFragmentDirections.actionFirstFragmentToSecondFragment(currentCount)//自定义一个action
   findNavController().navigate(action)
   ```

   + 对fragment_second操作
     + 导入navArgs
     
     ```kotlin
     import androidx.navigation.fragment.navArgs
     ```
     
     + 接受参数
     
     ```kotlin
     val args: SecondFragmentArgs by navArgs()
     ```
     
     
     
     + 增加逻辑处理,并显示
     
     ```kotlin
     val count = args.myArg
      val countText = getString(R.string.random_heading, count)
      view.findViewById<TextView>(R.id.textview_header).text = countText //显示上界
     //生成随机数
      val random = java.util.Random()
      var randomNumber = 0
     if (count > 0) {
          randomNumber = random.nextInt(count + 1)
     }
     view.findViewById<TextView>(R.id.textview_random).text = randomNumber.toString() //显示随机数
     
     ```

​	最终运行结果如下：

<img src="./img/image-20230419134105403.png" alt="image-20230419134105403" style="zoom:50%;" />

   

<img src="./img/image-20230419134127432.png" alt="image-20230419134127432" style="zoom:50%;" />



---



## 实验2_2 **构建CameraX应用**

### 1.创建项目

+ 点击file然后点击new ->new project，选择Empty Project,如下图所示

<img src="./img/image-20230422092555156.png" alt="image-20230422092555156" style="zoom:50%;" />

+ 在项目build.gradle(Model)文件的dependencies中添加 CameraX 依赖项

<img src="./img/image-20230422093025243.png" alt="image-20230422093229054" style="zoom:50%;" />

具体内容如下：

```gradle
def camerax_version = "1.1.0-beta01"
    implementation "androidx.camera:camera-core:${camerax_version}"
    implementation "androidx.camera:camera-camera2:${camerax_version}"
    implementation "androidx.camera:camera-lifecycle:${camerax_version}"
    implementation "androidx.camera:camera-video:${camerax_version}"

    implementation "androidx.camera:camera-view:${camerax_version}"
    implementation "androidx.camera:camera-extensions:${camerax_version}"
```

+ 由于项目使用的AndroidStudio版本较高，已经默认配置了java8的方法，否则需要配置

<img src="./img/image-20230422093501000.png" alt="image-20230422093501000" style="zoom:50%;" />



+ 因为项目使用了ViewBinding，在 android{} 代码块末尾添加如下片段

```gradle
 buildFeatures {
        viewBinding true
    }
```

至此项目基本配置完成

---



### 2.更新布局

+ 打开activity_main.xml  布局文件，并将其替换为如下代码：

```xml
<androidx.camera.view.PreviewView
        android:id="@+id/viewFinder"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

    <Button
        android:id="@+id/image_capture_button"
        android:layout_width="110dp"
        android:layout_height="110dp"
        android:layout_marginBottom="50dp"
        android:layout_marginEnd="50dp"
        android:elevation="2dp"
        android:text="@string/take_photo"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintEnd_toStartOf="@id/vertical_centerline" />

    <Button
        android:id="@+id/video_capture_button"
        android:layout_width="110dp"
        android:layout_height="110dp"
        android:layout_marginBottom="50dp"
        android:layout_marginStart="50dp"
        android:elevation="2dp"
        android:text="@string/start_capture"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toEndOf="@id/vertical_centerline" />

    <androidx.constraintlayout.widget.Guideline
        android:id="@+id/vertical_centerline"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        app:layout_constraintGuide_percent=".50" />
```



+ 更新strings.xml 文件

```xml
<resources>
    <string name="app_name">CameraXApp</string>
    <string name="take_photo">Take Photo</string>
    <string name="start_capture">Start Capture</string>
    <string name="stop_capture">Stop Capture</string>
</resources>
```

+ 布局效果如下：

<img src="./img/image-20230422094957324.png" alt="image-20230422094957324" style="zoom:50%;" />

### 3.编写 MainActivity.kt 代码

虽然系统已经实现相关方法，但是在实现文件中的方法前相机无法工作，我们的重写代码如下：

```kotlin
typealias LumaListener = (luma: Double) -> Unit

class MainActivity : AppCompatActivity() {
   private lateinit var viewBinding: ActivityMainBinding

   private var imageCapture: ImageCapture? = null

   private var videoCapture: VideoCapture<Recorder>? = null
   private var recording: Recording? = null

   private lateinit var cameraExecutor: ExecutorService

   override fun onCreate(savedInstanceState: Bundle?) {
       super.onCreate(savedInstanceState)
       viewBinding = ActivityMainBinding.inflate(layoutInflater)
       setContentView(viewBinding.root)

       // Request camera permissions
       if (allPermissionsGranted()) {
           startCamera()
       } else {
           ActivityCompat.requestPermissions(
               this, REQUIRED_PERMISSIONS, REQUEST_CODE_PERMISSIONS)
       }

       // Set up the listeners for take photo and video capture buttons
       viewBinding.imageCaptureButton.setOnClickListener { takePhoto() }
       viewBinding.videoCaptureButton.setOnClickListener { captureVideo() }

       cameraExecutor = Executors.newSingleThreadExecutor()
   }

   private fun takePhoto() {}

   private fun captureVideo() {}

   private fun startCamera() {}

   private fun allPermissionsGranted() = REQUIRED_PERMISSIONS.all {
       ContextCompat.checkSelfPermission(
           baseContext, it) == PackageManager.PERMISSION_GRANTED
   }

   override fun onDestroy() {
       super.onDestroy()
       cameraExecutor.shutdown()
   }

   companion object {
       private const val TAG = "CameraXApp"
       private const val FILENAME_FORMAT = "yyyy-MM-dd-HH-mm-ss-SSS"
       private const val REQUEST_CODE_PERMISSIONS = 10
       private val REQUIRED_PERMISSIONS =
           mutableListOf (
               Manifest.permission.CAMERA,
               Manifest.permission.RECORD_AUDIO
           ).apply {
               if (Build.VERSION.SDK_INT <= Build.VERSION_CODES.P) {
                   add(Manifest.permission.WRITE_EXTERNAL_STORAGE)
               }
           }.toTypedArray()
   }
}
```

### 4.请求必要权限

+ 打开 AndroidManifest.xml，添加以下代码行添加到 application 标记之前。

```xml
<uses-feature android:name="android.hardware.camera.any" />
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"
   android:maxSdkVersion="28" />
```

其中第一行android.hardware.camera.any 可确保设备配有相机，指定any表示可以使用前置或者后者摄像头

+ 向MainActivity.kt添加如下代码：

```kotlin
override fun onRequestPermissionsResult(
        requestCode: Int, permissions: Array<String>, grantResults:
        IntArray) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults)
        if (requestCode == REQUEST_CODE_PERMISSIONS) {
            if (allPermissionsGranted()) {
                startCamera()
            } else {
                Toast.makeText(this,
                    "Permissions not granted by the user.",
                    Toast.LENGTH_SHORT).show()
                finish()
            }
        }
    }
```

+ 运行结果如下(由于这里已经授权过了，就没有显示授权)：

<img src="./img/image-20230422101755751.png" alt="image-20230422101755751" style="zoom:33%;" />

+ 重新下载app他又回来了：

<img src="./img/image-20230422104314145.png" alt="image-20230422104314145" style="zoom:33%;" />

### 5.实现 Preview 用例

+ 实现startCamera() 函数，代码如下：

```kotlin
private fun startCamera() {
        val cameraProviderFuture = ProcessCameraProvider.getInstance(this)

        cameraProviderFuture.addListener({
            // Used to bind the lifecycle of cameras to the lifecycle owner
            val cameraProvider: ProcessCameraProvider = cameraProviderFuture.get()

            // Preview
            val preview = Preview.Builder()
                .build()
                .also {
                    it.setSurfaceProvider(viewBinding.viewFinder.surfaceProvider)
                }

            imageCapture = ImageCapture.Builder().build()

            val recorder = Recorder.Builder()
                .setQualitySelector(QualitySelector.from(Quality.HIGHEST))
                .build()
            videoCapture = VideoCapture.withOutput(recorder)



            // Select back camera as a default
            val cameraSelector = CameraSelector.DEFAULT_BACK_CAMERA

            try {
                // Unbind use cases before rebinding
                cameraProvider.unbindAll()

                // Bind use cases to camera
                cameraProvider.bindToLifecycle(this, cameraSelector, preview, videoCapture)



            } catch(exc: Exception) {
                Log.e(TAG, "Use case binding failed", exc)
            }

        }, ContextCompat.getMainExecutor(this))
    }
```

### 6.实现 ImageCapture 用例（拍照功能）

+ 该方法会在用户按下 photo 按钮时调用。填充takePhoto() 方法的代码如下：

```kotlin
private fun takePhoto() {
        // Get a stable reference of the modifiable image capture use case
        val imageCapture = imageCapture ?: return

        // Create time stamped name and MediaStore entry.
        val name = SimpleDateFormat(FILENAME_FORMAT, Locale.US)
            .format(System.currentTimeMillis())
        val contentValues = ContentValues().apply {
            put(MediaStore.MediaColumns.DISPLAY_NAME, name)
            put(MediaStore.MediaColumns.MIME_TYPE, "image/jpeg")
            if(Build.VERSION.SDK_INT > Build.VERSION_CODES.P) {
                put(MediaStore.Images.Media.RELATIVE_PATH, "Pictures/CameraX-Image")
            }
        }

        // Create output options object which contains file + metadata
        val outputOptions = ImageCapture.OutputFileOptions
            .Builder(contentResolver,
                MediaStore.Images.Media.EXTERNAL_CONTENT_URI,
                contentValues)
            .build()

        // Set up image capture listener, which is triggered after photo has
        // been taken
        imageCapture.takePicture(
            outputOptions,
            ContextCompat.getMainExecutor(this),
            object : ImageCapture.OnImageSavedCallback {
                override fun onError(exc: ImageCaptureException) {
                    Log.e(TAG, "Photo capture failed: ${exc.message}", exc)
                }

                override fun
                        onImageSaved(output: ImageCapture.OutputFileResults){
                    val msg = "Photo capture succeeded: ${output.savedUri}"
                    Toast.makeText(baseContext, msg, Toast.LENGTH_SHORT).show()
                    Log.d(TAG, msg)
                }
            }
        )
    }
```

+ 运行效果如下：

<img src="./img/image-20230422105154751.png" alt="image-20230422105154751" style="zoom:33%;" />



### 7.实现 ImageAnalysis 用例

+ 该用例用来处理图像，实现代码如下：

```kotlin
private class LuminosityAnalyzer(private val listener: LumaListener) : ImageAnalysis.Analyzer {

   private fun ByteBuffer.toByteArray(): ByteArray {
       rewind()    // Rewind the buffer to zero
       val data = ByteArray(remaining())
       get(data)   // Copy the buffer into a byte array
       return data // Return the byte array
   }

   override fun analyze(image: ImageProxy) {

       val buffer = image.planes[0].buffer
       val data = buffer.toByteArray()
       val pixels = data.map { it.toInt() and 0xFF }
       val luma = pixels.average()

       listener(luma)

       image.close()
   }
}

```

### 8.实现 VideoCapture 用例（拍摄视频）

```kotlin
private fun captureVideo() {
        val videoCapture = this.videoCapture ?: return

        viewBinding.videoCaptureButton.isEnabled = false

        val curRecording = recording
        if (curRecording != null) {
            // Stop the current recording session.
            curRecording.stop()
            recording = null
            return
        }

        // create and start a new recording session
        val name = SimpleDateFormat(FILENAME_FORMAT, Locale.US)
            .format(System.currentTimeMillis())
        val contentValues = ContentValues().apply {
            put(MediaStore.MediaColumns.DISPLAY_NAME, name)
            put(MediaStore.MediaColumns.MIME_TYPE, "video/mp4")
            if (Build.VERSION.SDK_INT > Build.VERSION_CODES.P) {
                put(MediaStore.Video.Media.RELATIVE_PATH, "Movies/CameraX-Video")
            }
        }

        val mediaStoreOutputOptions = MediaStoreOutputOptions
            .Builder(contentResolver, MediaStore.Video.Media.EXTERNAL_CONTENT_URI)
            .setContentValues(contentValues)
            .build()
        recording = videoCapture.output
            .prepareRecording(this, mediaStoreOutputOptions)
            .apply {
                if (PermissionChecker.checkSelfPermission(this@MainActivity,
                        Manifest.permission.RECORD_AUDIO) ==
                    PermissionChecker.PERMISSION_GRANTED)
                {
                    withAudioEnabled()
                }
            }
            .start(ContextCompat.getMainExecutor(this)) { recordEvent ->
                when(recordEvent) {
                    is VideoRecordEvent.Start -> {
                        viewBinding.videoCaptureButton.apply {
                            text = getString(R.string.stop_capture)
                            isEnabled = true
                        }
                    }
                    is VideoRecordEvent.Finalize -> {
                        if (!recordEvent.hasError()) {
                            val msg = "Video capture succeeded: " +
                                    "${recordEvent.outputResults.outputUri}"
                            Toast.makeText(baseContext, msg, Toast.LENGTH_SHORT)
                                .show()
                            Log.d(TAG, msg)
                        } else {
                            recording?.close()
                            recording = null
                            Log.e(TAG, "Video capture ends with error: " +
                                    "${recordEvent.error}")
                        }
                        viewBinding.videoCaptureButton.apply {
                            text = getString(R.string.start_capture)
                            isEnabled = true
                        }
                    }
                }
            }
    }
```



最终运行效果：

<img src="./img/image-20230422103713412.png" alt="image-20230422103713412" style="zoom: 33%;" />

<img src="./img/image-20230422103737255.png" alt="image-20230422103737255" style="zoom:50%;" />





