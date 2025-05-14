---
title: "From Code to Process: Understanding What Runs on Your Machine"
description: "Ever wondered what actually happens when you double-click an app? Let’s understand how code becomes a running process on your machine, explained in simple terms."
layout: post
date: 2025-05-03
tags: [operating-systems, processes, threads, system-design, multithreading]
---

## From Code to Process: Understanding What Runs on Your Machine

Have you ever stopped to think about what actually happens when you double-click on an app? Most developers jump directly into code without really understanding how that code transforms into something the machine runs — something called a **process**. Let’s break it down simply and clearly.

---

###  The Lifecycle of Code

Let’s walk through what happens from the moment code is written to when it runs as a process.

1. **Code to Executable**  
   The code we write — in Java, Python, C++, etc. — is compiled or interpreted into an **executable file** (`.exe`, `.apk`, `.jar`, etc.). This is what users ultimately download.

2. **Installation**  
   After downloading, the user installs the app/program using this executable. Once installed, the app is stored on the **Hard Disk (HDD/SSD)**.

   At this stage, it is simply an **application** sitting on the disk.

3. **Execution**  
   When the user double-clicks to launch the app, the OS loads the program from disk into **RAM**.

4. **Process Creation**  
   The OS creates a **process**, which is the running instance of that application in memory. This process gets resources like memory space, registers, a stack, and a unique Process ID (PID).

 **Only when an app is running in RAM is it called a Process.**

---

###  Why This Matters

Before we dive into multithreading, semaphores, or concurrency models — it’s crucial to understand what a **process** is. Threads _live inside_ processes, and they don’t exist on their own. So if you’ve ever jumped into threads without understanding processes, this is your missing foundation.

---

###  What’s Coming Next

In the next article, we’ll move deeper into the world of **threads and multithreading**, starting with:

- What is a thread?
- How threads differ from processes?
- Ways to create threads in Java
- Using `ExecutorService`, `Future`, and `Callable`
- Semaphores and synchronization

---

Thanks for reading —
Sachi <3