#
# mruby/c  sample_c/Makefile
#
# Copyright (C) 2015-2019 Kyushu Institute of Technology.
# Copyright (C) 2015-2019 Shimane IT Open-Innovation Center.
#
#  This file is distributed under BSD 3-Clause License.
#

CC = rx-elf-gcc
AS = rx-elf-as
LD = rx-elf-ld
TARGETS = mrubyc.mot
CFLAGS += -g -I ../../src -T linker_script.ld -nostartfiles -O0 -ffunction-sections -fdata-sections -g2 -Wstack-usage=100 -mcpu=rx230 -misa=v2 -mlittle-endian-data -std=gnu99 -D MRBC_NO_TIMER -Wall
LDFLAGS +=
LIBMRUBYC = ../../src/libmrubyc.a

all: $(TARGETS)

mrubyc.mot : mrubyc.elf
	rx-elf-objcopy -O srec -I elf32-rx-be-ns mrubyc.elf $@

mrubyc.elf: main.c $(LIBMRUBYC) linker_script.ld	makefile
	$(CC) $(CFLAGS) $(LDFLAGS) -o $@ ../sample01.c main.c reset_program.S $(LIBMRUBYC)

clean:
	@rm -rf $(TARGETS) *.o *.elf *.mot *.dSYM *~
