# pikeyusb

1. Enable a [devicetree](https://en.wikipedia.org/wiki/Devicetree) [overlay](https://www.kernel.org/doc/html/latest/devicetree/index.html#devicetree-overlays).  The dwc2 module is a driver that enables the USB On-the-Go gadget support.
  ```
  echo "dtoverlay=dwc2" | sudo tee -a /boot/config.txt
  echo "dwc2" | sudo tee -a /etc/modules
  ```

2. Enable the libcomposite driver.
  ```
  sudo echo "libcomposite" | sudo tee -a /etc/modules
  ```
