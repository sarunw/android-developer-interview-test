# Oozou Android Developer Test
Hi there! This is the interview test instruction for Android Developer position at Oozou. Please read the guidance carefully. Best of luck!

## What you will have to do.
- You will be given a zip file which can be download from this link www.example.com
- Open the project with Android Studio.
- Modify existing files or add new files to build an Android application according to the application description section.

**Note**

- Please write the code in a way that demonstrates your current set of skills
- Please use design pattern and libraries that you think are the best. 
- You are free to do anything to the given project to achieve the application described in the application description section. You can even delete every file we provided and start everything from scratch by yourself.

**Optional**

- Having unit tests and UI tests are not mandatory, but you are highly encouraged to do so.
- Any improvements to the project are welcome such as making changes to UI, caching the data, or other improvements you want to add. 

## Application Desciption: Pokemon Info

This section describes the application that you will have to build.

### Objective

This application displays the list of Pokemons. The user can click on each item of the list to see the detail of each pokemon.

### Overview

![ezgif-5-882a372cf276](https://user-images.githubusercontent.com/19642082/61866786-0a595c00-af00-11e9-9225-8b4c044dd8ed.gif)

### Screens
&nbsp;&nbsp;&nbsp;&nbsp;We will discuss about data and api in detail in the next section. 
1. **Pokemon List Screen**

&nbsp;&nbsp;&nbsp;&nbsp;Display paginated list from Pokemon List API(https://pokeapi.co/api/v2/pokemon).

![Screen Shot 2019-07-25 at 4 36 42 PM](https://user-images.githubusercontent.com/19642082/61863901-b13af980-aefa-11e9-8a83-f6bb221d6e23.png)

2. **Pokemon Detail Dialog**

&nbsp;&nbsp;&nbsp;&nbsp;Modal style dialog for displaying pokemon detail. This dailog show when the item in Pokemon List screen is clicked. There are only 4 field display in this page `base_experience`, `height`, `name`, `weight`.

![Screen Shot 2019-07-25 at 4 41 51 PM](https://user-images.githubusercontent.com/19642082/61864176-29a1ba80-aefb-11e9-9269-07a6c21aa923.png)

### Data

The data in this application is fetch from PokéAPI(https://pokeapi.co)
There are only two endpoinst called in this application.

1. **Pokemon List API** : https://pokeapi.co/api/v2/pokemon

&nbsp;&nbsp;&nbsp;&nbsp;Paginated list of Pokemon

&nbsp;&nbsp;&nbsp;&nbsp;Sample response

``` {  
   "count":964,
   "next":"https://pokeapi.co/api/v2/pokemon?offset=20&limit=20",
   "previous":null,
   "results":[  
      {  
         "name":"bulbasaur",
         "url":"https://pokeapi.co/api/v2/pokemon/1/"
      },
      {  
         "name":"ivysaur",
         "url":"https://pokeapi.co/api/v2/pokemon/2/"
      },
      {  
         "name":"venusaur",
         "url":"https://pokeapi.co/api/v2/pokemon/3/"
      },
      {  
         "name":"charmander",
         "url":"https://pokeapi.co/api/v2/pokemon/4/"
      },
      {  
         "name":"charmeleon",
         "url":"https://pokeapi.co/api/v2/pokemon/5/"
      }
   ]
}
```

2. **Pokemon Detail**: Use `url` field from item in `results` to get pokemon detail api url.

&nbsp;&nbsp;&nbsp;&nbsp;Please refer to sample below.
```
{  
    "name":"bulbasaur",
    "url":"https://pokeapi.co/api/v2/pokemon/1/"
}
```
&nbsp;&nbsp;&nbsp;&nbsp;Call https://pokeapi.co/api/v2/pokemon/1/ to get pokemon detail

&nbsp;&nbsp;&nbsp;&nbsp;Sample response: You only need to map these 4 fields to the model: `base_experience`, `height`, `name`, `weight`

``` 
{  
   "abilities":[...],
   "base_experience":64,
   "forms":[...],
   "game_indices":[...],
   "height":7,
   "held_items":[...],
   "id":1,
   "is_default":true,
   "location_area_encounters":"https://pokeapi.co/api/v2/pokemon/1/encounters",
   "moves":[...],
   "name":"bulbasaur",
   "order":1,
   "species":{...},
   "sprites":{...},
   "stats":[...],
   "types":[...],
   "weight":69
}
```

### Further Implementation Guide

&nbsp;&nbsp;&nbsp;&nbsp;Send Pokemon Detail url from Pokemon List Screen to Pokemon Detail dialog and use that url to fetch pokemon detail data.

<img width="764" alt="Screen Shot 2019-07-25 at 4 57 05 PM" src="https://user-images.githubusercontent.com/19642082/61865404-5eaf0c80-aefd-11e9-8be7-ecc09804bf1a.png">
