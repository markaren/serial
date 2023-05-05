# Serial Communication Library

This is a cross-platform library for interfacing with rs-232 serial like ports written in C++. It provides a modern C++ interface with a workflow designed to look and feel like PySerial, but with the speed and control provided by C++. 

This library is in use in several robotics related projects and can be built and installed to the OS like most unix libraries with make and then sudo make install, but because it is a catkin project it can also be built along side other catkin projects in a catkin workspace.

Serial is a class that provides the basic interface common to serial libraries (open, close, read, write, etc..) and requires no extra dependencies. It also provides tight control over timeouts and control over handshaking lines. 

### Documentation

Website: http://wjwwood.github.io/serial/

API Documentation: http://wjwwood.github.io/serial/doc/1.1.0/index.html


### License

[The MIT License](LICENSE)

### Original Authors

William Woodall <wjwwood@gmail.com>
John Harrison <ash.gti@gmail.com>
