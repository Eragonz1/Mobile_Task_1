# Лабораторная работа №1. Создание Activity и передача параметров между ними.
- Выполнил: Золотарев
- Язык программирования: Java

## Что делает приложение?
Этот проект демонстрирует простой пример перехода между двумя экранами (Activity) в Android-приложении. Чтобы запустить проект можно прочитать "Как запустить"

## Функциональность:
Приложение содержит две Activity:
![image](https://github.com/user-attachments/assets/ab5ab25b-786f-47b9-91c6-312d87d6618e)

MainActivity: На этом экране находится кнопка "Перейти к Activity 2".

![image](https://github.com/user-attachments/assets/26a9b512-529a-44bf-9fcc-5398c9cce71d)

SecondActivity: На этом экране отображается текст "Переданный параметр: Золотарев", где Золотарев* - это строка, переданная из MainActivity.

## Дополнительные сведения:
Проект использует стандартные компоненты Android: Activity, Intent, Button, TextView.
Переход между Activity осуществляется с помощью Intent - объекта, который содержит информацию о том, какую Activity нужно запустить.
Параметр передается с помощью putExtra("Фамилия", "Золотарев"), а затем извлекается в SecondActivity с помощью getIntent().getStringExtra("Фамилия").

## Как запустить:
- Импортируйте проект:
- Загрузите или клонируйте этот репозиторий.
- Откройте проект в Android Studio.
- Запустите приложение:
Нажмите кнопку "Run" в Android Studio.
Выберите эмулятор или устройство для запуска приложения.
Нажмите кнопку:
На экране MainActivity нажмите кнопку "Перейти к Activity 2".
Вы перейдете на экран SecondActivity, где увидите фамилию Золотарев, переданную из MainActivity.

## Код:
````
MainActivity.java:
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import com.example.laba1.SecondActivity;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private Button btn1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btn1 = findViewById(R.id.btn1);

        btn1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("Фамилия", "Золотарев");
                startActivity(intent);
            }
        });
    }
}
````
````
SecondActivity.java:
import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    private TextView textView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        textView = findViewById(R.id.textView);

        String фамилия = getIntent().getStringExtra("Фамилия");
        textView.setText("Переданный параметр: " + фамилия);
    }


}
````
````
activity_main.xml:
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/btn1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Перейти к Activity 2"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
````
````
activity_second.xml:
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Переданный параметр: "
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>}
````
