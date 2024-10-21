# Creating a Switch Controller with a Raspberry Pi Pico

This guide will show you how to transform a Raspberry Pi Pico into a custom game controller compatible with the Nintendo Switch using the open-source firmware **GP2040-CE**.

## Key Benefits

- **No programming required**
- **Supports multiple consoles** (although we’ll focus on the Switch)
- **Easy configuration** through a built-in website on the Pico:
  - Backup and restore configurations
  - Customize buttons, rotary encoders (knobs), and joysticks
  - Create macros (one button triggers multiple inputs)
  - Supports various optional add-ons
- **Quick setup** — can be done in under 30 minutes


---

## BOM (+/- €15) 

* Raspberry Pi Pico (RP2040) 
  * If you want to be sure buy the official one
  * Look for the one with headers if available (especially when you want to use the breakout board)
  * Cost +/- €7
  * [Amazon.de](https://www.amazon.de/-/en/SC0915-Raspberry-Pi-Pico/dp/B09KVB8LVR/ref=pd_ybh_a_d_sccl_16/260-4953542-4044665?pd_rd_w=GlHov&content-id=amzn1.sym.ad3cb1b1-7625-484d-ab4b-854fbcbac3d9&pf_rd_p=ad3cb1b1-7625-484d-ab4b-854fbcbac3d9&pf_rd_r=QXFAX8GKT7BTAACVMCT7&pd_rd_wg=0fWLD&pd_rd_r=348e6ed1-d75b-4076-8599-72424117d2bf&pd_rd_i=B09KVB8LVR&psc=1)
* Breakout board (**Optional**)
  * Simplifies making connections with the screw terminal by eliminating the need for soldering. **Highly recommend!** 
  * Cost +/- €5
  * [Amazon.de](https://www.amazon.de/-/en/Expansion-Interface-Dual-Core-Processor-Compatible/dp/B0CPY6F9FF/ref=pd_ybh_a_d_sccl_15/260-4953542-4044665?pd_rd_w=qmCUT&content-id=amzn1.sym.ad3cb1b1-7625-484d-ab4b-854fbcbac3d9&pf_rd_p=ad3cb1b1-7625-484d-ab4b-854fbcbac3d9&pf_rd_r=JS7GRGTH5J8F42P2EXBT&pd_rd_wg=vSN8e&pd_rd_r=a6b43f20-b7ba-451c-a03f-533db4138cc3&pd_rd_i=B0CPY6F9FF&psc=1)
* Buttons 
  * In my example I use standard arcade buttons but can work with any switches e.g. micro switches you embed in your product
* Wires, terminals,...


---

## Steps Overview

### Hardware Setup: Wiring the Buttons
### Software Setup:
1. Download the GP2040-CE firmware.
2. Put the Pico into USB mode.
3. Flash the firmware.
4. Configure the device for Switch mode.
5. Test the controller.

---

## Wiring the Buttons

For this example, we’ll wire five buttons:

- **Right**
- **Left**
- **A**
- **B**
- **S2** (used to boot the Pico into configuration mode)

You can wire more buttons (e.g., Up, Down) similarly for your final design.

### Pins Overview

| Button         | Wire 1 | Wire 2 |
| -------------- | ------ | ------ |
| Right          | GND    | GP04   |
| Left           | GND    | GP05   |
| A (B1)         | GND    | GP06   |
| B (B2)         | GND    | GP07   |
| Special 2 (S2) | GND    | GP17   |

- The GND (ground) pin is flexible and can be shared across buttons.

![Pins Overview](img/electronics/rpi.jpg)

### Connecting the Wires

Simply connect the wires to the headers and screw them down.

![Screwing the Headers](img/electronics/wire.jpg)

---

## Setting Up the Firmware

### 1) Download the Firmware

- Visit the [GP2040-CE downloads page](https://gp2040-ce.info/downloads).
- In the **Raspberry Pico** section, click **Download**.
- This will download a file like **GP2040-CE_X.X.X_Pico.uf2**.

![Firmware](img/firmware/firmware_download.jpg)

### 2) Enter USB Mode


- Find the **BootSel** button (near the USB port).
- **Unplug** the Pico.
- Open Windows Explorer.
- While holding the **BootSel** button, plug the Pico into the USB port.
- You should see a new removable drive named **RPI-RP2**.

![BootSel Button](img/firmware/bootsel_annot.jpg)


![File explorer](img/firmware/firmware1.jpg)


### 3) Flash the Firmware

- Drag and drop the **GP2040-CE_X.X.X_Pico.uf2** file into the **RPI-RP2** drive.
- The Pico will automatically disconnect and flash the firmware.

![Copy firmware](img/firmware/firmware2.jpg)


### 4) Enter Configuration Mode

- **Unplug** the device.
- **Hold the S2 button** and plug the Pico back into the USB port.
- Open your browser and navigate to [http://192.168.7.1](http://192.168.7.1).

### 5) Enable Switch Mode

1. Go to **Settings**.

![Step 1 - Settings](img/config/step1.jpg)

2. In the **Input Mode Settings**, set **Current Input Mode** to **Nintendo Switch**.

![Step 2 - Change Input Mode](img/config/step2.jpg)

3. Press **Save**, and then click **Reboot**.

![Step 3 - Save and Reboot](img/config/step3.jpg)

4. Click **Console** to test the configuration.

![Step 4 - Console Mode](img/config/step4.v)

---

## Testing the Controller

1. Go to [https://hardwaretester.com/gamepad](https://hardwaretester.com/gamepad).
2. When you press a button, the controller should be recognized as **POKKEN CONTROLLER**.
3. Button presses (like A or directional inputs) will be reflected in real-time.

![Testing the Controller](img/test/test1.jpg)

---


With this setup, you’ll have a fully functional Nintendo Switch controller that you can easily customize to fit your needs!





