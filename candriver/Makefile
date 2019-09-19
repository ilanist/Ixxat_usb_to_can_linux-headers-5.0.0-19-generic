all: ixx_usb

ixx_usb:
	$(MAKE) -C /lib/modules/$(shell uname -r)/build M=$(PWD)/usb-to-can_socketcan modules

clean:
	$(MAKE) -C can-ibxxx_socketcan clean
	$(MAKE) -C usb-to-can_socketcan clean

install: install_usb

install_usb:
	mkdir -p /lib/modules/$(shell uname -r)/kernel/drivers/net/can/usb/ixxat/
	install usb-to-can_socketcan/ixx_usb.ko /lib/modules/$(shell uname -r)/kernel/drivers/net/can/usb/ixxat/
	depmod -a
	modprobe ixx_usb

uninstall:
	rm -f /lib/modules/$(shell uname -r)/kernel/drivers/net/can/usb/ixxat/ixx_usb.ko
	modprobe -r ixx_usb
	depmod -a
	rm -f /lib/firmware/ixx-can-ib-1.9.3.fw
