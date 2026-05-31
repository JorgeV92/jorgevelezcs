---
layout: cpp
title: Asynchronous I/O and Coroutines
---

<h3>Asynchronous I/O and Coroutines</h3>

This page collects notes and links for reviewing asynchronous I/O and coroutines in C++.

<hr>

<h4>Topics</h4>

<ul>
  <li>Event loops and completion queues</li>
  <li>Callbacks, futures, and continuations</li>
  <li>C++20 coroutine basics</li>
  <li>Awaitable types and coroutine handles</li>
  <li>Async networking and file I/O patterns</li>
</ul>

<h4>Small Coroutine Example</h4>

```cpp
#include <coroutine>
#include <iostream>

struct Task {
    struct promise_type {
        Task get_return_object() {
            return {};
        }

        std::suspend_never initial_suspend() noexcept {
            return {};
        }

        std::suspend_never final_suspend() noexcept {
            return {};
        }

        void return_void() {}

        void unhandled_exception() {
            std::terminate();
        }
    };
};

Task say_hello() {
    std::cout << "Hello from a coroutine\n";
    co_return;
}

int main() {
    say_hello();
}
```
