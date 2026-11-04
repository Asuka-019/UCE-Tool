# UCE Tool

[简体中文](README.zh-CN.md) | **English** | [Deutsch](README.de.md) | [日本語](README.ja.md) | [Français](README.fr.md)

UCE Tool is the desktop companion for USB-C Explorer. It provides live measurements, E-Marker reading, PD detection and capture, device theme configuration, and firmware updates.

## Install and connect

Download the appropriate Windows or macOS package from the [releases page](https://github.com/Tamako-zz/UCE-Tool/releases/latest). Extract the Windows package and open the application, or install the Mac app in Applications.

Connect the device to the computer with a data-capable USB cable. The device appears in the left sidebar; click its card to connect. Click the connected card again to disconnect, or click another device card to switch devices. Scanning does not automatically connect a device.

## Dashboard

Open **Dashboard** and press the start icon to display live measurements and charts. Use the channel controls to select curves, adjust the sampling rate and time range, pause, or clear the chart.

## E-Marker

Connect the cable to the device as indicated by its ports and open **E-Marker**. Click **Read** to view the reported cable information, or **Continuous Read** to repeat the query; click it again to stop. Remove powered devices from the output before starting continuous reading, as prompted by the application.

Open **Detection Records** to view results from this session. Export them to Excel or clear the list. Fields not reported or not recognized are shown as unknown.

## PD Detection

Connect the charger to be tested and open **PD Detection**. Click **Start Detection**, read the warning and confirm. The page shows the detected PDOs and their individual results; the same button can stop an active detection. Records can be viewed, exported to Excel, or cleared.

**Voltage may rise during detection. Disconnect powered devices from the output before starting.**

## PD Analyzer

Connect the test circuit according to the device port markings. Open **PD Analyzer** and click **Start Capture**; click the same button to stop. Select a packet to inspect its header and data objects below the list. Drag the divider to resize the areas.

Use the GoodCRC switch to hide or show GoodCRC packets. **Export Excel** saves the capture, including hidden GoodCRC packets.

## Theme Configuration

Use the arrows to choose a device screen, then click a color region or the background color to edit it.

- **Restore Defaults** restores the default colors.
- **Read from Device** loads the current colors.
- **Apply to Device** applies colors temporarily.
- **Save to Device** saves them across restarts.

## Firmware update and settings

Open **Firmware Update**, fetch the available versions, and choose the firmware matching your device. Follow the on-screen instructions and keep the device connected and powered until the update finishes.

Use Settings to change the language and view device information; use the sidebar control to switch between light and dark modes. Records are kept for the current session, so export anything you need before closing the application. If the device is busy, stop any other detection or capture first.

## More detailed guidance

### Starting the application

The Windows and macOS application packages are intended for normal use and do not require a separate Python installation. On Mac, select the package for Apple Silicon or Intel as appropriate. If macOS blocks the first launch, check that the application came from the project, then allow it in **System Settings → Privacy & Security**.

Use the device's data interface to connect it to the computer; a charging-only cable may supply power without making the device available to the software. The sidebar shows the device name, abbreviated serial number, and APP version. The full serial number is available in device information. A device in BOOT mode can be used for firmware recovery, but live measurements and detection require the application firmware.

### Reading the dashboard

VBUS is voltage, IBUS is current, and POWER is power. D+ / D− and CC1 / CC2 show the corresponding signal voltages. The chart has separate scales for voltage, current, and power, so check the unit when comparing curves. Move the pointer over the chart to inspect samples; `--` means no value is available at that position.

You can choose a sampling rate of 1, 10, or 50 samples per second and a displayed time range of 10, 30, 60, or 120 seconds. Pausing holds the display; resuming continues acquisition. Clearing removes the displayed history.

### E-Marker and PD results

E-Marker information depends on what the cable and firmware report. The page can show cable type, current rating, maximum voltage, data speed, PD version, TBT, EPR, and length or latency. An estimated length is derived from cable latency and is not a physical measurement. Raw E-Marker data is shown below the cable information.

PD Detection reads the charger's advertised PDOs and, when the firmware supplies them, displays individual test states. A capability being advertised does not by itself mean that its test passed. The result and record views can be switched with the tabs above the results. If a required feature is not supported, update to compatible device firmware.

The E-Marker and PD Detection record lists are session histories. **Clear Records** removes the current list; **Export Excel** creates an `.xlsx` file. Choose a location before closing the application if you want to keep the results.

### Reading a PD capture

The capture table shows packet type, SOP channel, message ID, direction, object count, PD revision, elapsed time, voltage/current snapshot, raw data and notes. Select a row to see a breakdown of the message header and available data-object fields. The detail area can scroll horizontally and vertically when a packet contains many fields.

Attach and Detach are connection events; Hard Reset is a reset event on the monitored PD link. The analyzer may show raw values when it cannot safely determine a field's meaning. Cable-message direction is displayed as communication between the port and plug when the exact sender is not known.

GoodCRC filtering affects the display, not the stored capture: hidden entries are included in the Excel export.

### Applying colors and updating firmware

Theme colors are edited in the preview first. **Apply to Device** lets you inspect a temporary change; use **Save to Device** after confirming the result if it should remain after power cycling. **Read from Device** replaces the preview with the device's current colors, while **Restore Defaults** restores the default values in the editor.

For firmware updates, retrieve the available versions, select a package compatible with the device, and follow the on-screen progress and result. Do not disconnect power or the data cable during the update. Updating the UCE Tool application itself is a separate operation available from the About menu.

### Troubleshooting

- **No device appears:** check power, the data cable and port, then reconnect the device. If the card appears, click it to connect.
- **Device busy:** stop another E-Marker query, PD detection, capture, or update and wait for it to finish.
- **No E-Marker result:** check the cable and connection; not every cable has an E-Marker, and some details may not be reported.
- **No packets in the analyzer:** confirm the device is connected, capture is running, and the test circuit is connected to the correct ports. Check whether GoodCRC is hidden.
- **Update or export fails:** check the displayed error, available storage, the selected firmware, and the connection, then retry.
