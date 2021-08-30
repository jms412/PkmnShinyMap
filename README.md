# PkmnShinyMap

Pokemon shiny list custom map to use with PoracleJS


**New Method (August 2021):**

Poracle will now load shinyPossible.json without it needing to be copied into the CustomMaps directory. Thank you Jabes for making this possible.

**Monster, Raid & Quest DTS**

**Option 1:** `{{shinyPossibleEmoji}}` - This will use the default sparkles emoji, but can be modified in emoji.json

**Option 2:** `{{#if shinyPossible}} ✨{{/if}}` - You can replace this emoji with any other text or emoji

**Example DTS:**

`{{name}}{{#if shinyPossible}} ✨{{/if}}`

**Result:**
Pikachu ✨

Web:

![Screen Shot 2021-08-27 at 11 03 15 am 2](https://user-images.githubusercontent.com/80012316/131055902-f9ffa902-70d4-42ce-a148-5d470eecf8f2.png)

iOS:

![image0](https://user-images.githubusercontent.com/80012316/131055913-a08f8dbb-210f-4e50-8af5-0feb020750b1.jpeg)


You might also want to check out my half shiny icons to use with PMSF and PoracleJS. They are forked from NilePlumb's base. Thank you NilePlumb.


**Pokemon Shuffle Style Half Shiny 128x128**

URL: `https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/UICONS_Half_Shiny_128/`

Example:
https://raw.githubusercontent.com/jms412/PkmnShuffleMap/master/UICONS_Half_Shiny_128/pokemon/113.png

![113](https://user-images.githubusercontent.com/80012316/131056206-a6799bae-590b-49fb-8347-a206d352cc30.png)


**Pokemon Home Style Half Shiny 512x512**

URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny/`

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny/pokemon/113.png

![113](https://user-images.githubusercontent.com/80012316/131055587-3e800fba-fd4f-488b-a7c0-5ed31374e5a7.png)


**Pokemon Home Style Half Shiny 512x512 + Sparkles**

URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/`

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/pokemon/113.png

![113](https://user-images.githubusercontent.com/80012316/131055566-30e2905b-d213-47db-896b-3a08a89b6f19.png)


**Pokemon Home Style Half Shiny 128x128**

URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_128/`

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_128/pokemon/113.png

![113](https://user-images.githubusercontent.com/80012316/131055540-8e5795c3-b30d-493b-83ee-6551b233fd80.png)


**Pokemon Home Style Half Shiny 128x128 + Sparkles**

URL: `https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles_128/`

Example:
https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles_128/pokemon/113.png

![113](https://user-images.githubusercontent.com/80012316/131055504-a42f89dc-7af1-4bf9-bb64-df6ab5b28556.png)


**Coming Soon: Pokemon Shuffle Style Half Shiny 256x256**

![113](https://user-images.githubusercontent.com/80012316/131269262-ceb2f01a-593f-469d-9888-ce5311fd6fd9.png)


**Coming Soon: Pokemon Shuffle Style Half Shiny 256x256 + Sparkles**

![113](https://user-images.githubusercontent.com/80012316/131269253-3679bd25-8830-4b50-9536-0334297d52d5.png)





**Old Method (For Reference Only):**

Current files to put in your config/customMaps folder:
shinyPossible.json

**Monster & Raid DTS**

`{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (concat pokemonId '_' formId)}}`

Only one custom map will be applicable for each Pokemon. If the Pokemon doesn't have any forms or all forms are available as shinies the customMap will pick up the first part of the DTS: `{{map 'shinyPossible' pokemonId}}` and the second part will be blank. And if the Pokemon has muliple forms and only some of them have the shiny version available the first part of the DTS will be blank and it will pick up the second part: `{{map 'shinyPossible' (concat pokemonId '_' formId)}}`

The list is configured to have a physical space in front of each symbol already, so don't leave any extra spaces in your DTS. For example it can follow straight on from name and it will look like the following:

**Example DTS:**

`{{name}}{{map 'shinyPossible' pokemonId}}{{map 'shinyPossible' (concat pokemonId '_' formId)}}`

**Result:**
Pikachu ✨

If you would like to pull the half shiny image from my repo and the standard image from a non-shiny version of my repo when the shiny isn't available you can use the following in your DTS. This will mean you don't cache a non-shiny version of the image before the shiny is released. This method goes against the design of what UICONS is meant to do with fallback, but it's the only solution I've come up with so far to avoid discord caching incorrect images (this issue doesn't effect normal image repos as they don't need to modify their icons as shinies are released).

```"thumbnail": {"url": "{{#or (map 'shinyPossible' pokemonId) (map 'shinyPossible' (concat pokemonId '_' formId))}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS_Half_Shiny_Sparkles/pokemon/{{pokemonId}}{{#if evolution}}{{#compare evolution '!=' 0}}_e{{evolution}}{{/compare}}{{/if}}{{#if form}}{{#isnt formName 'Normal'}}{{#if formId}}_f{{formId}}{{/if}}{{/isnt}}{{/if}}.png{{else}}https://raw.githubusercontent.com/jms412/PkmnHomeIcons/master/UICONS/pokemon/{{pokemonId}}{{#if evolution}}{{#compare evolution '!=' 0}}_e{{evolution}}{{/compare}}{{/if}}{{#if form}}{{#isnt formName 'Normal'}}{{#if formId}}_f{{formId}}{{/if}}{{/isnt}}{{/if}}.png{{/or}}"}```
