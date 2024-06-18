# Not Jetpack Joyride
## A Class Project to Recreate a Popular Mobile Game

### Leah Taurisano, Technical Lead

### Clone Link
```
git clone https://github.com/LeahTaurisano/NotJetpackJoyride.git
```

### Build Instructions
- Open the project in Unity version 2022.3.23f1
- Navigate to the File header, and select Build Settings.
- Click the Build button in the bottom right, and select the folder to save the build into.
- Navigate to the folder and run the generated .exe.

### My Role as Project Technical Lead

A large part of my contribution to the project was as a technical supervisor. I managed pushes to the github, handled several merge conflicts, and bug fixed and refined several other people's contributions, as well as restructuring them to work together for the game.


- I managed at least one pull request from each team member per week, approximately seven a week. Typically they would all come very last minute before class, and as such I would quickly need to review, bugfix, and potentially reject requests.


- On top of this, in class there would typically be several additional pull requests for me to review and manage, ensure it was working properly and would fit with the structure of our game, and then connect to the main system upon merging.

I also was the primary person in charge of managing our primary Scene. I set up positioning, tested spawn locations, handled setup for the killbox and the killbox's functionality of cycling the background, and helped manage object layers.

In this video you can see the general layout of the scene view, examples of object spawning behavior, and the background cycling as it passes the killbox on the left side of the screen.
![EntitySpawning](https://github.com/LeahTaurisano/NotJetpackJoyride/assets/138742041/d5171942-596c-42de-9416-6a8ace211eac)

### Creating the Entity Spawn Manager Responsible for Handling all Objects Spawning in the Scene

My primary coding contribution was the Entity Spawn Manager. This class handles all spawning objects from coins to hazards by connecting Generators to each object's respective Manager, then all together to the Entity Spawn Manager.

Generators are objects containing the base spawning and behavior functionality of each entity spawned into the game. These were mostly created by other programmers, only modified by me to fit the system or to fix errors.
- Since many of the generators were initially designed by their respective programmers in testing scenes, I would frequently need to edit the logic of their spawn methods to be more modular to fit the random spawning system of the game. 
- Occassionally, as with the scientists, I also needed to add their base spawn functionality since they were tested without one.


Each Generator has a corresponding Manager. The Manager's job is to standardize the spawning methods, and to provide a quicker way to find relevant Serialized parameters for spawning purposes. Each Manager is then provided to the Entity Spawn Manager. This separation also acts as a security layer, allowing the base generator to be edited or changed freely without necessarily affecting the Managers.

An example of code from one of the managers, the Zapper Manager, my coding style tends to favor easily readable code.
![ZapperManager](https://github.com/LeahTaurisano/NotJetpackJoyride/assets/138742041/6c6010c3-c097-4fe4-aaad-0c1e0b7fe06a)

The Entity Spawn Manager has delays for each relevant object to allow for easy changes to the spawn timing for each entity. It runs several simultaneous timers and instantiates each entity at the relevant time, also handling randomness within the spawns for variety.

![EntitySpawnManagerGraph](https://github.com/LeahTaurisano/NotJetpackJoyride/assets/138742041/7af233b1-4ab5-4cca-809b-8e6cc1c647ac)

Here we can see a flowchart representing the Entity Spawn Manager. 
- Certain spawnable objects are in a pool with other obstacles to avoid certain situations, such as coins being uncollectable from being covered by a zapper, or a laser locking you in place only for an unavoidable rocket to hit you.
- Every frame the Entity Spawn Manager iterates the timers for each entity pairing.
- When a timer reaches 0, a random entity from the pair is spawned, and the timer is set to that specific entities spawn delay.
- Entities in pairs have distinct spawn delays to prevent unwanted overlaps, such as lasers having a long delay to give time for the animation to finish before the system can spawn another rocket.
- The individual delays are all easily adjusted through serialized fields to allow for quick on the fly adjustments to suit gameplay flow.

### Finalizing Spawn and Movement Behaviors for the NPC Scientists

I finished and connected the Scientist system to have them spawn in and animate properly when responding to the player flying. 

I also made them spawn in packs of a random number, with random distance between them, to  add to the realistic feel of finding groups of people.

![ScientistsSpawnGroup](https://github.com/LeahTaurisano/NotJetpackJoyride/assets/138742041/f7cfe38d-aab1-4bb0-a580-919341295e5e)

### Coin Collecting Functionality and Particle Effects
Additionally, as the programmer responsible for connecting the several systems, I created the system to allow the player to collect coins on touching them, and also connected the particle effect to this action.

![CoinCollecting](https://github.com/LeahTaurisano/NotJetpackJoyride/assets/138742041/e7db3984-0f1f-4274-8950-c9782e9637db)

## Other Contributors
![image](https://github.com/NicholasOkovic/NotJetpackJoyride/assets/139954443/c822852d-919a-49d6-b377-ee0781258936) https://github.com/SleepingDragon0

![image](https://github.com/NicholasOkovic/NotJetpackJoyride/assets/139954443/f2c4675a-b38a-4551-8ac2-e0234ec5df36) https://github.com/NicholasOkovic

![image](https://github.com/NicholasOkovic/NotJetpackJoyride/assets/139954443/0ac794c1-d76e-4cc7-be9f-8a6e3dc693dc) https://github.com/twdaviss

![image](https://github.com/NicholasOkovic/NotJetpackJoyride/assets/139954443/7c19a2af-05cf-49fa-9c1e-d1d088b4a17c) https://github.com/CultyMarble

![image](https://github.com/NicholasOkovic/NotJetpackJoyride/assets/139954443/859b874c-3a0c-44f5-9062-506bad1ea22e) https://github.com/PhiBeo

![image](https://github.com/NicholasOkovic/NotJetpackJoyride/assets/139954443/3ddd6336-0f50-485b-8698-ac1541474f4a) https://github.com/MiguelAyala25
