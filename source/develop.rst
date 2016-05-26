.. index:: development

.. _develop:

Developing guide
----------------

This guide will provide instructions to install the development environment needed to compile and debug the demo firmware of the PMOD-Lora. The development system is built for Windows.
The main steps are:

- Install Codewarrior Special Edition Software

- Import build & debug the source project

Hardware required:

- PMOD-Lora

- RSR1066 board

- FRDM-KL26Z board by Freescale

- Mini-USB cable

- PC with Windows

Install Codewarriror
********************

Special Editions are fully functional free download versions of the CodeWarrior Development Studio with code size restrictions on the build chain. Special Editions are pre-licensed, not bound to a single machine and are not time restricted. You do not need to register the tools or ask for a license.

Download the IDE from `this page <http://www.freescale.com/tools/software-and-tools/software-development-tools/codewarrior-development-tools/downloads/special-edition-software:CW_SPECIALEDITIONS>`_, we used Codewarriror for Microcontrollers **v10.6.4**.

Next, launch the downloaded file **CW_MCU_v10.6.4_Special_Edition.exe** following all the default options and selecting **Kinetis** as platform. Once it is installed will be created its icon on the desktop.

.. image:: _static/codewarrior_icon.jpg

Prepare the Hardware
********************

Here you will see all the messages sent by your device. Now take the FRDM-KL26Z board and connect it to the RSR1066 board. It is required mount the strip connectors:

.. image:: _static/strips.jpg
.. image:: _static/rsr1066.jpg

Connect the PMOD module to the CN7 then power supply the FRDM board via mini USB connection.

.. image:: _static/power_on.jpg

Configure the FRDM-KL26Z with OpenSDA interface
***********************************************

1. In order to install the lastest firmware go to the webpage `OpenSDA Support <http://www.pemicro.com/opensda/>`_. 

2. Download and install **Windows USB Drivers Download PEDrivers_install.exe** from `pemicro website <http://www.pemicro.com/downloads/download_file.cfm?download_id=301>`_. It is required to register in the website.

3. Then download the lastest `Firmware Apps (.zip file) <http://www.pemicro.com/downloads/download_file.cfm?download_id=378>`_.

4. Finally connect the FRDM-KL26Z board to the PC via mini-USB connector **OpenSDA**, remove the 1066 board and set the board in Bootloader mode (hold the Reset button down while connecting to USB, then release it). Your board will then be visible as a drive labelled **BOOTLOADER**. From the **Firmware Apps** zip copy into the BOOTLOADER disk the file **DEBUG_OpenSDA_for_MBED_Bootloader_by_Pemicro_v1XX.bin** (where XX is the lastest version). Now unplag the USB cable.

Import Project
**************

1. Create a folder named "workspace"

2. Take the zip project file and unzip it into the folder.

3. Launch Codewarrior and select a folder for the workspace. Our project will be imported in this directory. In this guide we used this path:

.. image:: _static/codewarrior_workspace.jpg

4. Go to **File -> Import...**

5. Select **General -> Existing Projects into Workspace** and click on **Next >** button.

.. image:: _static/codewarrior_import_project.jpg

6. Select the folder where is locate the project **lib_lora** and select **FRDM-KL26Z-UART**. Then click on **Finish**.

.. image:: _static/codewarrior_import_lora_project.jpg

Build & Debug
*************

If you want download the firmware in the board without debugging it go to step 5.
In order to debug the code you have to change the UART port because **PTA1** and **PTA2** are used for debug purpose from the OpenSDA.

1. Now you have to open **Process Expert Window** double clicking on **ProcessorExpert.pe**

.. image:: _static/codewarrior_processor_expert_icon_lora.jpg

2. In **Components - FRDM-KL26Z-UART** tab select **AS2:Serial_LDD** node

.. image:: _static/codewarrior_as2serial_ldd.jpg

3. In **Component Inspector - A2** select RxD **PTD6** and TxD **PTD7**

.. image:: _static/codewarrior_ptd6_ptd7.jpg

4. In order to debug you have to connect **PTD6** with **CN7 pin3** and **PTD7** with **CN7 pin2** as in figure. These pin must be disconnected from the board **1066**.

.. image:: _static/codewarrior_debug_connection.jpg

5. Now it's time to compile the sources code, go to **Project -> Build All**

6. Once compiling is finished connect the mini usb from the PC to the FRDM board. Then go to **Run -> Debug configurations...**

7. Finally select FRDM-KL26Z-UART_FLASH_OpenSDA and choose the type of connection **OpenSDA** than click on the **Debug** button.

.. image:: _static/codewarrior_debug_configuration.jpg

Processor Expert
****************
Processor Expert Software is a development system to create, configure, optimize, migrate, and deliver software components that generate source code for the microcontroller. For more information please go `here <http://www.nxp.com/products/software-and-tools/software-development-tools/processor-expert-and-embedded-components:BEAN_STORE_MAIN>`_,

