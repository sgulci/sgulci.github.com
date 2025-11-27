---
title: Spring Security
date: 2024-03-15
author: John Doe
tags: [golang, markdown, blog]
draft: true
---


# Spring Security

## Security Filter Chain

- Make stateless for no session type auth, like token based ones
- on this configuration class use jwtfilter class you created

```@Bean
     public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
             http
                 .csrf(AbstractHttpConfigurer::disable)
                 .authorizeHttpRequests(auth -> auth
                     .requestMatchers("/api/auth/**", "/v3/api-docs/**", "/swagger-ui/**").permitAll()
                     .anyRequest().authenticated()
                 )
                 .sessionManagement(session -> session.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
                 .addFilterBefore(jwtAuthenticationFilter, UsernamePasswordAuthenticationFilter.class);

        return http.build();
     }

```

- https://medium.com/@prasanta-paul/spring-security-for-web-and-api-f94b4834b0c0
- https://docs.spring.io/spring-security/reference/servlet/architecture.html
- https://www.baeldung.com/spring-security-custom-filter
- https://docs.spring.io/spring-security/reference/features/exploits/csrf.html
- https://www.baeldung.com/spring-boot-security-autoconfiguration
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Encoding
- https://medium.com/@AlexanderObregon/spring-microservices-data-compression-techniques-for-faster-responses-b61d3fc6fae1
- https://dev.to/rock_win_c053fa5fb2399067/enabling-gzip-compression-in-spring-boot-for-faster-web-apps-3abe
- https://medium.com/@narasimha4789/implementing-deflate-compression-in-spring-boot-446df8b92761

##

## Spring security fundamantels

Spring uses DispatcherServlet for matching and distributing requests.
