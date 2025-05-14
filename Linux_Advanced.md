# LINUX - DEBIAN BASED

## Creating .DEB file

### Step-by-Step Process to Create a .deb Package

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
└── var/
    └── DS_SFTP/
        ├── EXECUTABLE.bin
        ├── config.json
        ├── README.md
        ├── VERSION
        └── tools/
            └── app_name.service
````
