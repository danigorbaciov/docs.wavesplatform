# Альтернативный метод (Установка SBT)

Можно запустить ноду на любой системе, которая поддерживает java. Для **Ubuntu**, SBT packageAll ‌поддерживает только DEB пакет но для других операционных систем, можно использовать ZIP или fat JAR архив.  Чтобы запустить ноду Waves, выполните следующие шаги:

## 1. Подготовка среды

* ### Установка Java

```bash
sudo apt-get update
sudo apt-get install default-jre default-jdk
```

* ### Установка SBT

Следуйте шагам установки SBT в зависимости от операционной системы ([Mac](https://www.scala-sbt.org/1.0/docs/Installing-sbt-on-Mac.html), [Windows](https://www.scala-sbt.org/1.0/docs/Installing-sbt-on-Windows.html), [Linux](https://www.scala-sbt.org/1.0/docs/Installing-sbt-on-Linux.html)).

## 2. Получение исходных кодов

```bash
git clone git@github.com:wavesplatform/Waves.git
cd Waves
```

## 3. Запуск тестов

```bash
sbt test
```

## 4. Сборка пакетов

* ### Mainnet

```bash
sbt packageAll
```

* ### Testnet

```bash
sbt -Dnetwork=testnet packageAll
```

## 5. Установка DEB пакета

DEB находится в целевой папке. Замените '*' на фактическое название пакета:

```bash
sudo dpkg -i target/*.deb
```

## 6. Запуск Fat JAR

Замените **waves-all*.jar** фактическим названием jar файла (название должно содержать слово "all"):

```bash
java -jar target/waves-all*.jar path/to/config/file
```

<note type="info" title="">Для OSX - предпочтительно выбрать **homebrew**. Можно установить java с brew cask install java и sbt с brew instal sbt@1. Шаги запуска/теста общие для всех операционных систем \(но в Windows следует использовать ‘\' вместо '/').</note>
