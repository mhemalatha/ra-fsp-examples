/***********************************************************************************************************************
* Copyright [2020] Renesas Electronics Corporation and/or its affiliates.  All Rights Reserved.
*
* This software is supplied by Renesas Electronics America Inc. and may only be used with products of Renesas Electronics Corp.
* and its affiliates (“Renesas”).  No other uses are authorized.  This software is protected under all applicable laws, 
* including copyright laws.
* Renesas reserves the right to change or discontinue this software.
* THE SOFTWARE IS DELIVERED TO YOU “AS IS,” AND RENESAS MAKES NO REPRESENTATIONS OR WARRANTIES, AND TO THE FULLEST EXTENT 
* PERMISSIBLE UNDER APPLICABLE LAW,DISCLAIMS ALL WARRANTIES, WHETHER EXPLICITLY OR IMPLICITLY, INCLUDING WARRANTIES OF 
* MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT, WITH RESPECT TO THE SOFTWARE.  TO THE MAXIMUM 
* EXTENT PERMITTED BY LAW, IN NO EVENT WILL RENESAS BE LIABLE TO YOU IN CONNECTION WITH THE SOFTWARE (OR ANY PERSON 
* OR ENTITY CLAIMING RIGHTS DERIVED FROM YOU) FOR ANY LOSS, DAMAGES, OR CLAIMS WHATSOEVER, INCLUDING, WITHOUT LIMITATION, 
* ANY DIRECT, CONSEQUENTIAL, SPECIAL, INDIRECT, PUNITIVE, OR INCIDENTAL DAMAGES;
* ANY LOST PROFITS, OTHER ECONOMIC DAMAGE, PROPERTY DAMAGE, OR PERSONAL INJURY; AND EVEN IF RENESAS HAS BEEN ADVISED OF 
* THE POSSIBILITY OF SUCH LOSS,DAMAGES, CLAIMS OR COSTS.
* **********************************************************************************************************************/

1. Project Overview:
    This Example Project demonstrates SCI_I2C Master operation through loop-back with IIC Slave driver.
    6 bytes of data will be transmitted and received continuously on successful initialization. 
    The transmitted data is compared with the received data. If the data matches, on-board LED
    starts blinking. On a data mismatch, LED stays ON.
    Failure messages and status is displayed on RTTViewer.

    LED output Status on Master TX and RX data mismatch(failure) and data match(success)
    a) Failure  - Led is set as ON
    b) Success  - Led blinks for each transaction

2. Hardware Settings:
    Two jumper wires are required to establish loop back connection along IIC lines within the board with pins as mentioned below.

    RA6M3_EK & RA6M3G_EK
    --------
    Channel 0 has been used by SCI_I2C Master and IIC Slave.
    1) SCI_I2C Master pins
        SCI0 P411 (Jumper J3 Pin 36) ----> SDA
        SCI0 P410 (Jumper J3 Pin 35) ----> SCL
    2) Slave IIC pins
        IIC0 P401 (Jumper J3 Pin 09) ----> SDA
        IIC0 P408 (Jumper J3 Pin 37) ----> SCL

    RA6M2_EK
    --------
    Channel 0 has been used by SCI_I2C Master and IIC Slave.
    1) SCI_I2C Master pins
        SCI0 P411 (Jumper J2 Pin 20) ----> SDA
        SCI0 P410 (Jumper J2 Pin 02) ----> SCL
    2) Slave IIC pins
        IIC0 P401 (Jumper J4 Pin 11) ----> SDA
        IIC0 P400 (Jumper J4 Pin 13) ----> SCL

    RA6M1_EK
    --------
    Channel 0 has been used by SCI_I2C Master and IIC Slave.
    1) SCI_I2C Master pins
        SCI0 P411 (Jumper J2 Pin 20) ----> SDA
        SCI0 P410 (Jumper J4 Pin 14) ----> SCL
    2) Slave IIC pins
        IIC0 P401 (Jumper J1 Pin 03) ----> SDA
        IIC0 P400 (Jumper J1 Pin 01) ----> SCL

    RA4W1_EK
    --------
    Channel 0 has been used by SCI_I2C Master and IIC Slave.
    1) SCI_I2C Master pins
        SCI0 P101 (Header CN7 pin 26) ----> SDA
        SCI0 P100 (Header CN7 pin 27) ----> SCL
    2) Slave IIC pins
        IIC0 P407 (Header CN7 Pin 01) ----> SDA
        IIC0 P204 (Header CN7 Pin 09) ----> SCL

    RA4M1_EK
    --------
    Channel 0 has been used by SCI_I2C Master and IIC Slave.
    1) SCI_I2C Master pins
        SCI0 P411 (Jumper J2 Pin 04) ----> SDA
        SCI0 P410 (Jumper J2 Pin 02) ----> SCL
    2) Slave IIC pins
        IIC0 P401 (Jumper J2 Pin 08) ----> SDA
        IIC0 P400 (Jumper J2 Pin 37) ----> SCL

    RA2A1_EK
    --------
    Channel 0 has been used by SCI_I2C Master and IIC Slave.
    1) SCI_I2C Master pins
        SCI0 P302 (Jumper J2 Pin 04) ----> SDA
        SCI0 P301 (Jumper J2 pin 02) ----> SCL
    2) Slave IIC pins
        IIC0 P401 (Jumper J1 Pin 03) ----> SDA
        IIC0 P000 (Jumper J1 Pin 01) ----> SCL

Note:
* For the functioning of SCI_I2C Master and IIC Slave on all the boards except for EK-RA6M3/EK-RA6M3G, external pull up
  resistors of value 3.9 or 4.7k ohms are required to be connected on I2C(SDA/SCL) lines.
