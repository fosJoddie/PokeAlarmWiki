## Overview
* [Prerequisites](#prerequisites)
* [Introduction](#introduction)
* [Installation](#installation)
* [Updating PokeAlarm](#updating-pokealarm)

## Prerequisites
This guide assumes:

1. You have a working [RocketMap](https://github.com/RocketMap/RocketMap) installation. There is a detailed wiki [here](https://github.com/RocketMap/RocketMap/wiki) and [here](https://pgm.readthedocs.io/en/develop/index.html)
2. You have the latest version of python 2.7 installed
3. You have a working git installation
4. You have a good text editor installed.  Do **NOT** use Notepad or TextEdit! Use PyCharm or Notepad++

## Introduction
PokeAlarm Version 3 is a lightweight webserver designed to receive POST requests from your local RocketMap server. It sorts through these requests, letting you know through your favorite service something has happend. It might be a tweet when a rare pokemon spawning down the street, a Telegram message letting you know a lured pokestop only a few minutes away, or else a Discord notification letting you know your teams gym has fallen.

Below, we'll configure PokeAlarm and set it to listen for POST requests.  Then we'll start RocketMaps to send out POST requests at the specific HOST and PORT on which your PokeAlarm installation is listening.

## Installation

1. **Clone PokeAlarm locally.** Navigate to the folder you want to store the Alarm in. Use `git clone https://github.com/kvangent/PokeAlarm.git` to create a local copy of the project.

2. **Install dependencies.** Go into the root directory of your local PokeAlarm folder. Run `pip install -r requirements.txt`.  This will install additional packages that PokeAlarm needs to run.

3. **Configure filters and alarms (and maybe geofences).** (Windows or Mac users: do not use the default text editors like Notepad and TextEdit!)
    * Make a copy of the `filters.json.example` file and rename it to`filters.json`. Edit `filters.json` with your [filter configuration] settings by setting the Pokemon, Gym, and Pokestop values you want to `"True"`. Visit the [filter configutation](https://github.com/kvangent/PokeAlarm/wiki/Filters) wiki page for details.
    * Optional: Make a copy of the `geofence.txt.example` file and rename it to`geofence.txt`. Visit the [Geofencing] wiki page for details.
    * Make a copy of the `alarms.json.example` file and rename it to`alarms.json`. Edit `alarms.json` with your [alarm configuration](https://github.com/kvangent/PokeAlarm/wiki/Alarms) settings. Visit the [alarm configuration](https://github.com/kvangent/PokeAlarm/wiki/Alarms) wiki page for details.

4. **Start Pokealarm.** Run `python start_pokealarm.py`. You should receive a notification right away, letting you know your alarm has been set up correctly. The default listening address is `http://127.0.0.1:4000`. You can use the `-H HOST -P PORT` arguments to set a custom listening address and port. 
**Note:** This address/port should be DIFFERENT then the address/port your map is running on.

5. **Start RocketMap**. Start your map like normal, but add the `-wh http://127.0.0.1:4000` (or whatever listening address you specified in the last step). You can also put `webhook:http://127.0.0.1:4000` in `config.ini` file of your RocketMap installation as well.

6. **Monitor PokeAlarm output**.  PokeAlarm should log to console every time it learns about a pokemon - and will say `Pokemon notification was triggered!` when a Pokemon on your list was found. If you aren't receiving anything, make sure that you have the correct address running on your map and try again!

## Updating PokeAlarm

1. Change into the root directory of your PokeAlarm installation folder.
2. Run `git pull`.
3. Run `pip install -r requirements.txt`.
