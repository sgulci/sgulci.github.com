---
title: Spring Data Repository
date: 2024-03-15
author: John Doe
tags: [golang, markdown, blog]
draft: true
---


# Spring Data Repository

Spring Data Repository interface uses dynamic proxies for create proxy classes for repository interface


Links
 - https://medium.com/@mahammadkhalilov/understanding-spring-proxies-jdk-dynamic-proxy-vs-cglib-proxy-7d76bf5b85ac
 - https://docs.spring.io/spring-framework/reference/core/aop/proxying.html
 - https://medium.com/@AlexanderObregon/how-spring-boot-sets-up-spring-data-repositories-0638ee938133
 - App starts → Scans for repository interfaces
   → Creates proxy class implementing them
   → Routes calls to SimpleJpaRepository or generates query
   → Executes query via EntityManager