# Serial Communication Library

This is a cross-platform library for interfacing with rs-232 serial like ports written in C++.
It provides a modern C++ interface with a workflow designed to look and feel like PySerial, but with the speed and control provided by C++. 

Serial is a class that provides the basic interface common to serial libraries (open, close, read, write, etc..) and requires no extra dependencies. 
It also provides tight control over timeouts and control over handshaking lines. 

### Documentation

API Documentation: http://wjwwood.github.io/serial/doc/1.1.0/index.html

### Fork changes

This fork has replaced the previous build setup in order to successfully build with no extra dependencies.
Build it as any other regular CMake project. 

### License

[The MIT License](LICENSE)

### Original Authors

William Woodall <wjwwood@gmail.com>
John Harrison <ash.gti@gmail.com>
