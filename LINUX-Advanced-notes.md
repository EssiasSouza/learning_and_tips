# LINUX - DEBIAN BASED

## Creating .DEB file

### Step-by-Step Process to Create a .deb Package

- Attention: Dont use special characters or (_) you can separe-your-name-with-

- Second TIP: Create files writing on a Linux PC or after create in your Windows note editor, you can run the command below to convert it to a 

Example:
````
dos2unix package-name/DEBIAN/postinst
````

1. Prepare the Directory Structure

In this example I'm using bin files to create commands to manage the service.
You will create a root directory for the package, which mimics the Linux filesystem hierarchy:

````
my_package/
├── DEBIAN/
│   └── control
├── usr/
│   └── bin/
│       ├── app
│       ├── appStart
│       ├── appStop
│       ├── appStatus
│       └── appRestart
├── usr/
│   └── lib/
│       └── systemd/
│           └── system/
│               └── app_name.service
└── etc/
    └── application/
        ├── EXECUTABLE.bin
        ├── config.json
        ├── README.md
        ├── VERSION
        └── tools/
            └── app_name.service
````

2. Create the DEBIAN/control File

This file defines package metadata. Example:

NOTE: The control file should be terminated with a spaced line

````
Package: package-name(The same name used in the package .deb)
Version: 1.0.0
Section: base
Priority: optional
Architecture: amd64
Maintainer: Your Name <you@example.com>
Description: Description of your application

````

3. Set Permissions

If you need of especials permissions you can follow this step.

Files in /usr/bin: chmod 777

All files should be owned by root:root (can be set when building the package using fakeroot or by chown if running as root).

You will need to ensure `executable permissions` on your binary as well.

4. (Optional) Add Post-Install Script

If you want the service to be installed and enabled automatically, create a file postinst in the DEBIAN/ folder:

````
#!/bin/bash
systemctl daemon-reexec
systemctl daemon-reload
systemctl enable app_name.service
printf "enable app_name.service\n" | sudo tee -a /usr/lib/systemd/system-preset/90-systemd.preset
systemctl start app_name.service
````
Make this script executable:

````
chmod 755 my_package/DEBIAN/postinst
````

5. Build the .deb File

Once the structure is ready, run:

````
dpkg-deb --build my_package
````
This will create a file called my_package.deb.

6. Install the Package
To test your .deb package:

````
sudo dpkg -i my_package.deb
````
