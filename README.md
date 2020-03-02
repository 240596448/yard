# Yet anoter release downloader (YARD)

*Пока рабочее название*

Приложение oscript для "правильной" загрузки релизов конфигураций 1С (возможно не только конфигураций и не только от 1С).

## Сценарий использования

1. Настроечный файл JSON с указанием:

   - "пути" к релизам на сайте 1С
   - Папки для скачивания
   - Путь к каталогу шаблонов
   - Путь к служебной базе
   - Путь к хранилищу
   - путь к репозитарию

2. Порядок выполнения:

   - скачиваем релиз с сайта 1С (в указанную в настройках папку)
   - Устанавливаем релиз в каталог шаблонов, если есть полный, то берем полный иначе обновление (?)
   - открываем служебную базу (подключенную к хранилищу), выполняем обновление, помещаем результат в хранилище (используем v8runner)
   - Если скачано было только обновление, то выгружаем конфигурацию поставщика в папку релиза в каталоге шаблонов (надо или нет не понятно, функцию нужно предусмотреть, но использовать опционально)
   - очищаем каталог исходников
   - Выгружаем конфигурацию в репозитарий git (используем gitrunner) (можно отсюда взять полную конфигурацию поставщика)

## Модули

- src\yard.os - скачивание релизов
- experimental\1cdn-curl.os - экспериментальный скрипт получения списка конфигураций и версий с использованием утилиты curl

## Запуск

- yard.os <пользователь> <пароль>
- 1cdn-curl.os <пользователь> <пароль>

## Фильтр (yard.os)

Пока в коде:
- переменная **"ФильтрКонфигураций"** - регулярное выражение (или массив) для фильтра конфигураций по имени, как оно указано на сайте 1С
- переменная **"ФильтрВерсий"** - регулярное выражение (или массив) для фильтра версий по номеру версии, как оно указано на сайте 1С
- переменная **"ФильтрЗагрузок"** - регулярное выражение (или массив) для фильтра ссылок на загрузку файлов по заголовку ссылки, как оно указано на сайте 1С