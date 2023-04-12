TOP=../..

include $(TOP)/configure/CONFIG

LIBRARY_IOC_Linux += ADAravis

USR_CXXFLAGS_Linux += -std=c++11

# The following are compiled and added to the support library
ADAravis_SRCS += arvFeature.cpp
ADAravis_SRCS += ADAravis.cpp

DBD += ADAravisSupport.dbd

# Set aravis include and lib paths
ifneq ($(ARAVISPREFIX),)
	USR_INCLUDES += -I$(ARAVISPREFIX)/include/aravis-0.8
    ifneq (,$(wildcard $(ARAVISPREFIX)/lib64/libaravis-0.8*))
	# If these is a glibprefix/lib64/aravis-0.8 dir then use this	    
	aravis-0.8_DIR = $(ARAVISPREFIX)/lib64
    else
        # Assume it is in the lib directory
	aravis-0.8_DIR = $(ARAVISPREFIX)/lib
	endif
	LIB_INSTALLS += $(wildcard $(aravis-0.8_DIR)/lib*)
	BIN_INSTALLS += $(wildcard $(ARAVISPREFIX)/bin/*)
endif

# If glib is not in a standard place, tell the build system where to look
ifneq ($(GLIBPREFIX),)
	USR_INCLUDES += -I$(GLIBPREFIX)/include/glib-2.0
    ifneq (,$(wildcard $(GLIBPREFIX)/lib64/glib-2.0))
	# If these is a glibprefix/lib64/glib-2.0 dir then use this	    
	USR_INCLUDES += -I$(GLIBPREFIX)/lib64/glib-2.0/include
	glib-2.0_DIR = $(GLIBPREFIX)/lib64
    else
        # Assume it is in the lib directory
		USR_INCLUDES += -I$(GLIBPREFIX)/lib/glib-2.0/include		
		glib-2.0_DIR = $(GLIBPREFIX)/lib
	endif
	USR_INCLUDES += -I$(GLIBPREFIX)/include
	LIB_INSTALLS += $(wildcard $(glib-2.0_DIR)/lib*)
endif

LIB_LIBS += ADGenICam

USR_LIBS     += aravis-0.8

LIB_SYS_LIBS += gio-2.0 gobject-2.0 gthread-2.0 glib-2.0
LIB_SYS_LIBS += usb-1.0

include $(TOP)/configure/RULES
