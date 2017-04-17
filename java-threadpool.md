---
layout: post
title: Thread Pool
date: 2017-04-15 14:50:00
tags:
- Windows
categories: Windows
description: What is API and SPI.
---





# ScheduleExecutorService定时周期执行指定的任务

```java
public class App {
    public static void main(String[] args) {
        runScheduleTask();
        for (int i=0;i<10;i++) {
            System.out.println("Main thread......");
            Thread.sleep(2*1000);
        }
    }

    private static void runScheduleTask(){
        Executors.newSingleThreadScheduledExecutor().scheduleAtFixedRate(
                new Runnable() {
                    @Override
                    public void run() {
                        System.out.println("Execute thread......");

                    }
                },10,2, TimeUnit.SECONDS
        );
    }
}
```
程序的输出，程序不会退出:
```text
Main thread......
Execute thread...
Main thread......
Execute thread......
Main thread......
Execute thread......
Main thread......
Execute thread......
Main thread......
Execute thread......
Execute thread......
Execute thread......
Execute thread......
```

