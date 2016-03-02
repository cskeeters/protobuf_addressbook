# protobuf_addressbook

In an effort to test out google's [protobuf](https://github.com/google/protobuf), I starting by creating a project from their [c++ tutorial](https://developers.google.com/protocol-buffers/docs/cpptutorial).  This worked, when compiled with clang++, but not with g++.  I created an autotools configuration so that this could be compiled easily and the compiler could be changed easily for testing.

## Compiling

```
autoreconf -vfi && ./configure && make
```

## Changing the compiler

Inside of `configure.ac` there are lines
```
AC_PROG_CXX
#AC_PROG_CXX([g++-5])
#AC_PROG_CXX([clang++])
```

The first one takes the default for the machine.  The other two specify specific compilers.  Leave only one uncommented to change compilers.
