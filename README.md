## GGAC+R GGPO-BASED CASTER

(TODO: insert ggpo repo link)

It's happening, but no code will be written that hooks up with GGPO until we understand the game state completely.

Thanks to GGPO's recent switch to open-source, it is now possible to write casters without building an entire netcode from the ground up.

In fighting games, latency hurts more than in any other variety of game.  Games that do well in that department (even casters)
are few and far between (MBAACC's caster by madscientist, Killer Instinct, Skullgirls (also GGPO))

Currently there's just a CE table trying to gather game state so that it can be collected and synchronized through GGPO.

Feel free to contact me with any questions pretaining to **this caster** (two casters is far out, man)

If you'd like to communicate with me and help out, also reach out to me through the following:

Twitter: @MemeMongerBPM 

Discord: @Labryz#5752     

Looking for C++ devs that can hook ASM and/or navigate GGPO source.

Also looking for people like me who can take this game apart to try and understand what's going on under the hood.

You don't have to be either of the above, just reach out with your questions/comments/concerns.
 

Below are the big TODOS/Requirements that need to be finished and questions that need to be answered.

Feel free to answer.  Please. :D

#### Bigger Problems

* Skipping straight to 2P versus
* If we can't skip to PvP, how will this get to vs?
    * If unable to skip, find a menu input buffer and lock everyone out until 2P Vs.
* Synchronizing match start after stage pick
    * Uneven load times might even affect inter-round time as well
* What do we synchronize on mid-match?    
* How do we stop the game without it not responding for slower loaders (into or out of the match) to catch up?


#### Less big problems

* Where's Player 2's buffer?
* Which of the (currently 3) input buffers gets written to first?
    * If you intercept the first, will the others follow suit?
* Caster first which launches +R, but will it work launching the raw +R exe with some stuff in it?
* Find out stage IDs, still unknown, will be useful.

    

#### Input Buffer:

Currently there are three of them for P1 (AFAIK)
* All three independent of button settings
* All three independent of KB/Controller
    * May cause KB vs Controller issues...
* All three are 2 Bytes Long

Directions: (Bytes)

* Up: 10 00
* Right: 20 00
* Down: 40 00
* Left: 80 00

Buttons: (second byte)
* P: 00 40
* K: 00 20

(these next three i need to check)

* S: 00 80
* H: 00 02
* D: 00 01

Start needs to be blocked at all times, select only when a player hasn't picked a character yet (or maybe also blocked all the time, I don't know...)




