# Upland Public API Documentation

> Complete reference for Upland Web API endpoints, parameters, and representative JSON responses based on network inspection and reverse-engineering.  
> **Base URL:** `https://api.prod.upland.me`

Made with AI - errors may exist. 
---

## Table of Contents

1. [Authentication](#authentication)
2. [User & Profiles](#user--profiles)
   - [Get User Profile](#get-user-profile)
   - [Get User Properties](#get-user-properties)
   - [Get User Structures](#get-user-structures)
   - [Get User Block Explorers](#get-user-block-explorers)
   - [Get User Cars](#get-user-cars)
   - [Get User Uppies](#get-user-uppies)
   - [Get User Ornaments / Decorations](#get-user-ornaments--decorations)
   - [Get User Map Assets (Outdoor Decors)](#get-user-map-assets-outdoor-decors)
   - [Get User Seeds](#get-user-seeds)
   - [Get User Totems](#get-user-totems)
   - [Get User Racing Legits](#get-user-racing-legits)
   - [Get User Resident Totals](#get-user-resident-totals)
   - [Get Season Yield Multiplier](#get-season-yield-multiplier)
3. [Properties & Map](#properties--map)
   - [Get Property by ID](#get-property-by-id)
   - [Get Properties / Map Objects by Bounding Box](#get-properties--map-objects-by-bounding-box)
   - [Get Map Assets by Bounding Box](#get-map-assets-by-bounding-box)
   - [Search Map Assets](#search-map-assets)
   - [Get Property Collection Matches](#get-property-collection-matches)
   - [Get Property Spark Building Contributions](#get-property-spark-building-contributions)
   - [Get Property Edit Mode](#get-property-edit-mode)
   - [Get Models Available for Building](#get-models-available-for-building)
4. [NFTs & Asset Details](#nfts--asset-details)
   - [Structure / Building](#structure--building)
   - [Property Model Details](#property-model-details)
   - [Outdoor Decor (Map Asset)](#outdoor-decor-map-asset)
   - [Ornament / Decoration (SO Info)](#ornament--decoration-so-info)
   - [Ornament Preview with Season](#ornament-preview-with-season)
   - [Property Management / Decorations](#property-management--decorations)
   - [Legits (Football / Spirit)](#legits-football--spirit)
   - [Block Explorer](#block-explorer)
   - [Vehicle (Car by DGood ID)](#vehicle-car-by-dgood-id)
   - [Watercraft (Boat)](#watercraft-boat)
   - [Aircraft (Plane)](#aircraft-plane)
   - [Uppies](#uppies)
   - [Uppies Merge Price](#uppies-merge-price)
5. [Metaventures & Shops](#metaventures--shops)
   - [Get All Map Pins](#get-all-map-pins)
   - [Metaventure / Secondary Shop Info](#metaventure--secondary-shop-info)
   - [Factory / Manufacturing Plant Info](#factory--manufacturing-plant-info)
   - [Search / Filter Factories](#search--filter-factories)
6. [Life, Seeds & Plants](#life-seeds--plants)
   - [Seed Asset Info](#seed-asset-info)
   - [Seed Generation Details / Price Generator](#seed-generation-details--price-generator)
   - [Get User Plants](#get-user-plants)
   - [Get Plant Info](#get-plant-info)
7. [Construction Hub](#construction-hub)
   - [Active Construction Contracts](#active-construction-contracts)
   - [Construction Contract History](#construction-contract-history)
8. [Racing](#racing)
   - [Lobby / Race Results](#lobby--race-results)
9. [Metadata & Game Config](#metadata--game-config)
   - [Get All Cities](#get-all-cities)
   - [Get All Neighborhoods](#get-all-neighborhoods)
   - [System Configuration](#system-configuration)
   - [Collection Content Viewer](#collection-content-viewer)

---

## Authentication

| Type | Header | Description |
| :--- | :--- | :--- |
| **Public** | *None* | Open to anyone without authentication. |
| **Bearer Token** | `Authorization: Bearer <personal_token>` | Requires a valid session token obtained from an authenticated Upland session. |

---

## User & Profiles

### Get User Profile
Retrieves public profile details for a given username.

- **Method:** `GET`
- **Endpoint:** `/api/profile/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/profile/laban
  ```
- **Example Response:**
  ```json
  {
    "username": "laban",
    "eos_account": "cbab68",
    "rank": "Director",
    "bio": "Upland explorer & builder",
    "avatar": "https://arweave.net/avatar-hash",
    "created_at": "2021-04-12T14:32:00.000Z",
    "dossier": {
      "networth": 12500000,
      "properties_count": 142,
      "collections_count": 18
    }
  }
  ```
- **Key Fields:**
  - `eos_account`: Blockchain account identifier on the Upland Appchain.
  - `rank`: Player tier (`Visitor`, `Uplander`, `Pro`, `Director`, `Executive`).
  - `dossier`: Overall account stats (net worth in UPX, property counts).

---

### Get User Properties
Fetches all properties owned by an account (using the EOS account name).

- **Method:** `GET`
- **Endpoint:** `/api/properties/list/{eos_account}`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/properties/list/cbab68
  ```
- **Example Response:**
  ```json
  [
    {
      "prop_id": 77377277053639,
      "full_address": "12122 RAHN AVE",
      "status": "Owned",
      "sale_upx_price": null,
      "filter_sale_upx_amount": null,
      "sale_fiat_price": null,
      "filter_sale_fiat_amount": null,
      "neighborhood": "Granada Hills",
      "street": "RAHN",
      "city_name": "Los Angeles",
      "state_name": "CA"
    },
    {
      "prop_id": 77304564596481,
      "full_address": "5647 FALLBROOK AVE",
      "status": "For sale",
      "sale_upx_price": 24980,
      "filter_sale_upx_amount": 24980,
      "sale_fiat_price": null,
      "filter_sale_fiat_amount": null,
      "neighborhood": null,
      "street": "FALLBROOK",
      "city_name": "Los Angeles",
      "state_name": "CA"
    }
  ]
  ```
- **Key Fields:**
  - `prop_id`: Unique 64-bit integer property ID.
  - `status`: `"Owned"` or `"For sale"`.
  - `sale_upx_price`: Listed price in UPX (or `null` if unlisted).

---

### Get User Structures
Retrieves all 3D structures and buildings owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/structures/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/structures/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 11980,
      "nft_id": 11980,
      "name": "Townhouse",
      "model_id": 6371191,
      "owner": "laban",
      "property_id": 77377277053639,
      "status": "completed",
      "construction_finish": "2023-08-15T10:00:00.000Z"
    }
  ]
  ```

---

### Get User Block Explorers
Retrieves all Block Explorers associated with the specified username.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/block-explorers/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/block-explorers/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 2850961,
      "nft_id": 2850961,
      "name": "Viking Helmet Explorer",
      "category": "blockexplorer",
      "mint_number": 42,
      "total_minted": 500,
      "image_url": "https://storage.googleapis.com/upland-assets/be/2850961.png"
    }
  ]
  ```

---

### Get User Cars
Retrieves all vehicle NFTs owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/cars/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/cars/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 4297402,
      "dgood_id": 4297402,
      "name": "Standard Go-Kart",
      "model": "Go-Kart Series 1",
      "category": "landvehicle",
      "car_class": "Kart",
      "horsepower": 28,
      "trunk_size": 1,
      "owner": "laban"
    }
  ]
  ```

---

### Get User Uppies
Retrieves all Uppies (avatars/figures) owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/uppies/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/uppies/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 9240563,
      "nft_id": 9240563,
      "name": "Genesis Uppie #412",
      "series": "Series 1",
      "level": 3,
      "rarity": "Rare",
      "owner": "laban"
    }
  ]
  ```

---

### Get User Ornaments / Decorations
Retrieves all seasonal ornaments and structure decorations owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/decorations/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/decorations/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 9436048,
      "nft_id": 9436048,
      "name": "Holiday Snowman",
      "season": "Winter 2024",
      "category": "structure_ornament",
      "installed_on_property": 77377277053639
    }
  ]
  ```

---

### Get User Map Assets (Outdoor Decors)
Retrieves outdoor decorations and map assets placed or owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/outdoor-decors/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/outdoor-decors/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 9436002,
      "nft_id": 9436002,
      "name": "Norwegian Flag Pole",
      "category": "outdoor_decor",
      "installed_on_property": 77377277053639,
      "position": { "x": 1.25, "y": 0.0, "z": -2.4 }
    }
  ]
  ```

---

### Get User Seeds
Retrieves Life seeds (Seeds) owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/seeds/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/seeds/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 7353300,
      "nft_id": 7353300,
      "name": "Sprout Seedling",
      "rarity": "Uncommon",
      "dna": "0x3f8a...",
      "owner": "laban"
    }
  ]
  ```

---

### Get User Totems
Retrieves totems associated with a user or category/identifier.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/totems/{identifier}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/totems/scientist
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 884123,
      "name": "Scientist Totem",
      "type": "scientist",
      "level": 4,
      "boost_rate": 1.15,
      "owner": "laban"
    }
  ]
  ```

---

### Get User Racing Legits
Retrieves racing-related legits owned by the user.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/racing/{username}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/racing/laban
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 2305585,
      "nft_id": 2305585,
      "name": "Speedway Championship Badge",
      "season": "2024",
      "rarity": "Epic"
    }
  ]
  ```

---

### Get User Resident Totals
Displays aggregate resident totals and statistics for a given user.

- **Method:** `GET`
- **Endpoint:** `/business/residents/by-username/{username}/totals`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/residents/by-username/laban/totals
  ```
- **Example Response:**
  ```json
  {
    "username": "laban",
    "total_residents": 45,
    "unique_neighborhoods": 12,
    "active_resident_buildings": 8
  }
  ```

---

### Get Season Yield Multiplier
Retrieves current season yield/multiplier values.

- **Method:** `GET`
- **Endpoint:** `/yield/seasons/multiplier`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/yield/seasons/multiplier
  ```
- **Example Response:**
  ```json
  {
    "current_season": "Frost Season 2026",
    "base_multiplier": 1.0,
    "collection_boost_multiplier": 1.45,
    "active": true
  }
  ```

---

## Properties & Map

### Get Property by ID
Retrieves comprehensive details for a single property by its unique numeric ID.

- **Method:** `GET`
- **Endpoint:** `/api/properties/{property_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/properties/77377277053639
  ```
- **Example Response:**
  ```json
  {
    "prop_id": 77377277053639,
    "full_address": "12122 RAHN AVE",
    "street": { "id": 1421, "name": "RAHN" },
    "city": { "id": 1, "name": "Los Angeles" },
    "state": { "id": 1, "name": "CA" },
    "zipCode": "91344",
    "area": 42.0,
    "owner": "cbab68",
    "owner_username": "laban",
    "yield_per_hour": 1.85,
    "centerlat": 34.29059,
    "centerlng": -118.46971,
    "on_market": null,
    "is_fsa": false,
    "collection_boost": 1.1
  }
  ```
- **Key Fields:**
  - `area`: Size of parcel in UPX square units (UP2).
  - `yield_per_hour`: Hourly base UPX earnings.
  - `on_market`: Object containing currency and price if property is listed for sale.

---

### Get Properties / Map Objects by Bounding Box
Fetches all properties within a specified geographic bounding box.

- **Method:** `GET`
- **Endpoint:** `/api/map`
- **Auth:** Public
- **Query Parameters:**
  - `north` (float), `south` (float), `east` (float), `west` (float)
  - `marker` (boolean, optional): Include map markers
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/map?north=34.29059&south=34.29050&east=-118.46970&west=-118.46980
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 77377277053639,
      "center": [-118.46971, 34.29059],
      "owner": "laban",
      "status": "Owned",
      "price": null,
      "borders": "POLYGON((-118.4698 34.2905, ...))"
    }
  ]
  ```

---

### Get Map Assets by Bounding Box
Fetches placed map assets (structures, outdoor decors) inside the coordinate viewport.

- **Method:** `GET`
- **Endpoint:** `/api/map`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/map?north=34.2910&south=34.2900&east=-118.4690&west=-118.4700&marker=false
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 9436002,
      "type": "outdoor_decor",
      "property_id": 77377277053639,
      "model_id": 4187364,
      "lat": 34.29059,
      "lng": -118.46971
    }
  ]
  ```

---

### Search Map Assets
Full-text search for map assets and decorations.

- **Method:** `POST`
- **Endpoint:** `/assets-search/search/asset`
- **Auth:** Bearer Token
- **Query Parameters:**
  - `text` (string): Query string (e.g., `"norwegian flag"`)
  - `limit` (integer): Maximum items (e.g., `20`)
- **Example Request:**
  ```http
  POST https://api.prod.upland.me/assets-search/search/asset?text="norwegian flag"&limit=20
  ```
- **Example Response:**
  ```json
  {
    "total": 1,
    "items": [
      {
        "nft_id": 9436002,
        "name": "Norwegian Flag",
        "category": "outdoor_decor",
        "owner": "laban",
        "property_id": 77377277053639
      }
    ]
  }
  ```

---

### Get Property Collection Matches
Checks which collections a specific property matches.

- **Method:** `GET`
- **Endpoint:** `/api/properties/match/{property_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/properties/match/77377277053639
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 299,
      "name": "Los Angeles Rare",
      "category": "City",
      "boost": 1.4,
      "completed": true
    }
  ]
  ```

---

### Get Property Spark Building Contributions
Returns active Spark staking contributions and construction progress for a property.

- **Method:** `GET`
- **Endpoint:** `/business/contributions/property/{property_id}`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/contributions/property/77377277053639
  ```
- **Example Response:**
  ```json
  {
    "property_id": 77377277053639,
    "total_spark_staked": 2.5,
    "hours_remaining": 142.5,
    "contributors": [
      { "username": "laban", "staked": 1.5 },
      { "username": "builder_bob", "staked": 1.0 }
    ]
  }
  ```

---

### Get Property Edit Mode
Retrieves editing status, configuration, and constraints for a property.

- **Method:** `GET`
- **Endpoint:** `/business/edit-mode/{property_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/edit-mode/77377277053639
  ```
- **Example Response:**
  ```json
  {
    "property_id": 77377277053639,
    "allowed_actions": ["place_decor", "move_structure", "rotate"],
    "max_outdoor_decors": 5,
    "current_outdoor_decors": 1
  }
  ```

---

### Get Models Available for Building
Returns building models available for construction.

- **Method:** `GET`
- **Endpoint:** `/business/models/available-for-building/`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/models/available-for-building/
  ```
- **Example Response:**
  ```json
  [
    {
      "model_id": 6371191,
      "name": "Modern Luxury Villa",
      "required_area": 35.0,
      "build_duration_hours": 720,
      "base_spark_hours": 1800
    }
  ]
  ```

---

## NFTs & Asset Details

### Structure / Building
Fetches metadata and construction information for a structure by its NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/structure/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/structure/nft-id/11980
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 11980,
    "name": "Townhouse",
    "model_id": 6371191,
    "dimensions": { "width": 8.5, "depth": 12.0, "height": 7.2 },
    "construction_state": "completed",
    "minted_at": "2023-08-15T10:00:00.000Z"
  }
  ```

---

### Property Model Details
Fetches technical 3D model specifications and dimensions for a property model ID.

- **Method:** `GET`
- **Endpoint:** `/business/property-model/{model_id}/details`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/property-model/6371191/details
  ```
- **Example Response:**
  ```json
  {
    "model_id": 6371191,
    "name": "Townhouse",
    "category": "residential",
    "spark_hours": 1200,
    "living_units": 2,
    "preview_url": "https://static.upland.me/models/6371191.glb"
  }
  ```

---

### Outdoor Decor (Map Asset)
Fetches metadata and 3D rendering assets for outdoor decors by NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/outdoor-decors/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/outdoor-decors/nft-id/9436002
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 9436002,
    "name": "Norwegian Flag",
    "model_id": 4187364,
    "category": "outdoor_decor",
    "dgood_id": 9436002,
    "owner": "laban",
    "asset_url": "https://static.upland.me/decors/9436002.glb"
  }
  ```

---

### Ornament / Decoration (SO Info)
Fetches metadata for a structure ornament / decoration by NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/decorations/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/decorations/nft-id/9436048
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 9436048,
    "name": "Holiday Snowman",
    "season": "Winter",
    "year": 2024,
    "dgood_id": 9436048,
    "compatibility": ["Townhouse", "Ranch House", "Villa"]
  }
  ```

---

### Ornament Preview with Season
Fetches preview configuration for an ornament associated with a specific season.

- **Method:** `GET`
- **Endpoint:** `/business/decorations/{decor_id}/preview`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/decorations/875/preview
  ```
- **Example Response:**
  ```json
  {
    "decor_id": 875,
    "season_name": "Winter 2024",
    "is_active_season": false,
    "preview_texture": "https://static.upland.me/ornaments/875.png"
  }
  ```

---

### Property Management / Decorations
Retrieves decoration configuration and status for a managed property.

- **Method:** `GET`
- **Endpoint:** `/business/property-management/{property_id}`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/property-management/77377277053639
  ```
- **Example Response:**
  ```json
  {
    "property_id": 77377277053639,
    "active_ornament": 9436048,
    "installed_decors": [9436002],
    "is_sublet": false
  }
  ```

---

### Legits (Football / Spirit)
Fetches metadata for a Legit card (e.g. Football, Spirit) by NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/football/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/football/nft-id/2305585
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 2305585,
    "category": "football",
    "team": "Kansas City Chiefs",
    "player": "Patrick Mahomes",
    "year": 2023,
    "mint": 47,
    "rarity": "Rare"
  }
  ```

---

### Block Explorer
Fetches metadata for a Block Explorer NFT by NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/block-explorers/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/block-explorers/nft-id/2850961
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 2850961,
    "name": "Viking Explorer",
    "mint_number": 42,
    "total_supply": 500,
    "image_url": "https://storage.googleapis.com/upland-assets/be/2850961.png"
  }
  ```

---

### Vehicle (Car by DGood ID)
Fetches car details and specs using its on-chain DGood ID.

- **Method:** `GET`
- **Endpoint:** `/cars/cars/by-dgood/{dgood_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/cars/cars/by-dgood/4297402
  ```
- **Example Response:**
  ```json
  {
    "dgood_id": 4297402,
    "name": "Go-Kart #42",
    "model": "Go-Kart Series 1",
    "class": "Kart",
    "top_speed": 45,
    "horsepower": 28,
    "fuel_type": "electric",
    "color": "Racing Red"
  }
  ```

---

### Watercraft (Boat)
Fetches watercraft details by NFT ID via the vehicle service.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/cars/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/cars/nft-id/7135885
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 7135885,
    "category": "watercraft",
    "name": "Speedboat V2",
    "capacity": 4,
    "owner": "laban"
  }
  ```

---

### Aircraft (Plane)
Fetches plane/aircraft details by NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/cars/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/cars/nft-id/5762712
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 5762712,
    "category": "aircraft",
    "name": "Twin-Engine Propeller",
    "range_km": 1200,
    "owner": "laban"
  }
  ```

---

### Uppies
Fetches Uppie figurine details by NFT ID.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/uppies/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/uppies/nft-id/9240563
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 9240563,
    "name": "Uppie Pilot",
    "series": 1,
    "rarity": "Epic",
    "power_level": 75
  }
  ```

---

### Uppies Merge Price
Fetches token exchange pricing for merging or trading an Uppie asset by DGood ID.

- **Method:** `GET`
- **Endpoint:** `/nft/token-exchange/price?dGoodId={dgood_id}`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/token-exchange/price?dGoodId=9240563
  ```
- **Example Response:**
  ```json
  {
    "dgood_id": 9240563,
    "merge_cost_upx": 5000,
    "spark_required": 0.05,
    "resulting_level": 4
  }
  ```

---

## Metaventures & Shops

### Get All Map Pins
Retrieves all active business, shop, and Metaventure pins on the map.

- **Method:** `GET`
- **Endpoint:** `/business/pins`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/pins
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 5746,
      "type": "secondary_shop",
      "name": "Laban's Outdoor Decors",
      "lat": 34.29059,
      "lng": -118.46971,
      "property_id": 77377277053639
    }
  ]
  ```

---

### Metaventure / Secondary Shop Info
Retrieves shop information, inventory, and details for a secondary shop or Metaventure.

- **Method:** `GET`
- **Endpoint:** `/metaventures/secondary-shop/{shop_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/metaventures/secondary-shop/5746
  ```
- **Example Response:**
  ```json
  {
    "shop_id": 5746,
    "name": "Laban's Outdoor Decors",
    "owner": "laban",
    "property_id": 77377277053639,
    "commission_rate": 0.05,
    "inventory_count": 14,
    "status": "open"
  }
  ```

---

### Factory / Manufacturing Plant Info
Retrieves factory information and status for a manufacturing plant ID.

- **Method:** `GET`
- **Endpoint:** `/metaventures/plants/{plant_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/metaventures/plants/6159
  ```
- **Example Response:**
  ```json
  {
    "plant_id": 6159,
    "name": "West Coast Kart Factory",
    "category": "landvehicle",
    "owner": "laban",
    "queue_length": 3,
    "active_jobs": 1
  }
  ```

---

### Search / Filter Factories
Searches and filters manufacturing plants with pagination and optional property filter.

- **Method:** `POST`
- **Endpoint:** `/metaventures/plants/search`
- **Auth:** Public
- **Query Parameters:**
  - `limit` (integer): Results per page (e.g. `20`)
  - `propertyId` (integer, optional): Filter by property ID
- **Example Request:**
  ```http
  POST https://api.prod.upland.me/metaventures/plants/search?limit=20
  ```
- **Example Response:**
  ```json
  {
    "total": 38,
    "plants": [
      {
        "plant_id": 6159,
        "name": "West Coast Kart Factory",
        "city": "Los Angeles",
        "property_id": 77377277053639
      }
    ]
  }
  ```

---

## Life, Seeds & Plants

### Seed Asset Info
Fetches information about a Life seed NFT.

- **Method:** `GET`
- **Endpoint:** `/nft/assets/seeds/nft-id/{nft_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/nft/assets/seeds/nft-id/7353300
  ```
- **Example Response:**
  ```json
  {
    "nft_id": 7353300,
    "name": "Sprout Seed",
    "stage": "dormant",
    "potential_tree_type": "Oak",
    "dna": "0x7a8b..."
  }
  ```

---

### Seed Generation Details / Price Generator
Retrieves details and pricing calculations for seed generation.

- **Method:** `GET`
- **Endpoint:** `/life/seed-generation/details/{generation_id}`
- **Auth:** Public / Query Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/life/seed-generation/details/6461
  ```
- **Example Response:**
  ```json
  {
    "generation_id": 6461,
    "cost_upx": 15000,
    "guaranteed_rarity": "Rare",
    "cooldown_hours": 24
  }
  ```

---

### Get User Plants
Retrieves all live plants belonging to a user by their unique user UUID.

- **Method:** `GET`
- **Endpoint:** `/life/plants/user/{user_uuid}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/life/plants/user/3c9278a0-26aa-11eb-8d6e-5390e4e703f7
  ```
- **Example Response:**
  ```json
  [
    {
      "plant_id": 2627617,
      "seed_id": 7353300,
      "name": "Bonsai Tree",
      "growth_stage": 3,
      "health": 100,
      "property_id": 77377277053639
    }
  ]
  ```

---

### Get Plant Info
Retrieves growth state, watering status, and metadata for an individual plant.

- **Method:** `GET`
- **Endpoint:** `/life/plants/{plant_id}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/life/plants/2627617
  ```
- **Example Response:**
  ```json
  {
    "plant_id": 2627617,
    "species": "Golden Bonsai",
    "growth_percentage": 78.5,
    "last_watered": "2026-09-20T08:00:00.000Z",
    "next_watering_deadline": "2026-09-23T08:00:00.000Z"
  }
  ```

---

## Construction Hub

### Active Construction Contracts
Retrieves active construction hub contracts and staking assignments.

- **Method:** `GET`
- **Endpoint:** `/business/construction-hub/contracts/active/`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/construction-hub/contracts/active/?limit=20&offset=0
  ```
- **Example Response:**
  ```json
  {
    "total": 1,
    "contracts": [
      {
        "contract_id": "c-9012",
        "property_id": 77377277053639,
        "model_name": "Townhouse",
        "spark_staked": 2.5,
        "progress_pct": 65.4
      }
    ]
  }
  ```

---

### Construction Contract History
Retrieves past completed and historical construction hub contracts.

- **Method:** `GET`
- **Endpoint:** `/business/construction-hub/contracts/history/`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/business/construction-hub/contracts/history/?limit=20&offset=0
  ```
- **Example Response:**
  ```json
  {
    "total": 12,
    "contracts": [
      {
        "contract_id": "c-8101",
        "property_id": 77377277053639,
        "completed_at": "2025-11-10T14:20:00.000Z",
        "total_spark_hours": 1200
      }
    ]
  }
  ```

---

## Racing

### Lobby / Race Results
Retrieves real-time status or finished race results for an interactive race lobby.

- **Method:** `GET`
- **Endpoint:** `/interactive-race/api/lobbies/{lobby_uuid}`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/interactive-race/api/lobbies/7b8a7ae1-a731-443f-b156-b3e200e6a39b
  ```
- **Example Response:**
  ```json
  {
    "lobby_id": "7b8a7ae1-a731-443f-b156-b3e200e6a39b",
    "track": "Downtown LA GP",
    "status": "finished",
    "results": [
      { "position": 1, "username": "laban", "car_id": 4297402, "lap_time_s": 42.18 },
      { "position": 2, "username": "speedy_racer", "car_id": 5510291, "lap_time_s": 43.05 }
    ]
  }
  ```

---

## Metadata & Game Config

### Get All Cities
Returns a list of all cities in Upland along with geographic boundaries, status, and features.

- **Method:** `GET`
- **Endpoint:** `/api/feature/city`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/feature/city
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 1,
      "name": "Los Angeles",
      "state": "CA",
      "country": "USA",
      "status": "active",
      "center": [-118.2437, 34.0522]
    }
  ]
  ```

---

### Get All Neighborhoods
Returns all neighborhoods and their geographic boundary polygons.

- **Method:** `GET`
- **Endpoint:** `/api/neighborhood`
- **Auth:** Public
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/neighborhood
  ```
- **Example Response:**
  ```json
  [
    {
      "id": 412,
      "name": "Granada Hills",
      "city_id": 1,
      "center": [-118.4697, 34.2905]
    }
  ]
  ```

---

### System Configuration
Fetches global Upland game configuration, feature flags, and client settings.

- **Method:** `GET`
- **Endpoint:** `/api/settings/config`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/settings/config
  ```
- **Example Response:**
  ```json
  {
    "maintenance_mode": false,
    "min_send_fee": 5,
    "max_send_fee": 100,
    "spark_staking_rate": 0.01,
    "features": {
      "racing": true,
      "metaventures": true,
      "life": true
    }
  }
  ```

---

### Collection Content Viewer
Fetches the content, matching criteria, and reward structure for a given collection ID.

- **Method:** `GET`
- **Endpoint:** `/api/collections/match/{collection_id}`
- **Auth:** Bearer Token
- **Example Request:**
  ```http
  GET https://api.prod.upland.me/api/collections/match/299
  ```
- **Example Response:**
  ```json
  {
    "id": 299,
    "name": "Los Angeles Rare",
    "description": "Own 3 properties in Los Angeles rare neighborhoods",
    "reward_upx": 5000,
    "yield_boost": 1.4,
    "required_count": 3
  }
  ```
