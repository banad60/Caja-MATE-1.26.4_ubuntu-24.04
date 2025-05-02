# Howto: Compile Caja 1.26.4 on Ubuntu 24.04

This guide explains how to compile Caja 1.26.4 from source on Ubuntu 24.04.2. It specifically addresses issues with `autopoint` and `gettext` that may arise during the process.

## Prerequisites
- Ensure you have the necessary build tools and dependencies installed:
  ```bash
  sudo apt-get install build-essential git libexempi-dev libgirepository1.0-dev libnotify-dev libexif-dev gvfs-libs mate-common libmate-desktop-dev gettext autopoint
  ```

## Step 1: Clone the Caja Source Code
- Clone the Caja repository and switch to version 1.26.4:
  ```bash
  git clone --recurse-submodules https://github.com/mate-desktop/caja.git
  cd caja
  git checkout v1.26.4
  ```

## Step 2: Generate Build Files
- Run `autogen.sh`:
  ```bash
  ./autogen.sh --prefix=/usr
  ```
- **Note**: If you encounter an error like "autopoint not found," ensure `autopoint` is installed:
  ```bash
  sudo apt-get install autopoint
  ```

## Step 3: Configure and Compile
- Configure and build Caja:
  ```bash
  ./configure --prefix=/usr
  make
  sudo make install
  ```

## Step 4: Troubleshooting
- **Issue with `mate-common`**: If you see an error like "You need to install mate-common from the MATE Git," install `mate-common` from the Ubuntu repositories:
  ```bash
  sudo apt-get install mate-common
  ```
- **Missing Dependencies**: If additional dependencies are missing, install them with:
  ```bash
  sudo apt-get build-dep caja
  ```

## Additional Notes
- After installing Caja 1.26.4, you may need to log out and log back in to load the new version.
- If you encounter issues with `gettext` and `autopoint`, ensure both packages are installed:
  ```bash
  sudo apt-get install gettext autopoint
  ```

With these steps, you should be able to successfully compile and install Caja 1.26.4.