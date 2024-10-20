file name: update_system.sh

```sh
#!/bin/bash

# Update package list
echo "Updating package list..."
sudo apt update

# Upgrade installed packages
echo "Upgrading installed packages..."
sudo apt upgrade -y

# Clean up
echo "Cleaning up..."
sudo apt autoremove -y
sudo apt autoclean

echo "System update completed!"

```
