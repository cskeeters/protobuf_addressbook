bin_PROGRAMS = main
main_SOURCES = main.c++ addressbook.pb.cc addressbook.pb.h
# noinst_ : assures that this library is not installed to the user's computer
# libBLAH.a is a *nix convention. If you noticed, we replaced the . with _ in SOURCES line.
#main_LDADD = libhelper.a ../my_inc/libmyadd.a
# LDADD specifies which libraries to compile into "main". We have two libraries.
# libhelper comes from this directory and libmyadd come from my_inc directory.
main_LDFLAGS= $(PROTOBUF_LIBS)
#main_LDADD=$(PROTOBUF_LIBS)

dist_noinst_DATA = addressbook.proto
MOSTLYCLEANFILES = addressbook.pb.cc addressbook.pb.h

BUILT_SOURCES = addressbook.pb.cc addressbook.pb.h

%.pb.cc %.pb.h: %.proto
	$(PROTOC) --proto_path=$(srcdir) --cpp_out=$(builddir) $^
