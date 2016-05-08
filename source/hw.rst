.. index:: hardware

.. _hardware:

Hardware Guide
--------------

The board is provided with:

- NXP FRDM-KL26Z Board
- Microchip RN2483 Module
- RSR1066 board

The Microchip RN2483 module provides LoRaWAN™ protocol connectivity using a simple UART interface. The NXP **MKLS26Z** is connected to the Microchip module using the configuration 57600 8N1 without using RTS, CTS lines.

Configuration RN2483
********************

The connection used by **RN2483** is **ABP** (Activation by Personalization). To use this connection it is required to setup the RN device only one time. Every Lora Sensor Node bought is already configured. The commands used were:

 | sys factoryRESET
 | sys get hweui
 | mac set deveui [hweui key read]
 | mac set devaddr [last less significant hexs of hweui key]
 | mac set appskey AFBECD56473829100192837465FAEBDC
 | mac set nwkskey [hweui key repeated two times]
 | mac save

After saving this setup is not required repeat the opeation of setup. In order to send data in the Lora network the two used commands are:

- **mac join abp**: used to join the Lora network

- **mac tx cnf 4 18AABBCC**: used to send the frame *"18AABBCC"* on the port 4

Datasheet and more
******************

Please refer to `architechboards <http://architechboards.org/>`_ website.

.. image:: _static/logo_architech.jpg

