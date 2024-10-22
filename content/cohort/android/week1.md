why?
---
- caching  -> downloading data and making it offline in the app
- offline -> can work without internet as well
- notification -> for more connection

# Creation
1. Idea
2. Design
3. Development
4. choosing platform (flutter vs native)
5. Testing (Test driven development)
6. Publish
7. Market

# flutter vs native

Flutter
---
- it is cross platform
- It is slower
- It uses dart
- it converts to java and kotlin making it JVM compatible

Native
--
- it is faster
- write in java kotlin

# creating an app
- package name -> com.companyName.appName
- Build config -> I file to add dependencies and inject them
- Minimum SDK -> minimum Android version your app can support upto

## file structure
- java/kotlin files in java folder
- layout (XML) files in res folder

## steps to run a app
1. build -> checks for errors
2. run -> run your app one the emulator

## creating an emulator
- SDK -> Software Development Kit is used to run your app on specific android version
- Assigning ram and storage in advance setting

## files
- running an app first looks for file with name activity files (JAVA/KOTLIN)
---
```kotlin
// /app/java/com.microsoft.app1/MainActivity.kt
package com.microsoft.app1

import androidx.appcompat.app.AppCompatActivity

class MainActivity: AppCompatActivity() {
//extending mainactivity class with appcompatactivity which houses all important functions

}
```
----
- make layout files now
----
XML is just a way to representing data

```xml
<!-- app/res/layout/activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello"
        android:background="@color/teal_200"
        tools:layout_editor_absoluteX="179dp"
        tools:layout_editor_absoluteY="350dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
---
- Binding XML to java file
---
```kotlin
// /app/java/com.microsoft.app1/MainActivity.kt
package com.example.myapplication

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity:AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```
---
- AndroidManifest.xml
----
- this file if parent of the app you created
- this is the file where we define cycle (ie which file to launch first)
- Layers : Application -> Activity
- Here we create child tags and tell our loading structure

```xml
<!-- app/manifests/AndroidManifest.xml-->
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyApplication"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <action android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
    </application>
</manifest>
```
---
- sync files, build and run files

---
# layout

- `wrap_content` -> depending on the size of content it will change its size
- `match_parent` -> matching the size of the parent class (usually display of android)

## constraint layout

- using `layout_editor_absoluteX` is not good as it fixes the position of element.
- this makes element not adaptive to all screen sizes
- constraints are like cuff and binds element to each other or parent of it
---
1. `Top_toTopof`
2. `Top_toBottomof`
3. `Bottom_toTopof`
4. `Bottom_toBottomof`
5. `Start_toStartof`
6. `End_toStartof`
7. `Start_toEndof`
8. `End_toEndof`
---


```xml
<!-- app/res/layout/activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@color/teal_200"
        android:text="Hello"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toTopOf="@+id/button"/>

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="greet"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/textView"
        app:layout_constraintBottom_toTopOf="@+id/editTextDate"/>

    <EditText
        android:id="@+id/editTextDate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="DOB"
        android:inputType="date"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
# gitignore
