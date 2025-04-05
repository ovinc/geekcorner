# IDS Cameras

## Installation (Linux)


### IDS Peak

Follow the steps here to install IDS Peak:
https://en.ids-imaging.com/files/downloads/ids-peak/readme/ids-peak-linux-readme-2.5_EN.html

After installation (normally, in `opt/`), the camera needs to be "activated" by going to
`[install_folder]/local/scripts` and running the udev install script with
```bash
./ids_install_udev_rule.sh
```
(from the install manual:
*Under "/opt/ids_peak_[version]_[arch]/local/scripts" you can find a udev rule for the USB access the U3V cameras require. For a simple installation you can use the script install-udev-rule.sh in the same folder. Additionally you can find an uninstall script as well.*, see e.g. https://en.ids-imaging.com/tl_files/downloads/ids-peak/readme/ids-peak-linux-readme-1.0_EN.html
)

Without this installation the camera just shows up as *U3V Producer 0x8000*


## Python

Go to `local/src/ids/bindings` in the IDS Peak install folder.

Normally, for recent versions there is only a *python.txt* file that explains that there is no python binder but everything can be directly installed with
```bash
pip install ids_peak
```

For python programming to work, the following environment variable must be defined, e.g. in *.bashrc*:
```bash
export GENICAM_GENTL64_PATH="/opt/ids_peak_[version]_[arch]/lib/ids/cti"
```
(replacing the folder by the actual install folder name of IDS Peak)

*NOTE*: the documentation says to write something like
```bash
GENICAM_GENTL64_PATH=$GENICAM_GENTL64_PATH:/opt/ids_peak_[version]_[arch]/lib/ids/cti
```
maybe in the case where the environment variable already exists, but in Ubuntu it does not work.
(see e.g. https://en.ids-imaging.com/tl_files/downloads/ids-peak/readme/ids-peak-linux-readme-1.0_EN.html)

*NOTE*: examples scripts can be found in `local/src/ids/samples/peak/python`

