########################################################################
# Copyright (c) 1988-2016 $organization$
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
#   Date: 8/8/2016
#
# Thirdpary Makefile for zlib
########################################################################

MAKEDIR=$(PWD)

########################################################################
#
# zlib defs
#
########################################################################
ZLIB_VERSION_MAJOR = 1
ZLIB_VERSION_MINOR = 2
ZLIB_VERSION_RELEASE = 8

ZLIB_VERSION_SEPARATOR = .
ZLIB_VERSION_MAJOR_SEPARATOR = $(ZLIB_VERSION_SEPARATOR)
ZLIB_VERSION_MINOR_SEPARATOR = $(ZLIB_VERSION_SEPARATOR)

ZLIB_VERSION_SHORT = $(ZLIB_VERSION_MAJOR)$(ZLIB_VERSION_MINOR)$(ZLIB_VERSION_RELEASE)
ZLIB_VERSION = $(ZLIB_VERSION_MAJOR)$(ZLIB_VERSION_MAJOR_SEPARATOR)$(ZLIB_VERSION_MINOR)$(ZLIB_VERSION_MINOR_SEPARATOR)$(ZLIB_VERSION_RELEASE)

ZLIB_NAME_SEPARATOR = -
ZLIB_NAME_BASE = zlib
ZLIB_NAME = $(ZLIB_NAME_BASE)$(ZLIB_NAME_SEPARATOR)$(ZLIB_VERSION)
ZLIB_INSTALL_NAME_SEPARATOR = -
ZLIB_INSTALL_NAME = $(ZLIB_NAME_BASE)$(ZLIB_INSTALL_NAME_SEPARATOR)$(ZLIB_VERSION)

ZLIB_ARCHIVED = tar
ZLIB_COMPRESSED = gz
ZLIB_ARCHIVE_SEPARATOR = .
ZLIB_ARCHIVED_SEPARATOR = $(ZLIB_ARCHIVE_SEPARATOR)
ZLIB_COMPRESSED_SEPARATOR = $(ZLIB_ARCHIVE_SEPARATOR)

ZLIB_BUILD = $(MAKEDIR)/../build
ZLIB_PREFIX = $(ZLIB_BUILD)/$(ZLIB_INSTALL_NAME)
ZLIB_EXEC_PREFIX = $(ZLIB_PREFIX)
ZLIB_CONF_PREFIX = $(ZLIB_PREFIX)
ZLIB_DOCS_PREFIX = $(ZLIB_PREFIX)
ZLIB_LINK_NAME = $(ZLIB_BUILD)/$(ZLIB_NAME_BASE)
ZLIB_DIR = $(ZLIB_NAME)
ZLIB_EXTRACT_DIR = $(ZLIB_NAME)
ZLIB_TGZ_PREFIX =
ZLIB_TGZ = $(ZLIB_NAME)$(ZLIB_TGZ_PREFIX)$(ZLIB_ARCHIVED_SEPARATOR)$(ZLIB_ARCHIVED)$(ZLIB_COMPRESSED_SEPARATOR)$(ZLIB_COMPRESSED)
ZLIB_PATCH_TGZ_PREFIX = $(ZLIB_NAME_SEPARATOR)patch
ZLIB_PATCH_TGZ = $(ZLIB_NAME)$(ZLIB_PATCH_TGZ_PREFIX)$(ZLIB_ARCHIVED_SEPARATOR)$(ZLIB_ARCHIVED)$(ZLIB_COMPRESSED_SEPARATOR)$(ZLIB_COMPRESSED)
ZLIB_DOCS_TGZ_PREFIX = $(ZLIB_NAME_SEPARATOR)docs
ZLIB_DOCS_TGZ = $(ZLIB_NAME)$(ZLIB_DOCS_TGZ_PREFIX)$(ZLIB_ARCHIVED_SEPARATOR)$(ZLIB_ARCHIVED)$(ZLIB_COMPRESSED_SEPARATOR)$(ZLIB_COMPRESSED)

ifeq ($(ZLIB_ARCHIVED),tar)
ifeq ($(ZLIB_COMPRESSED),gz)
ZLIB_TAR_UNCOMPRESS = z
ZLIB_TAR_COMPRESS = z
else
ifeq ($(ZLIB_COMPRESSED),bz2)
ZLIB_TAR_UNCOMPRESS = j
ZLIB_TAR_COMPRESS = j
else
endif
endif
ZLIB_LIST = tar -tv$(ZLIB_TAR_UNCOMPRESS)f
ZLIB_EXTRACT = tar -x$(ZLIB_TAR_UNCOMPRESS)f
ZLIB_ARCHIVE = tar -cv$(ZLIB_TAR_COMPRESS)f
else
ifeq ($(ZLIB_ARCHIVED),zip)
ZLIB_LIST = unzip -l
ZLIB_EXTRACT = unzip
ZLIB_ARCHIVE = zip
else
ZLIB_LIST = echo unable to list
ZLIB_EXTRACT = echo unable to extract
ZLIB_ARCHIVE = echo unable to archive
endif
endif

ZLIB_MKDIR = mkdir -p
ZLIB_REMOVE = rm -r -f

ZLIB_MAKE_DIR = $(ZLIB_DIR)
ZLIB_MAKE_PUSHD = pushd $(ZLIB_MAKE_DIR)
ZLIB_MAKE = make

ZLIB_CONFIGURE_PUSHD = pushd $(ZLIB_MAKE_DIR)
ZLIB_CONFIGURE = ./configure --prefix=$(ZLIB_PREFIX) --eprefix=$(ZLIB_EXEC_PREFIX)
ZLIB_HELP = ./configure --help

ZLIB_LIST_TGZ = $(ZLIB_LIST) $(ZLIB_TGZ)
ZLIB_EXTRACT_TGZ = $(ZLIB_EXTRACT) $(ZLIB_TGZ)
ZLIB_TOUCH_EXTRACT = touch $(ZLIB_DIR)
ZLIB_REMOVE_DIR = $(ZLIB_REMOVE) $(ZLIB_DIR)

ZLIB_LIST_PATCH = $(ZLIB_LIST)
ZLIB_EXTRACT_PATCH = $(ZLIB_EXTRACT)
ZLIB_LIST_PATCH_TGZ = $(ZLIB_LIST_PATCH) $(ZLIB_PATCH_TGZ)
ZLIB_EXTRACT_PATCH_TGZ = $(ZLIB_EXTRACT_PATCH) $(ZLIB_PATCH_TGZ)

ZLIB_LIST_DOCS = $(ZLIB_LIST)
ZLIB_EXTRACT_DOCS = $(ZLIB_EXTRACT)
ZLIB_LIST_DOCS_TGZ = $(ZLIB_LIST_DOCS) $(ZLIB_DOCS_TGZ)
ZLIB_EXTRACT_DOCS_TGZ = $(ZLIB_EXTRACT_DOCS) $(ZLIB_DOCS_TGZ) -C$(ZLIB_DOCS_PREFIX)

########################################################################
#
# rules
#
########################################################################

all:

test: test-zlib

install-links: install-zlib-links

install-docs: install-zlib-docs

install-prefix: install-zlib-prefix

install: install-zlib

build: build-zlib

clean: clean-zlib

configed: configed-$(ZLIB_DIR)

config: config-$(ZLIB_DIR)

help: help-zlib

list-docs: list-zlib-docs

list-patch: list-zlib-patch

extract-patch: extract-zlib-patch

list: list-zlib

extract: extract-zlib

unextract: unextract-zlib

archive: archive-zlib

linked: zlib-linked

prefixed: zlib-prefixed

archived: zlib-archived

extracted: zlib-extracted

unconfig: unextract

########################################################################
#
# zlib rules
#
########################################################################

#
# Test zlib
#
test-zlib:
	@($(ZLIB_MAKE_PUSHD);\
	  (($(ZLIB_MAKE) test) || (exit 1));\
	  popd)

#
# Install zlib
#
install-zlib: configed-$(ZLIB_DIR)
	@(echo Installing $(ZLIB_DIR)...;\
	  $(ZLIB_MAKE_PUSHD);\
	  (($(ZLIB_MAKE) install) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(ZLIB_DIR)) || (exit 1));\
	  popd)

#
# Build zlib
#
build-zlib: configed-$(ZLIB_DIR)
	@(echo Building $(ZLIB_DIR)...;\
	  $(ZLIB_MAKE_PUSHD);\
	  (($(ZLIB_MAKE)) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(ZLIB_DIR)) || (exit 1));\
	  popd)

#
# Clean zlib
#
clean-zlib: configed-$(ZLIB_DIR)
	@(echo Cleaning $(ZLIB_DIR)...;\
	  $(ZLIB_MAKE_PUSHD);\
	  (($(ZLIB_MAKE) clean) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(ZLIB_DIR)) || (exit 1));\
	  popd)

#
# Config zlib
#
config-$(ZLIB_DIR): unconfig-$(ZLIB_DIR) configed-$(ZLIB_DIR)

unconfig-$(ZLIB_DIR):
	@(rm -f configed-$(ZLIB_DIR))

configed-$(ZLIB_DIR): $(ZLIB_DIR)
	@(echo Configing $(ZLIB_DIR)...;\
	  $(ZLIB_CONFIGURE_PUSHD);\
	  (($(ZLIB_CONFIGURE)) || (exit 1)) && \
	  ((touch $(ZLIB_DIR)) || (exit 1)) && \
	  ((touch $(MAKEDIR)/configed-$(ZLIB_DIR)) || (exit 1));\
	  popd)

#
# Help zlib
#
help-zlib:
	@($(ZLIB_CONFIGURE_PUSHD);\
	  (($(ZLIB_HELP)) || (exit 1));\
	  popd)

#
# List zlib Docs
#
list-zlib-docs: $(ZLIB_DOCS_TGZ)
	@(echo Listing $(ZLIB_DOCS_TGZ)...;\
	  (($(ZLIB_LIST_DOCS_TGZ)) || (exit 1)))

#
# Install zlib Docs
#
install-zlib-docs: $(ZLIB_DOCS_PREFIX)
	@(echo Extracting $(ZLIB_DOCS_TGZ)...;\
	  (($(ZLIB_EXTRACT_DOCS_TGZ)) || (exit 1)))

#
# List zlib Patch
#
list-zlib-patch: $(ZLIB_PATCH_TGZ)
	@(echo Listing $(ZLIB_PATCH_TGZ)...;\
	  (($(ZLIB_LIST_PATCH_TGZ)) || (exit 1)))

#
# Extract zlib patch
#
extract-zlib-patch: $(ZLIB_DIR)
	@(echo Extracting $(ZLIB_PATCH_TGZ)...;\
	  (($(ZLIB_EXTRACT_PATCH_TGZ)) || (exit 1)))

#
# List zlib
#
list-zlib:
	@(echo Listing $(ZLIB_TGZ)...;\
	  (($(ZLIB_LIST_TGZ)) || (exit 1)))

#
# Extract zlib
#
extract-zlib: unextract-zlib $(ZLIB_DIR)

unextract-zlib: unconfig-$(ZLIB_DIR)
	@(echo Removing $(ZLIB_DIR)...;\
	  (($(ZLIB_REMOVE_DIR)) || (exit 1)))

$(ZLIB_DIR): $(ZLIB_TGZ)
	@(echo Extracting $(ZLIB_TGZ)...;\
	  (($(ZLIB_EXTRACT_TGZ)) || (exit 1)) && \
	  (($(ZLIB_TOUCH_EXTRACT)) || (exit 1)))

#
# Archive zlib
#
archive-zlib:
	@(echo Archiving $(ZLIB_DIR) to $(ZLIB_TGZ)...;\
	  (($(ZLIB_ARCHIVE) $(ZLIB_TGZ) $(ZLIB_DIR)) || (exit 1)))

#
# Install zlib links
#
install-zlib-links:
	@((echo removing $(ZLIB_LINK_NAME)) && \
	  ((rm -f $(ZLIB_LINK_NAME)) || (exit 1)) && \
	  (echo Linking $(ZLIB_LINK_NAME) "->" $(ZLIB_PREFIX)) && \
	  ((ln -s $(ZLIB_PREFIX) $(ZLIB_LINK_NAME)) || (exit 1)))

#
# zlib linked
#
zlib-linked:
	@echo link is $(ZLIB_LINK_NAME) "->" $(ZLIB_PREFIX)

#
# Install zlib prefix
#
install-zlib-prefix:
	@((echo makeing $(ZLIB_PREFIX)) && \
	  ((mkdir -p $(ZLIB_PREFIX)) || (exit 1)) && \
	  (echo makeing $(ZLIB_EXEC_PREFIX)) && \
	  ((mkdir -p $(ZLIB_EXEC_PREFIX)) || (exit 1)))

#
# zlib prefixed
#
zlib-prefixed:
	@((echo prefix is $(ZLIB_PREFIX)) && \
	  (echo exec prefix is $(ZLIB_EXEC_PREFIX)) && \
	  (echo conf prefix is $(ZLIB_CONF_PREFIX)) && \
	  (echo docs prefix is $(ZLIB_DOCS_PREFIX)))

$(ZLIB_PREFIX):
	@(echo Makeing Directory $(ZLIB_PREFIX)...;\
	  (($(ZLIB_MKDIR) $(ZLIB_PREFIX)) || (exit 1)))

$(ZLIB_EXEC_PREFIX):
	@(echo Makeing Directory $(ZLIB_EXEC_PREFIX)...;\
	  (($(ZLIB_MKDIR) $(ZLIB_EXEC_PREFIX)) || (exit 1)))

$(ZLIB_CONF_PREFIX):
	@(echo Makeing Directory $(ZLIB_CONF_PREFIX)...;\
	  (($(ZLIB_MKDIR) $(ZLIB_CONF_PREFIX)) || (exit 1)))

$(ZLIB_DOCS_PREFIX):
	@(echo Makeing Directory $(ZLIB_DOCS_PREFIX)...;\
	  (($(ZLIB_MKDIR) $(ZLIB_DOCS_PREFIX)) || (exit 1)))

#
# zlib archived
#
zlib-archived:
	@(echo $(ZLIB_TGZ))

#
# zlib extracted
#
zlib-extracted:
	@(echo $(ZLIB_EXTRACT) $(ZLIB_TGZ))
