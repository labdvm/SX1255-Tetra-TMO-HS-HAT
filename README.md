# SX1255--HAT's

This is modified SXceiver, thanks to Tatu Peltola for shared schematic.
# Three versions of HAT's: HAT with (LPF_TX, BPF_RX filters and PA)/ HAT with (LPF_TX, BPF_RX filters without PA) and HAT with (BandPass filters, ceramic antennas without PA) and added SPI line protection IC. The first HAT also is known as "Little PA".
# The PA (TQP3M9036) can amplify up to ~25dBm @ (70cm-band) 
# I can make Custom design too. (pclab.mk@gmail.com)
# RPi 3/4/5, fast-write micro-sd card or upgraded with M.2 nvme drive.
# The eeprom is for HW-ID " https://github.com/tejeez/sxxcvr/blob/main/dts/README.md ".
# For Tetra-TMO Base Station this is the installing procedures, " https://github.com/MidnightBlueLabs/tetra-bluestation-docs/wiki ".
# BlueStation, https://github.com/MidnightBlueLabs/tetra-bluestation
# BlueStation Tetra TMO configurator " https://bluestation.russel053.com/ "
# FlowStation, https://github.com/razvanzeces/flowstation
# Nexus-BS, https://github.com/invictus737/nexus-bs

Install FlowStation ---for sxceiver---
# 1. Install Trixie 64bit-LITE
2. Install lib's:
# sudo apt update
# sudo apt install git make g++ cmake
# sudo apt install libsoapysdr-dev
# sudo apt install soapysdr-tools
# sudo apt install libasound2-dev
# sudo apt install clang llvm-dev libclang-dev

3. Install Rust:
# curl https://sh.rustup.rs -sSf | sh

4. RPi-setup:
"enable SPI and I2C"
# sudo raspi-config > Interface Options > "enable and reboot the rpi"
# sudo nano /boot/firmware/config.txt
"add"
# dtparam=i2c_vc=on
"Reboot the Rpi"

6. Install SoapySX:
# cd
# git clone "https://github.com/tejeez/sxxcvr.git"
# cd sxxcvr/SoapySX
# mkdir build
# cd build
# cmake ..
# make
# sudo make install
# sudo ldconfig

Check that the driver is available:
# SoapySDRUtil --info

Check that the device is detected:
# ls -l /proc/device-tree/hat
# SoapySDRUtil --probe=driver=sx

6. Install The FlowStation:
# git clone https://github.com/razvanzeces/flowstation
# cd flowstation
# . "$HOME/.cargo/env"
# cargo build --release
# cp example_config/config.toml config.toml
# nano config.toml "configure the base station"

7. Run:
# cd flowstation
# ./target/release/bluestation-bs ./config.toml

7. Update:
# git pull
# cargo build --release

# Z32IT
