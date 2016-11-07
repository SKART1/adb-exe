[![Release](https://jitpack.io/v/User/Repo.svg)](https://jitpack.io/#SKART1/adb-exe)

# adb-exe
Repo with adb from android-sdk as artifact


# Warning 
All rights to adb executable belongs to it`s respected owners. Goal of this repository is only 
to give more flexibility for using this artifacts
 

# Usage

## Getting dependencies

At this moment this artifact is not present in any official maven repositories. But you may use [jitpack.io](https://jitpack.io/)
an awesome project which pareses open-source projects on github, produces artifacts and hold them. How to tune it see 
[documentation](https://github.com/jitpack/jitpack.io) 


## Putting them in desired location
If you are using `maven` there is `maven-dependency-plugin` which allows you to copy this dependency anywhere you desire:
  
```xml
 <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-dependency-plugin</artifactId>
    <version>2.7</version>
    <executions>
        <execution>
            <id>unpack-dependency</id>
            <phase>compile</phase>
            <goals>
                <goal>unpack</goal>
            </goals>
            <configuration>
                <ignorePermissions>false</ignorePermissions>
                <artifactItems>
                    <artifactItem>
                        <groupId>com.github.SKART1</groupId>
                        <artifactId>adb-exe</artifactId>
                        <version>aa77dc91cf</version> 
                        <type>zip</type>
                        <overWrite>true</overWrite>
                        <outputDirectory>${basedir}/src/main/resources/containers/shared/adb</outputDirectory>
                        <destFileName>adb</destFileName>
                    </artifactItem>
                </artifactItems>
            </configuration>
        </execution>
    </executions>
 </plugin>
```

**Flat**. To make artifacts flat you may use `maven-antrun-plugin`

```xml
    <plugin>
        <artifactId>maven-antrun-plugin</artifactId>
        <executions>
            <execution>
                <phase>compile</phase>
                <goals>
                    <goal>run</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <tasks>
                <move todir="${basedir}/src/main/resources/containers/shared/adb">
                    <fileset dir="${basedir}/src/main/resources/containers/shared/adb"/>
                    <mapper type="flatten"/>
                </move>
            </tasks>
        </configuration>
    </plugin>
```
            