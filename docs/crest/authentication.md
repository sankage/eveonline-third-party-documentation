# Authentication and Scopes

## Authenticated CREST

When designing your application you will need to decide what information you require from CREST and if any of that information requires authentication.

Currently most data is available from public crest, so does not require authentication. Anything that does will be listed under a **scope**

Once you have decided what **scopes** you require for your app, you will need to follow the instructions in the [SSO section](../sso/intro) to register your app on the dev site and then to get an **access token**.


## Scopes

When designing your application you will need to decide what information you require from CREST and if any of that information requires authentication.

Currently most data is available from public crest, so does not require authentication. Anything that is not public will have a scope attached. In order to access these endpoints, your app must have been set up with that scope enabled on the dev site and you must have requested that scope when getting your access token from the SSO.

* __characterAccountRead__: Read your account subscription status.
* __characterAssetsRead__: Read your asset list.
* __characterBookmarksRead__: List your bookmarks and their coordinates.
* __characterCalendarRead__: Read your calendar events and attendees.
* __characterChatChannelsRead__: List chat channels you own or operate.
* __characterClonesRead__: List your jump clones, implants, attributes, and jump fatigue timer.
* __characterContactsRead__: Allows access to reading your characters contacts.
* __characterContactsWrite__: Allows applications to add, modify, and delete contacts for your character.
* __characterContractsRead__: Read your contracts.
* __characterFactionalWarfareRead__: Read your factional warfare statistics.
* __characterFittingsRead__: Allows an application to view all of your character's saved fits.
* __characterFittingsWrite__: Allows an application to create and delete the saved fits for your character.
* __characterIndustryJobsRead__: List your industry jobs.
* __characterKillsRead__: Read your kill mails.
* __characterLocationRead__: Allows an application to read your characters real time location in EVE.
* __characterLoyaltyPointsRead__: List loyalty points your character has for the different corporations.
* __characterMailRead__: Read your EVE Mail.
* __characterMarketOrdersRead__: Read your market orders.
* __characterMedalsRead__: List your public and private medals.
* __characterNavigationWrite__: Allows an application to set your ships autopilot destination.
* __characterNotificationsRead__: Receive in-game notifications.
* __characterOpportunitiesRead__: List the opportunities your character has completed.
* __characterResearchRead__: List your research agents working for you and research progress.
* __characterSkillsRead__: Read your skills and skill queue.
* __characterStatsRead__: Yearly aggregated stats about your character.
* __characterWalletRead__: Read your wallet status, transaction, and journal history.
* __corporationAssetRead__: Read your corporation's asset list.
* __corporationBookmarksRead__: List your corporation's bookmarks and their coordinates.
* __corporationContractsRead__: List your corporation's contracts.
* __corporationFactionalWarfareRead__: Read your corporation's factional warfare statistics.
* __corporationIndustryJobsRead__: List your corporation's industry jobs.
* __corporationKillsRead__: Read your corporation's kill mails.
* __corporationMarketOrdersRead__: List your corporation's market orders.
* __corporationMedalsRead__: List your corporation's issued medals.
* __corporationMembersRead__: List your corporation's members, their titles, and roles.
* __corporationShareholdersRead__: List your corporation's shareholders and their shares.
* __corporationStructuresRead__: List your corporation's structures, outposts, and starbases.
* __corporationWalletRead__: Read your corporation's wallet status, transaction, and journal history.
* __fleetRead__: Allows real time reading of your fleet information (members, ship types, etc.) if you're the boss of the fleet.
* __fleetWrite__: Allows the ability to invite, kick, and update fleet information if you're the boss of the fleet.
* __publicData__: Allows access to public data.
* __structureVulnUpdate__: Allows updating your structures' vulnerability timers.


## Using your access token

Once you have a valid access token from the SSO, you can make calls to authenticated CREST by adding an Authorization header and using the auth'd crest endpoint.

```http
Authorization: Bearer [Your access token]
```

An authenticated call that lists all regions would look like this (note that the url here should have been obtained dynamically from the root endpoint, rather than being hardcoded):

```http
POST https://crest-tq.eveonline.com/regions/ HTTP/1.1

Authorization: Bearer bG9...ZXQ=
Accept: application/vnd.ccp.eve.RegionCollection-v1+json
Host: crest-tq.eveonline.com
```    

For information on the Accept header used here, see the [Versioning](versioning.md) section.
