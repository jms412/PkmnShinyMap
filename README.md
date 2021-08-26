# PkmnShinyMap

Pokemon shiny list custom map to use with PoracleJS

Current files to put in your config/customMaps folder:
shinyPossible.json

Monster & Raid DTS

```{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (concat pokemonId '_' formId)}}```

Quest DTS & Invasion DTS
Coming soon... Maybe

Only one custom map will be applicable for each Pokemon. If the Pokemon doesn't have any forms or all forms are available as shinies the customMap will pick up the first part of the DTS: "{{map 'shinyPossible' pokemonId}}" and the second part will be blank. And if the Pokemon has muliple forms and only some of them have the shiny version available the first part of the DTS will be blank and it will pick up the second part: "{{map 'shinyPossible' (concat pokemonId '_' formId)}}"

The list is configured to have a physical space in front of each symbol already, so don't leave any extra spaces in your DTS. For example it can follow straight on from name and it will look like the following:

Example DTS:

```{{name}}{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (concat pokemonId '_' formId)}}```

Result:
Pikachu ✨

Big thank you to Jabes and petap0w for their help getting the DTS right.


I've also been working on some half shiny icons to use with PMSF and PoracleJS. They are forked from NilePlumb's base. Thank you NilePlumb.


Pokemon Shuffle Style Half Shiny 128x128
URL:
https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/UICONS_Half_Shiny_128/

Example:
https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/UICONS_Half_Shiny_128/pokemon/113.png


Pokemon Home Style Half Shiny 512x512
URL:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny/

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny/pokemon/113.png


Pokemon Home Style Half Shiny 512x512 + Sparkles
URL:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/pokemon/113.png


Pokemon Home Style Half Shiny 128x128
URL:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_128/

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_128/pokemon/113.png


Pokemon Home Style Half Shiny 128x128 + Sparkles
URL:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles_128/

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles_128/pokemon/113.png


If you would like to pull the half shiny image from my repo and the standard image from a non-shiny version of my repo when the shiny isn't available you can use the following in your DTS. This will mean you don't cache a non-shiny version of the image before the shiny is released. This method goes against the design of what UICONS is meant to do with fallback, but it's the only solution I've come up with so far to avoid discord caching incorrect images (this issue doesn't effect normal image repos as they don't need to modify their icons as shinies are released).

```"thumbnail": {"url": "{{#or (map 'shinyPossible' pokemonId) (map 'shinyPossible' (concat pokemonId '_' formId))}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/pokemon/{{pokemonId}}{{#if evolution}}{{#compare evolution '!=' 0}}_e{{evolution}}{{/compare}}{{/if}}{{#if form}}{{#isnt formName 'Normal'}}{{#if formId}}_f{{formId}}{{/if}}{{/isnt}}{{/if}}.png{{else}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS/pokemon/{{pokemonId}}{{#if evolution}}{{#compare evolution '!=' 0}}_e{{evolution}}{{/compare}}{{/if}}{{#if form}}{{#isnt formName 'Normal'}}{{#if formId}}_f{{formId}}{{/if}}{{/isnt}}{{/if}}.png{{/or}}"}```
