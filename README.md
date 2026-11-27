# Ex.No:4 Develop a simple application to display the avaliable sensor in android mobile devices using Sensor Manager in android studio.


## AIM:

To develop a sensor application to use the sensor manager class to identify and get the list of available sensors on a device. in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Giraffe)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as Sensor and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display avaliable sensor in android mobile devices.

Step 7: Save and run the application.

## PROGRAM:
```

Program to print the avaliable sensor in android mobile devices”.
Developed by: JEEVITHA K
Registeration Number : 212225040149

MAINACTIVITY:
package com.example.sensorlist

import android.hardware.Sensor
import android.hardware.SensorManager
import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.ListView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private lateinit var sensorManager: SensorManager
    private lateinit var listViewSensors: ListView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        listViewSensors = findViewById(R.id.listViewSensors)

        // Get the SensorManager service
        sensorManager = getSystemService(SENSOR_SERVICE) as SensorManager

        // Get the list of all available sensors
        val sensorList = sensorManager.getSensorList(Sensor.TYPE_ALL)

        // Prepare data for the ListView
        val sensorNames = ArrayList<String>()

        for (sensor in sensorList) {
            val sensorInfo = "${sensor.name} - ${getSensorTypeName(sensor.type)}"
            sensorNames.add(sensorInfo)
        }

        // If no sensors are found
        if (sensorNames.isEmpty()) {
            sensorNames.add("No sensors found")
        }

        // Display the list using ArrayAdapter
        val adapter = ArrayAdapter(
            this,
            android.R.layout.simple_list_item_1,
            sensorNames
        )

        listViewSensors.adapter = adapter
    }

    // Helper method to get readable sensor type names
    private fun getSensorTypeName(sensorType: Int): String {
        return when (sensorType) {
            Sensor.TYPE_ACCELEROMETER -> "Accelerometer"
            Sensor.TYPE_AMBIENT_TEMPERATURE -> "Ambient Temperature"
            Sensor.TYPE_GAME_ROTATION_VECTOR -> "Game Rotation Vector"
            Sensor.TYPE_GYROSCOPE -> "Gyroscope"
            Sensor.TYPE_LIGHT -> "Light"
            Sensor.TYPE_MAGNETIC_FIELD -> "Magnetic Field"
            Sensor.TYPE_PRESSURE -> "Pressure"
            Sensor.TYPE_PROXIMITY -> "Proximity"
            Sensor.TYPE_RELATIVE_HUMIDITY -> "Relative Humidity"
            Sensor.TYPE_ROTATION_VECTOR -> "Rotation Vector"
            Sensor.TYPE_STEP_COUNTER -> "Step Counter"
            Sensor.TYPE_STEP_DETECTOR -> "Step Detector"
            Sensor.TYPE_GRAVITY -> "Gravity"
            Sensor.TYPE_LINEAR_ACCELERATION -> "Linear Acceleration"
            Sensor.TYPE_ORIENTATION -> "Orientation (deprecated)"
            else -> "Sensor type $sensorType"
        }
    }
}




ACTIVITY_MAIN.XML

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Available Sensors"
        android:textSize="24sp"
        android:textStyle="bold"
        android:layout_marginBottom="16dp"/>

    <ListView
        android:id="@+id/listViewSensors"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
</LinearLayout>


```

## OUTPUT

<img width="462" height="808" alt="Screenshot 2026-11-27 134414" src="https://github.com/user-attachments/assets/80db1576-ead2-4c11-99d7-4256e2832165" />



## RESULT
Thus a Simple Android Application to display the avaliable sensor in android mobile devices using Sensor Manager in Android Studio is developed and executed successfully.
