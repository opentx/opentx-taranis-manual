# microSD Card

Check the Tx documentation from the manufacturer to determine which microSD card to use. To use the microSD card insert it into the card slot.
- Format: FAT12/16/32

## Version Warning

![](companion/sdcard/versionWarning.png)

If a microSD Card is present when the Tx is turned on OpenTX check its root/top level folder for a file to determine if the correct sound pack version is being used.
- opentx.sdcard.version

  ![](companion/sdcard/versionFile.png)

If the incorrect version is being used then it is possible that some announcements such as telemetry units will be incorrect and other file such as lua scripts are outdated.

## SD Card contents

A sound pack is available from within Companion.
- File > Download

  ![](companion/sdcard/companionFileDownload.png)
  
- Click on Download SD contents

  ![](companion/sdcard/dowbloadSDcontents.png)
  
- The zip file available for download depends on the Companion radio profile being used. 
- Click on the zip file link to download the microSD card contents

  ![](companion/sdcard/sdZipFileLink.png)
  
- Extract the ZIP file to the root/top level folder of the microSD Card. 

  ![](companion/sdcardsdUnzippedContents.png)

 ![](companion/sdcard/soundsDirectory01.png)
 ![](companion/sdcard/soundsDirectory02.png)
