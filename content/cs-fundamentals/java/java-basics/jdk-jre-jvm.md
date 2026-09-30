---
title: JDK, JRE, and JVM
tags: [java, jvm, java-fundamentals]
---

# JDK, JRE, and JVM

The JDK, JRE, and JVM represent different layers of the Java platform.

## JDK — Java Development Kit

The **JDK** provides the tools required to develop Java applications, including `javac`, `java`, debugging/development tools, and Java runtime components. The compiler converts `.java` source files into `.class` bytecode.

## JVM — Java Virtual Machine

The **JVM** executes Java bytecode.

```text
Java Source Code
       │ javac
       ▼
Java Bytecode (.class)
       │
       ▼
      JVM
       ├── Interpreter
       └── JIT Compiler
       │
       ▼
Native Machine Code
```

The JVM is more than a simple line-by-line interpreter. Modern JVMs combine bytecode interpretation, Just-In-Time compilation, garbage collection, memory management, and runtime optimization.

Frequently executed ("hot") code can be compiled into native machine code by the JIT compiler.

## JRE — Java Runtime Environment

Conceptually, the **JRE** provides the environment required to run Java applications:

```text
JRE
├── JVM
└── Java runtime libraries
```

The JDK additionally provides development tools.

> Modern Java distributions (Java 9+) no longer ship a separate JRE in quite the same way older Java distributions did, but the JDK/JRE/JVM distinction remains useful conceptually.

## Why Java Is Platform Independent

Java source is compiled into JVM bytecode rather than directly into a specific CPU instruction set. Each supported platform provides a JVM capable of executing that bytecode.

## Related
- [[../index|Java]]
