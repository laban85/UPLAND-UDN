# Upland Appchain 

### Endpoint
* GET:    https://chain-history.upland.me/v2/history/get_actions
* GET:   https://chain-history.upland.me/v2/history/get_transaction?id=[id]


### Actions
| action code | description | 
|--------------|--------------|
| a4 | Prop mint|
| a44 | Prop mint from bundle |
| i44 | Prop mint from bundle |
| n2 | Prop listed for sale |
| n4 | Prop de-listed |
| n5 | Prop sold |
| n52 | Prop sold for USD |
| n12 | Send UPX trade on property |
| n13 | Sucessful prop trade between two players, both upx and prop swap |
| n14 | |
| n15 | UPX from playuplandme to a player | 
| n21 | Props in collection |
| n24 | Collect send fees |
| n31 | Collect dividens | 
| n33 | Seen when a user levels up from visitor to uplander | 
| n34 | Visa expires ?? | 
| n41 | Send |
| n42 | |
| n43 | Start treasure hunt | 
| n44 | Seen when a user signs up and get his startup bonus. But there is more... |  
| n45 | Jailed |
| n51 | Let out of jail |
| n111 | Transfer UPX between two players, via Upland (for fees) |
| n112 | map asset sold |
| a32 | Player buys a nft? |
| n512 | Unstake sparklet, triggers a transfer right after |
| create | When something new is created, released to the game. |
| issue | When a player has minted a new nft |
| transfernft | When a player receives a nft |  


# List discovered by Wibenji. Thank you!
```
  , eosData = {
    actions: {
        burnall: "a2",
        burnprop: "a25",
        cleancoords: "a3",
        createprop: "a4",
        revealcoords: "a5",
        clearoldstng: "a11",
        append: "b1",
        putForSale: "n2",
        removeFromSale: "n4",
        buy: "n5",
        cnfrmtranesc: "n11",
        makeOffer: "n12",
        acceptOffer: "n13",
        cancelOffer: "n14",
        declineOffer: "n15",
        setcolboost: "n21",
        setinitprice: "n22",
        setintrate: "n23",
        collectvisitpart: "n24",
        getyieldall: "n25",
        getyieldpart: "n31",
        collectvisit: "n42",
        teleportTransaction: "n41",
        cnfrmtransfr: "n43",
        withdraw: "n32",
        transfer: "transfer",
        transfernft: "transfernft",
        sparkTransfer: "transfer",
        newaccount: "newaccount",
        updateauth: "updateauth",
        deleteauth: "deleteauth",
        buyrambytes: "buyrambytes",
        delegatebw: "delegatebw",
        linkauth: "linkauth",
        propose: "propose",
        approve: "approve",
        payforcpu: "payforcpu",
        buyfiat: "n52",
        demolish: "a32",
        withdrawSparks: "n512",
        exportnft: "exportnft"
    },
    params: {
        property_id: "a45",
        teleportPrice: "p54",
        property_ids: "p55",
        account: "a51",
        owner: "a54",
        upsquares: "a42",
        memo: "memo",
        lifetime: "a53",
        initial_price: "p44",
        collection_boost: "p35",
        quantity: "p45",
        user: "p51",
        amount: "p43",
        offset: "p42",
        offer_id: "p22",
        offerer: "p23",
        offering: "p21",
        onsaleprop: "p15",
        seller: "p25",
        buyer: "p14",
        price: "p24",
        fiat: "p3",
        token: "p11",
        transfered: "p12",
        allow_fiat_offers: "p31",
        allow_token_offers: "p32",
        allow_prop_offers: "p33",
        demolish_property_ids: "p115",
        nftId: "p113"
    },
    tables: {
        inexpacc: "a13",
        upscoords: "a14",
        properties: "a15",
        settings: "t1",
        market: "t2",
        offers: "t3",
        usertransfer: "t4",
        accounts: "accounts"
    },
    fields: {
        name: "f1",
        upsquare_id: "b3",
        lat: "a32",
        lng: "a33",
        property_id: "a34",
        owner: "a35",
        upsquares: "a31",
        initial_price: "b4",
        last_yield_time: "b5",
        collection_boost: "b11",
        token: "f4",
        fiat: "f3",
        allow_fiat_offers: "f21",
        allow_token_offers: "f22",
        allow_prop_offers: "f23",
        offer_id: "f15",
        onsaleprop: "f14",
        offering: "f25",
        offerer: "f31",
        amount: "b14",
        token_acc: "f5",
        pool_account: "b12",
        token_sym: "f11",
        fiat_sym: "f12",
        interest_rate: "b13"
    },
    obfuscatedFields: {
        a25: "name",
        b3: "upsquare_id",
        a32: "lat",
        a33: "lng",
        a34: "property_id",
        a35: "owner",
        a31: "upsquares",
        b4: "initial_price",
        b5: "last_yield_time",
        b11: "collection_boost",
        f4: "token",
        f3: "fiat",
        f14: "onsaleprop",
        f15: "offer_id",
        f21: "allow_fiat_offers",
        f22: "allow_token_offers",
        f23: "allow_prop_offers",
        f25: "offering",
        f31: "offerer",
        b14: "amount",
        f5: "token_acc",
        b12: "pool_account",
        f11: "token_sym",
        f12: "fiat_sym",
        b13: "interest_rate"
    }
```
