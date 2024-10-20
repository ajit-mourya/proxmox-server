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

# Check if NVIDIA driver is installed
if command -v nvidia-smi &> /dev/null; then
    echo "NVIDIA drivers are already installed."
    nvidia-smi
else
    echo "NVIDIA drivers are not installed. Installing..."
    
    # Install the recommended NVIDIA driver
    sudo apt install -y $(ubuntu-drivers devices | grep 'recommended' | awk '{print $3}')

    # Check if the installation was successful
    if command -v nvidia-smi &> /dev/null; then
        echo "NVIDIA drivers have been installed successfully."
        nvidia-smi
    else
        echo "Failed to install NVIDIA drivers. Please check for errors."
    fi
fi


```
