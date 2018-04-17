# Bechmark Programs

This repository contains four real-world project from GitHub. We have downloaded the latest version of these programs so that they are all compatible with the latest version of JDK. We have also tested all the programs on JDK 1.8 and 9 both on Windows and Linux platforms.

These programs are **buggy** so you will get `BUILD FAILURE` message if you try to run the command `mvn clean test`. The bugs are not real, we have manually inserted the bugs in the program. In each program we have inserted only one bug. The bugs are such that each mutators M1, ..., M4 can detect and fix them. The table below, shows the programs, the directory that they reside, and the purpose of the bugs they contain.

|Program             |Directory      |Suitable for Testing|
|:------------------:|:-------------:|:------------------:|
|Apache Commons Codec|`commons-codec`|M1                  |
|Joda Time           |`joda-time`    |M2                  |
|Apache Commons Lang |`commons-lang` |M3                  |
|JFree Chart         |`jfreechart`   |M4                  |

Pelase note that all the bugs have been successfully fixed by the Ali's implementation of the mutators M1, ..., M4. Note further that Joda Time requires Maven version 3.5.0, while other benchmark programs run on both versions 3.3.9 and 3.5.0 of Maven without any problem.

Last but not least, each benchmark program is equipped with a default POM file that Ali has prepared for you. You don't need to care other parts of the POM file. The only part that you might want to modify is shown below.

```xml
<plugin>
	<groupId>org.pitest</groupId>
	<artifactId>pitest-maven</artifactId>
	<version>1.4.0-SNAPSHOT</version>
	<configuration>
		<threads>1</threads>
		<mutators>
			<mutator>ALL</mutator>
		</mutators>
	</configuration>
</plugin>
```
As you can see, Maven is going to use version `1.4.0-SNAPSHOT` of PIT (make sure you are modifying and installing correct version of PIT). Furthermore, all mutators (including yours) are activated. Finally, PIT shall use only one thread of execution for mutation (you can increase it up to 4 so as to make your mutation process faster).

## Clonning
You can clone the repository using the following command, which works on both Windows and Unix platforms.

```
git clone https://github.com/ali-ghanbari/SW-Testing-Course-Project-Benchmark-Programs.git
```

