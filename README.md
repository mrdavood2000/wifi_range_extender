# Wi-Fi Range Extender (Raspberry Pi)

My B.Sc. capstone project (Electrical Engineering, K. N. Toosi University of Technology, 2022), graded 20/20. Supervisor: Dr. Mohammad Yousef Darmani.

A Raspberry Pi joins an existing Wi-Fi network through a USB dongle and re-broadcasts it as its own hotspot. A small Flask web page lets you change both networks without touching a terminal.

## How it works

- **Web panel** (`flask-final/`): shows the current upstream Wi-Fi and hotspot settings and saves new ones to a config file. It starts on boot via `crontab`.
- **Upstream Wi-Fi** (`wifi_main.py` + `wifi_functions.py`): writes `/etc/network/interfaces` from the config, then reboots.
- **Hotspot** (`hotspot_main.py` + `hotspot_functions.py`): writes the NetworkManager connection (`files/intel-extender.nmconnection`), then reboots.
- **Startup job** (`job_main.py` + `job_functions.py`): on boot, compares the saved config with what the system is actually using and re-applies whichever side changed.
- `files/`: templates for the interfaces file and the hotspot connection.
- `1.txt`, `2.txt`, `3..txt`: my original setup notes (OS install, Flask, FTP copy, crontab).

## Stack

Raspberry Pi OS · Python 3 · Flask · NetworkManager · `/etc/network/interfaces` · crontab

---

*The credentials in the setup notes and templates are from the 2022 prototype and are no longer in use.*
