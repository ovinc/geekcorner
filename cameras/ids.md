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
*Under "/opt/ids_peak_[version]_[arch]/local/scripts" you can find a udev rule for the USB access the U3V cameras require. For a simple installation you can use the script install-udev-rule.sh in the same folder. Additionally you can find an uninstall script as well.*, see e.g. 
https://en.ids-imaging.com/tl_files/downloads/ids-peak/readme/ids-peak-linux-readme-1.0_EN.html
or more recent
https://en.ids-imaging.com/files/downloads/ids-peak/readme/ids-peak-linux-readme-2.15.0_EN.html
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
**but attention**, the `GENICAM_GENTL64_PATH` environment variable might already be defined
(e.g. if another camera from another supplier is installed),
which can be verified by checking if
```bash
echo $GENICAM_GENTL64_PATH
```
returns anything. 
If this is the case, it is better to just append the IDS path to the existing variable:
```bash
export GENICAM_GENTL64_PATH="$GENICAM_GENTL64_PATH:/opt/ids_peak_[version]_[arch]/lib/ids/cti"
```
and probably it works to always do this just in case other programs try to define the variable.
(see e.g. https://en.ids-imaging.com/files/downloads/ids-peak/readme/ids-peak-linux-readme-2.15.0_EN.html)

*NOTE*: examples scripts can be found in `local/src/ids/samples/peak/python`

*NOTE*: some more specific documentation can be found in ids_peak_ipl, e.g. for pixel formats:
https://en.ids-imaging.com/manuals/ids-peak/ids-peak-ipl-documentation/2.15.0/en/namespacepeak_1_1ipl.html#a90d4d9ed4b1b3407a4fadad1da4fec07

*NOTE*: See GenICam_NamingConvention.pdf (in perso documentation folder) or downloadable here
for e.g. the pixel format names etc.
