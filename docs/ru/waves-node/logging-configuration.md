# Конфигурация логирования

## Про Framework

Ноды Waves используют [logback](https://logback.qos.ch/documentation.html) framework для логирования. Нода поставляется с готовой [конфигурацией логирования](https://logback.qos.ch/manual/configuration.html), отбразец стандартного файла `logback.xml` можно найти [тут](https://github.com/wavesplatform/Waves/blob/master/node/src/main/resources/logback.xml).

Чтобы переопределить стандартные настройки файла `logback.xml` ноды, создайте свой `logback.xml` в папке `/etc/waves/`. Воспользуйтесь секцией [Конфигурация собственного Logback.xml](#own-logback) для настройки.

До версии ноды 1.1.6, логи записывалиьс в STDOUT и `/var/log/waves.log` файл в удобочитаемом [формате](https://github.com/wavesplatform/Waves/blob/master/node/src/main/resources/logback.xml). После выпуска ноды версии 1.1.6, для уменьшения объемов логов, которые нода способна производить под большой нагрузкой, по умолчанию логи больше не пишутся в `waves.log`. Тем не менее, запись в отдельный файл можно [включить](#enable-traces).

Также waves.log теперь перезаписывается, при достижении лимита размера (по умолчанию 100 mb), в дополнении к ежедневной ротации.

Включение или выключение логирования осуществляется путём добавления параметров в `application.ini`, через командную строку или в `logback.xml`. Нет необходимости перезапускать ноду, после изменения настроек связанных с логированием.

Уровни логирования приведены далее в секции [Уровни логирования](#loglevels).

## Конфигурация собственного Logback.xml <a id="own-logback"></a>

Чтобы переопределить параметры ноды в существующем `logback.xml`, используйте тэг `included` в `/etc/waves/logback.xml`.

**Пример**:

```xml
<included>
    <property name="logback.file.level" value="TRACE"/>
</included>
```

## Активировать запись логов <a id="enable-traces"></a>

Добавьте `<property name="logback.utx-trace.enabled" value="true" />` в `logback.xml`.

Если логирование активировано, запись будет вестись в `/var/log/utx-trace.log`.

## Поменять путь хранения лог файла

* Если вы установили ноду из архива, отредактируйте `/etc/waves/application.ini`.
* Если вы запустили ноду из файла jar, используйте настройки Java, например, `java -Dsomeoption=somevalue -jar /path/to/waves-all.jar /path/to/config`

Стандартная папка это `/var/log`. Чтобы поменять путь, используйте команду `-Dlogback.file.directory=/path/to/directory/for/logs`. Обратите внимание, что нода должна иметь доступ для записи файлов в заданной папке.

## Настройка сети

* mainnet: `/etc/waves/`
* testnet: `/etc/waves-testnet/`

## Настрока уровня логирования для STDOUT

* `Dlogback.stdout.level={LEVEL_OF_LOGGING}`. По умолчанию уровень для STDOUT имеет значение `INFO`.

## Настройка уровня логирования для файлов

* `-Dlogback.file.level={LEVEL_OF_LOGGING}`. Уровень по умолчанию `DEBUG`.

## Стандартные лимиты для файлов логов

Изначально в [logback.xml](https://github.com/wavesplatform/Waves/blob/master/node/src/main/resources/logback.xml) заданы следующие лимиты:

* Логи старше 30 дней удаляются.
* Если общий размер логов превышает 1Gb, тогда самые старые логи удаляются, для соответствия данному лимиту.

Чтобы поменять эти лимиты, отредактируйте следующие строки в `logback.xml`:

```xml
<maxHistory>30</maxHistory>
<totalSizeCap>1GB</totalSizeCap>
```

## Включить логирование в файлы `JSON`

Задайте свою собственную конфигурацию логирования и задайте путь до неё следующей командой:

```bash
-Dlogback.configurationFile=/path/to/your/logback.xml
```

## Уровни логирования <a id="loglevels"></a>

1. `OFF` - логирование выключено. Подойдёт если вы хотите выключить логирование в файл или STDOUT;
2. `ERROR` - критически ошибки. Пожуйста читайте такие сообщения;
3. `WARN` - предупреждающие сообщения. Нода может продолжать работу, но стоит проверить в чём проблема;
4. `INFO` - важные сообщения. Система работает нормально;
5. `DEBUG` - информация для отладки;
6. `TRACE` - информация для отладки, когда DEBUG не помогает \(редкие случаи\).

Более низкие уровни логирования включены в более высокие. Напирмер, `DEBUG` включает в себя все более высокие уровни: `INFO`, `WARN` и `ERROR`.
