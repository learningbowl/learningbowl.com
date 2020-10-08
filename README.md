```sh
<?xml version="1.0" encoding="utf-8" ?>
<nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.nlog-project.org/schemas/NLog.xsd NLog.xsd"
      autoReload="true"
      throwExceptions="false"
      internalLogLevel="Off" internalLogFile="c:\temp\nlog-internal.log">
  <targets>
    <target name="logfile" xsi:type="File" fileName="${basedir}/logs/${shortdate}.log" />
    <target name="rotatelogfile" xsi:type="File"
           layout="${longdate} ${logger} ${level} ${message} ${exception:format=tostring}"
           fileName="${basedir}/${logger}-${shortdate}.log"
           archiveFileName="${basedir}\Archive\${logger}-${shortdate}.{####}.log"
           archiveAboveSize="5242880"
           archiveNumbering="Sequence"
           concurrentWrites="true"
           keepFileOpen="false"
           encoding="iso-8859-2" />
    <target name="levelfile" xsi:type="File"
        layout="${longdate} ${logger} ${message} ${exception:format=tostring}"
        fileName="${basedir}/logs/${level}.log" />
  </targets>
  <rules>   
    <logger name="*" minlevel="Debug" writeTo="rotatelogfile" />
  </rules>
</nlog>

 private static Logger NLogger = LogManager.GetLogger("PTXXXXX");
 NLogger.Debug("Test Log Started");

```
