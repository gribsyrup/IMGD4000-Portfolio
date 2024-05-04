## 1. Your role in the project
For this project, I served as one of the programmers on the tech side. I was also the team face for communicating with the professors and designing/updating the site. My responsibility as a programmer was to implement the ground level features to make sure the game properly worked rather than the runes, which were more of the unique abilities. Some examples of what I did are applying meshes and animations, creating the ability to switch between levels using triggerboxes (and refining that later in the process to create specific start points to create a sense of progression and flow between levels), creating and refining the golem blueprint to give them proper AI, and implementing a proper game instance in order to save variables across levels. <br> <br>
## 2. The challenges you faced <br>
### Broad Perspective: 
I struggled a great deal working on this project. From a broad perspective, Unreal was brand new to me at the time, as for my career at WPI I often chose to work on Godot for projects. However, blueprints ended up being surprisingly easy to grasp and I ended up having a good time working with them. In addition, another big problem that I faced was time constraints, as for the first two weeks of the term I was overloading due to an ISP that spilled over. This led to the art assets being implemented at a very slow pace and ultimately boiled over to our alpha being underbaked, lacking a lot of the actual content that was present in the final version since the player could not do anything but grapple and glide. Finally, the third broad problem that presented itself was the smaller team size - instead of having four tech students like all other groups, we only had three. In addition, Han focused on SFX rather than mechanical implementation, so between James and I the workload was a lot tighter. We were able to get our project into the state we wanted, but it took a lot of effort. Our version control also posed a big problem, but that will be covered in the version control section. <br>
### Technical Implementation: 
In terms of technical problems we faced during our alpha, the primary one that concerned me was the implementation of progression. During the alpha, it would often reset the player’s progress (health/collectibles) after traversing across the screen. In the same vein, when players re-entered the cave after leaving it, they would reset to the bottom of the cave, causing them to lose ALL progress while also potentially rendering the game un-completable because they would lose any gears from the mountain level. <br> <br>
## How you overcame those challenges, including specific APIs used and code fragments (both Blueprints and C++) <br>
### Broad Perspective: 
Unreal was a challenge to learn, but the knowledge came quickly thanks to the professor’s guides and other tutorials available online. This combined with the overload made it a harsh start to our project, but we started meeting more frequently and putting more time into the project after the first alpha, which led to us refining the product and really making it shine. One of our biggest goals for playtesting was to make the game feel more like an actual game and less like a sandbox, and I would say we succeeded. 
### Technical Implementation:  
I addressed the progression issue with two of unreal’s built in classes: The GameInstance and the PlayerStart. The GameInstance was extremely useful, but I also think it was quite difficult to set up. It allowed us to carry over variables between both levels we were using, including health and collectibles. It even allowed us to carry runes(like camouflage) over, but we decided not to use that code since the runes were only in the mountain level. 
![GameInstance](/images/GameInstanceEvents) <br>
The Implementation of the GameInstance involved the calling of Events created in the ThirdPersonCharacter, which were bound to certain event calls. These would update and store these values in the game instance, where they would then be set to the player to be called once the level changed. These are included below: <br>
![Health](/images/ThirdPersonCharacterHealth) <br>
![Collectibles](/images/Collectibles) <br>
As for preventing the player for restarting from the bottom of the cave, what we used was a blueprint triggerbox that was set up to take both a level name and PlayerStart using a specific string. This allowed us to both create a default LevelStart on Startup as well as allow the player to start from a specific location once they had exited the cave at least once.  <br>
![LevelChange](/images/LevelChange) <br>
Below is the code we used to make sure that a specific PlayerStart was used on startup: <br>
![](/images/ThirdPersonGameMode) <br> <br>

## 4. An architectural diagram(s) that roughly portrays the architecture of your final project and then shows the design of your specific parts in more detail. This might include UML, control flow diagram, networking diagrams etc. <br>

Here is a broad overview UML Diagram: 
![UML](/images/ScalingTheSummitUML)

Here is a detailed overview of the GameInstance: 
