# Spring-Boot-http2

## IDEA 配置

- File
    - settings
        - Build Execution Deployment
            - Compiler
                - Java Compiler
                    - Pre-mode bytecode version:
                        - Module
                            - 删除本模块的 jdk

    - Project Structure
        - Project
            - Project SDK:
                - 设置为 jdk 1.8
            
            - Project language level
                - 设置为 jdk 1.8

        - Modules
            - 项目名
                - Sources
                    - Language level
                        - 设置为 jdk 1.8
                
                - Dependencies
                    - Modele
                        - 设置为 JDK 1.8

## 文档

- [如何配置ssl](https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto-configure-ssl)
- [如何配置http2](https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto-configure-http2)

## 创建 SSL 文件

- [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/keytool.html)
    - keytool -help
    - 密钥和证书管理工具
    
    - genkeypair
        - keytool -genkeypair -help
        - 生成密钥对
    
            - alias
                - 要处理的条目的别名
        
            - keyalg
                - 密钥算法名称
        
            - validity
                - 有效天数
            
            - keystore
                - 密钥库名称
            
            - storepass
                - 密钥库口令

- 生成密钥对

~~~
keytool -genkeypair -alias spring-boot-http2 -keyalg RSA -validity 3650 -keystore spring-boot-http2.jks -storepass xuxiaowei
~~~

- JKS 密钥库使用专用格式。建议使用 "keytool -importkeystore -srckeystore spring-boot-http2.jks -destkeystore spring-boot-http2.jks -deststoretype pkcs12" 迁移到行业标准格式 PKCS12。

~~~
keytool -importkeystore -srckeystore spring-boot-http2.jks -destkeystore spring-boot-http2.jks -deststoretype pkcs12
~~~

## 查看 http/2
~~~
window.chrome.loadTimes()
~~~

## JDK 8

- 在 jdk 1.8 中，启动时错误日志
~~~
2020-08-09 12:39:43.246 ERROR 8700 --- [           main] o.a.coyote.http11.Http11NioProtocol      : The upgrade handler [org.apache.coyote.http2.Http2Protocol] for [h2] only supports upgrade via ALPN but has been configured for the ["https-jsse-nio-1443"] connector that does not support ALPN.
~~~
- 此日志说明未能正确配置 http/2，项目使用 http/1.1

- [Tomcat Native](http://tomcat.apache.org/download-native.cgi)

    - jdk 1.8 配置 http/2 所需依赖
    
    - JVM参数
        
        - Windows 环境配置
            ~~~
            -Djava.library.path=D:\tomcat-native-1.2.24-openssl-1.1.1g-win32-bin\bin\x64
            ~~~
