---
layout: post
title: CS7496 Computer Animation Final Project: The other side
categories : [projects]
---

This was our final project for CS7496 Computer Animation at Georgia Tech. We were given a scene with a character who could be controlled by specifying his desired joint angles and internal forces. In this scene there is a a huge gap between two platforms that we have to cross and some monkey bars above. The project was completely open ended, our only goal was to cross the gap.

To solve this problem, I first started tinkering with the code a bit, to see how each parameter affects the character's actions. The skeleton code already had a demo for jumping and grabbing, and also an IK solver written in a few lines which took us a whole separate project to implement without using the built in functionalities of DART for this. I figured out how to jump higher and at the desired angle, by making the character crouch deeper and lean more forward.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=iCCONe6ODjw
" target="_blank"><img src="http://img.youtube.com/vi/iCCONe6ODjw/0.jpg" 
alt="VIDEO: Initial tries" width="240" height="180" border="10" /></a>

The most obvious solution for the project was to use the bars to cross the gap, so next I had to figure out the optimal time to release the bars. I added an option to release the bar on a key press and timed the swing time and our velocity at the moment of release. Based on these I set minimum velocity requirements to release the bar. My solution was not very robust, since it did not take into account the distance of the other platform. A much better solution would have been to take our velocity's X component and check if we can travel forward enough in the time we would hit the ground. Or just accelerate our swing as much as we can and release when we are hanging -45 degrees (if 0 degree is at (1, 0, 0)) from the bar.

Since I had plenty of time till the deadline, I decided to fool around a bit and implement a nice method for landing. I chose a backflip, since it has very simple physics behind it so it was easy to code. To do a backflip, you just have to jump straight up, and the human body arches back a bit naturally, so you have to just tuck your arms and legs to flip over. While swinging forward on a bar, the condition of arching back in the air is already met, so we just have to tuck. I also added some variations for fun.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=2M515wQdfJE
" target="_blank"><img src="http://img.youtube.com/vi/2M515wQdfJE/0.jpg" 
alt="VIDEO: Backflip to oblivion" width="240" height="180" border="10" /></a>

Now that my character knew how to break his neck in style, I focused on gaining momentum while swinging on the bar. As a veteran playground swing user, I had the intuition how to do this: Swing my legs forward when travelling forward and arch my back when going backward. I also added a bit of delay when to initiate these poses, because that way it's more optimal. The result was more than satisfying, we actually has enough momentum, to ignore every other bar and just swing through the whole gap! Sometimes the character would bump its head or toes in the other bars, so I had to tilt its head forward and point its toes.

Only one thing was left. Jumping up to the bars. The skeleton code included a jump that could reach the second bar, but our second scene included randomized positions for the bars, so it would fail there. I configured the jump to succeed in reaching the second bar in every scenario and that was enough for my character to pass all three test scenes.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=W_a4lH0vZ5o
" target="_blank"><img src="http://img.youtube.com/vi/W_a4lH0vZ5o/0.jpg" 
alt="VIDEO: Final versions" width="240" height="180" border="10" /></a>

I really liked this project for its open endedness. My solution was not quite robust, but I didn't see any need for it if we has three similar scenes. For a better, more general solution I could have used target landing detection for releasing the bar, a part for determining which bar to jump up to and a method to swing from bars to bars. On the final presentation day, I saw many funny and creative solutions, like tripping over the edge to be able to catch the opposite platform and pull ourselves up, or some nice, but sadly imperfect attempts at travelling between bars.