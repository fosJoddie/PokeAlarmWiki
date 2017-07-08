## Overview
* [Prerequisites](#prerequities)
* [Introduction](#introduction)
* [Pokemon Text](#pokemon-text)
* [Pokestop Text](#pokestop-text)
* [Gym Text](#gym-text)
* [Reverse Location Text](#reverse-location-text)
* [Distance Matrix Text](#distance-matrix-text)
* [Example: Slack](#example-slack)

## Prerequisites
This guide assumes:

1. You have a working RocketMap installation
2. You are familiar with [JSON formatting](http://www.w3schools.com/json/default.asp)
3. You have read and understood the [Alarm Configuration](https://github.com/kvangent/PokeAlarm/wiki/Alarm-Configuration) Wiki
4. You are comfortable with the layout of `alarms.json`.
5. You are using the latest version of PokeAlarm

## Introduction


All alarms in the `alarms.json` alarm configuration file have customizable fields for each alert that allow you to insert your own message. This allows your to override the standard message and provide your own. You may customize as few or as many fields as you want - any field not present in your config will reset to default.

**Note:** The alarm configuration file is the only file within the PokeAlarm installation that you are **required** to directly edit (`config.ini` file is optional.)  Editing other files in your PokeAlarm installation directory is not supported.

In order to customize an Alert, you must specify what type of alert you want to config: Either `pokemon`, `pokestop`, or `gym`. Each of these has different defaults available. The following is an `alarms` config where a portion of the Alert has been updated:

```json
{
  "type":"slack",
  "active":"True",
  "api_key":"YOUR_API_KEY_HERE",
    "pokemon":{
        "channel":"Pokemon",
        "username":"<pkmn>",
        "title":"A GIANT <pkmn> jumped out of the grass!",
        "body": "Available until <24h_time> (<time_left>)."
    },
    "pokestop":{
        "channel":"Pokestop",
        "title":"Someone  has placed a lure on a Pokestop!",
        "body":"Better hurry! The lure only has <time_left> remaining!"
    }
}
```

The above might produce the following customized pokemon and pokestop notifications:

#### Pokemon notification output
> A GIANT Dragonite jumped out of the grass! Availble until 12:34:56 (14m 59s) remaining!

#### Pokestop notification output
> Better hurry! The lure only has 12m 34s remaining!

For what fields (title, message, etc) you have the option to change, please see the wiki page for the specific service.

## Pokemon Text


**Note:** There are **two** `pokemon` keys in `alarms.json` - one at the top level, and another optional at the alarm level.  The follow text substitutions below pertain to the `pokemon` field in the `alarms:[]` level.

| Text            | Description                            |
|:----------------|:---------------------------------------|
| `<pkmn_id>`     | ID of the alerted pokemon              |
| `<pkmn>`        | Name of the alerted pokemon            |
| `<lat>`         | Latitude of the pokemon                |
| `<lng>`         | Longitude of the pokemon               |
| `<gmaps>`       | Gmaps link to a pin of the pokemon     |
| `<dist>`        | *Distance from set location in meters  |
| `<time_left>`   | Time remaining for the pokemon         |
| `<12h_time>`    | Dissapear time in 12hour format        |
| `<24h_time>`    | Dissapear time in 24hour format        |
| `<dir>`         | Cardinal direction from set location   |
| `<respawn_text>`| **Respawn Message                      |
| `<iv>`          | Percent IV of the alerted pokemon      |
| `<atk>`         | Attack IV of the alerted pokemon       |
| `<def>`         | Defense IV of the alerted pokemon      |
| `<sta>`         | Stamina IV of the alerted pokemon      |
| `<quick_move>`  | Quick move of the alerted pokemon      |
| `<charge_move>` | Charge move of the alerted pokemon     |
| `<quick_id>`    | ID number of the quick move  |
| `<quick_damage>` | Damage value of quick move
| `<quick_duration>` | Duration value of quick move
| `<quick_dps>` | Damage per second value of quick move
| `<quick_energy>` | Energy of quick move
| `<charge_id>` | ID number of charge move
| `<charge_damage>` |  Damage value of charge move
| `<charge_duration>` | Duration value of charge move
| `<charge_dps>` | Damage per second value of charge move
| `<charge_energy>` | Energy of charge move
| `<id>`| Database encounter_id of the pokemon   |
| `<gender>`      | Gender of the alerted pokemon          |
| `<height>`      | Height of the alerted pokemon          |
| `<weight>`      | Weight of the alerted pokemon          |
| `<size>`        | Size of the alerted pokemon            |
| `<geofence>`     | Geofence name of where the alerted pokemon originated |
| `<gmaps>` | Google Maps URL to pokemon location
| `<applemaps>` | Apple Maps URL to pokemon location |
*If no location has been set, dist will always return 0 (meters or yards)

**For map tools supporting this feature, this will show messages for spawned pokemon, that'll be back after a hidden phase. I.e. for pokemon from a 2x15 point it'll show '15m later back for 15m.', when scanned during the first 15 minutes.

## Pokestop Text
A list of text substitutions for the `pokestop` field in the alarm section are below:

| Text           | Description                            |
|:-------------- |:---------------------------------------|
| `<id>`         | ID of the alerted pokestop             |
| `<lat>`        | Latitude of the pokestop               |
| `<lng>`        | Longitude of the pokestop              |
| `<gmaps>`      | Gmaps link to a pin of the pokestop    |
| `<dist>`       | *Distance from set location in meters  |
| `<time_left>`  | Time remaining for the pokestop        |
| `<12h_time>`   | Expire time in 12hour format           |
| `<24h_time>`   | Expire time in 24hour format           |
| `<dir>`        | Cardinal direction from set location   |
*If no location has been set, dist will always return 0 (meters or yards)

## Gym Text
A list of text substitutions for the `gym` field in the alarm section are below:

| Text           | Description                            |
|:-------------- |:---------------------------------------|
| `<id>`         | ID of the alerted gym              |
| `<lat>`        | Latitude of the gym                |
| `<lng>`        | Longitude of the gym               |
| `<gmaps>`      | Gmaps link to a pin of the gym     |
| `<dist>`       | *Distance from set location  |
| `<points>`     | Number of points the gym currently has |
| `<old_team>`   | Name of the team who lost the gym      |
| `<new_team>`   | Name of the team who captured the gym  |
*If no location has been set, dist will always return 0 (meters or yards)

## Egg Text
A list of text substitutions for the `gegg` field in the alarm section are below:

| Text                  | Description                            |
|:----------------------|:---------------------------------------|
| `<raid_level>`        | The tier level of the raid (1-5)       |
| `<lat>`               | Latitude of the raid pokemon           |
| `<lng>`               | Longitude of the raid pokemon          |
| `<gmaps>`             | Gmaps link to a pin of the raid        |
| `<dist>`              | *Distance from set location in meters  |
| `<time_left>`         | Time remaining before the raid ends    |
| `<12h_time>`          | Raid end time in 12hour format         |
| `<24h_time>`          | Raid end time in 24hour format         |
| `<begin_time_left>`   | Time remaining before the raid begins  |
| `<begin_12h_time>`    | Raid begin time in 12hour format       |
| `<begin_24h_time>`    | Raid begin time in 24hour format       |
| `<dir>`               | Cardinal direction from set location   |
| `<geofence>`          | Geofence name of where the alarm originated |
| `<gmaps>`             | Google Maps URL to pokemon location    |
| `<applemaps>`         | Apple Maps URL to pokemon location     |
*If no location has been set, dist will always return 0 (meters or yards)

## Raid Text
A list of text substitutions for the `raid` field in the alarm section are below:

| Text                  | Description                            |
|:----------------------|:---------------------------------------|
| `<raid_level>`        | The tier level of the raid (1-5)       |
| `<pkmn_id>`           | ID of the alerted raid pokemon         |
| `<pkmn>`              | Name of the alerted raid pokemon       |
| `<lat>`               | Latitude of the raid pokemon           |
| `<lng>`               | Longitude of the raid pokemon          |
| `<gmaps>`             | Gmaps link to a pin of the raid        |
| `<dist>`              | *Distance from set location in meters  |
| `<time_left>`         | Time remaining for the raid            |
| `<12h_time>`          | Raid end time in 12hour format         |
| `<24h_time>`          | Raid end time in 24hour format         |
| `<begin_12h_time>`    | Raid begin time in 12hour format       |
| `<begin_24h_time>`    | Raid begin time in 24hour format       |
| `<dir>`               | Cardinal direction from set location   |
| `<quick_move>`        | Quick move of the alerted pokemon      |
| `<charge_move>`       | Charge move of the alerted pokemon     |
| `<quick_id>`          | ID number of the quick move            |
| `<quick_damage>`      | Damage value of quick move             |
| `<quick_duration>`    | Duration value of quick move           |
| `<quick_dps>`         | Damage per second value of quick move  |
| `<quick_energy>`      | Energy of quick move                   |
| `<charge_id>`         | ID number of charge move               |
| `<charge_damage>`     |  Damage value of charge move           |
| `<charge_duration>`   | Duration value of charge move          |
| `<charge_dps>`        | Damage per second value of charge move | 
| `<charge_energy>`     | Energy of charge move                  |
| `<geofence>`          | Geofence name of where the alarm originated |
| `<gmaps>`             | Google Maps URL to pokemon location    |
| `<applemaps>`         | Apple Maps URL to pokemon location     |
*If no location has been set, dist will always return 0 (meters or yards)

## Reverse Location Text
The following text substitutions will only work if a Google Maps API Key with Geocoding API enabled has been provided to the PokeAlarm.

| Text             | Description                            |
|:---------------- |:---------------------------------------|
| `<street_num>`   | Street number of the alert location
| `<street>`       | Street name of the alert location
| `<address>`      | Address of the alert location, includes both street number and street name, in that order only
| `<postal>`       | Postal code of the alert location      |
| `<neighborhood>` | Neighborhood code of the alert location|
| `<sublocality>`  | Sublocality code of the alert location |
| `<city>`         | City code of the alert location        |
| `<county>`       | County code of the alert location      |
| `<state>`        | State code of the alert location       |
| `<country>`       | Country code of the alert location    |
The fields will return `None` if unable to derive a proper location

Each pokemon, pokestop, or gym will use up 1 point of your API quota, regardless of number of fields or alarms used.

## Distance Matrix Text
The following text substitutions will only work if a Google Maps API Key with Distance Matrix API enabled has been provided to the PokeAlarm.

| Text             | Description                            |
|:---------------- |:---------------------------------------|
| `<walk_dist>`    | Estimated walking distance to the alert location |
| `<walk_time>`    | Estimated walking time to alert location|

| Text             | Description                            |
|:---------------- |:---------------------------------------|
| `<bike_dist>`    | Estimated bike distance to the alert location |
| `<bike_time>`    | Estimated bike time to alert location|


| Text             | Description		                            |
|:---------------- |:-----------------------------------------------|
| `<drive_dist>`   | Estimated drive distance to the alert location |
| `<drive_time>`   | Estimated drive time to alert location			|

Each table represents 1 API quota used for all parameters per pokemon, pokestop, or gym regardless of number of fields or alarms specified. For example, `<walk_time>` and `<drive_time>` would require 2 points, but `<walk_time>` and `<walk_dist>` would only require 1 (per alert).

## Example: Slack

Below is an example for a single Slack alarm.

Let's say that a Dragonite spawns nearby.  You want PokeAlarm to post to your Slack **#general** channel with the format below:

> Dragonite (#149) at 830 5th Avenue 10065 (328m SW) - Available until 15:40:37 (14m 45s remaining)

>**Walking:** 328m SW, ~3 mins

>**Moves:** Dragon Breath / Dragon Claw

>**IVs:** 100% (15/15/15)

(Pretend that the above is single spaced - silly github.)

In other words, there is a Dragonite, pokemon number 149, at the given address, 328 meters southwest of your stated location when you launched `start_pokealarm.py` (assuming you ran with the `-l` argument and provided an address or coordinates).  It will be there until 17:40:37 (5:40pm), and you have 14 minutes and 45 seconds to catch it.

```json
{
	"alarms":[
		{
			"active": "True",
			"type":"slack",
			"api_key":"YOUR_SLACK_API_KEY",
			"startup_message":"False",
			"channel":"#general",
			"pokemon":{
				"channel":"#brooklyn",
				"username":"Pokemon",
				"title":"<pkmn> #<id> at <address> <postal>",
				"url":"<gmaps>",
				"body":"Available until <24h_time> (<time_left>). \n*Walking:* <walk_dist> <dir>, ~<walk_time> \nMoves: <quick_move> / <charge_move> \n**IVs:** <iv>% (<atk>/<def>/<sta>)",
				"map": { 
					"enabled":"True",
					"width":"330",
					"height":"250",
					"maptype":"roadmap",
					"zoom": "17"
				}
			},
			"pokestop":{
				"channel":"pokestops",
				"username":"Pokestop",
				"icon_url":"https://raw.githubusercontent.com/kvangent/PokeAlarm/master/icons/pokestop.png",
				"title":"New lure placed at <address> <city> <postal>",
				"url":"<gmaps>",
				"body":"expires at <24h_time> (<time_left>).",
				"map": { 
					"enabled":"True",
					"width":"330",
					"height":"250",
					"maptype":"roadmap",
					"zoom": "15"
				}
			},
			"gym":{
				"channel":"gyms",
				"username":"Gym",
				"icon_url":"https://raw.githubusercontent.com/kvangent/PokeAlarm/master/icons/gym_<team_id>.png",
				"title":"A Team <old_team> gym has fallen at <address> <city> <postal>",
				"url":"<gmaps>",
				"body": "It is now controlled by <new_team>.",
				"map": { 
					"enabled":"True",
					"width":"250",
					"height":"250",
					"maptype":"roadmap",
					"zoom": "13"
				}
			}
		}
	],
}
```
