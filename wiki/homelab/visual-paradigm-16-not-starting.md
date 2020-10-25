# Visual Paradigm v16.x not starting on Windows 10
I ran into issues when trying to start Visual Paradigm on Windows 10. The installer would run perfectly fine, but the application itself would not start.

### Environment
OS: Windows 10 Home, 64-bit
Java: 11.0.9, Oracle JDK

### Solution
1. In `C:\Program Files\Visual Paradigm\bin\` create file called `run.bat`
2. In this file paste the following:
```
..\jre\bin\java -Xms256m -Xmx1024m -cp ".;..\lib\vpplatform.jar;..\lib\jniwrap.jar;..\lib\jhall.jar;..\lib\vpuml-help.jar;..\lib\winpack.jar;..\lib\vpupdate.jar;..\lib\openapi.jar;..\ormlib\orm.jar;..\lib\jh.jar;..\lib\lib01.jar;..\lib\lib02.jar;..\lib\lib03.jar;..\lib\lib04.jar;..\lib\lib05.jar;..\lib\lib06.jar;..\lib\lib07.jar;..\lib\lib08.jar;..\lib\lib09.jar;..\lib\lib10.jar" RV debug
```
3. Launch Visual Paradigm using `run.bat`
4. Optionally, create a shortcut to e.g your desktop. You must always launch Visual Paradigm using `run.bat`
