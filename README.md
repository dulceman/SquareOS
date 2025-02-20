![logo](https://files.catbox.moe/1bqqfy.png)
# SquareOS
### The Square Kiosk Operating System for your Raspberry Pi
### Features:
- **Auto-login**: The Pi will log in as the `pi` user automatically.
- **Kiosk Mode**: Chromium will launch in full-screen mode, running a designated URL (like Square checkout or a custom page).
- **Minimal Setup**: The image is based on **Raspberry Pi OS Lite**, making it lightweight and fast for kiosk use.

## How to Use:

1. **Download the Image**:
 - Go to the [Releases](https://github.com/dulceman/SquareOS/releases) section to download the image file.

2. **Flash the Image to an SD Card**:
 - Use **Raspberry Pi Imager** or **Balena Etcher** to flash the image to an SD card (minimum 8GB recommended).
 - In **Raspberry Pi Imager**, select "Use custom" to choose the downloaded image file.

3. **Insert the SD Card and Boot the Pi**:
 - Insert the SD card into your Raspberry Pi and power it on.
 - The Raspberry Pi will automatically log in as the `pi` user and launch **Chromium** in kiosk mode, displaying the Square checkout page (or your configured URL).

4. **Configuration** (Optional):
 - If you want to modify the URL or make other changes, follow these steps:
 1. Access the Pi via SSH or open a terminal.
 2. Modify the `kiosk.desktop` file located at:
 `/etc/xdg/autostart/kiosk.desktop`
 
     3. Change the `Exec` line to the desired URL:
        ```bash
        Exec=chromium-browser --noerrdialogs --kiosk https://your-new-url.com --incognito --disable-extensions
        ```
     4. Save the file and reboot the Pi to apply changes. 
5. **Disabling the Desktop Environment** (Optional):
 - If you'd like to disable the desktop environment entirely, run:
 `sudo systemctl set-default multi-user.target`
 - This will boot the Raspberry Pi into a command-line interface only, without a graphical desktop. 
6. **Security & Other Considerations**:
 - Make sure to secure the Pi before deploying it in a public environment. You may want to:
 - Change the default `pi` user password.
 - Set up a firewall to block unnecessary ports.
 - Disable unused services like SSH or Wi-Fi. (If you use these things, don't disable them, try securing them.)

## Troubleshooting:
- **Chromium not launching in kiosk mode**: Ensure the `kiosk.desktop` file exists in `/etc/xdg/autostart/` and contains the correct `Exec` line.
- **The Pi doesn't log in automatically**: Check the `systemd` service for auto-login, or re-enable it with:
`sudo systemctl enable getty@tty1.service`

## Contributing:

Feel free to open issues or submit pull requests if you have suggestions or improvements. Contributions are welcome!

----------

### License

This project is licensed under the MIT License - see the [LICENSE](https://github.com/dulceman/SquareOS?tab=MIT-1-ov-file)  file for details.
