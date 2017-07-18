## Patch History

* [Patch 3.1](#Patch-3.1)
* [Patch 3.2](#Patch_3.2)

### Patch 3.2 --------------------------------------------------------------

#### Filters
* **Pokemon**
    * Pokemon can now be filtered by their form_id (example": `"form": [0, 1, 2]`)
    * Pokemon can now be filtered by their gender (example": `"gender": ["male", "female"`)
* **Egg**
    * "Egg" section is now added to the filters.json
    * `'enabled'` allows incoming raid alerts to be toggled on or off
    * `'min_level'` and `'max_level'` are used to limit the levels of incoming raids to alert on

* **Raids**
    * "Raids" section is now added to the filters.json
    * `'enabled'` allows raid alerts to be toggled on or off
    * `'default'` allows setting default settings for filters, and has the same options as pokemon filters do
    *  Filters for pokemon raids can be set similar to the "pokemon" section, with the `"name": {}` scheme

#### Dynamic Text Substitutions
* **General**
    * Added `'applemaps'` to most alerts for AppleMaps link for iOS users
    * Time DTS now switch to ##h##m format when longer than one hour
* **Pokemon**
    * Added support for the following subsitutions: `'cp', 'form', 'form_id', 'level'`
    * Added `'big_karp'` that displays 'big' on big magikarp and `'tiny_rat'` that displays 'tiny' on small rattata 
* **Egg**
    * "Egg" alerts have the following substitutions: `'type', 'id', 'raid_level', 'raid_end', 'raid_being', 'lat', 'lng'`
* **Raid**
    * "Raid" alerts have the following substitutions: `'type', 'id', 'pkmn_id', 'cp', 'quick_id', 'quick_damage', 'quick_dps', 'quick_duration', 'quick_energy', 'charge_id', 'charge_damage', 'charge_dps', 'charge_duration', 'charge_energy', 'raid_level', 'raid_end', 'raid_begin' 'lat', 'lng'`
* **Gyms**
    * Added the following 'Gym Leader' substitutions: `'old_team_id', 'new_team_leader', 'old_team_leader'`
    
#### Alarms
* **Twitter**
    * Twitter now automatically truncates to 140 characters - it will preserve <gmaps> links if added to the end
* **Discord**
    * Discord usernames now automatically truncates usernames to 32 characters
    * Added `'avatar_url'` to change the avatar of the post
    * Added `content` field that posts a message before the embed, allows for taging by user or roll
    * Added `'disable_embed'` that disables the discord embeds when set to `true`
    
    
### Patch_3.1 --------------------------------------------------------------

#### Filters
* **Multifilters** - Each filter can now be one of the following:
     * `'True'` for all defaults, `'False'` for entirely disabled
     * A single filter in a json object (Ex: `{ "min_iv":"0",  "max_iv" : "0" ... }`)
     * Multiple filters inside an array: `[ {"min_iv":"0", "max_iv":"25" }, {"min_iv":"75", "max_iv":"100"} ] `

     
* **Pokemon**
    * All default filter parameters are now encapsulated in a single filter under the label `default`
     * `size` requires an array of valid sizes from the following: `['tiny', 'small', 'normal', 'large', 'big']`
     * `move_1` and `move_2` are now `quick_move` and `charge_move`
     * `size`, `quick_move`, `charge_move`, `moveset` filter parameters will accept any value when set to `null`

* **Pokestops**
    * Now only two fields: `enabled` and `filters`
    * `filters` supports the Multifilter format with `min_dist` and `max_dist` fields
    
* **Gym**
    * Now only three fields `enabled`, `ignore_neutral`, and `filters`
    * `filters` supports multifilters with the following fields:
        * `"from_team` - Array of valid previous team names
        * `to_team` - Array of valid current team names
        * `min_dist` and `max_dist` working as before
    
#### Dynamic Text Substitution
* `<geofence>` added - the name of the first geofence in which the notifcation is in
* `<size>` now list either `'tiny'`, `'small'`, `'normal'`, `'large'`, or `'big'`
* Quick moves now use the following:  `<quick_move>`, `<quick_id>`, `<quick_damage>`, `<quick_dps>`, `<quick_duration>`, `<quick_energy>`
* Charges moves now use the following: `<charge_move>`, `<charge_id>`, `<charge_damage>`, `<charge_dps>`, `<charge_duration>`, `<charge_energy>`
    
#### Alarms
* All Services
    * `startup_list` is officially gone
* Boxcar
    * No longer supported
* Discord
    * `api_key` renamed to `webhook_url`
    * Will now retry if webhook was not received correctly
    * New optional alarm and alert level field: `map`
        * `enabled` - True of False to enabled/disabled map
        * Added other static map parameters
* Slack
    * `channel` parameter is now required at the Alarm level
        * Slack will no longer default to general if the correct channel cannot be found
        * Slack will still default to the Alarm level channel over the Alert level channel is not found (so everyone can still use `<pkmn>`!)
* Pushover
    * No longer supported
