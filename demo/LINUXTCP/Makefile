PROGRAM_NAME := linuxtcp

DEMO_SRCS := demo.c
DEMO_OBJS := ${DEMO_SRCS:.c=.c}

PORT_SRCS := $(wildcard port/*.c)
PORT_OBJS := ${PORT_SRCS:.c=.c}

COMMON_SOURCES := $(wildcard ../../modbus/*.c)
COMMON_SOURCES += $(wildcard ../../modbus/ascii/*.c)
COMMON_SOURCES += $(wildcard ../../modbus/functions/*.c)
COMMON_SOURCES += $(wildcard ../../modbus/rtu/*.c)
COMMON_SOURCES += $(wildcard ../../modbus/tcp/*.c)
COMMON_OBJS := ${COMMON_SOURCES:.c=.c}

MB_INCLUDE_DIRS := . \
	./port \
	../../modbus/rtu \
	../../modbus/ascii \
	../../modbus/include \
	../../modbus/tcp
MB_LIBRARY_DIRS :=
MB_LIBRARIES := pthread

CPPFLAGS += $(foreach includedir, $(MB_INCLUDE_DIRS),-I$(includedir))
LDFLAGS +=  $(foreach librarydir, $(MB_LIBRARY_DIRS),-L$(librarydir))
LDFLAGS +=  $(foreach library, $(MB_LIBRARIES),-l$(library))


.PHONY: all clean distclean

all: $(PROGRAM_NAME)

$(PROGRAM_NAME): $(DEMO_OBJS) $(PORT_OBJS) $(COMMON_OBJS)
	$(CC) -g -Wall $(DEMO_OBJS) $(PORT_OBJS) $(COMMON_OBJS) $(CPPFLAGS) $(LDFLAGS) -o $(PROGRAM_NAME)

clean:
	@- $(RM) $(PROGRAM_NAME)

distclean: clean
