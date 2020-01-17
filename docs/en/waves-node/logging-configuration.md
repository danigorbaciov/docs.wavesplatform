# Logging Configuration

## About the Framework

Waves nodes use [logback](https://logback.qos.ch/documentation.html) framework for log writing. The node is shipped with embedded [logback configuration](https://logback.qos.ch/manual/configuration.html), you can find the default `logback.xml` file example [here](https://github.com/wavesplatform/Waves/blob/master/node/src/main/resources/logback.xml).

To override the node's `logback.xml` settings, create own `logback.xml` in `/etc/waves/`. Refer to [Configuring Own Logback.xml](#own-logback) section to configure it.

Prior to node version 1.1.6, the logs were written to STDOUT and to `/var/log/waves.log` file in a human-readable format by [default](https://github.com/wavesplatform/Waves/blob/master/node/src/main/resources/logback.xml). After the node 1.1.6 version release, to reduce the amount of logs the node produces under heavy load,  by default the execution traces are no longer written to `waves.log`. However, writing the traces to separate file can be [enabled](#enable-traces).

Also waves.log is now rotated when the size limit is reached (100 mb by default), in addition to daily rotation.

Enabling or disabling of the logging features is done by adding properties to `application.ini`, via command line or in `logback.xml`. It is not necessary to restart the node after changing logging-related settings.

The log levels are listed in [Levels of Logging](#loglevels) section below.

## Configuring Own Logback.xml <a id="own-logback"></a>

To redefine the existing node's `logback.xml` properties, use the `included` tag in `/etc/waves/logback.xml`.

**Example**:

```xml
<included>
    <property name="logback.file.level" value="TRACE"/>
</included>
```

## Activate Writing the Traces <a id="enable-traces"></a>

Add `<property name="logback.utx-trace.enabled" value="true" />` to `logback.xml`.

If writing the traces is activated, it will be written to `/var/log/utx-trace.log`.

## Change Log File Location

* If you setup node from the package, edit `/etc/waves/application.ini`.
* If you run the node from the jar, use Java's options, for example, `java -Dsomeoption=somevalue -jar /path/to/waves-all.jar /path/to/config`

The default directory is `/var/log`. To change the logs directory, use `-Dlogback.file.directory=/path/to/directory/for/logs`. Note that the node must have access rights to write files to the seleted directory.

## Setting the Network

* mainnet: `/etc/waves/`
* testnet: `/etc/waves-testnet/`

## Setting Logging Level for STDOUT

* `Dlogback.stdout.level={LEVEL_OF_LOGGING}`. The default level for STDOUT is `INFO`.

## Setting Logging Lever for Files

* `-Dlogback.file.level={LEVEL_OF_LOGGING}`. The default level is `DEBUG`.

## Default Limits for File Logs

Initially, in [logback.xml](https://github.com/wavesplatform/Waves/blob/master/node/src/main/resources/logback.xml) the following limits are set:

* Logs older than 30 days are deleted.
* If total size of the logs is more than 1Gb, the oldest logs are deleted to fit this limit.

To change this limits, edit the following lines in `logback.xml`:

```xml
<maxHistory>30</maxHistory>
<totalSizeCap>1GB</totalSizeCap>
```

## Enable Logging to `JSON` Files

Define your own logging configuration and specify the path to it with the following option:

```bash
-Dlogback.configurationFile=/path/to/your/logback.xml
```

## Levels of Logging <a id="loglevels"></a>

1. `OFF` - logging is disabled. Useful when you want to disable file or STDOUT logs;
2. `ERROR` - severe errors. Please read these messages;
3. `WARN` - warning messages. The Node can work, but it is better to check the problem;
4. `INFO` - important messages. System works normally;
5. `DEBUG` - information for debugging;
6. `TRACE` - information for debugging, when DEBUG doesn't help \(rare cases\).

Lower levels of logging are included in the higher. For example, `DEBUG` includes itself and all the higher levels: `INFO`, `WARN` and `ERROR`.
