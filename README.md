# Hex Ships Game Design Notes

## Summary

Hex Ships is a turn based tactical combat game on a hex grid.

It represents spaceship combat in a fictional universe.

Its core mechanics are ship movement, energy management, and managing damage across the different sides of the ships.


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
Level 2: + 1 Initiative
Level 3: 1 X Reroll per Battle
Level 4: + 1 Initiative
Level 5: Second Reroll per Battle
Level 6: + 1 Initiative to entire fleet when included in deployment

### Gunnery Levels
Level 2: - 1 to hit difficulty on all attacks
Level 3: First missed shot of a battle with a weapon that fires ammo does not use ammo
Level 4: - 1 to hit difficulty on all attacks
Level 5: Can attack multiple targets in the same turn
Level 6: - 1 to hit difficulty on all attacks

### Engineering Levels
Level 2: + 1 energy recharge per turn
Level 3: Can use the Afterburners ability 1 x per battle
Level 4: + 1 energy recharge per turn
Level 5: Can repair 1 Critical damage per game
Level 6: + 1 energy recharge per turn
