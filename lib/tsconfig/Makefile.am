# Makefile.am for TS Config module.
#
#  Licensed to the Apache Software Foundation (ASF) under one
#  or more contributor license agreements.  See the NOTICE file
#  distributed with this work for additional information
#  regarding copyright ownership.  The ASF licenses this file
#  to you under the Apache License, Version 2.0 (the
#  "License"); you may not use this file except in compliance
#  with the License.  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.

lib_LTLIBRARIES = libtsconfig.la
noinst_PROGRAMS = test-tsconfig
libtsconfig_la_LDFLAGS = -no-undefined -version-info @TS_LIBTOOL_VERSION@

AM_YFLAGS = -d -p tsconfig

AM_CPPFLAGS = \
  -I$(top_srcdir)/lib

BUILT_SOURCES = \
  TsConfigGrammar.c TsConfigGrammar.h TsConfigGrammar.hpp \
  TsConfigSyntax.c 

CLEANFILES = $(BUILT_SOURCES)

libtsconfig_la_SOURCES = \
  TsConfigGrammar.y \
  TsConfigSyntax.l \
  Errata.cc \
  Errata.h \
  TsErrataUtil.cc \
  TsBuffer.h \
  NumericType.h \
  IntrusivePtr.h \
  TsBuilder.cc \
  TsBuilder.h \
  TsValue.cc \
  TsValue.h

test_tsconfig_SOURCES = test-tsconfig.cc

test_tsconfig_LDADD = libtsconfig.la ../ts/libtsutil.la

# Strip to just the enum in the ts::config namespace so we can use
# it more easily in C++.
TsConfigGrammar.hpp: TsConfigGrammar.h BisonHeaderToC++.sed
	$(SED) -f BisonHeaderToC++.sed TsConfigGrammar.h > $@
