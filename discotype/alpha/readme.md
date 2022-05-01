# General Charger Feed Specification - ⍺lpha

This ⍺lpha realase is first on. This one aims for Discovery based specification for dynamic feeds mainly for EVs. One feed can include multiple providers

### Legend

   `*` - is **REQUIRED**

   Double - a type as Number with Float. example - `48.15757`

## Discovery - `discovery.json`/`gcfs.json`

`$schema` - [https://gcfs.isithere.sk/discotype/alpha/discovery.schema.json](https://gcfs.isithere.sk/discotype/alpha/discovery.schema.json) `*`

`type` - [Feed:discovery](Feed:discovery) `*`

`data` **Object `*`**

   > `publisher` - **String**, link to this resource with the same directory `*`
   > 
   > `providers` - **String**, link to this resource with the same directory `*`
   > 
   > `chargers` - **String**, link to this resource with the same directory `*`

## Publisher - `publisher.json`

`$schema` - [https://gcfs.isithere.sk/discotype/alpha/publisher.schema.json](https://gcfs.isithere.sk/discotype/alpha/publisher.schema.json) `*`

`type` - [Feed:discovery:publisher](Feed:discovery:publisher) `*`

`data` **Object**

   > `$type` - [Feed:Publisher](Feed:Publisher) `*`
   >
   > `name` - String, name of publisher
   >
   > `url` - String, HTTP/S website of publisher
   >
   > `contact` **Array**

      > Mail begining with `mailto:`, **String**
      > 
      > telephone number begining with `tel:` with national +code, **String**
      > 
      > Or website with HTTP/S, **String**

## Providers - `providers.json`

`$schema` - [https://gcfs.isithere.sk/discotype/alpha/providers.schema.json](https://gcfs.isithere.sk/discotype/alpha/providers.schema.json) `*`

`type` - [`Feed:discovery:provider`](Feed:discovery:provider) `*`

`data` - **Array**

   > `$type` - [`Feed:Provider`](Feed:Provider) `*`
   >
   > `name` - **String**, General name of provider after public knows it
   >
   > `id` - **String**, if used thought out the feed of this provider `*`
   >
   > `url` - **String**, HTTP/S link to provider's website
   >
   > `contact` **Array**

      > Mail begining with `mailto:`, **String**
      > 
      > telephone number begining with `tel:` with national +code, **String**
      > 
      > Or website with HTTP/S, **String**

## Chargers - `chargers.json`

`$schema` - [https://gcfs.isithere.sk/discotype/alpha/chargers.schema.json](https://gcfs.isithere.sk/discotype/alpha/chargers.schema.json) `*`

`type` - `Feed:discovery:charger` `*`

`data`  **Array**

   > `$type` - `Feed:Charger` `*`
   >
   > `name` - A **String** of name of the charger, either name of street where charger is located or Point of interest (a shopping mall or station)
   >
   > `provider` - **String**, provider's id from [Feed:Provider](Feed:Provider) `*`
   >
   > `id` - **String**, static string needed to be used as same on every update `*`
   >
   > `gps` **Array `*`**

      > Longtitude in **Double**
      >
      > Latitude in **Double**

   > `plugs` **Array** - every plug no mater the type must be separate

      > `$type` - `Feed:Charger:Plug` `*`
      >
      > `type` - Type of charger in **string** as type1, type2, chademo, css, tesla, commando, schuko, j1772 `*`
      >
      > `voltage` - Voltage of plug in **Double/Number**
      >
      > `amperage` - Amperage of plug in **Double/Number**
      >
      > `available` - Availability of plug in **string** as available, unavailable, unknown

