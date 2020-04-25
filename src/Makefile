#
# mruby/c  src/Makefile
#
# Copyright (C) 2015-2019 Kyushu Institute of Technology.
# Copyright (C) 2015-2019 Shimane IT Open-Innovation Center.
#
#  This file is distributed under BSD 3-Clause License.
#

CC = rx-elf-gcc
AR = rx-elf-ar
AS = rx-elf-as

# for RX130
# CFLAGS += -O0 -ffunction-sections -fdata-sections -g2 -Wstack-usage=100 -mcpu=rx100 -misa=v1 -mlittle-endian-data -std=gnu99 -D MRBC_NO_TIMER -Wall -Wpointer-arith -g # -std=c99 -pedantic -pedantic-errors
# for RX231
# CFLAGS += -O0 -ffunction-sections -fdata-sections -g2 -Wstack-usage=100 -mcpu=rx230 -misa=v2 -mlittle-endian-data -std=gnu99 -D MRBC_NO_TIMER -Wall -Wpointer-arith -g # -std=c99 -pedantic -pedantic-errors
# for RX65N
# CFLAGS += -O0 -ffunction-sections -fdata-sections -g2 -Wstack-usage=100 -mcpu=rx64m -misa=v2 -mlittle-endian-data -std=gnu99 -D MRBC_NO_TIMER -Wall -Wpointer-arith -g # -std=c99 -pedantic -pedantic-errors

COMMON_SRCS = alloc.c class.c console.c error.c global.c keyvalue.c load.c rrt0.c static.c symbol.c value.c vm.c hal/clock.c hal/delay.c hal/register_protect.c hal/vector.c
RUBY_LIB_SRCS = c_array.c c_hash.c c_numeric.c c_math.c c_range.c c_string.c mrblib.c

TARGET = libmrubyc.a
OBJS = $(COMMON_SRCS:.c=.o) $(RUBY_LIB_SRCS:.c=.o)


all:
	$(MAKE) $(TARGET)

$(TARGET): $(OBJS)
	$(AR) $(ARFLAGS) $@ $?

clock.o: hal/clock.c hal/clock.h hal/hal.h

delay.o: hal/delay.c hal/delay.h hal/hal.h

register_protect.o: hal/register_protect.c hal/register_protect.h hal/hal.h

vector.o: hal/vector.c hal/vector.h hal/hal.h

vm.o: vm.c vm_config.h vm.h value.h class.h alloc.h load.h static.h \
  global.h opcode.h symbol.h console.h hal/hal.h c_string.h c_range.h \
  c_array.h c_hash.h

value.o: value.c vm_config.h value.h vm.h class.h alloc.h c_string.h \
  c_range.h c_array.h c_hash.h

alloc.o: alloc.c vm_config.h vm.h value.h class.h alloc.h console.h \
  hal/hal.h

keyvalue.o: keyvalue.c vm_config.h value.h alloc.h keyvalue.h

static.o: static.c vm_config.h static.h class.h value.h global.h

global.o: global.c vm_config.h value.h static.h class.h global.h mrubyc.h \
  vm.h alloc.h symbol.h c_array.h c_hash.h c_numeric.h \
  c_range.h c_string.h load.h console.h hal/hal.h rrt0.h

class.o: class.c vm_config.h value.h alloc.h class.h vm.h keyvalue.h \
  static.h symbol.h global.h console.h hal/hal.h opcode.h load.h error.h \
  c_array.h c_hash.h c_numeric.h c_math.h c_string.h c_range.h

error.o: error.c vm_config.h value.h vm.h static.h

symbol.o: symbol.c vm_config.h value.h vm.h class.h alloc.h static.h \
  symbol.h c_string.h c_array.h console.h hal/hal.h

load.o: load.c vm_config.h vm.h value.h class.h load.h alloc.h

console.o: console.c vm_config.h value.h console.h hal/hal.h

c_array.o: c_array.c vm_config.h value.h vm.h class.h alloc.h static.h \
  c_array.h c_string.h console.h hal/hal.h opcode.h

c_numeric.o: c_numeric.c vm_config.h opcode.h value.h static.h class.h \
  console.h hal/hal.h c_numeric.h vm.h c_string.h

c_math.o: c_math.c vm_config.h value.h static.h class.h

c_string.o: c_string.c vm_config.h value.h vm.h class.h alloc.h static.h \
  symbol.h c_array.h c_string.h console.h hal/hal.h

c_range.o: c_range.c vm_config.h value.h alloc.h static.h class.h \
  c_range.h c_string.h console.h hal/hal.h opcode.h

c_hash.o: c_hash.c vm_config.h value.h vm.h class.h alloc.h static.h \
  c_array.h c_hash.h c_string.h

rrt0.o: rrt0.c vm_config.h alloc.h static.h class.h value.h load.h vm.h \
  console.h hal/hal.h rrt0.h

clean:
	@rm -Rf $(TARGET) *.o hal/*.o *~
