# SX1255--HAT's
# You can Donate for better progress and support, https://www.paypal.com/donate/?hosted_button_id=WZ52L7DWVVQ28
This is modified SXceiver, thanks to Tatu Peltola for shared schematic.
# Three versions of HAT's: HAT with (LPF_TX, BPF_RX filters and PA)/ HAT with (LPF_TX, BPF_RX filters without PA) and HAT with (BandPass filters, ceramic antennas without PA) and added SPI line protection IC.
# The PA (TQP3M9036) can amplify up to 25dBm @ (70cm-band) 
# I can make Custom design too. (pclab.mk@gmail.com)
# RPi4/5, fast-write micro-sd card or upgraded with M.2 nvme drive.
# The eeprom is for HW-ID and if cannot be programmed by the procedures then you must programm with eeprom programmator. " https://github.com/tejeez/sxxcvr/blob/main/dts/README.md ".
# For Tetra-TMO Base Station this is the installing procedures, " https://github.com/MidnightBlueLabs/tetra-bluestation-docs/wiki ".
# BlueStation, https://github.com/MidnightBlueLabs/tetra-bluestation
# FlowStation, https://github.com/razvanzeces/flowstation
# BlueStation Tetra TMO configurator " https://bluestation.russel053.com/ "

Install FlowStation ---for sxceiver---
# 1. Install Trixie 64bit-LITE
# 2. 
# sudo apt update
# sudo apt install git make g++ cmake
# sudo apt install libsoapysdr-dev
# sudo apt install soapysdr-tools
# sudo apt install libasound2-dev
# sudo apt install clang llvm-dev libclang-dev

3. Rust
# curl https://sh.rustup.rs -sSf | sh

4. SoapySX "enable SPI and I2C on the RPi"
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

5. The FlowStation
# git clone https://github.com/razvanzeces/flowstation
# cd flowstation
# . "$HOME/.cargo/env"
# cargo build --release
# cp example_config/config.toml config.toml
# nano config.toml (configure the base station)

6. Run
# ./target/release/bluestation-bs ./config.toml

7. Update
# git pull
# cargo build --release

# Z32IT
