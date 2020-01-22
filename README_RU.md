Travelpayouts Travel App iOS
=================
[![Build Status](https://travis-ci.com/travelpayouts/travel-app-ios.svg?branch=master)](https://travis-ci.com/travelpayouts/travel-app-ios)
#### README in [English](https://github.com/travelpayouts/travel-app-ios/blob/master/README.md)
## Описание
[Travelpayouts](https://www.travelpayouts.com) Travelpayouts Travel App iOS — шаблон приложения для поиска авиабилетов и отелей. Когда пользователь покупает билет или бронирует отель, вы получаете вознаграждение. При разработке официальных приложений Aviasales и Hotellook используется та же самая кодовая база.

Вы можете использовать этот шаблон как основу для своего приложения, либо же просто сделать конфигурацию основных параметров (название, цветовая схема, иконка и др.) и использовать как есть.

Чтобы отслеживать выплаты, посетите нашу партнерскую сеть — [Travelpayouts.com](https://www.travelpayouts.com/).

Узнайте подробнее о доходах в [Travelpayouts FAQ](https://support.travelpayouts.com/hc/ru/articles/203955613-Комиссия-и-выплаты).

## <a name="usage"></a>Использование шаблонного проекта
### 📲 Установка
1. Скачайте себе последний release (не beta) шаблонного проекта отсюда: [https://github.com/travelpayouts/travel-app-ios/releases](https://github.com/travelpayouts/travel-app-ios/releases), файл Source Code (zip).
Либо клонируйте репозиторий, чтобы вести локальную разработку.
2. Для управления зависимостями используется CocoaPods (cocoapods.org). Установите его, если требуется, через Bundler.
Команды установки необходимо выполнять в каталоге проекта (распакованный zip архив, или клонированный репозиторий)
  ```bash
  sudo gem install bundler
  bundle install
  bunble exec pod install --repo-update
  ```

**После этого для работы с проектом используйте файл ```TravelpayoutsTravelApp.xcworkspace```**.

3. Подставьте правильные значения партнерского токена и маркера в файле ```TravelpayoutsTravelApp/default_config.plist``` в параметры ```partner_marker``` и ```api_token```.
Получить их можно на сайте [Travelpayouts](https://travelpayouts.com/).
4. Для публикации приложения в AppStore у него должен быть уникальный идентификатор (bundle id). Изменить его можно в Xcode.
![](https://github.com/travelpayouts/travel-app-ios/raw/master/readme_files/xcode_bundle_id.png)
5. Измените название приложения в файлах ```Info.plist``` и ```LaunchScreen.xib```.
6. В конфиге ```default_config.plist``` дополнительно можно включать и выключать вкладки поиска билетов / отелей, добавлять описание приложения, email для обратной связи, ссылку на веб-сайт приложения, и ссылку на приложение в App Store, которые будут отображаться в разделе «About», плюс локализованные значения для внешних ссылок.
7. Протестируйте приложение на вашем iPhone/iPad или в Xcode симуляторе.
8. Опубликуйте приложение через [App Store Connect](https://appstoreconnect.apple.com)

### 📱 Поддержка версий iOS
Поддерживаются версии, начиная с iOS 10.0

### 🖼 Иконка приложения
**Не забудьте заменить иконку приложения** (по умолчанию, в шаблоне используются иконки, залитые белым цветом). Для этого в папке ```TravelpayoutsTravelApp/AppIcon.xcassets/AppIcon.appiconset``` достаточно заменить картинки (20.png, 29.png, 40.png и т.д.) на свои с аналогичными именами.

### ✈️🏨 Выбор вкладок
1. Если вы хотите убрать вкладку поиска билетов или поиска отелей, поменяйте значения ```flights_enabled``` или ```hotels_enabled``` на NO в конфиге проекта. Вкладку информации убрать таким способом нельзя.
2. Вы можете добавить вкладку с арендой автомобилей. Для этого необходимо вступить в партнерскую программу из списка [Программ Travelpayouts](https://www.travelpayouts.com/programs). Затем нужно сгенерировать партнерскую ссылку и вставить ее в файл ```TravelpayoutsTravelApp/default_config.plist``` в параметр ```car_rental_link```.

### 🔧🌻 Настройка цветов
Выбрать цветовую схему можно в файле ```ColorSchemeManager.swift```. Достаточно прописать в переменной ```current``` одно из значений BlackColorScheme() / PurpleColorScheme(). Или установить значение CustomColorScheme() и настроить схему по своему усмотрению в файле ```CustomColorScheme.swift```.
Вот список основных полей с пояснениями:

|Название|Описание|
|--------|--------|
mainColor | Основной цвет приложения
actionColor | Цвет выделения основных действий

Более детально настроить цвета можно в файле ```ASTJRC.swift``` путем переопределения методов базового класса ```JRC```.

### 🔧📄 Настройка текста
Вы можете изменить заголовок поисковых форм в файле ```AppLocalizations.swift```. Раскомментируйте и измените переменную, соответствующую нужной форме. Строка может быть локализована на нескольких языках, если вы используете ```NSLocalizedString``` и добавите все переводы в файлы ```Localizable.strings```.

### 🤑 Настройка рекламы Appodeal
Для того чтобы вы могли получать дополнительную прибыль с рекламы, мы интегрировали в приложение рекламный SDK [Appodeal](https://www.appodeal.com/). Для его настройки задайте параметр ```appodeal_key```  в конфиге ```default_config.plist``` (получите ключ API, зарегистрировавшись в [Appodeal](https://www.appodeal.com/)).
По умолчанию, реклама будет отображаться на экранах ожидания поиска билетов и отелей.

### ⭐️ Обратная связь и оценка приложения
Задайте значения параметрам ```feedback_email``` и ```itunes_link``` в файле ```default_config.plist``` чтобы активировать пункты меню "Написать нам письмо" и "Оценить приложение".
Рекомендованный формат ссылки ```itunes_link```: ```https://itunes.apple.com/app/id1234567890?action=write-review```, где ```id1234567890``` это идентификатор опубликованного приложения.

### 🏭 Использование Firebase
Шаблонное приложение поддерживает сервисы **Firebase**. Для этого нужно подключить приложение в консоли Firebase, скачать и скопировать с заменой в папку ```TravelpayoutsTravelApp``` файл ```GoogleService-Info.plist``` и перевести флаг ```firebase_enabled``` в состояние ```YES``` в ```default_config.plist```.  Из коробки поддерживается работа аналитики, а именно поиск / переход на билет / покупка в билетной части и поиск / выбор отеля / покупка в отельной части.
