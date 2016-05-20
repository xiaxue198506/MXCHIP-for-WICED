# WICED for MXCHIP Wireless Modules
*Supports EMW3162 and EMW3165*

*Use sales@mxchip.com to contact MXCHIP*

##Using Method
###Preparations
* Download WICED-SDK-3.5.2 in `WICED-WIFI` plate of www.broadcom.com . First you need to register to be a member of their website **with what Broadcom calls a "corporate" e-mail address, so you can't use GMail, Outlook.com or other such e-mail addresses**.
* Download all files from the current repository to your local directory.

###Using Git and Apply Patch file
* Create a git repository for WICED-SDK-3.5.2 and commit it to your local repository.
* If you use git command line, do the following 3 steps : 
* 1. Put `mxchip_for_wiced_3.5.2_patch.diff` from the directory `MXCHIP-for-WICED-master\patchs` to  WICED-SDK-3.5.2 repository.
* 2. Make sure commit all files in `WICED-SDK-3.5.2` to your local repository.
* 3. In this repository, you need run `git apply mxchip_for_wiced_3.5.2_patch.diff` with git command line. This will patch WICED SDK.
* If you use graphical git command,It's not necessary to put `MXCHIP-for-WICED-master\patchs` in repository. Do the following 2 steps.
* 1. In the repository `WICED-SDK-3.5.2`,through your graphical tool, please enter into the `Apply Patch` interface.
* 2. Add the file `mxchip_for_wiced_3.5.2_patch.diff`and start the apply patch process.
* As a result,you will find in the path `WICED-SDK-3.5.2\platforms`，there are 2 folders added which are EMW3162 and EMW3165.


###Or Replace target files manually
* Add the file `EMW3162`,`EMW3165` in patchs directory to the WICED-SDK-3.5.2 directory `WICED-SDK\platforms`.
* Replace the same files in the `WICED-SDK\tools\OpenOCD` folder with the file in the `patchs\OpenOCD` folder. 

###Then
* Enter the WICED-SDK-3.5.2 SDK directory with the command: `cd WICED-SDK-3.5.2`
* Test flashing an application to the module. In SDK directory, you need run something like `./make EMW<module no>-<app-dir>.<app-name> download run JTAG=<jtag-adapter>` to compile and flash.The followings are examples for EMW3162 and EMW3165.

For EMW3162, using stlink-v2 for flashing, using the application *scan* from the *snip* directory, you should run command like this:
`./make EMW3162-snip.scan download run JTAG=stlink-v2`

For EMW3165, using stlink-v2 for flashing, using the application *scan* from the *snip* directory, you should run command like this:
`./make EMW3165-snip.scan download run JTAG=stlink-v2`

You may need to reset modules after flashing process while using st-link-v2.

* If the above steps are successful, you should be able to see log information from debug UART and see the list of Wi-Fi hot spots around.
* From now on，you can start playing around. WICED comes with loads of sample application, so, look around, hack around and make stuff happen.
* Please contact us if you encounter any issues while getting started and running.
