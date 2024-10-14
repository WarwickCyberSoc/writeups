## Join the Wild Hunt
You can view the source code for this challenge at: https://github.com/peterw18/Intake24

### Introduction
My apologies (but not really!) to anyone playing the game with the volume up at an inappropriate time.

This is a JWT (JSON Web Token) tampering vulnerability.

You must edit the leaderboard, but when attempting to edit it using the button (or by editing the outgoing request), it will return an *unauthorised* message.

There is *auth_token* cookie available for viewing in the developer console which is a JWT with a *rank* parameter. This must be changed to *admin* to have the necessary authentication.

### Playing the game to achieve leader-board score
Impossible. My deepest apologies.
The difficulty scales too quickly and there's a cooldown for projectile launching.

### Cracking the JWT
It is possible to read the content of the header and payload of the JWT (for more information about JWTs, have a look at https://jwt.io/introduction).

To create an authorised JWT, you will need a valid signature - a hash of both the header and payload content, however, this will require the key used to sign the original JWT.

1. Copy the entire content of the JWT (*eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyYW5rIjoiY2xpZW50In0.UhhF7PAFjSVcqrkEaywF9BkR2RJRvvc4v39nUEm2Wic*) to a file.
2. Using hashcat, or a similar too such as John, run a wordlist attack against the JWT:
```
hashcat -a 0 -m 16500 jwt.txt /usr/share/wordlists/rockyou.txt

# -a 0: wordlist attack
# -m 16500: a JWT is the target
```
3. This should (if not, double check the JWT is identical and you've copied the entire token) successfully crack the key, with any decent wordlist, which you can then use to sign the JWT.
4. Edit the JWT (I use https://jwt.io, but other methods are available) to edit the *rank* to *admin* and sign the token with the cracked key.
5. Paste the new JWT into the *auth_token* cookie value and attempt to edit the leaderboard either using the button or by request editing.