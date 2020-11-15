# getskin
![GitHub release (latest by date)](https://img.shields.io/github/v/release/FeelinVoids_/getskin)

Позволяет получать информацию о скинах игроков Minecraft:
- Имя
- UUID
- base64
- URL png картинки
- /give команда для получения головы со скином

Можно работать как с модулем Python, так и через команды в консоли.

![](https://i.imgur.com/qPk9fr3.png)

## Установка

    python -m pip install git+https://github.com/FeelinVoids/getskin.git

## Использование в Python

Пример использования модуля в Python с демонстрацией всех
методов можно найти в [test.py](./test/test.py).

Результаты выполнения теста: [test.txt](./test/).

## Консольные команды

- [Самый простой способ](#simple)
- [info](#info)
- [download](#download)
- [head](#head)
- [base64](#base64)

### Самый простой способ<a name="simple"></a>
Для получения всей информации о скине, достаточно выполнить следующую команду:

    getskin Notch

Команда выведет имя пользователя, UUID, URL скина, base64, а также команды
`/give` на получение головы со скином.

Также доступен режим работы с аргументами:

### --info (--i)<a name="info"></a>
Выводит всю информацию о скине. Эквивалентно просто `getskin <имя/UUID>`.

Примеры:

    getskin --info Notch
    getskin --i Notch

Результат был на скриншоте выше.

### --download (--d)<a name="download"></a>
Скачивает скин по пути `--path` (`--p`) (может быть как путём в папку, так и непосредственно в файл).

Если оставить параметр пути пустым, скин будет скачан в текущую
рабочую директорию.

Возвращает итоговый путь. Примеры:

    getskin --download Notch --path /home/
    # Или
    getskin --d Notch --path /home/

### --head (--d)<a name="head"></a>
Генерирует команду получения головы со скином.  

Параметр `--version` (`--v`) - версия майнкрафта. Может быть от `1.8` до `1.16`.
Способы получения голов разные в версиях:
- 1.8 - 1.12
- 1.13 - 1.15
- 1.16 - ... 

Параметр `--selector` (`--s`) - Кому выдавать голову.  
По умолчанию - `@p`.

    getskin --head Notch --selector @p --version 1.16
    # Или
    getskin --h Notch --s @p --v 1.16

Результат:

    /give @p minecraft:player_head{display:{Name:"{\"text\":\"Notch\"}"}, SkullOwner:{Id:[I;110787060,1156138790,-1514210135,238594805],Properties:{textures:[{Value:"eyJ0ZXh0dXJlcyI6IHsiU0tJTiI6IHsidXJsIjogImh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMjkyMDA5YTQ5MjViNThmMDJjNzdkYWRjM2VjZWYwN2VhNGM3NDcyZjY0ZTBmZGMzMmNlNTUyMjQ4OTM2MjY4MCJ9fX0="}]}}} 1


### --base64<a name="base64"></a>
Выводит хеш base64 данных скина.  
(Используется при получении голов, установке блоков и в конфигах плагинов для сервера)

    getskin --base64 Notch
    # Или
    getskin --b Notch

Результат:

    eyJ0ZXh0dXJlcyI6IHsiU0tJTiI6IHsidXJsIjogImh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMjkyMDA5YTQ5MjViNThmMDJjNzdkYWRjM2VjZWYwN2VhNGM3NDcyZjY0ZTBmZGMzMmNlNTUyMjQ4OTM2MjY4MCJ9fX0=