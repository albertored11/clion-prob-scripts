# clion-prob-scripts

## What and why

These are two bash scripts useful for creating files and testing in C++ problem solving using CLion IDE.

During my years as a CS student, I have to do problem solving in some courses related with fundamentals of programming, data structures and algorithms. In almost all of them, the language choice is C++. In addition to that, I have participated in a couple of competitive programming contests.

In my first year, I was using Windows, and our professor recommendation for the IDE was Visual Studio. Later, I switched back to Linux after a few years, and I tried different IDEs, until I found my favourite: [CLion](https://www.jetbrains.com/clion/). It's proprietary and paid (you can get a free license if you are a student!), and a bit resource heavy (compared to a plain text editor), but it is just amazing, just like other IDEs from [JetBrains](https://www.jetbrains.com/). CLion uses [CMake](https://cmake.org/) as its build system.

In almost every course related with problem solving, we use an automatic judge (like [DOMJudge](https://www.domjudge.org/) or [Online Judge](https://onlinejudge.org/)) in order to test our code, just like in a competitive programming contest. They usually provide sample test cases for input and output.

I create a project for every course or contest, then I create subdirectories if needed for organization, and finally I create a directory for each individual program, in which I put the source file, sample test files and the PDF describing the problem. I also have to create a configuration for that problem in CLion.

When I want to test my code to make sure it is correct and at least works for the provided sample test cases, I compile it with ```g++```, run binary redirecting input and output from/to files and ```diff``` output.

This is a really systematic task I have to do for every problem I want to solve, so I wrote two super simple bash scripts which currently need structural changes in order to help in these two tasks:

- ```new-problem```, for creating a new problem
- ```test-problem```, for testing a problem

(yes, script names are quite self-explainatory)

## Dependencies

- bash, coreutils, sed
- gcc (specifically, g++)
- CLion

## Installation

These are bash scripts! Just copy or, better yet, symlink them to ```~/.local/bin``` or whichever directory you prefer from your ```$PATH```.

## Usage

### new-problem

**Tip:** save a template for your problems called ```template.cpp``` in the directory of your CLion project.

In the directory you wish to create the directory for your new problem:

```
$ new-problem PROBLEM_ID
```

This creates a directory called ```PROBLEM_ID``` (if it does not exist), and, inside it, it creates a source file from template (if any) and adds configuration to ```CMakeLists.txt``` file so you can easily write code, run, test and debug.

### test-problem

In the directory of your problem:

```
$ test-problem SAMPLE_FILENAME
```

This compiles source code of the problem, runs the binary, passes ```SAMPLE_FILENAME.in``` as input, and ```diff```s output with ```SAMPLE_FILENAME.out```, informing whether output matches or not, and also about any other error (sample files not found, compilation, runtime).
