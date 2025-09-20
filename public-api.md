# Content
- [Property Info](#userinfo)
- [User info](#userinfo)


# Property Info

## Based on propertyId
https://api.prod.upland.me/api/properties/[propertyId]

<details><summary>Response</summary>

```json
{
    "prop_id": 77194422187902,
    "full_address": "5114 3RD AVE",
    "centerlat": "33.996327997386565",
    "centerlng": "-118.32001605443301",
    "boundaries": "{\"type\":\"Polygon\",\"coordinates\":[[[-118.31980149240054,33.996274981206398],[-118.31980101538049,33.996383439659688],[-118.32022989807642,33.996381566797965],[-118.32023037033942,33.996272009215858],[-118.31980149240054,33.996274981206398]]]}",
    "area": 52,
    "status": "Owned",
    "locked_until": null,
    "locked_user_id": null,
    "transaction_id": "ca18c0727a733723855144cf82ccccdf7950106aef3ccc589a87a6c0730a1058",
    "last_transaction_id": "ca18c0727a733723855144cf82ccccdf7950106aef3ccc589a87a6c0730a1058",
    "last_purchased_price": 14664,
    "terminal_id": null,
    "feature": null,
    "labels": {
        "fsa_allow": false
    },
    "on_market": null,
    "offers_made_by_you": null,
    "offers_with_property": null,
    "offers_to_property": null,
    "fiat_price": null,
    "is_offering": false,
    "is_blocked": false,
    "owner": "vdxgqnvuvppp",
    "owner_username": "laban",
    "yield_per_hour": 0.08316388165578295,
    "price": 14664,
    "can_make_offer": true,
    "collection_boost": 1,
    "street": {
        "id": 41224,
        "name": "3RD"
    },
    "city": {
        "id": 32,
        "name": "Los Angeles",
        "metropolisId": null
    },
    "teleport_price": 25,
    "buyer_transaction_fee": 0.05,
    "seller_transaction_fee": 0.05,
    "is_construction_forbidden": false,
    "ownership_changed_at": "2023-04-05T21:48:06.368Z",
    "customization": {
        "background_url": "https://static.upland.me/live-events/Customizations/2025/genesis_season/Pirate_Fighters_Genesis25.gif"
    },
    "building": {
        "propModelID": 375835,
        "propertyID": 77194422187902,
        "nftID": 2791256,
        "lat": 33.99632900953516,
        "lng": -118.3199921622191,
        "polygon": [
            [
                -1.49637,
                -3.13768
            ],
            [
                -1.49637,
                3.66623
            ],
            [
                1.61603,
                3.66623
            ],
            [
                1.61603,
                -3.13768
            ],
            [
                -1.49637,
                -3.13768
            ]
        ],
        "scale": 3,
        "rotate": [
            1.5707963267948966,
            -1.570794,
            0
        ],
        "constructionStatus": "completed",
        "buildingImage": "town_house_new/town_baked.png",
        "buildingType": "residential",
        "buildingName": "Town House",
        "modelId": 33,
        "residents": 0,
        "construction": null,
        "details": {
            "maxStackedSparks": 60000,
            "minStackedSparks": 200,
            "stepSparks": 10
        }
    },
    "buildings": [
        {
            "propModelID": 375835,
            "propertyID": 77194422187902,
            "nftID": 2791256,
            "lat": 33.99632900953516,
            "lng": -118.3199921622191,
            "polygon": [
                [
                    -1.49637,
                    -3.13768
                ],
                [
                    -1.49637,
                    3.66623
                ],
                [
                    1.61603,
                    3.66623
                ],
                [
                    1.61603,
                    -3.13768
                ],
                [
                    -1.49637,
                    -3.13768
                ]
            ],
            "scale": 3,
            "rotate": [
                1.5707963267948966,
                -1.570794,
                0
            ],
            "constructionStatus": "completed",
            "buildingImage": "town_house_new/town_baked.png",
            "buildingType": "residential",
            "buildingName": "Town House",
            "modelId": 33,
            "residents": 0,
            "construction": null,
            "details": {
                "maxStackedSparks": 60000,
                "minStackedSparks": 200,
                "stepSparks": 10
            }
        }
    ],
    "is_owner_in_jail": false,
    "state": {
        "id": 1,
        "name": "CA"
    },
    "addressWithCityAndState": "5114 3RD AVE, Los Angeles, CA"
}
```
</details>


## Based on Lat and Lng

https://api.prod.upland.me/api/map?north=[lat]&south=[lat]&east=[lng]&west=[lng]

<details><summary>Response</summary>

```json

[
    {
        "prop_id": 77194422187902,
        "boundaries": "{\"type\":\"Polygon\",\"coordinates\":[[[-118.31980149240054,33.996274981206398],[-118.31980101538049,33.996383439659688],[-118.32022989807642,33.996381566797965],[-118.32023037033942,33.996272009215858],[-118.31980149240054,33.996274981206398]]]}",
        "centerlat": "33.996327997386565",
        "centerlng": "-118.32001605443301",
        "labels": {
            "fsa_allow": false
        },
        "status": "Owned",
        "models": []
    }
]
```
</details>


# User details

## Userinfo
https://api.prod.upland.me/api/profile/[upland_username]

<details><summary>Response</summary>

```json

{
    "id": "3c9278a0-26aa-11eb-8d6e-5390e4e703f7",
    "avatar": {
        "id": 1085,
        "image": "https://static.upland.me/avatars/exclusive/laban_v2.svg"
    },
    "color": {
        "id": 24,
        "color": "#5AA9FF"
    },
    "avatar_background": "https://static.upland.me/live-events/Customizations/2025/frost_season/XStacks_Mania_avatar_bg_frost25.png",
    "collections": [
        {
            "id": 571,
            "name": "Miami Beach",
            "image": "https://static.upland.me/collections-assets/zu3DSdNQWVhArxgVEpm3NDbTZu4FjYHk-banner.png",
            "image_thumbnail": "https://static.upland.me/collections-assets/zu3DSdNQWVhArxgVEpm3NDbTZu4FjYHk-thumbnail.png",
            "city_id": 87
        },
        {
            "id": 358,
            "name": "Highland Park",
            "image": "https://static.upland.me/collections-assets/bIa3KbhunfNKeMmpoeDAZX1OXIn4jwhp-banner.png",
            "image_thumbnail": "https://static.upland.me/collections-assets/bIa3KbhunfNKeMmpoeDAZX1OXIn4jwhp-thumbnail.png",
            "city_id": 40
        },
        {
            "id": 72,
            "name": "Brooklyner",
            "image": "https://static.upland.me/collections-assets/brooklyner-72-banner.png",
            "image_thumbnail": "https://static.upland.me/collections-assets/brooklyner-72-thumbnail.png",
            "city_id": 6
        }
    ],
    "networth": 28035909.4,
    "properties": [
        {
            "property_id": 81376144365793
        },
        {
            "property_id": 81354283655218
        },
        {
            "property_id": 81349300820857
        }
    ],
    "badges": [
        {
            "image": "https://static.upland.me/explorer-badges/Builder.png",
            "id": 7,
            "help_type": "badge_builder",
            "name": "Builder",
            "user_id": "3c9278a0-26aa-11eb-8d6e-5390e4e703f7"
        },
        {
            "image": "https://static.upland.me/explorer-badges/completionist_x2.svg",
            "id": 179,
            "help_type": "completionist_x2",
            "name": "Completionist x2",
            "user_id": "3c9278a0-26aa-11eb-8d6e-5390e4e703f7"
        }
    ],
    "is_in_jail": false,
    "lvl": 4,
    "user_lvl_status": "LVL_UPED_WITH_CEREMONY",
    "home_address": {
        "property_id": 72087623621757,
        "neighborhood_id": 2393,
        "address": "3401 NW 19TH TER",
        "neighborhood_name": "NORTH GRAPELAND HEIGHTS",
        "city_name": "Miami",
        "state_name": "FL",
        "building_image": "town_house_new/town_baked.png"
    },
    "chatEnabled": true,
    "is_mayor": false
}

```
</details>


## User Map Assets

https://api.prod.upland.me/nft/assets/outdoor-decors/[upland_username]

<details><summary>Response</summary>

```json
[
    {
        "dgoodId": 2433689,
        "category": "outdoordecor",
        "serialNumber": 5,
        "mintingEnd": "2049-12-31T13:25:36.000Z",
        "metadata": {
            "displayName": "Maroon Mosaic Tile II (S)",
            "image": "3d-models/decorations/lclR13t-Foj3yRDwSYD0TvrpKgFv8-_2FmWp2aecZXo.png",
            "transactionId": "8c21130600b44db85da5e16b3ca4984dd49bbcff4292c5037ef14fa53fbaae2b",
            "username": "laban",
            "modelUrl": "3d-models/decorations/d2D06vgIOvsPoQQN0pxoUZWXW29Lh6084tq-vicjLAc.gltf",
            "property": {
                "id": 79548500263427,
                "cityName": "San Francisco",
                "stateName": "CA",
                "countryName": "us",
                "fullAddress": "2845 TURK BLVD"
            },
            "isExchangeable": false
        },
        "stat": {
            "maxSupply": 100,
            "currentSupply": 40,
            "issuedSupply": 40
        },
        "ownerUsername": "laban",
        "isLocked": false,
        "isChangingOwnership": false,
        "activeNftLock": null,
        "isRestrictedForSwapOffers": false
    },
    {
        "dgoodId": 2457746,
        "category": "outdoordecor",
        "serialNumber": 20,
        "mintingEnd": "2049-12-31T13:25:36.000Z",
        "metadata": {
            "displayName": "Gold Mosaic Tile IX (M)",
            "image": "3d-models/decorations/joYkTrg-PW-PLVjnvm02I-Lke6XnDBCp7ska8tpY_VI.png",
            "transactionId": "b1d35a07d2f48635c9e2554e854f0545ce23e8721888bd5ce98a07a09e03f3fc",
            "username": "laban",
            "modelUrl": "3d-models/decorations/-NjtKO4mPVVqQcfhZhw7mZ-EY5LGFOS10mR9iYTuH24.gltf",
            "property": {
                "id": 79548684812873,
                "cityName": "San Francisco",
                "stateName": "CA",
                "countryName": "us",
                "fullAddress": "2601 TURK BLVD"
            },
            "isExchangeable": false
        },
        "stat": {
            "maxSupply": 100,
            "currentSupply": 40,
            "issuedSupply": 40
        },
        "ownerUsername": "laban",
        "isLocked": false,
        "isChangingOwnership": false,
        "activeNftLock": null,
        "isRestrictedForSwapOffers": false
    },
    {
        "dgoodId": 2458178,
        "category": "outdoordecor",
        "serialNumber": 554,
        "mintingEnd": "2049-12-31T16:20:43.000Z",
        "metadata": {
            "displayName": "Single Mailbox",
            "image": "3d-models/decorations/9/16/thumbnail.png",
            "transactionId": "9449275aab759100732155cd553d182282f061831429bd14d2e654b8fa103a52",
            "username": "laban",
            "modelUrl": "3d-models/decorations/9/16/nft-model.gltf",
            "property": {
                "id": 78533025968283,
                "cityName": "Las Vegas",
                "stateName": "NV",
                "countryName": "us",
                "fullAddress": "4290 E CLEVELAND AVE"
            },
            "isExchangeable": false
        },
        "stat": {
            "maxSupply": 5000,
            "currentSupply": 4334,
            "issuedSupply": 4334
        },
        "ownerUsername": "laban",
        "isLocked": false,
        "isChangingOwnership": false,
        "activeNftLock": null,
        "isRestrictedForSwapOffers": false
    }
]
```
</details>


## User Structure Ornaments
https://api.prod.upland.me/nft/assets/decorations/[upland_username]

<details><summary>Response</summary>

```json
[
    {
        "dgoodId": 122061,
        "serialNumber": 115,
        "category": "structornmt",
        "metadata": {
            "isApplied": false,
            "decorationId": 1,
            "subtitle": "Small Town House",
            "displayName": "Lil Skelly",
            "image": "3d-models/halloween/decorations/Small Town House/Lil Skelly/Uncanny/asset-image.png",
            "transactionId": "cbf37f6bc944dcd2265e27e339b337aeaa082d5b5a7ec7fb6aab0c5c8b628498",
            "username": "laban",
            "isExchangeable": false,
            "rarityLevel": "Uncanny",
            "backgroundLandscapeUrl": "3d-models/halloween/decorations/Small Town House/Lil Skelly/Uncanny/background-image-landscape.jpg",
            "backgroundPortraitUrl": "3d-models/halloween/decorations/Small Town House/Lil Skelly/Uncanny/background-image-portrait.jpg",
            "property": {
                "id": 82092161955086,
                "cityName": "Chicago",
                "stateName": "IL",
                "countryName": "us",
                "fullAddress": "1414 S WABASH AVE"
            }
        },
        "stat": {
            "maxSupply": 383,
            "currentSupply": 383,
            "issuedSupply": 383
        },
        "ownerUsername": "laban",
        "isLocked": false,
        "isChangingOwnership": false,
        "activeNftLock": null,
        "isRestrictedForSwapOffers": false
    },
    {
        "dgoodId": 122323,
        "serialNumber": 58,
        "category": "structornmt",
        "metadata": {
            "isApplied": false,
            "decorationId": 6,
            "subtitle": "Small Town House",
            "displayName": "Freakshow Clown",
            "image": "3d-models/halloween/decorations/Small Town House/Freakshow Clown/Uncanny/asset-image.png",
            "transactionId": "d496a387e502aa4c9dc89cf25a11ae5247c11557af034a625f38f77a0b6cd098",
            "username": "laban",
            "isExchangeable": false,
            "rarityLevel": "Uncanny",
            "backgroundLandscapeUrl": "3d-models/halloween/decorations/Small Town House/Freakshow Clown/Uncanny/background-image-landscape.jpg",
            "backgroundPortraitUrl": "3d-models/halloween/decorations/Small Town House/Freakshow Clown/Uncanny/background-image-portrait.jpg",
            "property": {
                "id": 88714919107630,
                "cityName": "Birmingham",
                "stateName": "EN",
                "countryName": "uk",
                "fullAddress": "67A VICTORIA RD"
            }
        },
        "stat": {
            "maxSupply": 383,
            "currentSupply": 383,
            "issuedSupply": 383
        },
        "ownerUsername": "laban",
        "isLocked": false,
        "isChangingOwnership": false,
        "activeNftLock": null,
        "isRestrictedForSwapOffers": false
    }
]
```
</details>