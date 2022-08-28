CODE_DIRS=. #Add more folders
INC_DIRS=. #Add more folders
OUTPUT=prog.bin

CXX=/opt/riscv2/bin/riscv64-unknown-elf-gcc
OBJCOPY=/opt/riscv2/bin/riscv64-unknown-elf-objcopy
OBJDUMP=/opt/riscv2/bin/riscv64-unknown-elf-objdump

CFLAGS=-ffreestanding -fno-pic -march=rv32i -mabi=ilp32 -nostdlib -Ttext=0x0 -mno-relax

CFILES=$(foreach F,$(CODE_DIRS),$(wildcard $(F)/*.c))

OBJECTS=$(patsubst %.c,%.o,$(CFILES))

all: a.out
	#Generating the binary file from executable
	$(OBJCOPY) a.out -O binary prog.bin
	#Generating the disassembly
	$(OBJDUMP) -Mnumeric -Mno-aliases -dr a.out > prog.lst

a.out: $(CFILES)
	$(CXX) $(CFLAGS) $<

clean:
	rm -rf $(OUTPUT) $(OBJECTS) prog.lst a.out 

.PHONY: all clean
