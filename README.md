.xml --->


<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Travling Image"
        android:textStyle="bold"
        android:textSize="25dp"
        android:gravity="center"
        android:layout_margin="5dp"/>

    <androidx.constraintlayout.widget.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="350dp">

        <ImageView
            android:id="@+id/pic0"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:srcCompat="@drawable/pic0"
            tools:layout_editor_absoluteY="106dp"
            android:layout_margin="10dp"/>
        <ImageView
            android:id="@+id/pic1"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:srcCompat="@drawable/pic1"
            android:alpha="0"
            tools:layout_editor_absoluteY="106dp"
            android:layout_margin="10dp"/>
        <ImageView
            android:id="@+id/pic2"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:srcCompat="@drawable/pic2"
            android:alpha="0"
            tools:layout_editor_absoluteY="106dp"
            android:layout_margin="10dp"/>
        <ImageView
            android:id="@+id/pic3"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:srcCompat="@drawable/pic3"
            android:alpha="0"
            tools:layout_editor_absoluteY="106dp"
            android:layout_margin="10dp"/>


    </androidx.constraintlayout.widget.ConstraintLayout>
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="1dp"
        android:gravity="center">

        <ImageButton
            android:id="@+id/btnPrevious"
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            app:srcCompat="@android:drawable/ic_media_rew"
            tools:ignore="SpeakableTextPresentCheck"
            tools:layout_editor_absoluteX="148dp"
            tools:layout_editor_absoluteY="498dp" />

        <ImageButton
            android:id="@+id/btnNext"
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            app:srcCompat="@android:drawable/ic_media_ff"
            tools:ignore="SpeakableTextPresentCheck" />


    </LinearLayout>
    <TextView
        android:id="@+id/picName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Akshardham"
        android:textStyle="bold"
        android:textSize="25dp"
        android:gravity="center"
        android:layout_margin="5dp"/>

</LinearLayout>



.kt ---->

package com.example.practicewithkotlin

import android.os.Bundle
import android.widget.Button
import android.widget.ImageButton
import android.widget.ImageView
import android.widget.LinearLayout
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {
    var currentImage = 0
    lateinit var image : ImageView
    var places = arrayOf("Akshardham", "Mountain", "Temple", "India Gate")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        val previous = findViewById<ImageButton>(R.id.btnPrevious)
        val next = findViewById<ImageButton>(R.id.btnNext)
        val plcName = findViewById<TextView>(R.id.picName)

        previous.setOnClickListener {
            var idCurrentImageString = "pic$currentImage"
            var idCurrentImageInt = this.resources.getIdentifier(idCurrentImageString, "id", packageName)
            image = findViewById(idCurrentImageInt)
            image.alpha = 0f

            currentImage = (4+currentImage-1)%4
            var idImageToShowString = "pic$currentImage"
            var idImageToShowInt = this.resources.getIdentifier(idImageToShowString, "id", packageName)
            image = findViewById(idImageToShowInt)
            image.alpha = 1f
            plcName.text = places[currentImage]
        }
        next.setOnClickListener {
            var idCurrentImageString = "pic$currentImage"
            var idCurrentImageInt = this.resources.getIdentifier(idCurrentImageString, "id", packageName)
            image = findViewById(idCurrentImageInt)
            image.alpha = 0f

            currentImage = (4+currentImage+1)%4
            var idImageToShowString = "pic$currentImage"
            var idImageToShowInt = this.resources.getIdentifier(idImageToShowString, "id", packageName)
            image = findViewById(idImageToShowInt)
            image.alpha = 1f
            plcName.text = places[currentImage]
        }
    }
}
