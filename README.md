# PkmnShinyMap

Pokemon shiny list custom map to use with PoracleJS

Current files to put in your config/customMaps folder:
shinyPossible.json

Monster & Raid DTS
{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}

Quest DTS & Invasion DTS
Coming soon... Maybe

Only one custom map will be applicable for each Pokemon. If the Pokemon doesn't have any forms or all forms are available as shinies the customMap will pick up the first part of the DTS: "{{map 'shinyPossible' pokemonId}}" and the second part will be blank. And if the Pokemon has muliple forms and only some of them have the shiny version available the first part of the DTS will be blank and it will pick up the second part: "{{map 'shinyPossible' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}"

The list is configured to have a physical space in front of each symbol already, so don't leave any extra spaces in your DTS. For example it can follow straight on from name and it will look like the following:

DTS:
{{name}}{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}

Result:
Pikachu ✨

Big thank you to Jabes and petap0w for their help getting the DTS right.


I've also been working on some half shiny icons to use with PMSF and PoracleJS. They are forked from NilePlumb's base. Thank you NilePlumb.

Pokemon Home Style Half Shiny 128x128

iconurl:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/PMSF_Half_Shiny_128

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/PMSF_Half_Shiny_128/pokemon_icon_113_00.png


Pokemon Shuffle Style Half Shiny 128x128

iconurl:
https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/PMSF_Half_Shiny_128

Example:
https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/PMSF_Half_Shiny_128/pokemon_icon_113_00.png

If you would like to pull the half shiny image from my repo and the standard image from NilePlumb's repo when the shiny isn't available you can use the following in your DTS. This will mean your cache doesn't keep using the standard image after a new shiny is released and I update my repo.

```"thumbnail": {
"url": "{{#or (map 'shinyPossible' pokemonId) (map 'shinyPossible' (append (toFixed pokemonId) (append '_' (toFixed formId))))}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/PMSF_Half_Shiny_128/pokemon_icon_{{pad0 pokemonId}}_{{#if formId}}{{formId}}{{else}}00{{/if}}.png{{else}}https://raw.githubusercontent.com/nileplumb/PkmnHomeIcons/master/pmsf/pokemon_icon_{{pad0 pokemonId}}_{{#if formId}}{{formId}}{{else}}00{{/if}}.png{{/or}}"
}```
