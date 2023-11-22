<table>
  <tr>
    <th colspan="2">DATA MAHASISWA</th>
  </tr>
  <tr>
    <td>Nama</td>
    <td>Muhammad Arifin</td>
  </tr>
  <tr>
    <td>NIM</td>
    <td>312210330</td>
  </tr>
  <tr>
    <td>Kelas</td>
    <td>TI.22.A3</td>
  </tr>
  <tr>
    <td>Mata Kuliah</td>
    <td>Pemrograman Mobile</td>
  </tr>
</table>

# <p align="center">Implisit Intent</p>

![284047427](https://github.com/marifinnnnn/implisit-intent/assets/115518274/93286029-0552-4c62-943c-3209cecef32c)

# Langkah-langkah

Untuk membuat aplikasi Android dengan fitur splash screen dan tujuh project yang dapat diakses melalui metode eksplicit dan implisit intent, kita dapat mengikuti langkah-langkah sebagai berikut:

# 1. Membuat Splash Screen Layout ```(activity_splash_screen.xml)```:

Buat file layout untuk splash screen, misalnya ```activity_splash_screen.xml```. Dalam contoh ini, kita akan menampilkan logo masing-masing individu.

      <?xml version="1.0" encoding="utf-8"?>
      <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:background="@color/white"
          tools:content=".SplashScreen">
      
          <LinearLayout
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_centerInParent="true"
              android:gravity="center"
              android:orientation="vertical">
      
              <ImageView
                  android:id="@+id/logo"
                  android:layout_width="350dp"
                  android:layout_height="wrap_content"
                  android:adjustViewBounds="true"
                  android:src="@drawable/marifin" />
      
          </LinearLayout>
      
      </RelativeLayout>

# 2. Membuat SplashScreen ```(SplashScreen.java)```:

Buat kelas untuk menangani splash screen dan pindah ke MainActivity setelah beberapa detik.

      package com.hellotoast;
      
      import android.content.Intent;
      import android.os.Bundle;
      import android.os.Handler;
      import android.view.View;
      
      import androidx.appcompat.app.AppCompatActivity;
      
      public class SplashScreen extends AppCompatActivity {
      
          @Override
          protected void onCreate(Bundle savedInstanceState) {
              super.onCreate(savedInstanceState);
              setContentView(R.layout.activity_splash_screen);
      
              View decorView = getWindow().getDecorView();
              // Hide the status bar.
              int uiOptions = View.SYSTEM_UI_FLAG_FULLSCREEN;
              decorView.setSystemUiVisibility(uiOptions);
              // Hide ActionBar
              if (getSupportActionBar() != null) {
                  getSupportActionBar().hide();
              }
              new Handler().postDelayed(new Runnable() {
                  @Override
                  public void run() {
                      startActivity(new Intent(SplashScreen.this, MainHomePage.class));
                      finish();
                  }
              }, 2000); // Ubah delayMillis menjadi 2000
          }
      }

# 3. Menambahkan button pada ```activity_home.xml``` yang sudah disiapkan

Di sini namanya ```activity_home.xml```, anda bisa menyesuaikan dengan nama xm anda

      <?xml version="1.0" encoding="utf-8"?>
      <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:layout_marginStart="0dp"
          android:layout_marginEnd="0dp"
          android:background="@color/pink"
          android:gravity="center_vertical"
          android:orientation="vertical"
          tools:context=".SplashScreen">
      
          <Button
              android:id="@+id/btnHello"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Hello Toast"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnCount"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Count"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnSianida"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Kasus Sianida"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnTwoActivity"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Two Activity"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnAlarm"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:onClick="createAlarm"
              android:text="Project Set Alarm"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      </LinearLayout>

![284048480](https://github.com/marifinnnnn/implisit-intent/assets/115518274/a47d95d9-4cf0-4cb1-80c2-10ca058303d6)

# 4. Lalu atur MainActivity ```(MainHomePage.java)```

Karena saya sudah membuat activity sebelumnya untuk masing-masing project maka tinggal edit mainactivitynya tidak usah bikin activity satu-satu lagi: Di sini, kita akan menampilkan daftar project dan menangani eksplicit intent. nama saya MainHomePage.java, kalian bisa menyesuaikan dengan nama kalian.

      package com.hellotoast;
      
      import android.content.Intent;
      import android.os.Bundle;
      import android.provider.AlarmClock;
      import android.view.View;
      import android.widget.Button;
      
      import androidx.appcompat.app.AppCompatActivity;
      
      import java.util.ArrayList;
      
      public class MainHomePage extends AppCompatActivity {
      
          Button btnHello;
          Button btnCount;
          Button btnSianida;
          Button btnTwoActivity;
      
          @Override
          protected void onCreate(Bundle savedInstanceState) {
              super.onCreate(savedInstanceState);
              setContentView(R.layout.activity_home);
      
              setLayout();
              setKlik();
          }
      
          void setLayout() {
              btnHello = findViewById(R.id.btnHello);
              btnCount = findViewById(R.id.btnCount);
              btnSianida = findViewById(R.id.btnSianida);
              btnTwoActivity = findViewById(R.id.btnTwoActivity);
          }
      
          void setKlik() {
              btnHello.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intenthello = new Intent(MainHomePage.this, MainActivity.class);
                      startActivity(intenthello);
                  }
              });
      
              btnCount.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intentcount = new Intent(MainHomePage.this, MainToast.class);
                      startActivity(intentcount);
                  }
              });
      
              btnSianida.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intentsianida = new Intent(MainHomePage.this, MainScrollice.class);
                      startActivity(intentsianida);
                  }
              });
      
              btnTwoActivity.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intenttwoactivity = new Intent(MainHomePage.this, MainFirstActivity.class);
                      startActivity(intenttwoactivity);
                  }
              });
          }
      
          public void createAlarm(View view) {
              ArrayList<Integer> alarmDays = new ArrayList<>();
              alarmDays.add(2);
              alarmDays.add(3);
              alarmDays.add(4);
              Intent intent = new Intent(AlarmClock.ACTION_SET_ALARM)
                      .putExtra(AlarmClock.EXTRA_DAYS, alarmDays)
                      .putExtra(AlarmClock.EXTRA_MESSAGE, "Testing")
                      .putExtra(AlarmClock.EXTRA_HOUR, 7)
                      .putExtra(AlarmClock.EXTRA_MINUTES, 30)
                      .putExtra(AlarmClock.EXTRA_VIBRATE, false)
                      .putExtra(AlarmClock.EXTRA_RINGTONE, "VALUE_RINGTONE_SILENT");
              if (intent.resolveActivity(getPackageManager()) != null) {
                  startActivity(intent);
              }
          }
      }

# 5. Mengedit file ```AndroidManifest.xml``` untuk aplikasi Android dengan SplashScreenActivity dan MainActivity yang akan memulai tujuh project menggunakan eksplicit dan implisit intent:

Di sini saya sudah menyiapkan kodingannya:

      <?xml version="1.0" encoding="utf-8"?>
      <manifest xmlns:android="http://schemas.android.com/apk/res/android">
      
          <uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
      
          <application
              android:allowBackup="true"
              android:icon="@drawable/logowanda"
              android:label="Rosé"
              android:roundIcon="@drawable/logowanda"
              android:supportsRtl="true"
              android:theme="@style/Theme.HelloToast">
      
      
              <activity
                  android:name=".SplashScreen"
                  android:exported="true">
                  <intent-filter>
                      <action android:name="android.intent.action.MAIN" />
                      <category android:name="android.intent.category.LAUNCHER" />
                  </intent-filter>
              </activity>
      
              <activity android:name=".MainHomePage"></activity>
              <activity android:name=".MainActivity"></activity>
              <activity android:name=".MainScrollice"></activity>
              <activity android:name=".MainToast"></activity>
              <activity android:name=".MainFirstActivity"></activity>
      
          </application>
      </manifest>

# Output

# Luncher Splash

<img width="264" alt="Screenshot 2023-11-22 231555" src="https://github.com/marifinnnnn/implisit-intent/assets/115518274/03197c9c-29dd-4c89-bd7b-32e283dd9f5f">

# Home

![284051525](https://github.com/marifinnnnn/implisit-intent/assets/115518274/663e092e-0e81-43ec-b7a8-1c183e8c87aa)

# a. Project Hello Toast

![284052179](https://github.com/marifinnnnn/implisit-intent/assets/115518274/45a281f8-3507-4c44-9e66-246aa068ac09)

# b. Project Count

![fibonacci2](https://github.com/marifinnnnn/implisit-intent/assets/115518274/993d1e04-441a-4e7a-8bff-4014d7dd6ebb)

# c. Project Sianida

![284051718](https://github.com/marifinnnnn/implisit-intent/assets/115518274/d317588b-886a-4175-903b-5d9d8fe6697a)

# d. Project Set Alarm

![284051806](https://github.com/marifinnnnn/implisit-intent/assets/115518274/fdf0fa7e-146b-4a6a-a3be-83f3c619af78)
