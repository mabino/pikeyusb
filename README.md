# pikeyusb

Use a Raspberry Pi Zero W or Raspberry Pi 4 or later (devices that support the [USB On-the-Go](https://en.wikipedia.org/wiki/USB_On-The-Go) specification) to present itself as a USB keyboard, serial, ethernet, or storage device.

The guide presented here is heavily derived from a guide titled "[Composite USB Gadgets on the Raspberry Pi Zero](https://www.isticktoit.net/?p=1383)" originally posted 2/22/2016.

1. Print the IP address during startup by adding the following to `/etc/rc.local` or by creating a systemd startup script.
  ```
  _IP=$(hostname -I) || true
  if [ "$_IP" ]; then
    print "My IP address is %s\n" "$_IP"
  fi
  ```

2. Enable a [devicetree](https://en.wikipedia.org/wiki/Devicetree) [overlay](https://www.kernel.org/doc/html/latest/devicetree/index.html#devicetree-overlays).  The dwc2 module is a driver that enables the USB On-the-Go gadget support.
  ```
  echo "dtoverlay=dwc2" | sudo tee -a /boot/config.txt
  echo "dwc2" | sudo tee -a /etc/modules
  ```

3. Enable the libcomposite driver.
  ```
  sudo echo "libcomposite" | sudo tee -a /etc/modules
  ```

4. Add `/usr/bin/pikeyusb_device` to the 
