---
layout: page
title: Weak Types
published: true
---



An implementation of weak typing for C++11 and Arduino.

Thanks to [Foo Nathan](https://github.com/foonathan) for inspiration on variant implementation from his typesafe library. The type tracking internals of this library are largely based on his implementation, with some modifications to make things run in C++11/Arduino and to properly override operators to create the operator behavior you would expect from the underlying type.

[Github](https://github.com/eliwinkelman/Weak-Types)

## Usage

```cpp
  using var = weak<int, float, double, std::string>;
  
  var myInt = 1;
  var myDouble = 14.2;
  var myFloat = 1.3f;
  var myString = std::string("Hello World");
  
  var a = myInt + myDouble * myFloat;
  
```

