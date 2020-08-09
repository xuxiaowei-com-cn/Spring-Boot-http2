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
                - 设置为 jdk 14
            
            - Project language level
                - 设置为 jdk 14

        Modules
            - 项目名
                - Sources
                    - Language level
                        - 设置为 jdk 14
                
                - Dependencies
                    - Modele
                        - 设置为 JDK 14

## 文档

- [如何配置ssl](https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto-configure-ssl)
- [如何配置http2](https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto-configure-http2)
