CROSS=riscv32-unknown-elf-
CFLAGS := -mabi=ilp32 \
          -march=rv32im \
          -Wl,-Bstatic,-T,retrosoc_sections.lds,--strip-debug \
          -ffreestanding \
          -nostdlib

FIRMWARE_NAME := retrosoc_fw

SRC_PATH := ./start.s \
            ./tinyuart.c \
            ./tinystring.c \
            ./tinyprintf.c \
            ./tinyflash.c \
            ./tinygpio.c \
            ./tinyhkspi.c \
            ./tinytim.c \
            ./tinyarchinfo.c \
            ./tinyrng.c \
            ./tinyhpuart.c \
            ./tinypwm.c \
            ./tinyps2.c \
            ./tinyi2c.c \
            ./tinylcd.c \
            ./tinypsram.c \
            ./tinybench.c \
            ./tinysh.c \
            ./firmware.c

LDS_PATH := ./sections.lds


$(FIRMWARE_NAME).elf:
	$(CROSS)cpp -P -o retrosoc_sections.lds $(LDS_PATH)
	$(CROSS)gcc $(CFLAGS) -I./ -o $@ $(SRC_PATH)
	$(CROSS)objcopy -O verilog $@ $(FIRMWARE_NAME).hex
	sed -i 's/@30000000/@00000000/g' retrosoc_fw.hex
	$(CROSS)objcopy -O binary  $@ $(FIRMWARE_NAME).bin
	$(CROSS)objdump -d $@ > $(FIRMWARE_NAME).txt

clean:
	rm -f *.elf *.hex *.bin

.PHONY: $(FIRMWARE_NAME).elf clean
