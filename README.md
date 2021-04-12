# PkmnShinyMap

Pokemon shiny list custom map to use with PoracleJS

Current files to put in your config/customMaps folder:
shinyPossibleForms.json
shinyPossibleWild.json
shinyPossibleRaid.json

Monster DTS
{{map 'shinyPossibleWild' pokemonId}}{{map 'shinyPossibleForms' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}

Raid DTS
{{map 'shinyPossibleRaid' pokemonId}}{{map 'shinyPossibleForms' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}

Quest DTS & Invasion DTS
Coming soon... Maybe

Only one custom map will be applicable for each Pokemon. If the Pokemon doesn't have any forms or all forms are available as shinies the customMap will pick up the first part of the DTS: "{{map 'shinyPossibleWild' pokemonId}}" and the second part will be blank. And if the Pokemon has muliple forms and only some of them have the shiny version available the first part of the DTS will be blank and it will pick up the second part: "{{map 'shinyPossibleForms' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}"

The list is configured to have a physical space in front of each symbol already, so don't leave any extra spaces in your DTS. For example it can follow straight on from name and it will look like the following:

DTS:
{{name}}{{map 'shinyPossibleWild' pokemonId}}{{map 'shinyPossibleForms' (append (toFixed pokemonId) (append '_' (toFixed formId)))}}

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
