# Moxie messaging

a better way to default to safety

---

main system


first message sent includes `secure layer` message containing 
> Alice: "hey I'm on matrix, are you?"


second message sent will not include any more `secure layer` content, unless user specifies to resend handshake within conversation settings
> Alice: (N/A)


upon receiving a `secure layer` request, the client will prompt the user for handshake
> Bob - [ Alice wants to handshake ]


upon handshake request, user may decide one of three things
1. > Bob - yes
  * prompts end of handshake
  * convo will be moved to new protocol

2. > Bob - no
  * prompts end of handshake
  * convo will remain where it is
  * both clients will no longer attempt to find `secure layer` messages

3. > Bob - "ghost"
  * does not end handshake
  * Bob's client pretends it never saw the message and is on a non-moxie client
  * Bob's client will no longer attempt to find `secure layer` messages


> Bob - no
upon receiving no, client will no longer attempt to find `secure layer` messages


> Bob - "ghost"
client will never receive "ghost", as it's never sent


> Bob - yes
upon receiving handshake "yes", client will prompt user to send own matrix username
> Alice: "alice@home.server"

1. upon receiving hash and username, client can decide whether to finish handshake, or cancel
> Bob - alice@home.server


> Bob - yes
  * finalizes handshake
  * client sends hash of own username as activityPub message
  * client takes received matrix username and inits connection through matrix protocol

> Bob - no
  * prompts end of handshake
  * convo will remain where it is
  * both clients will no longer attempt to find `secure layer` messages

> Bob - "ghost"
  * Bob's client pretends it never saw the message and is on a non-moxie client
  * Bob's client will no longer attempt to find `secure layer` messages

upon receiving a matrix message, check if incoming username hashes to a received handshake
if yes, tie the two together
> Alice 

---


