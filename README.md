# PkmnShinyMap

Pokemon shiny list custom map to use with PoracleJS


**New Method (August 2021):**<br />
Poracle will now load shinyPossible.json without it needing to be copied into the CustomMaps directory. Thank you Jabes for making this possible.

**Monster, Raid & Quest DTS**<br />
**Option 1:** `{{shinyPossibleEmoji}}` - This will use the default sparkles emoji, but can be modified in emoji.json<br />
**Option 2:** `{{#if shinyPossible}} ✨{{/if}}` - You can replace this emoji with any other text or emoji


**Exceptions:**<br />
These Pokemon had their shiny version released for a limited time, depending on the length of the event I may add and remove them, otherwise I may just wait for their permanent release before including them.

Meltan - Fifth Anniversary Event (July 2021 - Also Feb 2019 & Nov 2020)<br />
Unown G, O - Go Fest 2020 (July 2020)<br />
Unown A, L, R, T, U - Enigma Week (Aug 2020)<br />
Unown C - City Spotlight Event (Nov 2020)<br />
Celebi - Special Research - Secrets Of The Jungle Event (Dec 2020)<br />
Mew - Special Research - Kanto Tour (Feb 2021)<br />
Arcanine - Season Of Legends (March 2021 - May 2021)<br />
Smeargle - Pokemon Snap Celebration (April 2021)<br />
Unown F - Go Fest 2021 (July 2021)<br />
Unown U - Ultra Unlock 2021 (Aug 2021)<br />
Butterfree Costume - Fashion Week 2021 (Sep 2021)<br />
Kirlia Costume - Fashion Week 2021 (Sep 2021)<br />


**Example DTS:**<br />
`{{name}}{{#if shinyPossible}} ✨{{/if}}`

**Result:**<br />
Pikachu ✨

Web:<br />
![Screen Shot 2021-08-27 at 11 03 15 am 2](https://user-images.githubusercontent.com/80012316/131055902-f9ffa902-70d4-42ce-a148-5d470eecf8f2.png)

iOS:<br />
![image0](https://user-images.githubusercontent.com/80012316/131055913-a08f8dbb-210f-4e50-8af5-0feb020750b1.jpeg)


You might also want to check out my half shiny icons to use with PMSF and PoracleJS. They are forked from NilePlumb's base. Thank you NilePlumb.


**Pokemon Home Style Half Shiny 512x512**<br />
URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny/`<br />
Example:<br />
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny/pokemon/113.png<br />
![113](https://user-images.githubusercontent.com/80012316/131055587-3e800fba-fd4f-488b-a7c0-5ed31374e5a7.png)<br />

**Pokemon Home Style Half Shiny 512x512 + Sparkles**<br />
URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/`<br />
Example:<br />
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/pokemon/113.png<br />
![113](https://user-images.githubusercontent.com/80012316/131055566-30e2905b-d213-47db-896b-3a08a89b6f19.png)<br />

**Pokemon Home Style Half Shiny 128x128**<br />
URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_128/`<br />
Example:<br />
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_128/pokemon/113.png<br />
![113](https://user-images.githubusercontent.com/80012316/131055540-8e5795c3-b30d-493b-83ee-6551b233fd80.png)<br />

**Pokemon Home Style Half Shiny 128x128 + Sparkles**<br />
URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles_128/`<br />
Example:<br />
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles_128/pokemon/113.png<br />
![113](https://user-images.githubusercontent.com/80012316/131055504-a42f89dc-7af1-4bf9-bb64-df6ab5b28556.png)<br />

**Pokemon Shuffle Style Half Shiny 256x256**<br />
URL: `https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/UICONS_Half_Shiny_256`<br />
Example:<br />
![113](https://user-images.githubusercontent.com/80012316/131269262-ceb2f01a-593f-469d-9888-ce5311fd6fd9.png)<br />

**Pokemon Shuffle Style Half Shiny 256x256 + Sparkles**<br />
URL: `https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/UICONS_Half_Shiny_Sparkles_256`<br />
Example:<br />
![113_s](https://user-images.githubusercontent.com/80012316/133961530-8f2b6d28-c97f-465a-b9e5-3454ce318498.png)<br />


**Old Method (For Reference Only):**<br />
Current files to put in your config/customMaps folder:
shinyPossible.json

**Monster & Raid DTS**<br />
`{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (concat pokemonId '_' formId)}}`

Only one custom map will be applicable for each Pokemon. If the Pokemon doesn't have any forms or all forms are available as shinies the customMap will pick up the first part of the DTS: `{{map 'shinyPossible' pokemonId}}` and the second part will be blank. And if the Pokemon has muliple forms and only some of them have the shiny version available the first part of the DTS will be blank and it will pick up the second part: `{{map 'shinyPossible' (concat pokemonId '_' formId)}}`

The list is configured to have a physical space in front of each symbol already, so don't leave any extra spaces in your DTS. For example it can follow straight on from name and it will look like the following:

**Example DTS:**<br />
`{{name}}{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (concat pokemonId '_' formId)}}`

**Result:**<br />
Pikachu ✨

If you would like to pull the half shiny image from my repo and the standard image from a non-shiny version of my repo when the shiny isn't available you can use the following in your DTS. This will mean you don't cache a non-shiny version of the image before the shiny is released. This method goes against the design of what UICONS is meant to do with fallback, but it's the only solution I've come up with so far to avoid discord caching incorrect images (this issue doesn't effect normal image repos as they don't need to modify their icons as shinies are released).

```"thumbnail": {"url": "{{#or (map 'shinyPossible' pokemonId) (map 'shinyPossible' (concat pokemonId '_' formId))}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/pokemon/{{pokemonId}}{{#if evolution}}{{#compare evolution '!=' 0}}_e{{evolution}}{{/compare}}{{/if}}{{#if form}}{{#isnt formName 'Normal'}}{{#if formId}}_f{{formId}}{{/if}}{{/isnt}}{{/if}}.png{{else}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS/pokemon/{{pokemonId}}{{#if evolution}}{{#compare evolution '!=' 0}}_e{{evolution}}{{/compare}}{{/if}}{{#if form}}{{#isnt formName 'Normal'}}{{#if formId}}_f{{formId}}{{/if}}{{/isnt}}{{/if}}.png{{/or}}"}```
