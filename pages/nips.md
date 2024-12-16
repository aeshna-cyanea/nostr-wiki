- sourced from https://wikifreedia.xyz/nips/laeserin@gitcitadel.com edited by me for formatting/clarity
- NIPs stand for *Nostr Implementation Possibilities*.
  They exist to document what may be implemented by [[Nostr]] -compatible _relay_ and _client_ software.
- ## List
	- [[NIP-01]] Basic protocol flow description
	- [[NIP-02]] Follow List
	- [[NIP-03]] OpenTimestamps Attestations for Events
	- [[NIP-04]] Encrypted Direct Message - `unrecommended`: deprecated in favor of [NIP-17](17.md)
	- [[NIP-05]] Mapping Nostr keys to DNS-based internet identifiers
	- [[NIP-06]] Basic key derivation from mnemonic seed phrase
	- [[NIP-07]] window.nostr  capability for web browsers
	- [[NIP-08]] Handling Mentions - Warning*  `unrecommended`: deprecated in favor of [NIP-27](27.md)
	- [[NIP-09]] Event Deletion
	- [[NIP-10]] Conventions for clients' use of e and p  tags in text events
	- [[NIP-11]] Relay Information Document
	- [[NIP-13]] Proof of Work
	- [[NIP-14]] Subject tag in text events
	- [[NIP-15]] Nostr Marketplace (for resilient marketplaces)
	- [[NIP-17]] Private Direct Messages
	- [[NIP-18]] Reposts
	- [[NIP-19]] bech32-encoded entities
	- [[NIP-21]] nostr:  URI scheme
	- [[NIP-23]] Long-form Content
	- [[NIP-24]] Extra metadata fields and tags
	- [[NIP-25]] Reactions
	- [[NIP-26]] Delegated Event Signing
	- [[NIP-27]] Text Note References
	- [[NIP-28]] Public Chat
	- [[NIP-29]] Relay-based Groups
	- [[NIP-30]] Custom Emoji
	- [[NIP-31]] Dealing with Unknown Events
	- [[NIP-32]] Labeling
	- [[NIP-34]] git  stuff
	- [[NIP-35]] Torrents
	- [[NIP-36]] Sensitive Content
	- [[NIP-38]] User Statuses
	- [[NIP-39]] External Identities in Profiles
	- [[NIP-40]] Expiration Timestamp
	- [[NIP-42]] Authentication of clients to relays
	- [[NIP-44]] Versioned Encryption
	- [[NIP-45]] Counting results
	- [[NIP-46]] Nostr Connect
	- [[NIP-47]] Wallet Connect
	- [[NIP-48]] Proxy Tags
	- [[NIP-49]] Private Key Encryption
	- [[NIP-50]] Search Capability
	- [[NIP-51]] Lists
	- [[NIP-52]] Calendar Events
	- [[NIP-53]] Live Activities
	- [[NIP-54]] Wiki
	- [[NIP-56]] Reporting
	- [[NIP-57]] Lightning Zaps
	- [[NIP-58]] Badges
	- [[NIP-59]] Gift Wrap
	- [[NIP-65]] Relay List Metadata
	- [[NIP-71]] Video Events
	- [[NIP-72]] Moderated Communities
	- [[NIP-75]] Zap Goals
	- [[NIP-78]] Application-specific data
	- [[NIP-84]] Highlights
	- [[NIP-89]] Recommended Application Handlers
	- [[NIP-90]] Data Vending Machines
	- [[NIP-92]] Media Attachments
	- [[NIP-94]] File Metadata
	- [[NIP-96]] HTTP File Storage Integration
	- [[NIP-98]] HTTP Auth
	- [[NIP-99]] Classified Listings
- ## Event Kinds
  
  Please see [[NIP Event Register]].
- ## Message types
- ### Client to Relay
  
  | type    | description                                         | NIP         |
  | ------- | --------------------------------------------------- | ----------- |
  | EVENT  | used to publish events                              | [[NIP-01]] |
  | REQ    | used to request events and subscribe to new updates | [[NIP-01]] |
  | CLOSE  | used to stop previous subscriptions                 | [[NIP-01]] |
  | AUTH   | used to send authentication events                  | [[NIP-42]] |
  | COUNT  | used to request event counts                        | [[NIP-45]] |
- ### Relay to Client
  
  | type     | description                                             | NIP         |
  | -------- | ------------------------------------------------------- | ----------- |
  | EOSE    | used to notify clients all stored events have been sent | [[NIP-01]] |
  | EVENT   | used to send events requested to clients                | [[NIP-01]] |
  | NOTICE  | used to send human-readable messages to clients         | [[NIP-01]] |
  | OK      | used to notify clients if an EVENT was successful       | [[NIP-01]] |
  | CLOSED  | used to notify clients that a REQ was ended and why     | [[NIP-01]] |
  | AUTH    | used to send authentication challenges                  | [[NIP-42]] |
  | COUNT   | used to send requested event counts to clients          | [[NIP-45]] |
  
  Please update these lists when proposing NIPs introducing new event kinds.
- ## Standardized Tags
  
  | name              | value                                | other parameters                | NIP                                   |
  | ----------------- | ------------------------------------ | ------------------------------- | ------------------------------------- |
  | e                | event id (hex)                       | relay URL, marker, pubkey (hex) | [[NIP-01]], [[NIP-10]]              |
  | p                | pubkey (hex)                         | relay URL, petname              | [[NIP-01]], [[NIP-02]]              |
  | a                | coordinates to an event              | relay URL                       | [[NIP-01]]                           |
  | d                | identifier                           | --                              | [[NIP-01]]                           |
  | g                | geohash                              | --                              | [[NIP-52]]                           |
  | i                | identity                             | proof                           | [[NIP-39]]                           |
  | k                | kind number (string)                 | --                              | [[NIP-18]], [[NIP-25]], [[NIP-72]] |
  | l                | label, label namespace               | annotations                     | [[NIP-32]]                           |
  | L                | label namespace                      | --                              | [[NIP-32]]                           |
  | m                | MIME type                            | --                              | [[NIP-94]]                           |
  | q                | event id (hex)                       | relay URL                       | [[NIP-18]]                           |
  | r                | a reference (URL, etc)               | petname                         |                                       |
  | r                | relay url                            | marker                          | [[NIP-65]]                           |
  | t                | hashtag                              | --                              |                                       |
  | alt              | summary                              | --                              | [[NIP-31]]                           |
  | amount           | millisatoshis, stringified           | --                              | [[NIP-57]]                           |
  | bolt11          | bolt11  invoice                     | --                              | [[NIP-57]]                           |
  | challenge        | challenge string                     | --                              | [[NIP-42]]                           |
  | client           | name, address                        | relay URL                       | [[NIP-89]]                           |
  | clone            | git clone URL                        | --                              | [[NIP-34]]                           |
  | content-warning  | reason                               | --                              | [[NIP-36]]                           |
  | delegation       | pubkey, conditions, delegation token | --                              | [[NIP-26]]                           |
  | description      | description                          | --                              | [[NIP-34]], [[NIP-57]], [[NIP-58]] |
  | emoji            | shortcode, image URL                 | --                              | [[NIP-30]]                           |
  | encrypted        | --                                   | --                              | [[NIP-90]]                           |
  | expiration       | unix timestamp (string)              | --                              | [[NIP-40]]                           |
  | goal             | event id (hex)                       | relay URL                       | [[NIP-75]]                           |
  | image            | image URL                            | dimensions in pixels            | [[NIP-23]], [[NIP-58]]              |
  | imeta            | inline metadata                      | --                              | [[NIP-92]]                           |
  | lnurl           | bech32 encoded lnurl              | --                              | [[NIP-57]]                           |
  | location         | location string                      | --                              | [[NIP-52]], [[NIP-99]]              |
  | name             | name                                 | --                              | [[NIP-34]], [[NIP-58]]              |
  | nonce            | random                               | difficulty                      | [[NIP-13]]                           |
  | preimage        | hash of bolt11  invoice             | --                              | [[NIP-57]]                           |
  | price            | price                                | currency, frequency             | [[NIP-99]]                           |
  | proxy            | external ID                          | protocol                        | [[NIP-48]]                           |
  | published_at     | unix timestamp (string)              | --                              | [[NIP-23]]                           |
  | relay            | relay url                            | --                              | [[NIP-42]], [[NIP-17]]              |
  | relays           | relay list                           | --                              | [[NIP-57]]                           |
  | server           | file storage server url              | --                              | [[NIP-96]]                           |
  | subject          | subject                              | --                              | [[NIP-14]], [[NIP-17]]              |
  | summary          | article summary                      | --                              | [[NIP-23]]                           |
  | thumb            | badge thumbnail                      | dimensions in pixels            | [[NIP-58]]                           |
  | title            | article title                        | --                              | [[NIP-23]]                           |
  | web              | webpage URL                          | --                              | [[NIP-34]]                           |
  | zap              | pubkey (hex), relay URL              | weight                          | [[NIP-57]]                           |
- ## Breaking Changes
  
  [Breaking Changes](https://github.com/nostr-protocol/nips/blob/master/BREAKING.md[]
- ## License
  
  All NIPs are public domain.