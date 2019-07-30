# Oozou Android Developer Test
Hi there! This is the interview test instruction for Android Developer position at Oozou. Please read the guidance carefully. Best of luck!

## What you will have to do.
- You will be given a zip file which can be download from this link www.example.com .
- Open the project with Android Studio.
- Modify existing files or add new files to build an Android application according to the application description section.

**Note**

- Please write the code in a way that demonstrates your current set of skills.
- Please use design pattern and libraries that you think are the best. 
- You are free to do anything to the given project to achieve the application described in the application description section. You can even delete every file we provided and start everything from scratch by yourself.

**Optional**
- Using `git` to track your work history is strongly recommened.
- Having unit tests and UI tests are not mandatory, but you are highly encouraged to do so.
- Any improvements to the project are welcome such as making changes to UI, caching the data, or other improvements you want to add. 

## Application Desciption: Pokemon Info

This section describes the detail of the application that you will have to build.

### Objective

This application displays the list of Pokemons. The user can click on each item of the list to see the detail of each pokemon.

### Overview

![ezgif-5-882a372cf276](https://user-images.githubusercontent.com/19642082/61866786-0a595c00-af00-11e9-9225-8b4c044dd8ed.gif)

### Screens
This section describes the behavior and detail of each screen. We will discuss about data and api in detail in the next section. 

#### 1. Pokemon List Screen ####
Display paginated list from Pokemon List API(https://pokeapi.co/api/v2/pokemon). When clicking on each item in the list, the URL for fetching pokemon detail will be passed to Pokemon detail dialog, and the dialog will be shown.

![Screen Shot 2019-07-25 at 4 36 42 PM](https://user-images.githubusercontent.com/19642082/61863901-b13af980-aefa-11e9-8a83-f6bb221d6e23.png)

#### 2. Pokemon Detail Dialog ####
Modal style dialog for displaying pokemon detail. This dailog show when the item in Pokemon List screen is clicked. There are only 4 field display in this page `base_experience`, `height`, `name`, `weight`.

![Screen Shot 2019-07-25 at 4 41 51 PM](https://user-images.githubusercontent.com/19642082/61864176-29a1ba80-aefb-11e9-9269-07a6c21aa923.png)

### Data

The data in this application is fetch from PokéAPI(https://pokeapi.co)
There are only two endpoinst called in this application.

#### 1. Pokemon List API ####
https://pokeapi.co/api/v2/pokemon

Paginated list of Pokemon

Sample response
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

#### 2. Pokemon Detail ####
Use `url` field from item in `results` to get pokemon detail api url.

Please refer to one of the item in `results` of response of the pokemon list endpoint.
```
{  
    "name":"bulbasaur",
    "url":"https://pokeapi.co/api/v2/pokemon/1/"
}
```
Call https://pokeapi.co/api/v2/pokemon/1/ to get pokemon detail

Sample response: You only need to map these 4 fields to the model: `base_experience`, `height`, `name`, `weight`

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

## Implementation Guide 
You **don't** need to follow this guide strictly.

### Pokemon List Screen ###

#### 1. Set up RecyclerView in `PokemonListFragment.kt` ####
You don't need to create a layout for **Pokemon List Screen** by yourself. We've provided `pokemon_list_fragment.xml` as the layout of  **Pokemon List Screen**, and the layout for each item in `RecyclerView` is defined in `pokemon_view_holder.xml`. What left for you to do is create new files to get the `RecyclerView` ready for displaying data from API.

#### 2. Calling Api ####
Call this endpoint **https://pokeapi.co/api/v2/pokemon** to get paginated list of Pokemons. Use the fields; `count`, `next`, and `previous` to make the `RecyclerView` load and display the data in the pagination way.

#### 3. Passing URL to Pokemon Detail ####
Send Pokemon Detail URL from **Pokemon List Screen** to **Pokemon Detail** and use that URL to fetch pokemon detail data.

<img width="764" alt="Screen Shot 2019-07-25 at 4 57 05 PM" src="https://user-images.githubusercontent.com/19642082/61865404-5eaf0c80-aefd-11e9-8be7-ecc09804bf1a.png">

### Pokemon Detail ###

#### 1. Create layout XML file and other related files ####
For Pokemon detail screen, we haven't provided anything yet. Therefore, you will need to create an XML file and other related files by yourself. You can decide the dimension of the element in the layout base on your judgement.

#### 2. Calling Api ####
Call the URL passing from **Pokemon List Screen** to get the pokemon detail data. Then display the data on the UI.

## Submission

Please zip the project and send it to this email example@mail.com 

