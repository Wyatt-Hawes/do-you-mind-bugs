# do-you-mind-bugs
A small game made with a couple of friends as a group using the free version of the Construct 3 creation engine

# How to view the code
- Visit [https://editor.construct.net/](https://editor.construct.net/)
- Download the do_you_mind_bugs.cp3 file
- Open the file inside the Construct Editor
- Enjoy!

# Clever Engineering
------
Construct 3 only allows 50 conditional statements in the free version. This means that in order to make a game (especially an RPG) you need to be clever with how you use your 50 conditionals as even a simple "If these two objects collide" uses a valuable conditional statement. Here are some of my favorite workarounds I found. 

- In order to deal with all player animations with a single conditional. The 4 directional animations are simply labeled as 0, 1, 2, or 3 and are attached to the current "Mood" of the player. For example, if I wanted the "Angry player facing right" animation, it would simply be called Angry0. Since the mood of the player is a variable that is attached to the player. We can use the angle of the player's current movement direction to figure out which animation to play. By using the equation ```floor((angle(Player.X, Player.Y, Player.X + X_Movement, Player.Y + Y_Movement) + 90) / 90)``` We can map the direction the player is moving to 0,1,2, or 3. This allows us to always set the player's animation to their "Player.Mood + direction_map" every tick which handles our need for every animation that we need to play in all 4 directions, all 4 moods, and all weapon animations without using any conditionals. By labeling our animations correctly, the single line of code in construct ```Set Player Animation to: (Mood) + direction_map + weapon_animation``` handles all of our animations perfectly. It is worth noting that all of these values are converted to strings so they can be concatenated.
- We are able to figure out if the player has picked up certain weapons (Painting or cooking in this case) while only using a single conditional (to pick them up) by making all the weapons a single entity with an internal value. This value will either be 1 or 10. We then add this number to the players "Weapon pool" so we can simply check if the player has picked up a weapon by using / or % to 'extract' the ones or tens place when we attempt to use the weapon. 
