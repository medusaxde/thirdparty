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
# Thirdparty Gcc Makefile for cgicc
########################################################################


########################################################################
#
# cgicc defs
#
########################################################################
CGICC_MAKEDIR=$(PWD)

CGICC_HOME_BUILD = $(HOME)/build
CGICC_HOME_SOURCE_BUILD = $(HOME)/source/build
CGICC_THIRDPARTY_BUILD = $(CGICC_MAKEDIR)/..

ifeq ($(CGICC_BUILD_HOME),HOME_BUILD)
CGICC_BUILD_HOME = $(CGICC_HOME_BUILD)
else
ifeq ($(CGICC_BUILD_HOME),HOME_SOURCE_BUILD)
CGICC_BUILD_HOME = $(CGICC_HOME_SOURCE_BUILD)
else
ifeq ($(CGICC_BUILD_HOME),CGICC_THIRDPARTY_BUILD)
CGICC_BUILD_HOME = $(CGICC_THIRDPARTY_BUILD)
else
ifndef CGICC_BUILD_HOME
CGICC_BUILD_HOME = $(CGICC_THIRDPARTY_BUILD)
endif
endif
endif
endif

ifndef CGICC_UNAME
CGICC_UNAME = $(shell uname)
endif

ifndef CGICC_OS
ifneq ($(CGICC_UNAME),Darwin)
CGICC_OS = linux
else
CGICC_OS = macosx
endif
endif

#
# cgicc version
#
ifeq ($(VERSION),3216)
CGICC_VERSION_MAJOR = 3
CGICC_VERSION_MINOR = 2
CGICC_VERSION_RELEASE = 16
else
CGICC_VERSION_MAJOR = 3
CGICC_VERSION_MINOR = 2
CGICC_VERSION_RELEASE = 16
endif

CGICC_VERSION_SEPARATOR = .
CGICC_VERSION_MAJOR_SEPARATOR = $(CGICC_VERSION_SEPARATOR)
CGICC_VERSION_MINOR_SEPARATOR = $(CGICC_VERSION_SEPARATOR)

CGICC_VERSION_SHORT = $(CGICC_VERSION_MAJOR)$(CGICC_VERSION_MINOR)$(CGICC_VERSION_RELEASE)
CGICC_VERSION = $(CGICC_VERSION_MAJOR)$(CGICC_VERSION_MAJOR_SEPARATOR)$(CGICC_VERSION_MINOR)$(CGICC_VERSION_MINOR_SEPARATOR)$(CGICC_VERSION_RELEASE)

#
# cgicc name
#
CGICC_NAME_SEPARATOR = -
CGICC_NAME_BASE = cgicc
CGICC_NAME = $(CGICC_NAME_BASE)$(CGICC_NAME_SEPARATOR)$(CGICC_VERSION)
CGICC_INSTALL_NAME_SEPARATOR = -
CGICC_INSTALL_NAME_BASE = cgicc
CGICC_INSTALL_NAME = $(CGICC_INSTALL_NAME_BASE)$(CGICC_INSTALL_NAME_SEPARATOR)$(CGICC_VERSION)
CGICC_DIR = $(CGICC_NAME)

#
# cgicc archive
#
CGICC_ARCHIVED = tar
CGICC_COMPRESSED = gz
CGICC_ARCHIVE_SEPARATOR = .
CGICC_ARCHIVED_SEPARATOR = $(CGICC_ARCHIVE_SEPARATOR)
CGICC_COMPRESSED_SEPARATOR = $(CGICC_ARCHIVE_SEPARATOR)

CGICC_EXTRACT_DIR = $(CGICC_NAME)
CGICC_TGZ_NAME = $(CGICC_NAME)
CGICC_TGZ_PREFIX =
CGICC_TGZ = $(CGICC_TGZ_NAME)$(CGICC_TGZ_PREFIX)$(CGICC_ARCHIVED_SEPARATOR)$(CGICC_ARCHIVED)$(CGICC_COMPRESSED_SEPARATOR)$(CGICC_COMPRESSED)
CGICC_PATCH_TGZ_PREFIX = $(CGICC_NAME_SEPARATOR)mxde-win-patch
CGICC_PATCH_TGZ = $(CGICC_TGZ_NAME)$(CGICC_PATCH_TGZ_PREFIX)$(CGICC_ARCHIVED_SEPARATOR)$(CGICC_ARCHIVED)$(CGICC_COMPRESSED_SEPARATOR)$(CGICC_COMPRESSED)
CGICC_PATCHED_TGZ_PREFIX = $(CGICC_PATCH_TGZ_PREFIX)ed
CGICC_PATCHED_TGZ = $(CGICC_TGZ_NAME)$(CGICC_PATCHED_TGZ_PREFIX)$(CGICC_ARCHIVED_SEPARATOR)$(CGICC_ARCHIVED)$(CGICC_COMPRESSED_SEPARATOR)$(CGICC_COMPRESSED)
CGICC_DOCS_TGZ_PREFIX = $(CGICC_NAME_SEPARATOR)docs
CGICC_DOCS_TGZ = $(CGICC_TGZ_NAME)$(CGICC_DOCS_TGZ_PREFIX)$(CGICC_ARCHIVED_SEPARATOR)$(CGICC_ARCHIVED)$(CGICC_COMPRESSED_SEPARATOR)$(CGICC_COMPRESSED)
CGICC_BUILD_TGZ_PREFIX = $(CGICC_NAME_SEPARATOR)build
CGICC_BUILD_TGZ = $(CGICC_TGZ_NAME)$(CGICC_DOCS_TGZ_PREFIX)$(CGICC_ARCHIVED_SEPARATOR)$(CGICC_ARCHIVED)$(CGICC_COMPRESSED_SEPARATOR)$(CGICC_COMPRESSED)

#
# cgicc extract
#
ifeq ($(CGICC_ARCHIVED),tar)
ifeq ($(CGICC_COMPRESSED),gz)
CGICC_TAR_UNCOMPRESS = z
CGICC_TAR_COMPRESS = z
else
ifeq ($(CGICC_COMPRESSED),bz2)
CGICC_TAR_UNCOMPRESS = j
CGICC_TAR_COMPRESS = j
else
ifeq ($(CGICC_COMPRESSED),xz)
CGICC_TAR_UNCOMPRESS = J
CGICC_TAR_COMPRESS = J
else
endif
endif
endif
CGICC_LIST = tar -tv$(CGICC_TAR_UNCOMPRESS)f
CGICC_EXTRACT = tar -x$(CGICC_TAR_UNCOMPRESS)f
CGICC_ARCHIVE = tar -cv$(CGICC_TAR_COMPRESS)f
else
ifeq ($(CGICC_ARCHIVED),zip)
CGICC_LIST = unzip -l
CGICC_EXTRACT = unzip
CGICC_ARCHIVE = zip
else
CGICC_LIST = echo unable to list
CGICC_EXTRACT = echo unable to extract
CGICC_ARCHIVE = echo unable to archive
endif
endif

CGICC_LIST_TGZ = $(CGICC_LIST) $(CGICC_TGZ)
CGICC_EXTRACT_TGZ = $(CGICC_EXTRACT) $(CGICC_TGZ)
CGICC_TOUCH_EXTRACT = touch $(CGICC_DIR)
CGICC_REMOVE_DIR = $(CGICC_REMOVE) $(CGICC_DIR)

CGICC_LIST_PATCH = $(CGICC_LIST)
CGICC_EXTRACT_PATCH = $(CGICC_EXTRACT)
CGICC_LIST_PATCH_TGZ = $(CGICC_LIST_PATCH) $(CGICC_PATCH_TGZ)
CGICC_EXTRACT_PATCH_TGZ = $(CGICC_EXTRACT_PATCH) $(CGICC_PATCH_TGZ)

CGICC_LIST_PATCHED = $(CGICC_LIST)
CGICC_EXTRACT_PATCHED = $(CGICC_EXTRACT)
CGICC_LIST_PATCHED_TGZ = $(CGICC_LIST_PATCHED) $(CGICC_PATCHED_TGZ)
CGICC_EXTRACT_PATCHED_TGZ = $(CGICC_EXTRACT_PATCHED) $(CGICC_PATCHED_TGZ)

CGICC_LIST_DOCS = $(CGICC_LIST)
CGICC_EXTRACT_DOCS = $(CGICC_EXTRACT)
CGICC_LIST_DOCS_TGZ = $(CGICC_LIST_DOCS) $(CGICC_DOCS_TGZ)
CGICC_EXTRACT_DOCS_TGZ = $(CGICC_EXTRACT_DOCS) $(CGICC_DOCS_TGZ) -C$(CGICC_DOCS_PREFIX)

CGICC_LIST_BUILD = $(CGICC_LIST)
CGICC_EXTRACT_BUILD = $(CGICC_EXTRACT)
CGICC_LIST_BUILD_TGZ = $(CGICC_LIST_BUILD) $(CGICC_BUILD_TGZ)
CGICC_EXTRACT_BUILD_TGZ = $(CGICC_EXTRACT_BUILD) $(CGICC_BUILD_TGZ) -C$(CGICC_BUILD_PREFIX)

#
# cgicc build
#
ifndef CGICC_BUILD_HOME
CGICC_BUILD = $(HOME)/build
else
CGICC_BUILD = $(CGICC_BUILD_HOME)/build
endif
CGICC_PREFIX = $(CGICC_BUILD)/$(CGICC_INSTALL_NAME)
CGICC_EXEC_PREFIX = $(CGICC_PREFIX)
CGICC_CONF_PREFIX = $(CGICC_PREFIX)
CGICC_DOCS_PREFIX = $(CGICC_PREFIX)
CGICC_LINK_NAME = $(CGICC_BUILD)/$(CGICC_INSTALL_NAME_BASE)

CGICC_MKDIR = mkdir -p
CGICC_REMOVE = rm -r -f

CGICC_MAKE_DIR = $(CGICC_DIR)
CGICC_MAKE_PUSHD = pushd $(CGICC_MAKE_DIR)
CGICC_MAKE = make

#
# cgicc configure
#
ifdef STATIC
CGICC_CONFIGURE_UNAME = --enable-shared=no
else
ifneq ($(CGICC_UNAME), Darwin)
CGICC_CONFIGURE_UNAME = --enable-shared=no
else
CGICC_CONFIGURE_UNAME = --enable-shared=yes
endif
endif
CGICC_CONFIGURE_CONFIGURE = ./configure
CGICC_CONFIGURE_HELP = $(CGICC_CONFIGURE_CONFIGURE) --help
CGICC_CONFIGURE_PUSHD = pushd $(CGICC_MAKE_DIR)
CGICC_CONFIGURE = $(CGICC_CONFIGURE_CONFIGURE) \
$(CGICC_CONFIGURE_UNAME) --prefix=$(CGICC_PREFIX) --exec_prefix=$(CGICC_EXEC_PREFIX)

#
# cgicc help
#
CGICC_HELP = $(CGICC_CONFIGURE_HELP)

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
	@(echo extract -- extract $(CGICC_TGZ))
	@(echo config -- config $(CGICC_DIR) Makefile)
	@(echo build -- $(CGICC_DIR)/make build )
	@(echo install -- $(CGICC_DIR)/make install "->" $(CGICC_PREFIX))
	@(echo install-links -- link $(CGICC_LINK_NAME) "->" $(CGICC_PREFIX))
	@(echo)

package: archive unextract

again: unextract build

test: test-cgicc

########################################################################
# install
########################################################################

install-links: install-cgicc-links

install-docs: install-cgicc-docs

install-prefix: install-cgicc-prefix

install: install-cgicc

uninstall: uninstall-cgicc

########################################################################
# build
########################################################################

build: build-cgicc

clean: clean-cgicc

configed: configed-$(CGICC_DIR)

config: config-$(CGICC_DIR)

unconfig: unextract

help: help-cgicc

########################################################################
# docs
########################################################################

list-docs: list-cgicc-docs

extract-docs: extract-cgicc-docs

archive-docs: archive-cgicc-docs

docs-archived: cgicc-docs-archived

########################################################################
# patch
########################################################################

list-patch: list-cgicc-patch

extract-patch: extract-cgicc-patch

archive-patch: archive-cgicc-patch

patch-archived: cgicc-patch-archived

########################################################################
# patched
########################################################################

list-patched: list-cgicc-patched

extract-patched: extract-cgicc-patched

archive-patched: archive-cgicc-patched

patched-archived: cgicc-patched-archived

########################################################################
# build
########################################################################

list-build: list-cgicc-build

extract-build: extract-cgicc-build

archive-build: archive-cgicc-build

build-archived: cgicc-build-archived

########################################################################
# archive
########################################################################

list: list-cgicc

extract: extract-cgicc

unextract: unextract-cgicc

archive: archive-cgicc

linked: cgicc-linked

prefixed: cgicc-prefixed

archived: cgicc-archived

extracted: cgicc-extracted

########################################################################
#
# cgicc rules
#
########################################################################

#
# Help cgicc
#
help-cgicc: $(CGICC_DIR)
	@($(CGICC_CONFIGURE_PUSHD);\
	  (($(CGICC_HELP)) || (exit 1));\
	  popd)

#
# Install cgicc
#
install-cgicc: configed-$(CGICC_DIR)
	@(echo Installing $(CGICC_DIR)...;\
	  $(CGICC_MAKE_PUSHD);\
	  (($(CGICC_MAKE) install) || (exit 1)) && \
	  ((touch $(CGICC_MAKEDIR)/configed-$(CGICC_DIR)) || (exit 1));\
	  popd)

#
# Build cgicc
#
build-cgicc: configed-$(CGICC_DIR)
	@(echo Building $(CGICC_DIR)...;\
	  $(CGICC_MAKE_PUSHD);\
	  (($(CGICC_MAKE)) || (exit 1)) && \
	  ((touch $(CGICC_MAKEDIR)/configed-$(CGICC_DIR)) || (exit 1));\
	  popd)

#
# Clean cgicc
#
clean-cgicc: configed-$(CGICC_DIR)
	@(echo Cleaning $(CGICC_DIR)...;\
	  $(CGICC_MAKE_PUSHD);\
	  (($(CGICC_MAKE) clean) || (exit 1)) && \
	  ((touch $(CGICC_MAKEDIR)/configed-$(CGICC_DIR)) || (exit 1));\
	  popd)

#
# Test cgicc
#
test-cgicc: configed-$(CGICC_DIR)
	@(echo Building test $(CGICC_DIR)...;\
	  $(CGICC_MAKE_PUSHD);\
	  (($(CGICC_MAKE) test) || (exit 1)) && \
	  ((touch $(CGICC_MAKEDIR)/configed-$(CGICC_DIR)) || (exit 1));\
	  popd)

#
# Config cgicc
#
config-$(CGICC_DIR): unconfig-$(CGICC_DIR) configed-$(CGICC_DIR)

unconfig-$(CGICC_DIR):
	@(rm -f configed-$(CGICC_DIR))

configed-$(CGICC_DIR): $(CGICC_DIR)
	@(echo Configing $(CGICC_DIR)...;\
	  $(CGICC_CONFIGURE_PUSHD);\
	  (($(CGICC_CONFIGURE)) || (exit 1)) && \
	  ((touch $(CGICC_DIR)) || (exit 1)) && \
	  ((touch $(CGICC_MAKEDIR)/configed-$(CGICC_DIR)) || (exit 1));\
	  popd)

########################################################################
# docs
########################################################################

#
# List cgicc docs
#
list-cgicc-docs: $(CGICC_DOCS_TGZ)
	@(echo Listing $(CGICC_DOCS_TGZ)...;\
	  (($(CGICC_LIST_DOCS_TGZ)) || (exit 1)))

#
# Install cgicc docs
#
install-cgicc-docs: $(CGICC_DOCS_PREFIX)
	@(echo Extracting $(CGICC_DOCS_TGZ)...;\
	  (($(CGICC_EXTRACT_DOCS_TGZ)) || (exit 1)))

#
# cgicc docs archived
#
cgicc-docs-archived:
	@(echo $(CGICC_DOCS_TGZ))

#
# Archive cgicc docs
#
archive-cgicc-docs:
	@(echo Archiving $(CGICC_DIR) to $(CGICC_DOCS_TGZ)...;\
	  (($(CGICC_ARCHIVE) $(CGICC_DOCS_TGZ) $(CGICC_DIR)) || (exit 1)))

########################################################################
# patch
########################################################################

#
# List cgicc patch
#
list-cgicc-patch: $(CGICC_PATCH_TGZ)
	@(echo Listing $(CGICC_PATCH_TGZ)...;\
	  (($(CGICC_LIST_PATCH_TGZ)) || (exit 1)))

#
# Extract cgicc patch
#
extract-cgicc-patch: $(CGICC_DIR)
	@(echo Extracting $(CGICC_PATCH_TGZ)...;\
	  (($(CGICC_EXTRACT_PATCH_TGZ)) || (exit 1)))

#
# cgicc patch archived
#
cgicc-patch-archived:
	@(echo $(CGICC_PATCH_TGZ))

#
# Archive cgicc patch
#
archive-cgicc-patch:
	@(echo Archiving $(CGICC_DIR) to $(CGICC_PATCH_TGZ)...;\
	  (($(CGICC_ARCHIVE) $(CGICC_PATCH_TGZ) $(CGICC_DIR)) || (exit 1)))

########################################################################
# patched
########################################################################

#
# List cgicc patched
#
list-cgicc-patched: $(CGICC_PATCHED_TGZ)
	@(echo Listing $(CGICC_PATCHED_TGZ)...;\
	  (($(CGICC_LIST_PATCHED_TGZ)) || (exit 1)))

#
# Extract cgicc patched
#
extract-cgicc-patched: $(CGICC_DIR)
	@(echo Extracting $(CGICC_PATCHED_TGZ)...;\
	  (($(CGICC_EXTRACT_PATCHED_TGZ)) || (exit 1)))

#
# cgicc patched archived
#
cgicc-patched-archived:
	@(echo $(CGICC_PATCHED_TGZ))

#
# Archive cgicc patched
#
archive-cgicc-patched:
	@(echo Archiving $(CGICC_DIR) to $(CGICC_PATCHED_TGZ)...;\
	  (($(CGICC_ARCHIVE) $(CGICC_PATCHED_TGZ) $(CGICC_DIR)) || (exit 1)))

########################################################################
# build
########################################################################

#
# List cgicc build
#
list-cgicc-build: $(CGICC_BUILD_TGZ)
	@(echo Listing $(CGICC_BUILD_TGZ)...;\
	  (($(CGICC_LIST_BUILD_TGZ)) || (exit 1)))

#
# Extract cgicc build
#
extract-cgicc-build: $(CGICC_DIR)
	@(echo Extracting $(CGICC_BUILD_TGZ)...;\
	  (($(CGICC_EXTRACT_BUILD_TGZ)) || (exit 1)))

#
# cgicc build archived
#
cgicc-build-archived:
	@(echo $(CGICC_BUILD_TGZ))

#
# Archive cgicc build
#
archive-cgicc-build:
	@(echo Archiving $(CGICC_DIR) to $(CGICC_BUILD_TGZ)...;\
	  (($(CGICC_ARCHIVE) $(CGICC_BUILD_TGZ) $(CGICC_DIR)) || (exit 1)))

########################################################################
# archive
########################################################################

#
# List cgicc
#
list-cgicc:
	@(echo Listing $(CGICC_TGZ)...;\
	  (($(CGICC_LIST_TGZ)) || (exit 1)))

#
# cgicc extracted
#
cgicc-extracted:
	@(echo $(CGICC_EXTRACT) $(CGICC_TGZ))

#
# Extract cgicc
#
extract-cgicc: unextract-cgicc $(CGICC_DIR)

unextract-cgicc: unconfig-$(CGICC_DIR)
	@(echo Removing $(CGICC_DIR)...;\
	  (($(CGICC_REMOVE_DIR)) || (exit 1)))

$(CGICC_DIR): $(CGICC_TGZ)
	@(echo Extracting $(CGICC_TGZ)...;\
	  (($(CGICC_EXTRACT_TGZ)) || (exit 1)) && \
	  (($(CGICC_TOUCH_EXTRACT)) || (exit 1)))

#
# cgicc archived
#
cgicc-archived:
	@(echo $(CGICC_TGZ))

#
# Archive cgicc
#
archive-cgicc:
	@(echo Archiving $(CGICC_DIR) to $(CGICC_TGZ)...;\
	  (($(CGICC_ARCHIVE) $(CGICC_TGZ) $(CGICC_DIR)) || (exit 1)))

########################################################################
# links
########################################################################

#
# cgicc linked
#
cgicc-linked:
	@echo link is $(CGICC_LINK_NAME) "->" $(CGICC_PREFIX)

#
# Install cgicc links
#
install-cgicc-links:
	@((echo removing $(CGICC_LINK_NAME)) && \
	  ((rm -f $(CGICC_LINK_NAME)) || (exit 1)) && \
	  (echo Linking $(CGICC_LINK_NAME) "->" $(CGICC_PREFIX)) && \
	  ((ln -s $(CGICC_PREFIX) $(CGICC_LINK_NAME)) || (exit 1)))

#
# Uninstall cgicc
#
uninstall-cgicc: 
	@((echo Removing $(CGICC_LINK_NAME)) && \
	  ((rm -f $(CGICC_LINK_NAME)) || (exit 1)) && \
	  (echo Removing $(CGICC_PREFIX)) && \
	  ((rm -rf $(CGICC_PREFIX)) || (exit 1)))
	  
########################################################################
# prefix
########################################################################

#
# cgicc prefixed
#
cgicc-prefixed:
	@((echo prefix is $(CGICC_PREFIX)) && \
	  (echo exec prefix is $(CGICC_EXEC_PREFIX)) && \
	  (echo conf prefix is $(CGICC_CONF_PREFIX)) && \
	  (echo docs prefix is $(CGICC_DOCS_PREFIX)))

#
# Install cgicc prefix
#
install-cgicc-prefix:
	@((echo makeing $(CGICC_PREFIX)) && \
	  ((mkdir -p $(CGICC_PREFIX)) || (exit 1)) && \
	  (echo makeing $(CGICC_EXEC_PREFIX)) && \
	  ((mkdir -p $(CGICC_EXEC_PREFIX)) || (exit 1)))

$(CGICC_PREFIX):
	@(echo Makeing Directory $(CGICC_PREFIX)...;\
	  (($(CGICC_MKDIR) $(CGICC_PREFIX)) || (exit 1)))

$(CGICC_EXEC_PREFIX):
	@(echo Makeing Directory $(CGICC_EXEC_PREFIX)...;\
	  (($(CGICC_MKDIR) $(CGICC_EXEC_PREFIX)) || (exit 1)))

$(CGICC_CONF_PREFIX):
	@(echo Makeing Directory $(CGICC_CONF_PREFIX)...;\
	  (($(CGICC_MKDIR) $(CGICC_CONF_PREFIX)) || (exit 1)))

$(CGICC_DOCS_PREFIX):
	@(echo Makeing Directory $(CGICC_DOCS_PREFIX)...;\
	  (($(CGICC_MKDIR) $(CGICC_DOCS_PREFIX)) || (exit 1)))


