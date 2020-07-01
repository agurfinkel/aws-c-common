# Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0.

###########
# Max needs to be big enough to have multiple loop unrollings to have full coverage
# 160 is well larger than that, and still completes quite fast: ~ 40s
MAX = 160
DEFINES += -DMAX=$(MAX)
UNWINDSET += memset_impl.0:$(shell echo $$(($(MAX) + 1)))
UNWINDSET += memset_using_uint64_impl.0:$(shell echo $$(( $$(( $(MAX) / 8 )) + 1)))

CBMCFLAGS +=

HARNESS_ENTRY = memset_using_uint64_harness
HARNESS_FILE = $(HARNESS_ENTRY).c

PROOF_SOURCES += $(HARNESS_FILE)
PROOF_SOURCES += $(PROOF_SOURCE)/utils.c

PROOF_SOURCES += $(PROOF_STUB)/memset_override.c
PROOF_SOURCES += $(PROOF_STUB)/memset_using_uint64.c

###########

include ../Makefile.common