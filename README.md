# Overview
Bash scripts to automate configuration and operation of the Ulanzi Smart Pixel clock with the alternative AWTRIX Light (AWL) firmware.

## Getting Started
These instructions will show how to install, configure, test and automate the operation of your Smart Pixel clock.

### Prerequisites
- Bash
- `jo`, a small utility to create JSON objects on the command line (https://github.com/jpmens/jo)
- Cron (for automation)
- A small system which runs 24/7 (ideally), e.g. Raspberry Pi or LXC

### Installation
1. Clone the repository
1. Copy `config.sh.example` to `config.sh`
1. Set IP address or name of the Smart Pixel clock in `config.sh`
1. Configure colors and messages in `smartclock_watch`

## Running
### Set clock mode depending on time
```
./smartclock_watch
```
Depending on current time (hour only), the script sets a different configuration on the Smart Pixel clock. For testing, the hour can be overriden in the file itself.

### Switch LED matrix on and off
```
./smartclock_power
```
The script will toggle the LED matrix on and off. For this, it uses a toggle file, which is configured in `config.sh`. The location of the file needs to be writeable for the user running the script.

## Automation
1. Copy `CRON.example` to `/etc/cron.d/smartclock` and chown to `root:root`
1. Choose a user to run the script under
1. Set `smartclock_watch` to run every hour
1. If you want to turn the matrix display e.g. during the night, set `smartclock_power` to run when to switch off and on again

## License
See [LICENSE](LICENSE) for licensing information.

## Links
- https://www.ulanzi.com/products/ulanzi-pixel-smart-clock-2882 (Hardware)
- https://github.com/Blueforcer/awtrix-light (AWTRIX Light firmware)
- https://blueforcer.github.io/awtrix-light/#/api (API)