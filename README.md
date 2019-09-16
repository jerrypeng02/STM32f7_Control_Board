## STM32F7_Control_Board

## Purpose:
In Sensor Systems Lab, there is a PR2 robot that has the internal cable connecting proximity sensors to the computer for trasmitting data. However, we want an application that can employ this feature on other robots. So for this application, it does not require the robot to have the internal cable. It can transfer the data from registers in proximity sensors to the Wi-Fi hub and send the data back to a computer wirelessly.

---

## Requirement:

System: Windows 7 or higher

Hardware: STM32F411E Discovery board

Software: STM32CubeMX, Keil uVision IDE with MDK-ARM toolchain

---

## Hardware construction:

The hardware has three parts: I2C to connectors, microcontroller, and the USB
I2C: the I2C circuits are for connecting the proximity sensors. (The connectors are FFC & FPC connectors)
Microcontroller: STM32F723 microcontroller, which has embedded PHY chip for the USB 2.0
USB: the USB circuits consist of suggested ESD protection (Check details from datasheet of ECMF02-2AMX6)
The rest of the components are mostly capacitors and resistors. Resistors are for LEDs and as pull-up resistors. Capacitors are as simple low pass filters for filtering high frequency noise signals for pairs of VDD and VSS on microcontroller.

---

## Configuration:

**Pre-connection:**
Disconnect the 2 jumpers from CN3 on STM32F411 Discovery board for programming/debugging external STM32 application and connect CN2 debug connector to the connector on the control board (Check details on the datasheet from STM32F411 discovery board)

Use the STM32CubeMX to configure the following setting of the microcontroller:

**Peripherals:**

I2C: I2C1

RCC: High Speed Clock (HSE) -> Crystal/Ceramic Resonator

SYS: Debug -> Serial Wire

USB_STG_HS: Internal Phy -> Device_Only, Active_VBUS checkbox

**MiddleWares:**

USB_DEVICE: Classs for HS IP -> Communication Device Class (Virtual Port Com)

**On_board:**

Configure PE2 as GPIO_Output

---

## Code:


---

## Testing:


---

**Edit a file, create a new file, and clone from Bitbucket in under 2 minutes**

When you're done, you can delete the content in this README and update the file with details for others getting started with your repository.

*We recommend that you open this README in another tab as you perform the tasks below. You can [watch our video](https://youtu.be/0ocf7u76WSo) for a full demo of all the steps in this tutorial. Open the video in a new tab to avoid leaving Bitbucket.*

---

## Edit a file

You’ll start by editing this README file to learn how to edit a file in Bitbucket.

1. Click **Source** on the left side.
2. Click the README.md link from the list of files.
3. Click the **Edit** button.
4. Delete the following text: *Delete this line to make a change to the README from Bitbucket.*
5. After making your change, click **Commit** and then **Commit** again in the dialog. The commit page will open and you’ll see the change you just made.
6. Go back to the **Source** page.

---

## Create a file

Next, you’ll add a new file to this repository.

1. Click the **New file** button at the top of the **Source** page.
2. Give the file a filename of **contributors.txt**.
3. Enter your name in the empty file space.
4. Click **Commit** and then **Commit** again in the dialog.
5. Go back to the **Source** page.

Before you move on, go ahead and explore the repository. You've already seen the **Source** page, but check out the **Commits**, **Branches**, and **Settings** pages.

---

## Clone a repository

Use these steps to clone from SourceTree, our client for using the repository command-line free. Cloning allows you to work on your files locally. If you don't yet have SourceTree, [download and install first](https://www.sourcetreeapp.com/). If you prefer to clone from the command line, see [Clone a repository](https://confluence.atlassian.com/x/4whODQ).

1. You’ll see the clone button under the **Source** heading. Click that button.
2. Now click **Check out in SourceTree**. You may need to create a SourceTree account or log in.
3. When you see the **Clone New** dialog in SourceTree, update the destination path and name if you’d like to and then click **Clone**.
4. Open the directory you just created to see your repository’s files.

Now that you're more familiar with your Bitbucket repository, go ahead and add a new file locally. You can [push your change back to Bitbucket with SourceTree](https://confluence.atlassian.com/x/iqyBMg), or you can [add, commit,](https://confluence.atlassian.com/x/8QhODQ) and [push from the command line](https://confluence.atlassian.com/x/NQ0zDQ).