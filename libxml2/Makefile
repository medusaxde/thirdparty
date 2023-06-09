########################################################################
# Copyright (c) 1988-2021 $organization$
#
# This software is provided by the author and contributors ``as is''
# and any express or implied warranties, including, but not limited to,
# the implied warranties of merchantability and fitness for a particular
# purpose are disclaimed. In no event shall the author or contributors
# be liable for any direct, indirect, incidental, special, exemplary,
# or consequential damages (including, but not limited to, procurement
# of substitute goods or services; loss of use, data, or profits; or
# business interruption) however caused and on any theory of liability,
# whether in contract, strict liability, or tort (including negligence
# or otherwise) arising in any way out of the use of this software,
# even if advised of the possibility of such damage.
#
#   File: Makefile
#
# Author: $author$
#   Date: 11/2/2021, 11/3/2021
#
# Thirdparty Gcc Makefile for libxml2
########################################################################


########################################################################
#
# libxml2 defs
#
########################################################################
LIBXML2_MAKEDIR=$(PWD)

LIBXML2_HOME_BUILD = $(HOME)/build
LIBXML2_HOME_SOURCE_BUILD = $(HOME)/source/build
LIBXML2_THIRDPARTY_BUILD = $(LIBXML2_MAKEDIR)/..

ifeq ($(LIBXML2_BUILD_HOME),HOME_BUILD)
LIBXML2_BUILD_HOME = $(LIBXML2_HOME_BUILD)
else
ifeq ($(LIBXML2_BUILD_HOME),HOME_SOURCE_BUILD)
LIBXML2_BUILD_HOME = $(LIBXML2_HOME_SOURCE_BUILD)
else
ifeq ($(LIBXML2_BUILD_HOME),LIBXML2_THIRDPARTY_BUILD)
LIBXML2_BUILD_HOME = $(LIBXML2_THIRDPARTY_BUILD)
else
ifndef LIBXML2_BUILD_HOME
LIBXML2_BUILD_HOME = $(LIBXML2_THIRDPARTY_BUILD)
endif
endif
endif
endif

ifndef LIBXML2_UNAME
LIBXML2_UNAME = $(shell uname)
endif

ifndef LIBXML2_OS
ifneq ($(LIBXML2_UNAME),Darwin)
LIBXML2_OS = linux
else
LIBXML2_OS = macosx
endif
endif

#
# libxml2 version
#
ifeq ($(VERSION),278)
LIBXML2_VERSION_MAJOR = 2
LIBXML2_VERSION_MINOR = 7
LIBXML2_VERSION_RELEASE = 8
else
LIBXML2_VERSION_MAJOR = 2
LIBXML2_VERSION_MINOR = 7
LIBXML2_VERSION_RELEASE = 8
endif

LIBXML2_VERSION_SEPARATOR = .
LIBXML2_VERSION_MAJOR_SEPARATOR = $(LIBXML2_VERSION_SEPARATOR)
LIBXML2_VERSION_MINOR_SEPARATOR = $(LIBXML2_VERSION_SEPARATOR)

LIBXML2_VERSION_SHORT = $(LIBXML2_VERSION_MAJOR)$(LIBXML2_VERSION_MINOR)$(LIBXML2_VERSION_RELEASE)
LIBXML2_VERSION = $(LIBXML2_VERSION_MAJOR)$(LIBXML2_VERSION_MAJOR_SEPARATOR)$(LIBXML2_VERSION_MINOR)$(LIBXML2_VERSION_MINOR_SEPARATOR)$(LIBXML2_VERSION_RELEASE)

#
# libxml2 name
#
LIBXML2_NAME_SEPARATOR = -
LIBXML2_NAME_BASE = libxml2
LIBXML2_NAME = $(LIBXML2_NAME_BASE)$(LIBXML2_NAME_SEPARATOR)$(LIBXML2_VERSION)
LIBXML2_INSTALL_NAME_SEPARATOR = -
LIBXML2_INSTALL_NAME_BASE = libxml2
LIBXML2_INSTALL_NAME = $(LIBXML2_INSTALL_NAME_BASE)$(LIBXML2_INSTALL_NAME_SEPARATOR)$(LIBXML2_VERSION)
LIBXML2_DIR = $(LIBXML2_NAME)

#
# libxml2 archive
#
LIBXML2_ARCHIVED = tar
LIBXML2_COMPRESSED = gz
LIBXML2_ARCHIVE_SEPARATOR = .
LIBXML2_ARCHIVED_SEPARATOR = $(LIBXML2_ARCHIVE_SEPARATOR)
LIBXML2_COMPRESSED_SEPARATOR = $(LIBXML2_ARCHIVE_SEPARATOR)

LIBXML2_EXTRACT_DIR = $(LIBXML2_NAME)
LIBXML2_TGZ_NAME = $(LIBXML2_NAME)
LIBXML2_TGZ_PREFIX =
LIBXML2_TGZ = $(LIBXML2_TGZ_NAME)$(LIBXML2_TGZ_PREFIX)$(LIBXML2_ARCHIVED_SEPARATOR)$(LIBXML2_ARCHIVED)$(LIBXML2_COMPRESSED_SEPARATOR)$(LIBXML2_COMPRESSED)
LIBXML2_PATCH_TGZ_PREFIX = $(LIBXML2_NAME_SEPARATOR)xde-windows-patch
LIBXML2_PATCH_TGZ = $(LIBXML2_TGZ_NAME)$(LIBXML2_PATCH_TGZ_PREFIX)$(LIBXML2_ARCHIVED_SEPARATOR)$(LIBXML2_ARCHIVED)$(LIBXML2_COMPRESSED_SEPARATOR)$(LIBXML2_COMPRESSED)
LIBXML2_PATCHED_TGZ_PREFIX = $(LIBXML2_PATCH_TGZ_PREFIX)ed
LIBXML2_PATCHED_TGZ = $(LIBXML2_TGZ_NAME)$(LIBXML2_PATCHED_TGZ_PREFIX)$(LIBXML2_ARCHIVED_SEPARATOR)$(LIBXML2_ARCHIVED)$(LIBXML2_COMPRESSED_SEPARATOR)$(LIBXML2_COMPRESSED)
LIBXML2_DOCS_TGZ_PREFIX = $(LIBXML2_NAME_SEPARATOR)docs
LIBXML2_DOCS_TGZ = $(LIBXML2_TGZ_NAME)$(LIBXML2_DOCS_TGZ_PREFIX)$(LIBXML2_ARCHIVED_SEPARATOR)$(LIBXML2_ARCHIVED)$(LIBXML2_COMPRESSED_SEPARATOR)$(LIBXML2_COMPRESSED)
LIBXML2_BUILD_TGZ_PREFIX = $(LIBXML2_NAME_SEPARATOR)build
LIBXML2_BUILD_TGZ = $(LIBXML2_TGZ_NAME)$(LIBXML2_DOCS_TGZ_PREFIX)$(LIBXML2_ARCHIVED_SEPARATOR)$(LIBXML2_ARCHIVED)$(LIBXML2_COMPRESSED_SEPARATOR)$(LIBXML2_COMPRESSED)

#
# libxml2 extract
#
ifeq ($(LIBXML2_ARCHIVED),tar)
ifeq ($(LIBXML2_COMPRESSED),gz)
LIBXML2_TAR_UNCOMPRESS = z
LIBXML2_TAR_COMPRESS = z
else
ifeq ($(LIBXML2_COMPRESSED),bz2)
LIBXML2_TAR_UNCOMPRESS = j
LIBXML2_TAR_COMPRESS = j
else
ifeq ($(LIBXML2_COMPRESSED),xz)
LIBXML2_TAR_UNCOMPRESS = J
LIBXML2_TAR_COMPRESS = J
else
endif
endif
endif
LIBXML2_LIST = tar -tv$(LIBXML2_TAR_UNCOMPRESS)f
LIBXML2_EXTRACT = tar -x$(LIBXML2_TAR_UNCOMPRESS)f
LIBXML2_ARCHIVE = tar -cv$(LIBXML2_TAR_COMPRESS)f
else
ifeq ($(LIBXML2_ARCHIVED),zip)
LIBXML2_LIST = unzip -l
LIBXML2_EXTRACT = unzip
LIBXML2_ARCHIVE = zip
else
LIBXML2_LIST = echo unable to list
LIBXML2_EXTRACT = echo unable to extract
LIBXML2_ARCHIVE = echo unable to archive
endif
endif

LIBXML2_LIST_TGZ = $(LIBXML2_LIST) $(LIBXML2_TGZ)
LIBXML2_EXTRACT_TGZ = $(LIBXML2_EXTRACT) $(LIBXML2_TGZ)
LIBXML2_TOUCH_EXTRACT = touch $(LIBXML2_DIR)
LIBXML2_REMOVE_DIR = $(LIBXML2_REMOVE) $(LIBXML2_DIR)

LIBXML2_LIST_PATCH = $(LIBXML2_LIST)
LIBXML2_EXTRACT_PATCH = $(LIBXML2_EXTRACT)
LIBXML2_LIST_PATCH_TGZ = $(LIBXML2_LIST_PATCH) $(LIBXML2_PATCH_TGZ)
LIBXML2_EXTRACT_PATCH_TGZ = $(LIBXML2_EXTRACT_PATCH) $(LIBXML2_PATCH_TGZ)

LIBXML2_LIST_PATCHED = $(LIBXML2_LIST)
LIBXML2_EXTRACT_PATCHED = $(LIBXML2_EXTRACT)
LIBXML2_LIST_PATCHED_TGZ = $(LIBXML2_LIST_PATCHED) $(LIBXML2_PATCHED_TGZ)
LIBXML2_EXTRACT_PATCHED_TGZ = $(LIBXML2_EXTRACT_PATCHED) $(LIBXML2_PATCHED_TGZ)

LIBXML2_LIST_DOCS = $(LIBXML2_LIST)
LIBXML2_EXTRACT_DOCS = $(LIBXML2_EXTRACT)
LIBXML2_LIST_DOCS_TGZ = $(LIBXML2_LIST_DOCS) $(LIBXML2_DOCS_TGZ)
LIBXML2_EXTRACT_DOCS_TGZ = $(LIBXML2_EXTRACT_DOCS) $(LIBXML2_DOCS_TGZ) -C$(LIBXML2_DOCS_PREFIX)

LIBXML2_LIST_BUILD = $(LIBXML2_LIST)
LIBXML2_EXTRACT_BUILD = $(LIBXML2_EXTRACT)
LIBXML2_LIST_BUILD_TGZ = $(LIBXML2_LIST_BUILD) $(LIBXML2_BUILD_TGZ)
LIBXML2_EXTRACT_BUILD_TGZ = $(LIBXML2_EXTRACT_BUILD) $(LIBXML2_BUILD_TGZ) -C$(LIBXML2_BUILD_PREFIX)

#
# libxml2 build
#
ifndef LIBXML2_BUILD_HOME
LIBXML2_BUILD = $(HOME)/build
else
LIBXML2_BUILD = $(LIBXML2_BUILD_HOME)/build
endif
LIBXML2_PREFIX = $(LIBXML2_BUILD)/$(LIBXML2_INSTALL_NAME)
LIBXML2_EXEC_PREFIX = $(LIBXML2_PREFIX)
LIBXML2_CONF_PREFIX = $(LIBXML2_PREFIX)
LIBXML2_DOCS_PREFIX = $(LIBXML2_PREFIX)
LIBXML2_LINK_NAME = $(LIBXML2_BUILD)/$(LIBXML2_INSTALL_NAME_BASE)

LIBXML2_MKDIR = mkdir -p
LIBXML2_REMOVE = rm -r -f

LIBXML2_MAKE_DIR = $(LIBXML2_DIR)
LIBXML2_MAKE_PUSHD = pushd $(LIBXML2_MAKE_DIR)
LIBXML2_MAKE = make

#
# libxml2 configure
#
ifdef STATIC
LIBXML2_CONFIGURE_UNAME = --enable-shared=no
else
ifneq ($(LIBXML2_UNAME), Darwin)
LIBXML2_CONFIGURE_UNAME = --enable-shared=no
else
LIBXML2_CONFIGURE_UNAME = --enable-shared=yes
endif
endif
LIBXML2_CONFIGURE_CONFIGURE = ./configure
LIBXML2_CONFIGURE_HELP = $(LIBXML2_CONFIGURE_CONFIGURE) --help
LIBXML2_CONFIGURE_PUSHD = pushd $(LIBXML2_MAKE_DIR)
LIBXML2_CONFIGURE = $(LIBXML2_CONFIGURE_CONFIGURE) \
$(LIBXML2_CONFIGURE_UNAME) --prefix=$(LIBXML2_PREFIX) --exec_prefix=$(LIBXML2_EXEC_PREFIX) 

#
# libxml2 help
#
LIBXML2_HELP = $(LIBXML2_CONFIGURE_HELP)

########################################################################
#
# rules
#
########################################################################

all: usage

usage:
	@(echo)
	@(echo usage make extract config build install install-links)
	@(echo)
	@(echo extract -- extract $(LIBXML2_TGZ))
	@(echo config -- config $(LIBXML2_DIR) Makefile)
	@(echo build -- $(LIBXML2_DIR)/make build )
	@(echo install -- $(LIBXML2_DIR)/make install "->" $(LIBXML2_PREFIX))
	@(echo install-links -- link $(LIBXML2_LINK_NAME) "->" $(LIBXML2_PREFIX))
	@(echo)

package: archive unextract

again: unextract build

test: test-libxml2

########################################################################
# install
########################################################################

install-links: install-libxml2-links

install-docs: install-libxml2-docs

install-prefix: install-libxml2-prefix

install: install-libxml2

uninstall: uninstall-libxml2

########################################################################
# build
########################################################################

build: build-libxml2

clean: clean-libxml2

configed: configed-$(LIBXML2_DIR)

config: config-$(LIBXML2_DIR)

unconfig: unextract

help: help-libxml2

########################################################################
# docs
########################################################################

list-docs: list-libxml2-docs

extract-docs: extract-libxml2-docs

archive-docs: archive-libxml2-docs

docs-archived: libxml2-docs-archived

########################################################################
# patch
########################################################################

list-patch: list-libxml2-patch

extract-patch: extract-libxml2-patch

archive-patch: archive-libxml2-patch

patch-archived: libxml2-patch-archived

########################################################################
# patched
########################################################################

list-patched: list-libxml2-patched

extract-patched: extract-libxml2-patched

archive-patched: archive-libxml2-patched

patched-archived: libxml2-patched-archived

########################################################################
# build
########################################################################

list-build: list-libxml2-build

extract-build: extract-libxml2-build

archive-build: archive-libxml2-build

build-archived: libxml2-build-archived

########################################################################
# archive
########################################################################

list: list-libxml2

extract: extract-libxml2

unextract: unextract-libxml2

archive: archive-libxml2

linked: libxml2-linked

prefixed: libxml2-prefixed

archived: libxml2-archived

extracted: libxml2-extracted

########################################################################
#
# libxml2 rules
#
########################################################################

#
# Help libxml2
#
help-libxml2: $(LIBXML2_DIR)
	@($(LIBXML2_CONFIGURE_PUSHD);\
	  (($(LIBXML2_HELP)) || (exit 1));\
	  popd)

#
# Install libxml2
#
install-libxml2: configed-$(LIBXML2_DIR)
	@(echo Installing $(LIBXML2_DIR)...;\
	  $(LIBXML2_MAKE_PUSHD);\
	  (($(LIBXML2_MAKE) install) || (exit 1)) && \
	  ((touch $(LIBXML2_MAKEDIR)/configed-$(LIBXML2_DIR)) || (exit 1));\
	  popd)

#
# Build libxml2
#
build-libxml2: configed-$(LIBXML2_DIR)
	@(echo Building $(LIBXML2_DIR)...;\
	  $(LIBXML2_MAKE_PUSHD);\
	  (($(LIBXML2_MAKE)) || (exit 1)) && \
	  ((touch $(LIBXML2_MAKEDIR)/configed-$(LIBXML2_DIR)) || (exit 1));\
	  popd)

#
# Clean libxml2
#
clean-libxml2: configed-$(LIBXML2_DIR)
	@(echo Cleaning $(LIBXML2_DIR)...;\
	  $(LIBXML2_MAKE_PUSHD);\
	  (($(LIBXML2_MAKE) clean) || (exit 1)) && \
	  ((touch $(LIBXML2_MAKEDIR)/configed-$(LIBXML2_DIR)) || (exit 1));\
	  popd)

#
# Test libxml2
#
test-libxml2: configed-$(LIBXML2_DIR)
	@(echo Building test $(LIBXML2_DIR)...;\
	  $(LIBXML2_MAKE_PUSHD);\
	  (($(LIBXML2_MAKE) test) || (exit 1)) && \
	  ((touch $(LIBXML2_MAKEDIR)/configed-$(LIBXML2_DIR)) || (exit 1));\
	  popd)

#
# Config libxml2
#
config-$(LIBXML2_DIR): unconfig-$(LIBXML2_DIR) configed-$(LIBXML2_DIR)

unconfig-$(LIBXML2_DIR):
	@(rm -f configed-$(LIBXML2_DIR))

configed-$(LIBXML2_DIR): $(LIBXML2_DIR)
	@(echo Configing $(LIBXML2_DIR)...;\
	  $(LIBXML2_CONFIGURE_PUSHD);\
	  (($(LIBXML2_CONFIGURE)) || (exit 1)) && \
	  ((touch $(LIBXML2_DIR)) || (exit 1)) && \
	  ((touch $(LIBXML2_MAKEDIR)/configed-$(LIBXML2_DIR)) || (exit 1));\
	  popd)

########################################################################
# docs
########################################################################

#
# List libxml2 docs
#
list-libxml2-docs: $(LIBXML2_DOCS_TGZ)
	@(echo Listing $(LIBXML2_DOCS_TGZ)...;\
	  (($(LIBXML2_LIST_DOCS_TGZ)) || (exit 1)))

#
# Install libxml2 docs
#
install-libxml2-docs: $(LIBXML2_DOCS_PREFIX)
	@(echo Extracting $(LIBXML2_DOCS_TGZ)...;\
	  (($(LIBXML2_EXTRACT_DOCS_TGZ)) || (exit 1)))

#
# libxml2 docs archived
#
libxml2-docs-archived:
	@(echo $(LIBXML2_DOCS_TGZ))

#
# Archive libxml2 docs
#
archive-libxml2-docs:
	@(echo Archiving $(LIBXML2_DIR) to $(LIBXML2_DOCS_TGZ)...;\
	  (($(LIBXML2_ARCHIVE) $(LIBXML2_DOCS_TGZ) $(LIBXML2_DIR)) || (exit 1)))

########################################################################
# patch
########################################################################

#
# List libxml2 patch
#
list-libxml2-patch: $(LIBXML2_PATCH_TGZ)
	@(echo Listing $(LIBXML2_PATCH_TGZ)...;\
	  (($(LIBXML2_LIST_PATCH_TGZ)) || (exit 1)))

#
# Extract libxml2 patch
#
extract-libxml2-patch: $(LIBXML2_DIR)
	@(echo Extracting $(LIBXML2_PATCH_TGZ)...;\
	  (($(LIBXML2_EXTRACT_PATCH_TGZ)) || (exit 1)))

#
# libxml2 patch archived
#
libxml2-patch-archived:
	@(echo $(LIBXML2_PATCH_TGZ))

#
# Archive libxml2 patch
#
archive-libxml2-patch:
	@(echo Archiving $(LIBXML2_DIR) to $(LIBXML2_PATCH_TGZ)...;\
	  (($(LIBXML2_ARCHIVE) $(LIBXML2_PATCH_TGZ) $(LIBXML2_DIR)) || (exit 1)))

########################################################################
# patched
########################################################################

#
# List libxml2 patched
#
list-libxml2-patched: $(LIBXML2_PATCHED_TGZ)
	@(echo Listing $(LIBXML2_PATCHED_TGZ)...;\
	  (($(LIBXML2_LIST_PATCHED_TGZ)) || (exit 1)))

#
# Extract libxml2 patched
#
extract-libxml2-patched: $(LIBXML2_DIR)
	@(echo Extracting $(LIBXML2_PATCHED_TGZ)...;\
	  (($(LIBXML2_EXTRACT_PATCHED_TGZ)) || (exit 1)))

#
# libxml2 patched archived
#
libxml2-patched-archived:
	@(echo $(LIBXML2_PATCHED_TGZ))

#
# Archive libxml2 patched
#
archive-libxml2-patched:
	@(echo Archiving $(LIBXML2_DIR) to $(LIBXML2_PATCHED_TGZ)...;\
	  (($(LIBXML2_ARCHIVE) $(LIBXML2_PATCHED_TGZ) $(LIBXML2_DIR)) || (exit 1)))

########################################################################
# build
########################################################################

#
# List libxml2 build
#
list-libxml2-build: $(LIBXML2_BUILD_TGZ)
	@(echo Listing $(LIBXML2_BUILD_TGZ)...;\
	  (($(LIBXML2_LIST_BUILD_TGZ)) || (exit 1)))

#
# Extract libxml2 build
#
extract-libxml2-build: $(LIBXML2_DIR)
	@(echo Extracting $(LIBXML2_BUILD_TGZ)...;\
	  (($(LIBXML2_EXTRACT_BUILD_TGZ)) || (exit 1)))

#
# libxml2 build archived
#
libxml2-build-archived:
	@(echo $(LIBXML2_BUILD_TGZ))

#
# Archive libxml2 build
#
archive-libxml2-build:
	@(echo Archiving $(LIBXML2_DIR) to $(LIBXML2_BUILD_TGZ)...;\
	  (($(LIBXML2_ARCHIVE) $(LIBXML2_BUILD_TGZ) $(LIBXML2_DIR)) || (exit 1)))

########################################################################
# archive
########################################################################

#
# List libxml2
#
list-libxml2:
	@(echo Listing $(LIBXML2_TGZ)...;\
	  (($(LIBXML2_LIST_TGZ)) || (exit 1)))

#
# libxml2 extracted
#
libxml2-extracted:
	@(echo $(LIBXML2_EXTRACT) $(LIBXML2_TGZ))

#
# Extract libxml2
#
extract-libxml2: unextract-libxml2 $(LIBXML2_DIR)

unextract-libxml2: unconfig-$(LIBXML2_DIR)
	@(echo Removing $(LIBXML2_DIR)...;\
	  (($(LIBXML2_REMOVE_DIR)) || (exit 1)))

$(LIBXML2_DIR): $(LIBXML2_TGZ)
	@(echo Extracting $(LIBXML2_TGZ)...;\
	  (($(LIBXML2_EXTRACT_TGZ)) || (exit 1)) && \
	  (($(LIBXML2_TOUCH_EXTRACT)) || (exit 1)))

#
# libxml2 archived
#
libxml2-archived:
	@(echo $(LIBXML2_TGZ))

#
# Archive libxml2
#
archive-libxml2:
	@(echo Archiving $(LIBXML2_DIR) to $(LIBXML2_TGZ)...;\
	  (($(LIBXML2_ARCHIVE) $(LIBXML2_TGZ) $(LIBXML2_DIR)) || (exit 1)))

########################################################################
# links
########################################################################

#
# libxml2 linked
#
libxml2-linked:
	@echo link is $(LIBXML2_LINK_NAME) "->" $(LIBXML2_PREFIX)

#
# Install libxml2 links
#
install-libxml2-links:
	@((echo removing $(LIBXML2_LINK_NAME)) && \
	  ((rm -f $(LIBXML2_LINK_NAME)) || (exit 1)) && \
	  (echo Linking $(LIBXML2_LINK_NAME) "->" $(LIBXML2_PREFIX)) && \
	  ((ln -s $(LIBXML2_PREFIX) $(LIBXML2_LINK_NAME)) || (exit 1)))

#
# Uninstall libxml2
#
uninstall-libxml2:
	@((echo Removing $(LIBXML2_LINK_NAME)) && \
	  ((rm -f $(LIBXML2_LINK_NAME)) || (exit 1)) && \
	  (echo Removing $(LIBXML2_PREFIX)) && \
	  ((rm -rf $(LIBXML2_PREFIX)) || (exit 1)))

########################################################################
# prefix
########################################################################

#
# libxml2 prefixed
#
libxml2-prefixed:
	@((echo prefix is $(LIBXML2_PREFIX)) && \
	  (echo exec prefix is $(LIBXML2_EXEC_PREFIX)) && \
	  (echo conf prefix is $(LIBXML2_CONF_PREFIX)) && \
	  (echo docs prefix is $(LIBXML2_DOCS_PREFIX)))

#
# Install libxml2 prefix
#
install-libxml2-prefix:
	@((echo makeing $(LIBXML2_PREFIX)) && \
	  ((mkdir -p $(LIBXML2_PREFIX)) || (exit 1)) && \
	  (echo makeing $(LIBXML2_EXEC_PREFIX)) && \
	  ((mkdir -p $(LIBXML2_EXEC_PREFIX)) || (exit 1)))

$(LIBXML2_PREFIX):
	@(echo Makeing Directory $(LIBXML2_PREFIX)...;\
	  (($(LIBXML2_MKDIR) $(LIBXML2_PREFIX)) || (exit 1)))

$(LIBXML2_EXEC_PREFIX):
	@(echo Makeing Directory $(LIBXML2_EXEC_PREFIX)...;\
	  (($(LIBXML2_MKDIR) $(LIBXML2_EXEC_PREFIX)) || (exit 1)))

$(LIBXML2_CONF_PREFIX):
	@(echo Makeing Directory $(LIBXML2_CONF_PREFIX)...;\
	  (($(LIBXML2_MKDIR) $(LIBXML2_CONF_PREFIX)) || (exit 1)))

$(LIBXML2_DOCS_PREFIX):
	@(echo Makeing Directory $(LIBXML2_DOCS_PREFIX)...;\
	  (($(LIBXML2_MKDIR) $(LIBXML2_DOCS_PREFIX)) || (exit 1)))
