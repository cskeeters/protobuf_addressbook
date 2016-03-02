# Initialize AC: ACINIT( package_name, version, bug_report_address)
AC_INIT([addressbook], [0.1])
# Initialize Automake
AM_INIT_AUTOMAKE([foreign])
# AM stands for Automake commands, AC stands for Autoconf commands
# We use libraries
AC_PROG_RANLIB
# Let's check for a C++ compiler
AC_LANG(C++)
# Let's set a C++ compiler
AC_PROG_CXX
#AC_PROG_CXX([g++-5])
#AC_PROG_CXX([clang++])

PKG_CHECK_MODULES(PROTOBUF, protobuf >= 2.4.0)
AC_SUBST(PROTOBUF_LIBS)
AC_CHECK_PROG([PROTOC], [protoc], [protoc])
AS_IF([test "x${PROTOC}" == "x"], [AC_MSG_ERROR([ProtoBuf compiler "protoc" not found.])])

# This suppresses the error we get for also having the cc version of helper library.
AC_SUBST([CC])
# Let's specify where the Makefiles should be produced.
# These are the same locations as your Makefile.in's, but named as Makefile only
# We need to do this because both Autoconf and Automake read this file and
# produce Makefiles from this list.
AC_CONFIG_FILES([Makefile])
# Finally produce "configure" script
AC_OUTPUT
