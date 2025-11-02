
# Tasmota config

Template:
```json
{"NAME":"PWS-Room-v2","GPIO":[1,1,1,1,608,640,1,1,224,1632,225,1600,226,1],"FLAG":0,"BASE":18}
```


# Compile firmware

Prepare environment first.
Note: important to use same console, as it uses virtual environment activated.
All commands should be executed from repo root.

```bash
# Prepare Python env
python -m venv build/venv
source build/venv/bin/activate
# Install PlatformIO
pip install -U platformio
git clone https://github.com/arendst/Tasmota.git build/tasmota
```

Select release, what you want to use as a base:
```bash
cd build/tasmota
git checkout v15.1.0
```

Copy overrides config, where we have proper sensors enabled:
```bash
cp user_config_override.h build/tasmota/tasmota/
```

Now you can compile firmware. Replace upload port with your own:
```bash
cd build/tasmota
platformio run -e tasmota --target upload --upload-port /dev/ttyUSB0
```

Precompiled firmware can be found under `.pio/build/tasmota/firmware.bin`.

Precompiled firmwares could be found here:
* [Version 14.3.0](https://petro.ws/s/tasmota-14.3.0-pws-module-v2.bin)
* [Version 15.1.0](https://petro.ws/s/tasmota-15.1.0-pws-module-v2.bin)
