It seems like you're sharing a link to a raw script hosted on GitHub. However, the link you provided is incomplete or malformed (`https://` should be `https://`). Here's the corrected link:

```
https://raw.githubusercontent.com/MarioMSamy/cloudpanel_maintinance_ubuntu/main/server_maintenance.sh
```

If this is a script you'd like to document or use, I can help you create a `README.md` file for it or provide instructions on how to use it. Let me know how I can assist! 

For now, here’s a general template for a `README.md` file that you can use for your script:

---

# Server Maintenance Script

This script automates server maintenance tasks such as updating, upgrading, and improving security. It also allows the user to disable specific PHP versions and provides an option to reboot the server after completing the tasks.

## Features

1. **Auto Update and Upgrade**:
   - Updates the package list.
   - Upgrades installed packages.
   - Performs a distribution upgrade.
   - Removes unused packages and cleans up the package cache.

2. **Security Improvements**:
   - Enables automatic security updates using `unattended-upgrades`.
   - Configures UFW (Uncomplicated Firewall) to allow SSH and enable the firewall.
   - Installs and enables `fail2ban` to prevent brute-force attacks.

3. **Disable PHP Versions**:
   - Provides a menu to select which PHP versions to disable.
   - Allows the user to disable all PHP versions at once.
   - Uses `systemctl` to stop and disable the selected PHP versions.

4. **Reboot or Exit**:
   - Prompts the user to reboot the server or exit after completing the tasks.

5. **Root Check**:
   - Ensures the script is run as root for proper execution.

## Supported PHP Versions

The script supports the following PHP versions for disabling:
- php7.1-fpm
- php7.2-fpm
- php7.3-fpm
- php7.4-fpm
- php8.0-fpm
- php8.1-fpm
- php8.2-fpm
- php8.3-fpm
- php8.4-fpm

## Instructions

### Prerequisites
- The script must be run as root.
- Ensure you have a backup of your server before running the script.

### Installation
1. Download the script:
   ```bash
   wget https://raw.githubusercontent.com/MarioMSamy/cloudpanel_maintinance_ubuntu/main/server_maintenance.sh
   ```

2. Make the script executable:
   ```bash
   chmod +x server_maintenance.sh
   ```

### Usage
1. Run the script as root:
   ```bash
   sudo ./server_maintenance.sh
   ```
   or switch to the root user and run it:
   ```bash
   sudo su
   ./server_maintenance.sh
   ```

2. Follow the prompts:
   - The script will update and upgrade the server.
   - It will improve security by enabling automatic updates, configuring UFW, and installing `fail2ban`.
   - You will be asked if you want to disable PHP versions. If yes, select the versions to disable (comma-separated list) or choose to disable all.
   - After completing the tasks, you will be prompted to reboot the server or exit.

### Example Usage

#### Scenario 1: Disable Specific PHP Versions
1. Run the script:
   ```bash
   sudo ./server_maintenance.sh
   ```
2. When prompted, enter:
   ```
   Do you want to disable PHP versions? (y/n): y
   Select PHP versions to disable (comma-separated list, e.g., 1,2,3): 2,5,7
   ```
3. The script will disable:
   - `php7.2-fpm`
   - `php8.0-fpm`
   - `php8.2-fpm`

#### Scenario 2: Disable All PHP Versions
1. Run the script:
   ```bash
   sudo ./server_maintenance.sh
   ```
2. When prompted, enter:
   ```
   Do you want to disable PHP versions? (y/n): y
   Select PHP versions to disable (comma-separated list, e.g., 1,2,3): 10
   ```
3. The script will disable all PHP versions listed in the `php_versions` array.

#### Scenario 3: Reboot the Server
1. Run the script:
   ```bash
   sudo ./server_maintenance.sh
   ```
2. Complete the server maintenance tasks.
3. When prompted:
   ```
   Do you want to reboot the server now? (y/n): y
   ```
4. The server will reboot.

#### Scenario 4: Exit Without Rebooting
1. Run the script:
   ```bash
   sudo ./server_maintenance.sh
   ```
2. Complete the server maintenance tasks.
3. When prompted:
   ```
   Do you want to reboot the server now? (y/n): n
   ```
4. The script will exit with the message:
   ```
   Exiting without rebooting. Have a great day!
   ```

## Customization

### Adding or Removing PHP Versions
To add or remove PHP versions, edit the `php_versions` associative array in the script:
```bash
declare -A php_versions=(
    ["1"]="php7.1-fpm"
    ["2"]="php7.2-fpm"
    ["3"]="php7.3-fpm"
    ["4"]="php7.4-fpm"
    ["5"]="php8.0-fpm"
    ["6"]="php8.1-fpm"
    ["7"]="php8.2-fpm"
    ["8"]="php8.3-fpm"
    ["9"]="php8.4-fpm"
)
```

### Changing Security Settings
- To modify UFW rules, edit the `ufw allow ssh` line in the `improve_security` function.
- To configure `fail2ban` further, edit the `/etc/fail2ban/jail.local` file after installation.

## License

This script is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Support

For issues or feature requests, please open an issue on the [GitHub repository](https://github.com/MarioMSamy/cloudpanel_maintinance_ubuntu) or contact the maintainer.

---

Let me know if you need further assistance!
