# This directory is not compiled automatically when you do make under src/
# to compile the TensorFlow related code,

# you would need to run tools/extras/install_tensorflow_cc.sh first to generate
# the static library files required for compilation, and then

# cd ${KALDI_ROOT}/src
# cd tfrnnlm
# make
# cd ../tfrnnlmbin/
# make

include ../kaldi.mk

TENSORFLOW = ../../tools/tensorflow

all:

EXTRA_CXXFLAGS = -Wno-sign-compare -I$(TENSORFLOW)/bazel-tensorflow/external/protobuf/src \
                 -I$(TENSORFLOW)/bazel-genfiles -I$(TENSORFLOW) \
                 -I$(TENSORFLOW)/tensorflow/contrib/makefile/downloads/eigen/

OBJFILES = tensorflow-rnnlm.o

TESTFILES =

LIBNAME = kaldi-tensorflow-rnnlm

ADDLIBS = ../lm/kaldi-lm.a ../util/kaldi-util.a ../thread/kaldi-thread.a \
          ../matrix/kaldi-matrix.a ../base/kaldi-base.a \
          $(shell pwd)/../../tools/tensorflow/bazel-bin/tensorflow/tensorflow_cc.so

LDLIBS +=  -lz -ldl -fPIC -lrt
LDLIBS += -L$(TENSORFLOW)/bazel-bin/tensorflow -ltensorflow_cc

include ../makefiles/default_rules.mk