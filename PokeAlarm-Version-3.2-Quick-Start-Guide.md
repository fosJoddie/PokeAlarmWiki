Updated: 8 July 2017

## Purpose
* This document is intended to quickly provide PokeAlarm users with info to get started. It is not intended to replace the full wiki.

## Overview

* [Before you begin](#before-you-begin)
* [Notes](#notes)
* [Introduction](#introduction)
  * [Upgrading from 3.1](#upgrading-from-3.1)
  * [Filters](#Updating Filter Configuration)
  * [Alarms](#alarms)

## Before you begin
* Version 3.2 is now in the master branch.  Read the patch notes if you are upgrading from version 3.
* Features are constantly being added. Always visit the #announcements discord channel for udpates
* Contact us in the [#troubleshooting discord channel](https://discordapp.com/channels/215181169761714177/218822834225545216) or open a ticket on our [github page](https://github.com/kvangent/PokeAlarm/issues)

## Notes

* 
* Remember - you only need to edit the JSON, `geofence.txt`, and `config.ini` files.  Other modifications to the code are not supported!!!
* PyCharm is a great IDE to manage your JSON and config files.  The EDU edition is free: https://www.jetbrains.com/pycharm-edu . This will will help you avoid those pesky formatting errors.
* Alternatively, use an online JSON editor like http://www.jsoneditoronline.org which will yell at you if the json is incorrectly formatted

## Introduction
PokeAlarm v3.2 introduces support for 
* Raid alarms
* New Dynamic Text Substitution for pokemon CP, level and more gym information

## Upgrading from 3.1

1. Update PokeAlarm  `git pull`
2. Make sure requirements are in oder `pip install -r requirements.txt`
3. Change the configuration with the new raid filters - see the information below
4. (Optional) modify your `alarms.json` to customize egg and raid messages.

### Updating Filter Configuration
To use 3.2, existing filters.json file must be updated with the new section describing raids in filters.example.json. Either copy the new section into your existing configuration(s) or start from scratch by making a copy of the example file.

The filter following filters are available:

- **min_level**:  An integer describing the minimum level of the raid you want to send alarms about. Raids with a lower level will not be sent
- **max_level**: An integer describing he maximum level of the raid you want to send alarms about. Raids with a higher level will not be sent
- **ignore_eggs**: A boolean describing whether or not alarms should be sent if the raid does not yet have an active pokemon battle.

The default pokemon filter  is kept the same way as pokemon filters for simplicity, but some values like iv and size will not have a meaningful use. Raid pokemon will only report CP and have perfect IVs. 

See the pokemon filter documentation (<https://github.com/kvangent/PokeAlarm/wiki/Filters> ) for more information.

Example raids filter:
```json
"raids":{
        "enabled":"True",
        "filters": {
            "min_level": "1",
            "max_level": "5",
            "ignore_eggs": "False"
        },
        "default": {
            "min_dist":"0", "max_dist":"inf", "min_cp": "0", "max_cp": "999999", "min_iv":"0", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "gender": null, "form": null, "ignore_missing": "False"
        },
        "Bulbasaur": "True",
        "Ivysaur": "True",
        "Venusaur": "True",
        "Charmander": "True",
        "Charmeleon": "True",
        "Charizard":"True",
        "Squirtle":"True",
        "Wartortle":"True",
        "Blastoise":"True",
        "Caterpie":"True",
        "Metapod":"True",
        "Butterfree":"True",
        "Weedle":"True",
        "Kakuna":"True",
        "Beedrill":"True",
        "Pidgey":"True",
        "Pidgeotto":"True",
        "Pidgeot":"True",
        "Rattata":"True",
        "Raticate":"True",
        "Spearow":"True",
        "Fearow":"True",
        "Ekans":"True",
        "Arbok":"True",
        "Pikachu":"True",
        "Raichu":"True",
        "Sandshrew":"True",
        "Sandslash":"True",
        "Nidoran?":"True",
        "Nidorina":"True",
        "Nidoqueen":"True",
        "Nidoran?":"True",
        "Nidorino":"True",
        "Nidoking":"True",
        "Clefairy":"True",
        "Clefable":"True",
        "Vulpix":"True",
        "Ninetales":"True",
        "Jigglypuff":"True",
        "Wigglytuff":"True",
        "Zubat":"True",
        "Golbat":"True",
        "Oddish":"True",
        "Gloom":"True",
        "Vileplume":"True",
        "Paras":"True",
        "Parasect":"True",
        "Venonat":"True",
        "Venomoth":"True",
        "Diglett":"True",
        "Dugtrio":"True",
        "Meowth":"True",
        "Persian":"True",
        "Psyduck":"True",
        "Golduck":"True",
        "Mankey":"True",
        "Primeape":"True",
        "Growlithe":"True",
        "Arcanine":"True",
        "Poliwag":"True",
        "Poliwhirl":"True",
        "Poliwrath":"True",
        "Abra":"True",
        "Kadabra":"True",
        "Alakazam":"True",
        "Machop":"True",
        "Machoke":"True",
        "Machamp":"True",
        "Bellsprout":"True",
        "Weepinbell":"True",
        "Victreebel":"True",
        "Tentacool":"True",
        "Tentacruel":"True",
        "Geodude":"True",
        "Graveler":"True",
        "Golem":"True",
        "Ponyta":"True",
        "Rapidash":"True",
        "Slowpoke":"True",
        "Slowbro":"True",
        "Magnemite":"True",
        "Magneton":"True",
        "Farfetch'd":"True",
        "Doduo":"True",
        "Dodrio":"True",
        "Seel":"True",
        "Dewgong":"True",
        "Grimer":"True",
        "Muk":"True",
        "Shellder":"True",
        "Cloyster":"True",
        "Gastly":"True",
        "Haunter":"True",
        "Gengar":"True",
        "Onix":"True",
        "Drowzee":"True",
        "Hypno":"True",
        "Krabby":"True",
        "Kingler":"True",
        "Voltorb":"True",
        "Electrode":"True",
        "Exeggcute":"True",
        "Exeggutor":"True",
        "Cubone":"True",
        "Marowak":"True",
        "Hitmonlee":"True",
        "Hitmonchan":"True",
        "Lickitung":"True",
        "Koffing":"True",
        "Weezing":"True",
        "Rhyhorn":"True",
        "Rhydon":"True",
        "Chansey":"True",
        "Tangela":"True",
        "Kangaskhan":"True",
        "Horsea":"True",
        "Seadra":"True",
        "Goldeen":"True",
        "Seaking":"True",
        "Staryu":"True",
        "Starmie":"True",
        "Mr. Mime":"True",
        "Scyther":"True",
        "Jynx":"True",
        "Electabuzz":"True",
        "Magmar":"True",
        "Pinsir":"True",
        "Tauros":"True",
        "Magikarp":"True",
        "Gyarados":"True",
        "Lapras":"True",
        "Ditto":"True",
        "Eevee":"True",
        "Vaporeon":"True",
        "Jolteon":"True",
        "Flareon":"True",
        "Porygon":"True",
        "Omanyte":"True",
        "Omastar":"True",
        "Kabuto":"True",
        "Kabutops":"True",
        "Aerodactyl":"True",
        "Snorlax":"True",
        "Articuno":"True",
        "Zapdos":"True",
        "Moltres":"True",
        "Dratini":"True",
        "Dragonair":"True",
        "Dragonite":"True",
        "Mewtwo":"True",
        "Mew":"True",
        "Chikorita":"True",
        "Bayleef":"True",
        "Meganium":"True",
        "Cyndaquil":"True",
        "Quilava":"True",
        "Typhlosion":"True",
        "Totodile":"True",
        "Croconaw":"True",
        "Feraligatr":"True",
        "Sentret":"True",
        "Furret":"True",
        "Hoothoot":"True",
        "Noctowl":"True",
        "Ledyba":"True",
        "Ledian":"True",
        "Spinarak":"True",
        "Ariados":"True",
        "Crobat":"True",
        "Chinchou":"True",
        "Lanturn":"True",
        "Pichu":"True",
        "Cleffa":"True",
        "Igglybuff":"True",
        "Togepi":"True",
        "Togetic":"True",
        "Natu":"True",
        "Xatu":"True",
        "Mareep":"True",
        "Flaaffy":"True",
        "Ampharos":"True",
        "Bellossom":"True",
        "Marill":"True",
        "Azumarill":"True",
        "Sudowoodo":"True",
        "Politoed":"True",
        "Hoppip":"True",
        "Skiploom":"True",
        "Jumpluff":"True",
        "Aipom":"True",
        "Sunkern":"True",
        "Sunflora":"True",
        "Yanma":"True",
        "Wooper":"True",
        "Quagsire":"True",
        "Espeon":"True",
        "Umbreon":"True",
        "Murkrow":"True",
        "Slowking":"True",
        "Misdreavus":"True",
        "Unown":"True",
        "Wobbuffet":"True",
        "Girafarig":"True",
        "Pineco":"True",
        "Forretress":"True",
        "Dunsparce":"True",
        "Gligar":"True",
        "Steelix":"True",
        "Snubbull":"True",
        "Granbull":"True",
        "Qwilfish":"True",
        "Scizor":"True",
        "Shuckle":"True",
        "Heracross":"True",
        "Sneasel":"True",
        "Teddiursa":"True",
        "Ursaring":"True",
        "Slugma":"True",
        "Magcargo":"True",
        "Swinub":"True",
        "Piloswine":"True",
        "Corsola":"True",
        "Remoraid":"True",
        "Octillery":"True",
        "Delibird":"True",
        "Mantine":"True",
        "Skarmory":"True",
        "Houndour":"True",
        "Houndoom":"True",
        "Kingdra":"True",
        "Phanpy":"True",
        "Donphan":"True",
        "Porygon2":"True",
        "Stantler":"True",
        "Smeargle":"True",
        "Tyrogue":"True",
        "Hitmontop":"True",
        "Smoochum":"True",
        "Elekid":"True",
        "Magby":"True",
        "Miltank":"True",
        "Blissey":"True",
        "Raikou":"True",
        "Entei":"True",
        "Suicune":"True",
        "Larvitar":"True",
        "Pupitar":"True",
        "Tyranitar":"True",
        "Lugia":"True",
        "Ho-Oh":"True",
        "Celebi":"True"
    }
```

## Alarms
if you want custom alarm messages you can use dynamic text substitution as with existing alarms. There are two new messages to set up:
- **egg** - Alarm when a raid battle is announced - only contains raid level and start/end times but no pokemon
- **raid** - Alarm when a pokemon battle has started in a gym. Contains raid level, start and end times and pokemon information

For raid messages you can use the same keywords as pokemon alarms, including cp and moves.

Additionally there are a few new keywords:
- <raid_level>:  Puts in the level of the raid
- <begin_24h_time>, <begin_12h_time>, <begin_time_left> the time for the raid start in 24 hour, 12 hour and time left until start.

The following is the default alarms for egg and raid in Discord:

### Raid
```json
"raid": {
    "username": "Raid",
    "content": "",
    "icon_url": "https://raw.githubusercontent.com/kvangent/PokeAlarm/master/icons/<pkmn_id>.png",
    "avatar_url": "https://raw.githubusercontent.com/fosJoddie/PokeAlarm/raids/icons/egg_<raid_level>.png",
    "title": "Level <raid_level> Raid is available against <pkmn>!",
    "url": "<gmaps>",
    "body": "The raid is available until <24h_time> (<time_left>)."
}
```

### Egg
```json
"egg": {
    "username": "Egg",
    "content": "",
    "icon_url": "https://raw.githubusercontent.com/fosJoddie/PokeAlarm/raids/icons/egg_<raid_level>.png",
    "avatar_url": "https://raw.githubusercontent.com/fosJoddie/PokeAlarm/raids/icons/egg_<raid_level>.png",
    "title": "Raid is incoming!",
    "url": "<gmaps>",
    "body": "A level <raid_level> raid will hatch <begin_24h_time> (<begin_time_left>)."
}
```