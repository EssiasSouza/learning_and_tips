## Reinstall WSL

````
wsl --unregister distro_name
wsl --shutdown
wsl --uninstall


````

## Distros
Download WSL image from this link:

https://ubuntu.com/desktop/wsl

Create a folder where will stay the files. Example:

mkdir C:\WSL\Ubuntu24

````
wsl --import Ubuntu-24.04 C:\WSL\Ubuntu24 C:\Users\<Your User>\Downloads\ubuntu-24.04.3-wsl-amd64.gz --version 2

wsl --install
wsl --set-default Ubuntu-24.04
wsl --list --verbose

# Change the defaul user from WSL.
sudo nano /etc/wsl.conf
# Add these lines:
[user]
default=essias
````
