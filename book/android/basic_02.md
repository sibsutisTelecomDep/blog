# 2. Построение пользовательского интерфейса (основы)
При создании первого приложения, вы могли увидеть интерфейс работы с **"внешним видом"** вашего Android-приложения. 

По умолчанию, файл `/layout/activity_main.xml` определяет разметку первой `"страницы" (activity)`, которую видит, с которой взаимодействует пользователь.

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/book/figures/android/basic_01_main_xml.PNG?raw=true)
Рис. 1. Окно макета `Activity`.

Макет `Activity`, по умолчанию, определяет два виджета (`widgets`): 
- ConstraintLayout;
- TextView;
- p.s. Button (из примера выше) мы добавили **после** создания первого приложения.

Виджеты представляют собой структурные элементы пользовательского интерфейса. Существую различные виджеты по своим функциям\свойствам: вывод текста на экран, ввод текста, нажатие кнопки и другие взаимодействия с пользователем. В примере выше `Button`, `TextView` - это лишь разновидности виджетов.

Android SDK включает множество виджетов, которые являются дочерним классом класса `View`. Таким образом, каждый виджет является экземпляром класса `View`, как и отражено на рисунке ниже. 

![alt text](https://github.com/sibsutisTelecomDep/blog/blob/main/book/figures/android/android_class_hierarchy_view.svg?raw=true )

Рис. 2. Иерархия класса `View`. [Источник изображения](https://www.mathematik.uni-marburg.de/~thormae/lectures/graphics1/media/vectorart/android_class_hierarchy_view.svg).

В нашем примере, на рис. 1 показан экран с виджетами `ConstraintLayout`, `TextView` и `Button`.

## Иерархия представлений виджетов
Все виджеты в `Activity` входят в **иерархию представлений**. 


```{mermaid}

flowchart TD 
    ConstraintLayout["`**ConstraintLayout**
    xmlns:android=http..//schemas.android.com/apk/res/android
    android:id=@+id/main
    android:layout_width=match_parent
    android:layout_height=match_parent
    tools:context=.MainActivity`"]
    TextView["`**TextView**
    android:id=@+id/textView2
    android:layout_width=wrap_content
    android:layout_height=wrap_content
    android:text=Hello World!
    ...`"]
    Button["`**TextView**
    android:id=@+id/go_to_second_activity
    android:layout_width=wrap_content
    android:layout_height=wrap_content
    android:text=SecondActivity
    ...`"]

    style ConstraintLayout text-align:left
    style TextView text-align:left
    style Button text-align:left

    ConstraintLayout --> TextView
    ConstraintLayout --> Button
```
Рис. 3. Иерархия представлений виджетов и атрибутов `Activity`.