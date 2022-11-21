# Xcollections Standard
The standard by which the Xcollections project operates. This document defines procedures project owners may take to support Xcollections.

"Xcollections" is a new product created by the [Xdragons](https://xdragons.io) team. Xcollections are XLS-20 NFTs that act as accessories to other PFP NFTs, such as Xdragons. These accessories appear as visual assets that overlay or appear within existing NFTs. A few examples of hypothetical Xcollections are: hats, sunglasses, eyes, mouths, outerwear, backgrounds, and anything one could think of. A single Xcollection may only have one design, but there can be any number of NFTs in the Xcollection; creators may deploy any number of Xcollections that they like.

 Xcollections can be bought, sold, and traded like traditional XLS-20 NFTs. Xcollection deployers determine the price of their NFTs and all of the revenue goes to them, less a 5% royalty collected by Xdragons.

## Supported Methods

### Metadata Method (preferred)

The preferred way of supporting Xcollections from a collection's perspective is the Metadata Method. This method involves altering the metadata of live NFT collections "base NFTs". It requires that the metadata of each base NFT be hosted on a server controlled by the issuer. The Metadata Method [is not supported](#Remarks) for NFTs that utilize IPFS for metadata retrieval. When an NFT owner chooses to apply an Xcollection, the metadata is adjusted by the issuer, [per the schema](#Schema), and a [new image is generated](#Image-Generation) that includes the Xcollection. The Xcollection NFT itself is burned in order to trigger this adjustment and regeneration, which is handled by the Xcollections software.

*Note: Developers will have to write code in order to match their process of image generation of their collection.*

When removing an Xcollection from a base NFT, the metadata is readjusted to its original state, and the image is either regenerated, or if it is still available, replaced within the metadata. The removal of the Xcollection is triggered by a manual execution from the NFT owner. The logic is handled by the Xcollection software running on the issuer's server; it acts as an API that can be triggered from a button on a website or any other method of delivering an HTTP notification. When the running program receives a request to remove an Xcollection, it will notify the central Xcollections API (run by Xdragons) to remint the Xcollection into existence, and create an NFTokenSellOffer for 0 XRP, that the token owner will immediately accept.

### Burn & Remint Method

Xcollections can be applied to an NFT by burning the Xcollection in a special way, burning the base NFT, and reminting the base NFT with the Xcollection applied. They can be removed by requesting a remint of the Xcollection from Xdragons' Xcollection API, and burning and reminting the base NFT. In order for Xcollections to be properly applied and removed from the base NFTs, NFT collection project managers will need to implement server-side programs created by the Xdragons team. These programs, provided sufficient access to the issuer account of the collection, handle the burns and mints of the collections' NFTs to support Xcollections.

Only the owner of the base NFT may burn their NFT unless the [burn flag is provided](https://github.com/XRPLF/XRPL-Standards/discussions/46) when minting the NFT. Most collections do not release with the burn flag enabled as it is seen as a security risk. Xcollections' Burn & Remint Method does **not** require, or even support, burning the NFT from the perspective of the issuer. The Xcollections software simply offers a means of triggering a remint once the original (base) NFT has been burned.

***

Developers should remember to perform due diligence when working with this method, as running the Xcollections software requires the provision of the private key that controls their project's mints.

## Metadata

### Schema

*Coming soon*

*The metadata schema will continue to support the '[art.v0](https://github.com/XRPLF/XRPL-Standards/discussions/69)' schema*

### Image Generation

*Coming soon*

## Remarks

The Metadata Method is not possible for those that utilize IPFS hases for metadata retreival.
