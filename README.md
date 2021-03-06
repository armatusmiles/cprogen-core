# Modern cpp library

## Investigates best way to build modern project for develop UNIX C++ library based on C API for binding any language

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/7673e38427c340dd8e534f8f39a91a7f)](https://app.codacy.com/app/armatusmiles/modern-cpp-lib?utm_source=github.com&utm_medium=referral&utm_content=armatusmiles/modern-cpp-lib&utm_campaign=Badge_Grade_Dashboard)
[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/armatusmiles/moderncpp.svg)](https://hub.docker.com/r/armatusmiles/moderncpp)
[![codecov](https://codecov.io/gh/armatusmiles/cprogen-core/branch/master/graph/badge.svg)](https://codecov.io/gh/armatusmiles/modern-cpp-lib)

| Build status          | Systems / Compilers         |
| ------------- | ------------------------------------------ |
| [![Build Status](https://travis-ci.org/armatusmiles/modern-cpp-lib.svg?branch=master)](https://travis-ci.org/armatusmiles/modern-cpp-lib) | Linux (gcc)   OSX (XCode 10.2 clang) |

## Features
-   Creates shared(*.so, *.dylib) library
-   [Google test(gtest)](https://github.com/armatusmiles/modern-cpp-lib/blob/master/tests/main.cpp) simple and powerful test framework
-   [Catch2](https://github.com/armatusmiles/modern-cpp-lib/tree/add-catch2/tests-catch2) single header test library
-   [Python bindings](https://github.com/armatusmiles/modern-cpp-lib/blob/master/test_api.py) Load library and call C API function from Python.
-   [Codecov](https://codecov.io/gh/armatusmiles/modern-cpp-lib) - reports generate automatically
-   [Docker](https://github.com/armatusmiles/modern-cpp-lib/blob/master/Dockerfile) file and [auto build](https://hub.docker.com/r/armatusmiles/moderncpp) with [Docker Hub](https://hub.docker.com/r/armatusmiles/moderncpp)
-   [Travis-CI](https://travis-ci.org/armatusmiles/moderncpp) auto build for ubuntu xenial and osx
-   [Cppcheck](http://cppcheck.sourceforge.net) is a static analysis tool for C/C++ code

## Libraries used
-   [Google Test (gtest)](https://github.com/google/googletest) - [test](https://github.com/armatusmiles/modern-cpp-lib/blob/master/tests/main.cpp) framework 
-   [gcov](https://linux.die.net/man/1/gcov) / [lcov](https://linux.die.net/man/1/lcov) - generates and shows in html format code coverage

## Build and Run
```
git clone https://github.com/armatusmiles/modern-cpp-lib.git \
    && cd modern-cpp-lib \
    && mkdir build && cd build \
    && cmake ../ \
    && make moderncpp_coverage
``` 

<details>
  <summary>cppcheck  simple example</summary>
    
    cppcheck ./src/
    
    Checking src/interface.cpp ...
    [src/interface.cpp:11]: (error) Array 'a[5]' accessed at index 6, which is out of bounds.

</details>

###### Notice: For choose catch2 test framework. Should add var -DTEST_TYPE="catch2"</br> Exmaple : cmake ../ -DTEST_TYPE="catch2"

> "make moderncpp_coverage" builds library, runs gtest and generate code coverage(html) report

## References
-   [ModernCppCI](https://github.com/LearningByExample/ModernCppCI)
-   [cmake-modules](https://github.com/bilke/cmake-modules)
-   [Catch2](https://github.com/catchorg/Catch2)
-   [cppcheck manual](http://cppcheck.sourceforge.net/manual.pdf)
