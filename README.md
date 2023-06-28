# Hex Ships Game Design Notes

## Contents
1. [Summary](#Summary)
2. [Units](#Units)
    - [Silhouette](#silhouette)
    - [Shields](#shields)
    - [Unit Energy](#unit-energy)
    - [Weapon Hardpoints](#weapon-hardpoints)
3. [Captains](#captains)
    - [Command Levels](#command-levels)
    - [Gunnery Levels](#gunnery-levels)
    - [Engineering Levels](#engineering-levels)
4. [Campaign Management](#campaign-management)
5. [Weapons and Attacks](#weapons-and-attacks)
    - [Weapon Accuracy](#weapon-accuracy)
    - [Damage Order](#damage-order)
    - [Critical Damage](#critical-damage)


## Summary

Hex Ships is a turn based tactical combat game on a hex grid.

It represents spaceship combat in a fictional universe.

Its core mechanics are:
- ship movement
- ship facing
- weapon facing
- energy management 
- managing damage across the different sides of the ships
- managing damage across shields, armor, and hull
- multi battle campaigns with a persistent fleet
- managing fleet in between battles


## Units

Each play piece is a unit.

The basic unit of Hex Ships is a capital ship.

Most units will have the following attributes:
1. Hull Structure (Current/Max): how much damage the unit can take before being destroyed
2. Base Initiative: starting initiative value for this unit before captain bonus
3. Armor Faces (Current/Max): armor plating in front, right, left, and rear of the unit that absorbs damage before it affects the Hull Structure
4. Shield Faces (Current/Max): energy shielding that absorbs damage in front, right, left, and rear of the unit before it affects the Armor Plating, shields can be recharged
5. Shield generator: The maximum number of shield points that can be regained in a single round
6. Size: effective size of the ship (for tie breakers and certain mission limitations)
7. Silhouette: How big the ship appears to enemies from the four faces. Only 2 values here, front to back, and side to side
8. Max Speed: the maximum number of spaces this ship could move in a single movement phase
9. Current Speed: the number of spaces this unit must move this loop,  negative speed indicates moving in reverse
10. Thrust Rating: positive and negative values indicate how much this unit can increase or decrease its speed in a single movement phase. 
11. Maneuverability: how many hex face rotations a unit can make in a single movement phase 
12. Energy Cells:  How much energy the unit currently has available for firing weapons, charging shields, and special abilities
13. Max Energy: The maximum number of energy this unit can have at once
14. Energy regen: how much energy this unit gets back at the beginning of the play loop
15. Energy Disruption: how much EMP damage this ship has taken.  If it gets to high, the ship becomes disabled.
16. Weapon Hardpoints: Slots that can hold turrets or weapons. They have a facing and allowed weapon types



### Silhouette:
When an attack is made against a ship, it takes into account the silhouette the ship presents to it as how difficult it is to hit.
The larger the silhouette, the easier to hit.  The smaller the silhouette, the harder to hit.
Silhouette sizes are as follows
Mini:  +5 to hit difficulty (represents fighters, bombers, other very small craft) ** for an expansion with squadrons
Tiny:  +2 to hit difficulty
Small: +1 to hit difficulty
Medium: 0 change to hit difficulty
Large: - 1 to hit difficulty

Some units are smaller from the front and larger from the sides.
Other units are larger from the front and smaller from the sides.
Finally there are some units that have the same silhouette from any direction.

### Shields
The shield charge action is performed during the movement and action phase
Shields cost 2 energy to restore 1 shield point
A shield may not be increased higher than its max value
Shield charge action may not be performed more times than the units Shield generator value in a single turn

### Unit Energy
Units use energy to charge shields, fire weapons and use special abilities

When a target is selected during the attack phase
the game will automatically try to enable any weapon that can reach the target
It will go through the weapons sequentially in order of highest power cost to lowest power cost
If the remaining energy exists to fire a weapon it will be auto enabled
Game will keep track of how many weapons have been enabled so far and how much total energy is available
Otherwise it will be skipped and the next weapon will be attempted

Players can manually disable weapons to avoid using the energy
Players can manually enable weapons if enough energy is available

Units replenish their energy based on their Energy Generation value at the start of each turn
Units may not have more energy than their Max Energy value

Some special abilities cost energy such as Afterburners

### Weapon Hardpoints
Ships weapons are located in hard points

A hard point represents a turret or fixed weapon mount

Fixed weapons can fire directly down a row or column out of a single hex face

Turrets have a field of fire, ranging from 2-6 hex faces

## Captains

Each ship has a captain with 3 skills with ranks from 1-6
The 3 skills are:
- Command
- Gunnery
- Engineering

A level 1 captain will have 1 rank in all skills
Each level up provides 1 point that can be used to rank up a skill
Max level for a captain is 10

### Command Levels
- Level 2: + 1 Initiative
- Level 3: 1 X Reroll per Battle
- Level 4: + 1 Initiative
- Level 5: Second Reroll per Battle
- Level 6: + 1 Initiative to entire fleet when included in deployment

### Gunnery Levels
- Level 2: - 1 to hit difficulty on all attacks
- Level 3: Reduce speed of target penalty by 1 to a min of zero
- Level 4: - 1 to hit difficulty on all attacks
- Level 5: Can attack multiple targets in the same turn
- Level 6: - 1 to hit difficulty on all attacks

### Engineering Levels
- Level 2: + 1 energy recharge per turn
- Level 3: Can use the Afterburners ability 1 x per battle (increase speed by engine rating +1, can exceed max speed by 1 for a turn)
- Level 4: + 1 energy recharge per turn
- Level 5: Can repair 1 Critical damage per battle
- Level 6: + 1 energy recharge per turn


## Campaign Management

The game is played in a campaign usually consisting of several battles.

The Player's fleet that may be managed in between battles.

In Between battles a player can:
- Assign skill points of Captains that have leveled up to the 3 ability scores
- Place damaged ships in "Repair dock" to be repaired during the next battle
- Select which units will participate in the upcoming battle
- Start the next battle with the selected units (may not start the battle with no units)

## Weapons and Attacks

There are 7 types of capital ship weapons

- Lasers: Basic energy beams that maintain high accuracy but the damage drops off over range
- Heavy Lases: higher energy requirement than standard lasers but lower damage drop off over range
- EMP Beams: Energy disrupting beams, high damage to shields, low to armor and hull but with an energy generation disruption affect. Range slightly limited.
- Ballistic Cannons: High velocity projectile launchers.  Accuracy drops over range but damage stays consistent.  Uses Ammo.
- Missiles:  Guided explosives.  At least one missile in a barrage always hits. attack roll is for number of missiles that hit.  Damage from a missile hit does not bleed through defensive layers.
- Rockets: Unguided explosives. Accuracy drops significantly over range. Also does not bleed through layers but does more damage than missiles.
- Torpedoes: Special explosive with a unique shield penetration ability.  Very difficult to hit with but high damage.  Ignores shields.  High risk, high reward weapon.  fixed firing angles


Weapon damage is balanced so that the expected damage of any one weapon over a 10 round battle is very near to each other.
Exceptions are torpedoes and heavy lasers which should have somewhat higher than expected damage due to low ammo for torpedoes and higher energy cost for heavy lasers
EMP Beams are a special control weapon that is not balanced for damage.

Total expected damage is:
 (damage * accuracy * number of attacks)

 Balance is based on energy weapons can fire 8 out of 10 turns in place of ammo.

### Weapon Accuracy:

Attacks are rolled on 2 d6 die.  (2 random numbers between 1 and 6)
If the value on the 2 die are greater than or equal to the difficulty of the attack, the attack  hits.
1 roll is used for all attacks for simplicity

For example if you have torpedoes with a to hit difficulty of 11 and lasers with a to hit difficulty of a  7 and the attack roll comes up 8,  then the lasers will hit and the torpedoes will not.

Weapons each have their own accuracy rating but the actual difficulty is affected by other factors.
Captain Gunnery skill reduces the difficulty
Unit Silhouette can increase or decrease the difficulty
Unit Speed can increase or decrease the difficulty

Difficulty to hit is generally determined as follows
Base weapon hit difficulty - Captain Gunnery Skill bonus + Target Silhouette Penalty/Bonus + Target Speed Penalty/Bonus

Further hit difficulty bonuses or penalties may be added to the design later
such as Electronic Counter Measures which increases difficulty to hit in an aura around the ship
Anti Missile Systems that remove missile hits

### Damage Order

Damage from weapons should be applied in the following order
1. Laser weapons
2. EMP Beam weapons
3. ballistic weapons
4. missile weapons (missiles and rockets)
5. torpedo weapons

Representing the speed at which the weapons reach their target

Damage to the target is applied in the following order
1. Target Shield on appropriate face
2. Target armor on appropriate face
3. Target hull

with the exception of torpedoes which bypass the shield

### Critical Damage
Attacks that hit the internal hull of a ship have a chance to do critical damage

Any attack that hits on a 12 (two sixes)
counts as a critical
also torpedoes always cause a critical if they damage the hull

Critical hits have different effects depending on which side of the ship was hit

If a critical is rolled,  a follow up roll of 1 d6 determines what damage was done

For the front of the ship:
1.  no damage
2. Forward Weapons:  one of the weapons that can fire with the forward arc is disabled
3. Forward Weapons: "
4. Forward thrusters: ship cannot reduce speed
5. Sensors: +2 difficulty of all this ships attacks
6. Bridge:  Captain skills are reduced to 1 for all skills to a minimum of 1

For the side of the ship:
1. no damage
2. side weapon
3. side weapon
4. side thrusters: ship must roll a 7 or higher on 2d6 to successfully rotate for each maneuverability point spent
5. Communications: captain can no longer use special abilities 
6. Life support: All captain skills reduced by 1 to a min of 1 (cannot be reduced to 0)


For the rear of the ship
1. no damage
2. rear weapon
3. rear weapon
4. Engines: max speed reduced by 1
5. Engines: max speed reduced by 1
6. Shield generator: all shields immediately drop and cannot be regenerated