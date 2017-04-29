# S.Port Firmware Flashing

## File Preparation

- Download the firmware

  ![](images/sport-flash-001-download-firmware.png)
  
- Place the firmware on the SDCARD in the FIRMWARE folder
  
  ![](images/sport-flash-104-sd-hc-firmware.bmp)

- Ensure that the file name is 33 characters or less including the dot and extension

  ![](images/sport-flash-106-sd-hc-firmware-file-selected.bmp)
  
## Hardware Preparation

### All transmitters except for Taranis Q X7 shipped with bottom S.Port pins

- The external module bay’s +ve pin has the same voltage as the transmitter’s battery

  Check that the device being flashed is rated for the transmitter’s battery voltage

  If it is not then either change the battery or add a BEC in between the module bay’s  and device’s power pins

- Use a servo cable with the positive and negative wires swapped at one end

  ![](images/sport-flash-002-modified-servo-cable-small.jpg)

- Plug the modified servo cable on to the external module bay pins with the signal wire on the pin in the corner

  ![](images/sport-flash-003-ext-bay-small.jpg)

- Plug the other end of the modified servo cable onto the S.Port pins of the device to be flashed

  ![](images/sport-flash-004-gps-small.jpg)

### Taranis Q X7 shipped with bottom S.Port pins

- Use a regular servo cable

- Plug one end into the bottom S.Port

- Plug the other end onto the S.Port pins of the device to be flashed

### Taranis Q X7 bottom S.Port pins added

- Will not work

## Flashing Steps

- From the main view

  ![](images/sport-flash-101-main-view.bmp)
  
- Long press MENU

  ![](images/sport-flash-102-radio-setup.bmp)
  
- Press PAGE to get to the SD-HC CARD screen

  ![](images/sport-flash-103-sd-hc-card.bmp)
  
- Scroll down to the FIRMWARE directory

  ![](images/sport-flash-104-sd-hc-firmware.bmp)
  
- Press ENT to enter the directory

  ![](images/sport-flash-105-sd-hc-firmware-files.bmp)
  
- Scroll down to the firmware file

  ![](images/sport-flash-106-sd-hc-firmware-file-selected.bmp)

- Long press ENT to display the pop up menu

- Select Flash ext. device

  ![](images/sport-flash-107-flash-ext.bmp)
  
- Press ENT
  
- Wait for the progress bar screen to be displayed, it could take a few seconds

  ![](images/sport-flash-108-writing.png)
  
- When done the SD-HC CARD screen is displayed again

## FW Update Errors

- Not responding
  
  Check the connections
  
  Try a different device and corresponding firmware

  ![](images/sport-flash-109-no-response.bmp)
  
- Module refused data

  Check connections

  Try a different device and corresponding firmware
  
  ![](images/sport-flash-110-module-refused-data.bmp)
  
