## prereqs
```bash
yay -Suy dkms libi2c-dev i2c-tools dmidecode 
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

# install the scripts
```bash
sudo cp scripts/ugreen-diskiomon /usr/bin/
sudo chmod +x /usr/bin/ugreen-diskiomon
sudo cp scripts/ugreen-netdevmon /usr/bin/
sudo chmod +x /usr/bin/ugreen-netdevmon
sudo cp scripts/ugreen-probe-leds /usr/bin/
sudo chmod +x /usr/bin/ugreen-probe-leds
sudo cp cli/ugreen_leds_cli /usr/bin
```
