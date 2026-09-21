# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:
Start the program.

Create a new Android project in Android Studio.

Design the layout using activity_main.xml

Add an ImageView to display the image.

Add Buttons for each animation (Move, Blink, Fade, Clockwise, Zoom, Slide).

Import the image into the drawable folder.

Create animation XML files under res/anim/ for each animation type:

move.xml – defines translation.

blink.xml – defines alpha visibility changes.

fade.xml – defines fade-in/out.

clockwise.xml – defines rotation.

zoom.xml – defines scale-up/down.

slide.xml – defines translation along the X/Y axis.

## PROGRAM:
```
/*
Developed by: Kanishk Arya
Registeration Number : 212225220047
*/
```
## Activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:src="@mipmap/ic_launcher"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:layout_marginBottom="20dp" />

    <Button
        android:id="@+id/blinkBtn"
        android:text="Blink Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/rotateBtn"
        android:text="Rotate Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/fadeBtn"
        android:text="Fade Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/moveBtn"
        android:text="Move Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/zoomBtn"
        android:text="Zoom Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/stopBtn"
        android:text="Stop Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dp" />

</LinearLayout>

```
## MainActivity.java
```
package com.example.animation;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

import com.example.animation.R;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    Button blinkBtn, rotateBtn, fadeBtn, moveBtn, zoomBtn, stopBtn;
    Animation animation;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blinkBtn = findViewById(R.id.blinkBtn);
        rotateBtn = findViewById(R.id.rotateBtn);
        fadeBtn = findViewById(R.id.fadeBtn);
        moveBtn = findViewById(R.id.moveBtn);
        zoomBtn = findViewById(R.id.zoomBtn);
        stopBtn = findViewById(R.id.stopBtn);

        blinkBtn.setOnClickListener(v -> startAnim(R.anim.blink));
        rotateBtn.setOnClickListener(v -> startAnim(R.anim.rotate));
        fadeBtn.setOnClickListener(v -> startAnim(R.anim.fade));
        moveBtn.setOnClickListener(v -> startAnim(R.anim.move));
        zoomBtn.setOnClickListener(v -> startAnim(R.anim.zoom));

        stopBtn.setOnClickListener(v -> {
            if (animation != null) {
                imageView.clearAnimation(); // Stop animation
            }
        });
    }

    private void startAnim(int animRes) {
        animation = AnimationUtils.loadAnimation(getApplicationContext(), animRes);
        imageView.startAnimation(animation);
    }
}

```
## AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Animation">

        <!-- Add android:exported="true" -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```
## Blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:duration="500"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
## Rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<rotate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromDegrees="0"
    android:toDegrees="360"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatCount="infinite" />

```
## Fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="1.0"
    android:toAlpha="0.0"
    android:duration="2000"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
## Move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXDelta="0"
    android:toXDelta="200"
    android:fromYDelta="0"
    android:toYDelta="200"
    android:duration="1500"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
## Zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<scale xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXScale="1.0"
    android:toXScale="1.5"
    android:fromYScale="1.0"
    android:toYScale="1.5"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```

## OUTPUT
Blink
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/4b8b4f3c-381c-4849-8035-20c35b52d655" />

Fade
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a6034af7-941b-425a-8098-a5d7bbd193cb" />


Zoom
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3fcd869b-382f-4cf9-82c7-d9536fcf3858" />

Rotate
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5a11bd77-016b-4453-a31c-12b56fdd0a4a" />


Move
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b6dbd2a7-d07e-4131-bb6b-438244b31618" />

Stop Animation
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/4b8b4f3c-381c-4849-8035-20c35b52d655" />



## RESULT
Thus,the experiment Implementation of Animation application using android studio executed successfully.
