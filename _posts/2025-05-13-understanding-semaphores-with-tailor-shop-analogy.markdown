---
title: Understanding Semaphores in Java Using a Real-Life Tailor Shop Analogy
date: 2025-05-13
author: Sachidanand
tags: [Java, Concurrency, Multithreading, Semaphores, System Design]
---

When you're learning about concurrency in Java, one of the most powerful yet misunderstood tools is the **semaphore**. In this article, I’ll help you understand how semaphores work by walking through a **real-life analogy** — a tailor shop.

---

## 🧵 The Real-Life Scenario: A Tailor Shop

Imagine a **tailor shop** with:

- 🪡 **6 sewing machines**
- 🧑‍🔧 Multiple **tailors** trying to use them
- Only **one tailor per machine**
- Tailors must **wait** if no machine is available
- Once done, the tailor **releases** the machine for others

This problem maps beautifully to the **Producer-Consumer Problem** in concurrency.

---

## 🔄 Mapping Real World to Java

| Real-World Concept     | Java Concurrency Concept       |
| ---------------------- | ------------------------------ |
| Sewing machines        | `Semaphore` (initialized to 6) |
| Tailor (worker)        | Thread                         |
| Machine usage          | Critical Section               |
| Locking machine access | `mutex` semaphore (value 1)    |
| Waiting if no machine  | `acquire()`                    |
| Releasing machine      | `release()`                    |

---

## 💡 Java Implementation: Tailor Shop Simulation

```java
import java.util.concurrent.Semaphore;

public class TailorShop {

    static Semaphore sewingMachines = new Semaphore(6); // Only 6 machines
    static Semaphore mutex = new Semaphore(1); // For logging or shared resources

    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            new Tailor("Tailor-" + i).start();
        }
    }

    static class Tailor extends Thread {
        public Tailor(String name) {
            super(name);
        }

        public void run() {
            try {
                System.out.println(getName() + " wants to sew.");
                sewingMachines.acquire(); // Wait if no machines are free
                mutex.acquire(); // Optional: protect shared resources (e.g., logs)
                System.out.println(getName() + " is sewing...");
                Thread.sleep(2000); // Simulate sewing
                System.out.println(getName() + " is done sewing.");
                mutex.release();
                sewingMachines.release(); // Free up machine
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```
