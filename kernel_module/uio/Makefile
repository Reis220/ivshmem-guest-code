# obj-m is a list of what kernel modules to build.  The .o and other
# objects will be automatically built from the corresponding .c file -
# no need to list the source files explicitly.
export ARCH := arm64
export CROSS_COMPILE := aarch64-linux-gnu-
obj-m := uio_ivshmem.o 

$(info current arch=$(ARCH))
$(info current cc=$(CROSS_COMPILE))

BASE_DIR := /home/joao/Desktop/PetaLinux2018_2

# KDIR is the location of the kernel source.  The current standard is
# to link to the associated source tree from the directory containing
# the compiled modules.
#KDIR  := /lib/modules/$(shell uname -r)/build
KDIR  := $(BASE_DIR)/petalinux_project/build/tmp/work/ultra96_zynqmp-xilinx-linux/linux-xlnx/4.14-xilinx-v2018.2+gitAUTOINC+ad4cd988ba-r0/linux-ultra96_zynqmp-standard-build

$(info current KDIR=$(KDIR))

# PWD is the current working directory and the location of our module
# source files.
PWD   := $(shell pwd)

# default is the default make target.  The rule here says to run make
# with a working directory of the directory containing the kernel
# source and compile only the modules in the PWD (local) directory.
default:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

install:
	cp uio_ivshmem.ko /lib/modules/4.14-xilinx-v2018.2/kernel/drivers/uio/

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean
	#rm -f *.ko *.o uio_ivshmem.mod.c Module.symvers
