# History

## 1.3.2

* fix autoversion in online mode

## 1.3.1

* improve autoversion support
* fix tests

## 1.3.0

* 1.12 support

## 1.2.0

* some 1.12 snapshots support
* disable validator for protocol (use too much memory and cpu, and already validated in mcdata tests)
* Added a errorHandler option to createServer.

## 1.1.3

* requires node 6

## 1.1.2

* use last protodef

## 1.1.1

* update to yggdrasil 0.2.0
* Fix the REGISTER channel type

## 1.1.0

* added plugin channel support (thanks @plexigras)
* add doc for client.end

## 1.0.1

* a small fix to autoversion

## 1.0.0

* update prismarine-nbt
* fixed options.favicon in createServer
* enable strict mode
* update to minecraft-data 2.0.0
* finally move to a major version

## 0.19.6

* update mcwrap
* use caret in dependencies
* use debug package

## 0.19.5

* check if e.field is defined when completing serializer/deserializer errors

## 0.19.4

* fix spawn_painting in 1.9

## 0.19.3

* update mcdata again : u8 not byte

## 0.19.2

* some fixes in 1.9 protocol

## 0.19.1

* update mcdata, support 1.9 release

## 0.19.0

* update minecraft-data, support 1.9-pre4

## 0.18.3

* update protodef and minecraft-data for new protocol schema

## 0.18.2

* update protodef
* custom packets
* fix tab_complete in 1.9

## 0.18.1

* update protodef dependency

## 0.18.0

* Supports Minecraft version 1.7.10, 1.8.8 and 1.9 (15w40b and 16w05b)
* improve auto version detection

## 0.17.2

* fix readUUID

## 0.17.1

* use correct default timeout value : 30 for the server, 20 for the client
* fix a small dependency error

## 0.17.0

* requires node>=4
* big refactor of createClient : split in several modules (thanks @deathcap)
* stop using es7
* make it easy to create client plugins (and create minecraft-protocol-forge) (thanks @deathcap)
* use babel6
* add dynamic version support in client
* update minecraft-data

## 0.16.6

* fix latency before the first keep alive

## 0.16.5

* initialize latency to 0

## 0.16.4

 * add client.latency (thanks @netraameht)

## 0.16.3

 * update protodef : fix bug in switch
 * don't write after end and unpipe everything when ending

## 0.16.2

 * update protodef version which fix a bug in writeOption

## 0.16.1

 * add checkTimeoutInterval to createClient
 * parse nbt in all packets (in particular tile_entity_data and update_entity_nbt)

## 0.16.0

 * cross version support exposed : version option in createClient and createServer
 * expose createSerializer and createDeserializer, createPacketBuffer and parsePacketData are now available in serializer/parser instances (BREAKING CHANGE)
 * stop exposing packetFields, packetNames, packetIds, packetStates. That data is available by requiring minecraft-data package (BREAKING CHANGE)
 * don't expose version anymore but supportedVersions (BREAKING CHANGE)
 * use node-yggdrasil : index.js now doesn't expose yggdrasil, use node-yggdrasil directly if needed (BREAKING CHANGE)
 * createServers's beforePing option can now takes an async function
 * enable compression by default in createServer
 * update ursa to get node4 (and node5) compatibility
 * lot of internal changes : using the new general serializing/parsing library ProtoDef
 * fix compression in proxy example
 * fix gamemode3 in proxy
 * generate the same uuidv3 than the vanilla server does in offline mode

## 0.15.0

 * UUIDs are now strings instead of arrays. (BREAKING CHANGE)
 * Server clients have a new property, client.profile, containing the result
 of the yggdrasil authentication
 * Protocol.json now lives in minecraft-data
 * Don't bubble up errors from client to server. (BREAKING CHANGE). If you want
   to catch the client errors, you need to add an error listener on that client.
   The old behavior was confusing, error-prone and undocumented !
 * Add keepAlive option to createServer, in order to optionally disable it.
 * Lots of low-level changes to allow minecraft-data to be more generic.
 * NMP code is able to work with both 1.8 and 1.9 data with the same code,
   opening a path for cross-versioning.
 * The packet events now take two parameters : `function (packetData, packetMetadata)`
   * `packetMetadata` contains the packet name, id and state (more may be added later)
   * `packetData` contains the actual data content

## 0.14.0

 * Huge rewrite of the internals, using transform streams, which eliminates two
   classes of problems from node-minecraft-protocol :
   * Uncatchable errors being triggered inside the protocol parser
   * Packets ariving out of order, causing several race conditions
 * All the attributes that were previously exposed via `mc.protocol` are now directly
   attached to the `mc` object, e.g. `mc.protocol.states` => `mc.states`. This is
   prone to further changes.
 * open_window now reports the entityId correctly for horses
 * Properly handle the set_compression packet
 * Fix small bug in scoreboard_team and player_info packets causing crashes
 * Fix the login implementation logging out people from their launchers.

## 0.13.4

 * Added hook to modify server ping (thanks [Brian Schlenker](https://github.com/bschlenk))
 * Exposed the Client class to the browser, after removing node-specific details
 * Fixed the examples
 * Silenced the "DID NOT PARSE THE WHOLE THING" debug message, and made it print more useful info
 * Updated ursa-purejs dependency, which in turned fixed windows version of node-minecraft-protocol.

## 0.13.3

 * Fixed readPosition for negative packets (thanks [rom1504](https://github.com/rom1504))

## 0.13.2

 * Fixed particle packet.
 * Fixed release. 0.13.1 release was missing an entire folder.

## 0.13.1

 * Externalized rsa-wrap library to its own npm module, named ursa-native
 * Fixed broken bed-related packets (thanks [rom1504](https://github.com/rom1504))

## 0.13.0

 * Updated protocol version to support 1.8.1 (thanks [wtfaremyinitials](https://github.com/wtfaremyinitials))
 * Lots of changes in how some formats are handled.
 * Crypto now defaults to a pure-js library if URSA is missing, making the lib easier to use on windows.
 * Fix a bug in yggdrasil handling of sessions, making reloading a session impossible (thanks [Frase](https://github.com/mrfrase3))
 * Set noDelay on the TCP streams, making the bot a lot less laggy.

## 0.12.3

 * Fix for/in used over array, causing glitches with augmented Array prototypes (thanks [pelikhan](https://github.com/pelikhan))

## 0.12.2

 * Updated protocol version to support 1.7.10
 * Some bug fixes in parser (thanks [Luke Young](https://github.com/innoying))
 * 'raw' event to catch all raw buffers (thanks [deathcap](https://github.com/deathcap))
 * Misc bug fixes

## 0.12.1

 * Updated protocol version to support 1.7.6

## 0.12.0
 
 * Updated protocol version to support 1.7.2
 * Overhaul the serializer backend to be more general-purpose and future-proof.
 * Support listening packets by name (thanks [deathcap](https://github.com/deathcap))
 * Support reading/writing a raw buffer to the socket.

## 0.11.6

 * Updated protocol version to support 1.6.4 (thanks [Matt Bell](https://github.com/mappum))

## 0.11.5

 * Fix handling of some conditional fields (thanks [Florian Wesch](https://github.com/dividuum))

## 0.11.4

 * Chat packet string max length fix (thanks [Robin Lambertz](https://github.com/roblabla))

## 0.11.3

 * packet 0x2c: packet writing fixed, UUID format simplified, tests updated

## 0.11.2

 * 1.6.2 support fixes: updated 0x2c packets to include `elementList` and added 0x85 *Tile Editor Open* packets

## 0.11.1

 * support minecraft protocol 1.6.2 / protocol version 74 (thanks [Matt Bell](https://github.com/mappum))

## 0.11.0

 * support minecraft protocol 1.6.1 / protocol version 73 (thanks [Matt Bell](https://github.com/mappum))
   * *note:* chat packets have a new format (see [the examples](https://github.com/andrewrk/node-minecraft-protocol/tree/master/examples) for how to upgrade).

## 0.10.1

 * support minecraft protocol 1.5.2 / protocol version 61

## 0.10.0

 * Added SRV record support when connecting to a server (thanks [Matt Stith](https://github.com/stith))
 * 0x66: `shift` renamed to `mode` and changed from bool to byte

## 0.9.0

 * 0xce: create changed from bool to byte (thanks [Robin Lambertz](https://github.com/roblabla))

## 0.8.1

 * fix buffer length checking bug in readSlot() (thanks [Xabier de Zuazo](https://github.com/zuazo))
 * fix C2 calculation bug (fixed #35) (thanks [Xabier de Zuazo](https://github.com/zuazo))
 * fix oob Buffer at readEntityMetadata (fixed #40) (thanks [Xabier de Zuazo](https://github.com/zuazo))

## 0.8.0

 * fix remaining bugs for 1.5.1 protocol (thanks [Xabier de Zuazo](https://github.com/zuazo))
 * writing packets is 6% faster (thanks [Matt Bell](https://github.com/mappum))

## 0.7.9

 * support minecraft protocol 1.5 / protocol version 60 (thanks [Matt Bell](https://github.com/mappum))

## 0.7.8

 * server: ability to change `motd` and `maxPlayers`
 * server: fix incorrect `playerCount`

## 0.7.7

 * server: fix crash when client disconnects quickly

## 0.7.6

 * onlineModeExceptions are all lowercase now. fixes security hole.

## 0.7.5

 * server: add `onlineModeExceptions`. When server is in:
   - online mode: these usernames are exempt from online mode.
   - offline mode: these usernames must authenticate.

## 0.7.4

 * server: online mode: don't log in client until username verification

## 0.7.3

 * revert removing socket delays to reduce latency as it was causing
   errors and test failures.
 * server: Client now emits more predictable 'end' events.

## 0.7.2

 * fix objectData writer. This fixes sending an 0x17 packet.

## 0.7.1

 * remove socket delays to reduce latency. (thanks [Matt Bell](https://github.com/mappum))

## 0.7.0

 * `createServer`: rename `encryption-enabled` option to `encryption` to stay
   consistent with the examples. (thanks [Robin Lambertz](https://github.com/roblabla))
 * `createClient`: don't require both `email` and `username`.
   - The `username` and `password` arguments are used to authenticate with the
     official minecraft servers and determine the case-correct username. If
     you have migrated your user account to a mojang login, `username` looks
     like an email address.
   - If you leave out the `password` argument, `username` is used to connect
     directly to the server. In this case you will get kicked if the server is
     in online mode.

## 0.6.7

Emit 'error' event instead of crashing when other computers abuse the
minecraft protocol.

Big thanks to [Robin Lambertz](https://github.com/roblabla) for this release.

## 0.6.6

 * ping: fix calling callback twice when server sends kick
 * server: send a kick packet when kicking clients. (thanks [Robin Lambertz](https://github.com/roblabla))
 * ping: include latency property (thanks [Jan Buschtöns](https://github.com/silvinci))

## 0.6.5

 * createServer: allow empty options
 * server: support online mode and encryption (thanks [Robin Lambertz](https://github.com/roblabla))

## 0.6.4

 * Allow minecraft username instead of mojang email. (thanks [Robin Lambertz](https://github.com/roblabla))

## 0.6.3

 * y values when only 1 byte are always unsigned

## 0.6.2

 * 0x0e: change face to unsigned byte

## 0.6.1

 * 0x0d: fix incorrectly swapped stance and y
