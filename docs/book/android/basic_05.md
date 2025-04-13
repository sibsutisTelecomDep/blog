# 5. Работа виджетами из Activity
Снова про `root` класс для всех виджетов. 
# View
Android SDK включает множество виджетов, которые являются дочерним классом класса `View`. Таким образом, каждый виджет является экземпляром класса `View`, как и отражено на рисунке ниже. 

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/docs/figures/android/android_class_hierarchy_view.svg?raw=true )

Рис. 1. Иерархия класса `View`. [Источник изображения](https://www.mathematik.uni-marburg.de/~thormae/lectures/graphics1/media/vectorart/android_class_hierarchy_view.svg).


## Создание нового Activity

Для начала, создадим новое `Activity`, в котором будем создавать виджеты и работать из `Activity`.

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/docs/figures/android/basic_05_create_new_activity.png?raw=true )

Рис. 2. Создание нового `Activity`.

Далее, вам откроется окно с настройками нового `Activity`. Необходимо ввести имя и поставить галочку на автоматическое создание файла `layout` для `Activity`.

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/docs/figures/android/basic_05_create_new_activity_naming.PNG?raw=true )

Рис. 3. Настройка нового `Activity`.

Замем вы увидите изменения в структуре проекта: добавится файл с кодом `имя_класса.kt`, появится к нему файл `имя_layout.xml`. Также, не мало важным является добавление `Activity` в файл `AndroidManifest.xml`, который является **основой** вашего проекта.

Содержание файла `AndroidManifest.xml`:

```xml
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
        android:theme="@style/Theme.Android_notes"
        tools:targetApi="31">
        <activity
            android:name=".activities.ViewExamples"
            android:exported="false" />
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

Где мы можем увидеть наше новое `Activity` в списке проекта.

### Переход между Activity (Intent, вкратце)

В рамках "удобства" по работе с несколькими `Activity` рассмотрим небольшой пример работы класса [Intent]()

`Intent` — это абстрактное описание операции, которая должна быть выполнена. Его можно использовать с [startActivity](https://developer.android.com/reference/android/content/Context#startActivity(android.content.Intent)) для запуска [Activity](https://developer.android.com/reference/android/app/Activity), [broadcastIntent](https://developer.android.com/reference/android/content/Context#sendBroadcast(android.content.Intent)) для отправки его любым заинтересованным компонентам [BroadcastReceiver](https://developer.android.com/reference/android/content/BroadcastReceiver) и [Context.startService(Intent)](https://developer.android.com/reference/android/content/Context#startService(android.content.Intent)) или [Context.bindService(Intent, BindServiceFlags, Executor, ServiceConnection)](https://developer.android.com/reference/android/content/Context#bindService(android.content.Intent,%20android.content.Context.BindServiceFlags,%20java.util.concurrent.Executor,%20android.content.ServiceConnection)) для связи с фоновой службой [Service](https://developer.android.com/reference/android/app/Service).

Для начала, нам понадобится только метод `startActivity()`. Добавим переход на другое `Activity` при помощи `Button` во время нажатия (`setOnClickListener`).
Добавим кнопку в файле `activity_имя.xml`:

```xml
<Button
    android:id="@+id/bViews"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Views" />
```

Инициализируем кнопку в коде `ИМЯ_Activity.kt`, выделяя память под кнопку в методе `onCreate()`, инициализируя обработчик нажатия на кнопку в методе `onResume()` (когда `Activity` уже видна пользователю):

```Kotlin
class MainActivity : AppCompatActivity() {

    private lateinit var bViewExamples: Button

    // onCreate() – вызывается при первом создании Activity
    override fun onCreate(savedInstanceState: Bundle?) {

        ...
        ...
        bViewExamples = findViewById<Button>(R.id.bViews)
    }

    override fun onResume() {
        super.onResume()
        bViewExamples.setOnClickListener({
            val randomIntent = Intent(this, ViewExamples::class.java)
            startActivity(randomIntent)
        });
    }
```
Из обработчика нажатия мы видим создание экземпляра класса `Intent`, используя конструктор `public Intent(Context packageContext, Class<?> cls)`:

```Kotlin
val randomIntent = Intent(this, ViewExamples::class.java)
startActivity(randomIntent)
```

Согласно документации аргументами функции являются:
```
Создание `Intent` для определенного компонента.  Это обеспечивает удобный способ создания `Intent`, которое предназначено для выполнения `hard-coded` класса.

Params:
packageContext – A Context of the application package implementing this class. 
cls – The component class that is to be used for the intent.
```

Первый параметр – это `Context`. `Activity` является подклассом `Context`, можем использовать запись `ИМЯ_КЛАССА_В_КОТОРОМ_НАХОДИМСЯ.this`, или укороченную запись `this`.

Метод `startActivity(randomIntent)` выполняет переход на необходимый нам класс, т.е. `Activity`.


## Виджеты (Views)

### TextView

Здесь будет примерчик еще фикс abrc

### Button

### 