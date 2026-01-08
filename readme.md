# Billionaire Blast
##### A Game by William Wang
## January 7, 2025: Alpha 1.1.0 release

## Introduction
Billionaire Blast is a game based the old style of bullet-dodging games. You fly through space as a ship shooting down enemies and eventually you get to the boss. Although many typical features of conventional "bullet-hell" games are missing, such as weapon power ups, pickups, a wider variety of enemy and bullet patterns (not to mention proper optimization for spawning many bullets), the core gameplay mechanics remain the same.

However in Billionaire Blast, unlike traditional games where the score and the player health are separate, here they use the same resource. When shooting, and also when getting hit, the player loses money. The score at the end of the game is determined by how much damage they can output onto the boss, which depends on how much money the player has by the end of the game.

Perceptive players will notice a similarity between the amount of starting money and boss health with the median and top net worth of individuals. Thus a single player is unable to defeat the boss alone, but many players combined can eventually whittle down the health after many playthroughs. This is to encourage multiple play throughs as well as to encourage people to share this game with others.

## Controls
* The arrow keys move the ship.
* `Z` or `Space` shoots a bullet.
* Swap bullet strengths with `Q` and `E`, or with `X` and `C`. Stronger bullets deal more damage and are bigger, but cost more money to shoot.
* Holding `Shift` will cause you to move more precisely.
* `Esc` brings up the pause menu in game.

Theoretically, joypad controls should also work, although these are not tested. These are the implemented buttons (Xbox style controls):
* `RT` shoots
* `RB` and `LB` swaps weapons
* `A` slows you down
* `Menu` pauses

## Development
Billionaire Blast was developed in Godot using GDscript over the course of about a week, working part time. This is my first game using the Godot engine and so this project was an opportunity to develop a simple game while learning the engine. Overall, the transition was fairly painless due to the pythonic nature of GDscript, with only minor adjustments needed to typical script organization and node hierarchy due to the limitations/features of the engine. 

In developing this game, I have created simple player controllers, instantiating objects, game managers, tools/gizmos, particle effects, user interfaces, networking, and the creation of modular resource blocks to represent both the shooting and movement pattern of the enemies, as well as how they spawn.

For the assets, all of the sprites were made from scratch while many of the sound effects and music were taken from FreeSound.org with the Creative Commons 0 license. The art style was chosen as low resolution pixel art to make it easier for me to come up with "convincing" sprites, as I am not a pixel artist. These sprites are also lacking in significant animation and effects when they move or shoot.

To accomplish the "server-wide" boss health, simple networking was implemented using a Firebase backend. This includes player login and player stat tracking, along with a basic form of player progression for logged in players. This also served as a learning experience as this is my first game that implements any sort of networking. 

## Future Updates
I currently have some future ideas for polish, such as cleaning up some of the animations, sprites, and sound effects. In the future, I aim to replace all of the sound and music assets with my own.

Gameplay wise, additional waves or enemy variations and bullet patterns could be implemented. A level select may be better than a simple difficulty modififer and actual boss attack patterns could prove more interesting than the current implementation. 
In particular, the addition of a laser weapon could be implemented for enemies and for players.

Beyond that, further networking implementations could be added, such as further player progression with some sort of currency or upgrade system. 
There could also be a leaderboard that keeps track of the players who have dealt the most damage so far. I would also spend some more time developing the security rules and data validation on Firebase, as well as possibly implementing AppCheck reCAPTCHA as well as deploying some cloud functions.
Eventually, I want to allow players to sign up with an account with their current stats even if they started the run without signing in (i.e. convert anonymous account to real account). I mainly need some way to purge anonymous accounts that do not get converted (through cloud functions or some other method).
