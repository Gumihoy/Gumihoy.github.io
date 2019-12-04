---
title: Java Agent详解
date: 2019-08-13 11:29:09
categories: 
    - Java
    - JavaAgent
tags:
    - Java
    - JavaAgent
---


`Java Agent`就是利用 `Java5` 提供的 `Instrumentation` 机制。
在 `Java SE 5` 中，`Instrument` 要求与应用一块启动（设置参数启动 `-javaagent:agent.jar` ）
在 `Java SE 6` 里面，`Instrumentation` 被赋予了更强大的功能：启动后的 instrument、本地代码（native code）instrument，以及动态改变 classpath 等等.


`Java Agent`在不侵入代码字节码注入的方式对应用功能的增强和修改。


<!-- more -->


## 代码实现步骤

### 1、代码

**一、以vm参数的方式载入，在Java程序的main方法执行之前执行（JDK1.5和以上）**

```java
// 如果同时存在下面两个方法，第一个方法先执行

public static void premain(String arguments, Instrumentation instrumentation) {
}

public static void premain(String arguments) {
}

```


**二、以Attach的方式载入，在Java程序启动后执行（JDK1.6和以上）**

```java
// 如果同时存在下面两个方法，第一个方法先执行

public static void agentmain(String arguments, Instrumentation instrumentation) {

}
public static void agentmain(String arguments) {

}
```



<br/>
### 2、配置
#### 打包配置
`META-INF/MANIFEST.MF`文件必须有以下参数配置
```java
Manifest-Version: 1.0
// JDK1.5，必须与应用一块启动
Premain-Class: com.gumihoy.apm.agent.APMAgent
// JDK1.6, 可以在应用启动之后再启动
Agent-Class: com.gumihoy.apm.agent.APMAgent
// 布尔值（true 或 false，与大小写无关）, 是否能重定义此代理所需的类
Can-Redefine-Classes: true
// 布尔值（true 或 false，与大小写无关）, 是否能重转换此代理所需的类
Can-Retransform-Classes: true
// 布尔值（true 或 false，与大小写无关）, 是否能设置此代理所需的本机方法前缀
Can-Set-Native-Method-Prefix: true
空行
```
> 最后一行（空行）必须要有

<br/>
#### 实现方式
##### 一、Maven

**方法一：使用插件maven-jar-plugin**
只有一个包：
- agent.jar: 包含第三方jar

```xml
 <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-jar-plugin</artifactId>
    <version>3.1.2</version>
    <configuration>
        <archive>
            <manifest>
                <addClasspath>true</addClasspath>
            </manifest>
            <manifestEntries>
                <Premain-Class>com.gumihoy.apm.agent.APMAgent</Premain-Class>
                <Can-Redefine-Classes>true</Can-Redefine-Classes>
                <Can-Retransform-Classes>true</Can-Retransform-Classes>
            </manifestEntries>
        </archive>
    </configuration>
</plugin>
```

**方法二：使用插件maven-shade-plugin**
两个包：
- agent.jar: 包含第三方jar
- original-agent.jar: 不饱和第三方jar，原始包

```xml
<plugin>
    <artifactId>maven-shade-plugin</artifactId>
    <executions>
        <execution>
            <phase>package</phase>
            <goals>
                <goal>shade</goal>
            </goals>
            <configuration>
                <shadedArtifactAttached>false</shadedArtifactAttached>
                <createDependencyReducedPom>true</createDependencyReducedPom>
                <createSourcesJar>true</createSourcesJar>
                <shadeSourcesContent>true</shadeSourcesContent>
                <transformers>
                    <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                        <manifestEntries>
                            <Premain-Class>${premain.class}</Premain-Class>
                            <Can-Redefine-Classes>${can.redefine.classes}</Can-Redefine-Classes>
                            <Can-Retransform-Classes>${can.retransform.classes}</Can-Retransform-Classes>
                        </manifestEntries>
                    </transformer>
                </transformers>
            </configuration>
        </execution>
    </executions>
</plugin>
```

**方法三：使用插件maven-assembly-plugin**
两个包：
- agent.jar: 不饱和第三方jar，原始包
- agent-jar-with-dependencies.jar: 包含第三方jar

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>2.4.1</version>
    <configuration>
        <!-- get all project dependencies -->
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
        <!-- MainClass in mainfest make a executable jar -->
        <archive> 
            <manifest>
                <addClasspath>true</addClasspath>
            </manifest>
            <manifestEntries>
                <Premain-Class>com.gumihoy.apm.agent.APMAgent</Premain-Class>
                <Can-Redefine-Classes>true</Can-Redefine-Classes>
                <Can-Retransform-Classes>true</Can-Retransform-Classes>
            </manifestEntries>
                    
        </archive>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <!-- bind to the packaging phase -->
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

##### 二、Gradle
```gradle
jar {
    manifest {
        attributes(
                'Premain-Class': 'xx.Agent',
                'Agent-Class': 'cxx.Agent',
                'Can-Redefine-Classes': 'true',
                'Can-Retransform-Classes': 'true',
                'Can-Set-Native-Method-Prefix': 'true',
                'Implementation-Title': "CallSpy",
                'Implementation-Version': rootProject.version,
                'Built-By': System.getProperty('user.name'),
                'Built-Date': new Date(),
                'Built-JDK': System.getProperty('java.version')
        )
    }
}

```


<br/>
### 3、启动
**一、vm参数配置启动**
```java
-javaagent:agent.jar[=arguments]
```
> arguments: 参数，String 类型。多个参数后端必须处理（如a=1,b=2 or a=1;b=2）


<br/>
## 框架

 | baseline | Byte Buddy | cglib | Javassist | Java proxy
-|----------|------------|-------|-----------|-----------
trivial class creation | 0.003 (0.001) | 142.772 (1.390) | 515.174 (26.753) | 193.733 (4.430) | 70.712 (0.645)
interface implementation | 0.004 (0.001) | 1'126.364 (10.328) | 960.527 (11.788) | 1'070.766 (59.865) | 1'060.766 (12.231)
stub method invocation | 0.002 (0.001) | 0.002 (0.001) | 0.003 (0.001) | 0.011 (0.001) | 0.008 (0.001)
class extension | 0.004 (0.001) | 885.983 5'408.329 | (7.901) (52.437) | 1'632.730 (52.737) | 683.478 (6.735) | –
super method invocation | 0.004 (0.001) | 0.004 <br/> 0.004 | (0.001) <br/> (0.001) | 0.021 (0.001) | 0.025 (0.001) | –


> - javassist更偏向底层，比较难于使用并且在动态组合字符串以实现更复杂的逻辑时很容易出错
> - cglib现在维护的则相当慢了，基本处于无人维护的阶段了，而这些缺点ByteBuddy都没有
> - ByteBuddy性能相对来说在三者中是最优的


### 使用 Byte Buddy 实现 JavaAgent

#### 一、导入`jar`
```xml
<!-- https://mvnrepository.com/artifact/net.bytebuddy/byte-buddy -->
<dependency>
    <groupId>net.bytebuddy</groupId>
    <artifactId>byte-buddy</artifactId>
    <version>1.10.0</version>
</dependency>
<!-- https://mvnrepository.com/artifact/net.bytebuddy/byte-buddy-agent -->
<dependency>
    <groupId>net.bytebuddy</groupId>
    <artifactId>byte-buddy-agent</artifactId>
    <version>1.10.0</version>
</dependency>
```

#### 二、`Agent`代码
```java
public class APMAgent {


    /**
     * http://bytebuddy.net/#/tutorialTypeValidation
     *
     * @param arguments
     * @param instrumentation
     */
    public static void premain(String arguments, Instrumentation instrumentation) {
        System.out.println("xx");
//        ByteBuddy buddy = new ByteBuddy().with(TypeValidation.of(false)).with(ClassFileVersion.JAVA_V8);
        new AgentBuilder.Default()
                .type(ElementMatchers.nameStartsWith("com.gumihoy.apm.agent.demo"))
                .transform(new AgentTransformer())
                .with(AgentBuilder.RedefinitionStrategy.RETRANSFORMATION)
                .with(new AgentListener())
                .installOn(instrumentation);
    }

    public static void agentmain(String arguments, Instrumentation instrumentation) {

    }

    protected static ElementMatcher<? super TypeDescription> buildIgnoreMatcher() {
        return ElementMatchers.nameStartsWith("net.bytebuddy.*");
    }


    static class AgentTransformer implements AgentBuilder.Transformer {
        @Override
        public DynamicType.Builder<?> transform(DynamicType.Builder<?> builder, TypeDescription typeDescription, ClassLoader classLoader, JavaModule module) {
            return builder
                    .method(ElementMatchers.any()) // 拦截任意方法
                    .intercept(MethodDelegation.to(MethodIntercept.class)); // 委托
        }
    }


    static class AgentListener implements AgentBuilder.Listener {
        @Override
        public void onDiscovery(String typeName, ClassLoader classLoader, JavaModule module, boolean loaded) {

        }

        @Override
        public void onTransformation(TypeDescription typeDescription, ClassLoader classLoader, JavaModule module, boolean loaded, DynamicType dynamicType) {

        }

        @Override
        public void onIgnored(TypeDescription typeDescription, ClassLoader classLoader, JavaModule module, boolean loaded) {

        }

        @Override
        public void onError(String typeName, ClassLoader classLoader, JavaModule module, boolean loaded, Throwable throwable) {

        }

        @Override
        public void onComplete(String typeName, ClassLoader classLoader, JavaModule module, boolean loaded) {

        }
    }

}


public class MethodIntercept {

    @RuntimeType
    public static Object intercept(@Origin Method method,
                                   @SuperCall Callable<?> callable) throws Throwable {
        long start = System.currentTimeMillis();
        try {
            // 原有函数执行
            return callable.call();
        } finally {
            System.out.println(method + ": took " + (System.currentTimeMillis() - start) + "ms");
        }
    }
}
```

#### 三、应用代码
```
package com.gumihoy.apm.agent.demo;

public class AgentTest {

    public void fun1() throws Exception {
        System.out.println("this is fun 1.");
        Thread.sleep(500);
    }

    private void fun2() throws Exception {
        System.out.println("this is fun 2.");
        Thread.sleep(500);
    }

    public static void main(String[] args) throws Exception {
        AgentTest test = new AgentTest();
        test.fun1();
        test.fun2();
    }
}
```

#### 四、打包
[pom.xml配置](#实现方式)
```
mvn clean package
```

#### 五、启动
![](1565784207465.jpg)


#### 六、运行结果
![](1565786297241.jpg)





如何自定义类加载器，避免污染目前进程
如何实现字节码的修改
如何实现字节码的多次修改
如何恢复被修改过的字节码
如何卸载Java Agent的类
卸载自定义类加载器遇到的一些坑

---
参考

[Instrumentation介绍](https://www.ibm.com/developerworks/cn/java/j-lo-jse61/index.html)