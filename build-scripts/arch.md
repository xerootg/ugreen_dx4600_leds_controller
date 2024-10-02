## prereqs
```bash
yay -Suy dkms
```

# build the kernel module
```bash
sudo mkdir  /usr/src/ugreen-dx4600-leds-0.1/
sudo cp ./kmod/* /usr/src/ugreen-dx4600-leds-0.1/
sudo dkms add ugreen-dx4600-leds/0.1
sudo dkms build ugreen-dx4600-leds/0.1
sudo dkms install ugreen-dx4600-leds/0.1
sudo modprobe led_ugreen
```

# build cli
```bash
cd cli
make
```

# check everything:
```bash
sudo modprobe i2c-dev
sudo ./ugreen_leds_cli -status 0
```

if there's no errors (and possibly no output) then all went well
