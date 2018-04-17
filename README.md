# Bechmark Programs

This repository contains four real-world projects from GitHub. We have downloaded the latest versions of these programs so that they are all compatible with the latest version of JDK. We have also tested all the programs using JDK 1.8 and 9 both on Windows and Linux platforms.

These programs are **buggy**, so you will get `BUILD FAILURE` message if you try to run the command `mvn clean test`. The bugs are not real, we have manually inserted the bugs in the programs. In each program we have inserted only one bug. The bugs are such that each mutators M1, ..., M4 can detect and fix them. The table below, shows the programs, the directory that they reside, and the purpose of the bugs they contain.

|Program             |Directory      |Suitable for Testing|Citation                                    |
|:------------------:|:-------------:|:------------------:|:------------------------------------------:|
|Apache Commons Codec|`commons-codec`|M1                  |https://github.com/apache/commons-codec.git |
|Joda Time           |`joda-time`    |M2                  |https://github.com/JodaOrg/joda-time.git    |
|Apache Commons Lang |`commons-lang` |M3                  |https://github.com/apache/commons-lang.git  |
|JFree Chart         |`jfreechart`   |M4                  |https://github.com/jfree/jfreechart.git     |

Pelase note that all the bugs have been successfully fixed by the Ali's implementation of the mutators M1, ..., M4. Note further that Joda Time requires Maven version 3.5.0, while all other benchmark programs run on both versions 3.3.9 and 3.5.0 of Maven without any problem. Linux systems, by default install version 3.3.9 of Maven, thus you need to be careful if you are using a Linux Operating System. You can query the version of your Maven using the command `mvn -version`.

Last but not least, each benchmark program is equipped with a default POM file that Ali has prepared for you. You don't need to care about other parts of the POM file. The only part that you might want to modify is shown below.

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
As you can see, Maven is going to use version `1.4.0-SNAPSHOT` of PIT (so make sure you are modifying and installing the correct version of PIT). Furthermore, all mutators (including yours) are activated. Finally, PIT shall use only one thread of execution for mutation (you can increase it up to 4 so as to make your mutation process faster).

## Clonning
You can clone the repository using the following command, which works on both Windows and Unix platforms.

```
git clone https://github.com/ali-ghanbari/SW-Testing-Course-Project-Benchmark-Programs.git
```

## Testing
Since the programs are modified to become buggy, you should not execute test cases. Please use the command `mvn clean test -DskipTests` to compile the source files and test cases without executing the test cases. After that you can execute the command `mvn org.pitest:pitest-maven:mutationCoverage` to run your version of PIT.