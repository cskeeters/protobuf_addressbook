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

## Compiling with g++-5 on OSX

Brew provides protobuf precompiled with clang++.  Since the ABI for clang++ compiled libraries is not compatible with that of g++, protobuf must be [downloaded](https://developers.google.com/protocol-buffers/docs/downloads) and recompiled.  For me, running the following commands used g++-5 without having to change anything else.  If this is not the case open up configure.ac and change `AC_PROG_CXX` to `AC_PROG_CXX([g++-5])` and run `autoreconf -vfi`.

```
cd protobuf-2.6.1
./configure --prefix=/build/protobuf/2.6.1
make -j16
sudo make install
```

```
cd protobuf_addressbook
# Make change to use g++-5 if necessary
autoreconf -vfi && ./configure && make clean && make
DYLD_LIBRARY_PATH=.:./lib ./main addressbook.dat
```
