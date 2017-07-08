## Patch History

* [Patch 3.2](#Patch-3.2)
* [Patch 3.1](#Patch-3.1)

## Patch 3.2 

For information about how to update from 3.1 see the [migration guide](PokeAlarm-Version-3.2-Quick-Start-Guide)

#### Raids
There's now support to handle raid event notifications.  You can get alarms for both upcoming raids (eggs) and started raids (hatched eggs).



##### Raid Filters
Filters now have a segment for what kind of raids to trigger alarms. See the updated filters.example.json for a full example.
    * The label `filter` is used to determine some common properties of the filter:
        * `min_level` -  minimum raid level as a number, inclusive
        * `max_level` - maximum raid level as a number, inclusive
        * `ignore_eggs` - If set to true, ignores any raid without a pokemon set. Boolean value (`True`/`False`).
    * The rest of the raid filter works exactly like the pokemon filter, one `default` field and a list of Pokemon.      

**Raid alarms** 

There are now two new alarm types: `raid` and `egg`. If the filter for raid is enabled, default formats for your alarm will be used unless otherwise specificed.
The wiki pages for different alarm services has been updated with examples for both eggs and raids. (See sidebar). 
* **Egg**: Message that is sent when a raid is first announced but we do not know the pokemon that will be in the raid.
* **Raid**: Message that is sent when a raid has started and the pokemon is revealed. 

**Dynamic Text Substitution**
 
There's new keywords for dynamic text substitution that are only available for raids
For all raids alarms : 
* `<raid_level>` - the level of the raid
* `<begin_24h_time>`, `<begin_12h_time>` - the start time for the raid in 24 hour or 12 hour format
 * `<begin_time_left>` - the amount of time left until raid begins

For raid messages some pokemon information is available: `<pkmn>`, `<pkmn_id>`, `<cp>` in addition to all the move messages:  `<quick_move>`, `<quick_id>`, `<quick_damage>`, `<quick_dps>`, `<quick_duration>`, `<quick_energy>`, `<charge_move>`, `<charge_id>`, `<charge_damage>`, `<charge_dps>`, `<charge_duration>`, `<charge_energy>`.

Do note that IV for raid pokemon is currently reported as 100%, and is therefore meaningless (real IV is random when catching)
  

## Patch 3.1

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
