# 5. Работа виджетами из Activity
Снова про `root` класс для всех виджетов. 
# View
Android SDK включает множество виджетов, которые являются дочерним классом класса `View`. Таким образом, каждый виджет является экземпляром класса `View`, как и отражено на рисунке ниже. 

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/book/figures/android/android_class_hierarchy_view.svg?raw=true )

Рис. 1. Иерархия класса `View`. [Источник изображения](https://www.mathematik.uni-marburg.de/~thormae/lectures/graphics1/media/vectorart/android_class_hierarchy_view.svg).


# Создание нового Activity

Для начала, создадим новое `Activity`, в котором будем создавать виджеты и работать из `Activity`.

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/book/figures/android/basic_05_create_new_activity.png?raw=true )

Рис. 2. Создание нового `Activity`.

Далее, вам откроется окно с настройками нового `Activity`. Необходимо ввести имя и поставить галочку на автоматическое создание файла `layout` для `Activity`.

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/book/figures/android/basic_05_create_new_activity_naming.png?raw=true )

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

Где мы можем увидеть наше новое `Activity`.