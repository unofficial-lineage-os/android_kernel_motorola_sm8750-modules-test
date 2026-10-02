M=$(PWD)
AUDIO_ROOT=$(KERNEL_SRC)/$(M)

# leap: symbols from mm-drivers (ported from LOS oneplus copy)
KBUILD_OPTIONS += KBUILD_EXTRA_SYMBOLS=$(M)/../mm-drivers/msm_ext_display/Module.symvers
KBUILD_OPTIONS+=  AUDIO_ROOT=$(AUDIO_ROOT)
# leap: asoc/Kbuild treats an unset MODNAME as an in-kernel build and re-adds codecs/ (duplicate .ko names)
KBUILD_OPTIONS += MODNAME=audio_dlkm

all: modules

clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) clean

%:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $@ $(KBUILD_OPTIONS)

