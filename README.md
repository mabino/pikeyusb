# pikeyusb

1. Print the IP address during startup.
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

