all: lib_driver_cmd_rtl.a

clean:
	rm -f *~ *.o *.d lib_driver_cmd_rtl.a

install:
	@echo Nothing to be made.


WPA_SUPPL_DIR = ../../..
SRCS :=

include $(WPA_SUPPL_DIR)/wpa_supplicant/.config

CFLAGS += -DANDROID
CFLAGS += -I.
CFLAGS += -I$(WPA_SUPPL_DIR)/src
CFLAGS += -I$(WPA_SUPPL_DIR)/src/common
CFLAGS += -I$(WPA_SUPPL_DIR)/src/drivers
CFLAGS += -I$(WPA_SUPPL_DIR)/src/l2_packet
CFLAGS += -I$(WPA_SUPPL_DIR)/src/utils
CFLAGS += -I$(WPA_SUPPL_DIR)/src/wps
CFLAGS += -I$(WPA_SUPPL_DIR)/wpa_supplicant

ifdef CONFIG_DRIVER_NL80211
OBJS += driver_cmd_nl80211.o
endif

ifdef CONFIG_DRIVER_WEXT
OBJS += driver_cmd_wext.c
endif

objs:
	$(CC) $(CFLAGS) -o $(SRCS)

lib_driver_cmd_rtl.a: $(OBJS)
	$(AR) crT $@ $?

#-include $(OBJS:%.o=%.d)
