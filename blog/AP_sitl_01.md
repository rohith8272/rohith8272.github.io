# 🚁 Building ArduPilot SITL on Ubuntu 24.04 (Noble)

> Instructions to clone, build, and run ArduCopter SITL on Ubuntu 24.04.2 LTS (noble).

---

Check your system version using 

```bash
lsb_release -a
```

1. Clone the ArduPilot Repository

```bash
git clone https://github.com/ArduPilot/ardupilot
cd ardupilot
git submodule init
git submodule update --recursive
```

2. Run the provided script to install prerequisites:


```bash
Tools/environment_install/install-prereqs-ubuntu.sh -y
. ~/.profile
```

3. Configure the Build System
Configure for Software-In-The-Loop (SITL) with the SITL board:

```bash
./waf configure --board=sitl
```

4. Build ArduCopter SITL
Compile ArduCopter:

```bash
./waf copter #plane, rover
```


5. Launch SITL
Use sim_vehicle.py to run the simulator:

```bash
./sim_vehicle.py -v ArduCopter -f copter --console --map -N
```

Flags explained:
-v ArduCopter: Select the firmware type

-f copter: physics model to be used

--console: Launch MAVProxy console

--map: Launch MAVProxy map

-N: Skip firmware rebuild (ignore this argument if your building for the first time)
