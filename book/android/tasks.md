# Практические задания

## 0. Ведение Git-репозитория (требования)

1. Зарегистрироваться на `Github` (или аналоги);
2. Создать **ОДИН** репозиторий под `Android`-проект;
3. **НИКОГДА** не менять или создавать новый репозиторий при возникших проблемах с `commit`, `push`;
4. Репозиторий должен содержать 1 (**ОДНУ**) основную ветку, если не противоречит заданию. 
5. На `Git`-репозиторий загружать весть `Android`-проект, **НЕ** просто файлы с `MainActivity.kt` или `activity_main.xml`.

## 1. Разработка простейшего калькулятора
Разработать простую версию калькулятора, используя `TextView`, `Button` и обработчик нажатия (`onClickListener`).

**Требования к "калькулятору"**:

1. Калькулятор должен состояить из кнопок циферблата (от `0` до `9`);
2. Должен включать в состав `Layout` кнопки "действий" ( `+` , `-`, `*`, `/`, `=`);
3. Должен включать в состав `TextView` для отображения результата нажатия на  `Button`'s из пунктов 1 и 2.
4. При нажатии на `=` необходимо обработать строку из `TextView` вручную и выполнить записанные в строку операции;
5. Достаточно обработки **одной** операции, **нет** необходимости обработки нескольких операций.
6. Результата отправить на **Github** (или аналоги) - репозиторий.

## 2. Разработать MediaPlayer для воспроизведения музыки

Цель: Научиться работать с файлами внутренней (или внешней) памяти смартфона, в частности, со звуковыми "дорожками". Исползование класса `MediaPlayer` поможет в создании "каркаса" для MP3-проигрователя. 

1. Создать новое `Activity` для работы с `MediaPlayer`;
2. MediaPlayer должен поддерживать функции: воспроизведение текущего трека, пауза текущего трека, обработка перехода `Activity` в состояние `onPause()`, регулировка громкости, `SeekBar` для отображения текущей длительности трека и его движение, перемотка трека (при помощи `SeekBar`);
3. Возможность вопроизводить музыку из хранилища телефона при помощи  [Permission](https://github.com/sibsutisTelecomDep/android_notes/blob/master/Examples/android_notes/app/src/main/java/com/example/android_notes/activities/MediaPlayerActivity.kt), строки 41-53;
4. Важно реализовать проверку текущего файла на директорию (`isDirectory`);
4. Отображение списка треков на экране `Activity`.

## 3. Местоположение смартфона. Location.
 Цель: получить доступ к данным о местоположении Android-телефона и вывести на экран значения.

 1. Создать `Activity` **Location**, в основном окне `MainActivity` добавить кнопку перехода в новую 'Activity';
 2. Получить доступ к классу [Location](https://developer.android.com/reference/android/location/Location) при помощи **permissions**: `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION`;
 3. Вывести в `Activity` данные о текущем (или последнем известном) местоположении смартфона:
    - [Latitude](https://developer.android.com/reference/android/location/Location#getLatitude());
    - [Longitude](https://developer.android.com/reference/android/location/Location#getLongitude());
    - [Altitude](https://developer.android.com/reference/android/location/Location#getAltitude());
    - [Current Time](https://developer.android.com/reference/android/location/Location#getTime());
4. Получить данные можно при помощи метода [getLastLocation()](https://developer.android.com/develop/sensors-and-location/location/retrieve-current)
5. При каждом обновлении местоположения записывать данные в файл (лучше в формате `Json`);
6. **ДОП. БАЛЛЫ**. Обернуть получение местоположения смартфона в [сервис](https://developer.android.com/develop/background-work/services) с целью записывать данные о местоположении в `backgroud`-режиме (когда приложение закрыто, `activity` не видно пользователю).

## 4. Данные о сетях мобильной связи (2G, 3G, 4G-LTE, 5G-NR).

1.  Создать новое `Activity`, добавив кнопку перехода основном "окне" `MainActivity`;
2. При помощи класса `Telephony`;