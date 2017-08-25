---
layout: post
title: Gradle - The Best Automation Build Tool of 21 Century
date: 2015-06-28 18:58:17
tags:
- Gradle
categories: 
- Java
- Gradle
description: The tutoria will show you how to use Gradle to build your project.
---

# 环境
* Gradle版本4.1(Gradle 2.X测试过是不能使用该插件的)


# build.gradle
```groovy

apply plugin: 'java'
apply plugin: "jacoco"

sourceCompatibility = 1.8

repositories {
    mavenCentral()
}

dependencies {
    testCompile group: 'junit', name: 'junit', version: '4.11'
}

jacoco {
    toolVersion = "0.7.6.201602180812"
    reportsDir = file("$buildDir/customJacocoReportDir")
}

jacocoTestCoverageVerification {
    violationRules {
        rule {
            limit {
                minimum = 0.8
            }
        }

        rule {
            enabled = false
            element = 'CLASS'
            includes = ['org.gradle.*']

            limit {
                counter = 'LINE'
                value = 'TOTALCOUNT'
                maximum = 0.3
            }
        }
    }
}

```

### 生成单元测试覆盖率报表
```bash
gradle --rerun-tasks test jacocoTestReport
```
> jacocoTestReport不会随着build这个task一起执行，需要单独执行
> 添加`--rerun-tasks`是为了让Gradle强制执行task，Gradle默认会跳过up-to-date的task
> 先执行`test`的task是必须的，如果不先执行test，没有测试的源数据，jacoco会跳过jacocoTestReport这个task


### 检查单元测试覆盖率是否达标
```bash
gradle --rerun-tasks test jacocoTestCoverageVerification
```
> `jacocoTestCoverageVerification`不会随着`build`这个task一起执行，需要单独执行
> 添加`--rerun-tasks`是为了让Gradle强制执行task，Gradle默认会跳过up-to-date的task
> 先执行`test`的task是必须的，如果不先执行test，没有测试的源数据，jacoco会跳过jacocoTestCoverageVerification这个task


### 多模块项目使用jacoco
多模块的project，如果在根目录下执行`jacocoTestCoverageVerification`的task，不会有任何效果，因为根项目下没有java类，所以单元测试覆盖率肯定不会失败的。          
需要在各个子项目中添加jacoco插件。



