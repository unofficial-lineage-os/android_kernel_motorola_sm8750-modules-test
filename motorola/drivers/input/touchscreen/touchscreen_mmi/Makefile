all: modules

modules:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) modules $(KBUILD_OPTIONS)

modules_install:
	$(MAKE) INSTALL_MOD_STRIP=1 -C $(KERNEL_SRC) M=$(M) modules_install

%:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $@ $(KBUILD_OPTIONS)

KBUILD_EXTRA_SYMBOLS += $(M)/../../../sensors/Module.symvers
KBUILD_EXTRA_SYMBOLS += $(M)/../../../mmi_relay/Module.symvers
ifneq ($(filter m y, $(CONFIG_DRM_DYNAMIC_REFRESH_RATE)),)
# leap: LineageOS kernel.mk builds external modules with O=$(KERNEL_OUT); display-drivers' objects sit next to this
# module's under sm8750-modules/ (5 levels up). Motorola's own layout (vendor/...) is kept as the fallback.
LEAP_DISP_SYMVERS := $(M)/../../../../../qcom/opensource/display-drivers/msm/Module.symvers
ifneq ($(wildcard $(LEAP_DISP_SYMVERS)),)
KBUILD_EXTRA_SYMBOLS += $(LEAP_DISP_SYMVERS)
else
KBUILD_EXTRA_SYMBOLS += $(OUT_DIR)/../../vendor/qcom/opensource/display-drivers/msm/Module.symvers
endif
endif
