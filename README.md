# assignment_4_second_attempt
python class incorporation


def combat(combatChance, playerHealth, maxHealth, playerAccuracy, 
playerDamage):
enemyName = ""
enemyHealth = 0
enemyAccuracy = 0
enemyDamage = 0
# Check to see if we should engage in combat
if combatChance > random.randint(0, 9):
print("You have engaged in combat!")
print()
# Randomly select an enemy
monsterSelection = random.randint(0, 0)
if monsterSelection == 0: # SLIME monster
enemyName = "SLIME"
maxEnemyHealth = 2
enemyHealth = maxEnemyHealth
enemyAccuracy = 5
enemyDamage = 1
print("You have encountered an enemy {0} 
monster...".format(enemyName))
print()
print("It has {0} HP and {1} ATTACK 
strength...".format(enemyHealth, enemyDamage))
print()
else:
print("Error - 'combat' function: 'monsterSelection' value is 
invalid:", monsterSelection)
# Choose a random turn to go first
currentTurn = random.randint(0, 1)
if currentTurn == 0:
print("You have taken the initiative!")
else:
print("The enemy {0} monster has struck 
first!".format(enemyName))
print()
# Take turns
while playerHealth > 0 and enemyHealth > 0:
if currentTurn == 0: # Human Turn
# Get the action the human wants to take
action = input("COMBAT: [a]ttack, [f]lee: ")
while action != "a" and action != "f":
print("Invalid combat choice...")
action = input("COMBAT: [a]ttack, [f]lee: ")
print()
# Engage in combat depending on the action
if action == "a":
if random.randint(0, 9) < playerAccuracy:
enemyHealth -= playerDamage
print("You have HIT the enemy monster! Its HP is: 
{0} / {1}".format(enemyHealth, maxEnemyHealth))
print()
else:
print("You have MISSED the enemy monster...")
print()
elif action == "f":
if random.randint(0, 9) < playerDamage:
print("You have escaped from combat!")
print()
break
else:
print("Error - 'combat' function: 'action' value is 
invalid:", action)
else: # Computer Turn
if random.randint(0, 9) < enemyAccuracy:
playerHealth -= enemyDamage
print("You have been HIT by the the enemy {0} monster! 
Your HP is: {1} / {2}".format(enemyName, playerHealth, maxHealth))
print()
else:
print("The enemy {0} monster has MISSED 
you...".format(enemyName))
print()
# switch turns
currentTurn += 1
currentTurn %= 2
# Announce the winner
if playerHealth > 0 and enemyHealth <= 0:
print("Congratulations! You have defeated the enemy {0} 
monster...".format(enemyName))
print()
elif playerHealth > 0 and enemyHealth > 0:
print("That was a close one! The enemy {0} monster almost got 
you!".format(enemyName))
print()
else:
print("Sadly, the enemy {0} monster was 
victorious...".format(enemyName))
print()
else:
print("Fortunately, there were no monsters in this room...")
print()
return playerHealth



COM S 127 - Assignment #4 Grading Rubric
This assignment was assigned on 10-10-2022
This assignment is due by 11:59 p.m. Friday, October the 21st (10-21-2022). It will be considered 'late' if turned in after this 
time. However, there will be a two (2) day 'grace period' extended until 11:59 p.m. Sunday, October the 23rd (10-23-2022). If the 
assignment is turned in after 11:59 p.m. Friday, October the 21st, but before 11:59 p.m. Sunday, October the 23rd, it will suffer 
at 10% 'late penalty' to the grading. The assignment will not be accepted after 11:59 p.m. Sunday, October the 23rd.
Assignment Objective
The purpose of this assignment is to allow students to become more familiar with the use of 'functions.' This assignment will 
require the use of several 'functions,' as well as the application of 'input validation' to player input. The student will be given a 
pre-coded 'start' file, to which they will have to add several new features. This assignment will also require more substantial use 
of logical thinking to complete its objectives than previous assignments.
Instructions
Students should study the file provided, and notice the various 'TODO' comments. These indicate tasks in the file that students 
should complete by typing in their own original code. These 'TODO' comments indicate items in the script which will be 
evaluated for the final grade on the assignment. The file the student submits must be named dungeonCrawl.py.
The various 'TODO' comments can all be found inside the dungeonCrawl.py start file.
Files Provided
Students will have access to the following 'start file,' which will detail all of the TODO tasks:
dungeonCrawl.py
Example Output
Welcome to Dungeon Crawl...
By: Matthew Holman
[COM S 127 A]
-----------------------------------------------------------------
MAIN MENU: [p]lay, [i]nstructions, or [q]uit?: asdf
Please enter [p], [i], or [q]...
-----------------------------------------------------------------
MAIN MENU: [p]lay, [i]nstructions, or [q]uit?: i
Traverse the dangerous dungeon and collect all the gold...
-----------------------------------------------------------------
MAIN MENU: [p]lay, [i]nstructions, or [q]uit?: p
-----------------------------------------------------------------
You have entered the dungeon in search of gold! What will you find in the rooms beyond?
The room has 10 gold pieces in it...
After taking the gold, you currently have 10 gold pieces in your possession...
[n] ?: n
-----------------------------------------------------------------
You have moved deeper into the dungeon... You sense this is a central crossroads of the dungeon!
Fortunately, there were no monsters in this room...
The room has 10 gold pieces in it...
After taking the gold, you currently have 20 gold pieces in your possession...
[n] [s] [e] [w] ?: e
-----------------------------------------------------------------
You have engaged in combat!
You have encountered an enemy SLIME monster...
It has 2 HP and 1 ATTACK strength...
COMBAT: [a]ttack, [f]lee: a
You have HIT the enemy monster! Its HP is: 1 / 2
You have been HIT by the the enemy SLIME monster! Your HP is: 9 / 10
COMBAT: [a]ttack, [f]lee: a
You have MISSED the enemy monster...
The enemy SLIME monster has MISSED you...
COMBAT: [a]ttack, [f]lee: a
You have MISSED the enemy monster...
You have been HIT by the the enemy SLIME monster! Your HP is: 8 / 10
COMBAT: [a]ttack, [f]lee: a
You have MISSED the enemy monster...
You have been HIT by the the enemy SLIME monster! Your HP is: 7 / 10
COMBAT: [a]ttack, [f]lee: a
You have HIT the enemy monster! Its HP is: 0 / 2
Congratulations! You have defeated the enemy SLIME monster...
The room has 20 gold pieces in it...
After taking the gold, you currently have 40 gold pieces in your possession...
[w] ?: w
-----------------------------------------------------------------
Fortunately, there were no monsters in this room...
You have already visited this room before...
[n] [s] [e] [w] ?: w
-----------------------------------------------------------------
You have encountered a magical shop! You have 7 / 10 HP. Will you pay 15 / 40 gold to heal your wounds?
HEAL?: [y]es [n]o: y
You have healed yourself! You currently have 10 / 10 HP, and 25 gold.
The room has 0 gold pieces in it...
After taking the gold, you currently have 25 gold pieces in your possession...
[e] ?: e
-----------------------------------------------------------------
Fortunately, there were no monsters in this room...
You have already visited this room before...
[n] [s] [e] [w] ?: n
-----------------------------------------------------------------
You have engaged in combat!
You have encountered an enemy SLIME monster...
It has 2 HP and 1 ATTACK strength...
COMBAT: [a]ttack, [f]lee: f
The enemy SLIME monster has MISSED you...
COMBAT: [a]ttack, [f]lee: a
You have HIT the enemy monster! Its HP is: 1 / 2
You have been HIT by the the enemy SLIME monster! Your HP is: 9 / 10
COMBAT: [a]ttack, [f]lee: a
You have HIT the enemy monster! Its HP is: 0 / 2
Congratulations! You have defeated the enemy SLIME monster...
The room has 5 gold pieces in it...
After taking the gold, you currently have 30 gold pieces in your possession...
[n] [s] ?: n
-----------------------------------------------------------------
You sense that the EXIT of the dungeon is just ahead! Will you escape? Or will you keep exploring?
You have engaged in combat!
You have encountered an enemy SLIME monster...
It has 2 HP and 1 ATTACK strength...
COMBAT: [a]ttack, [f]lee: a
You have HIT the enemy monster! Its HP is: 1 / 2
The enemy SLIME monster has MISSED you...
COMBAT: [a]ttack, [f]lee: a
You have HIT the enemy monster! Its HP is: 0 / 2
Congratulations! You have defeated the enemy SLIME monster...
The room has 10 gold pieces in it...
After taking the gold, you currently have 40 gold pieces in your possession...
[n] [s] ?: n
You have escaped with 40 gold from the dungeon!
-----------------------------------------------------------------
MAIN MENU: [p]lay, [i]nstructions, or [q]uit?: q
Goodbye!
Special Notes
NOTE: This assignment is substantially more difficult than previous assignments.
l Completing this assignment may require the student to start their work 'before the last minute.' Please plan accordingly. 
l The student's script CANNOT crash under any circumstances. Any portions of the student's code where the script crashes 
will receive a zero (0) for that aspect of the game. 
¡ For example, if a student's script crashes during the 'combat' section, the student will not earn the point for
implementing that particular feature. 
l Much of the logic in this assignment is the same as in the previous one. The student should feel free to reuse as much 
previously written code as possible. 
NOTE: Assignments turned in in any other format other than a .py file will not be accepted.
l Screenshots of code will not be accepted. 
l .sln files are not code files - they contain no Python code and will not be accepted. 
l .zip, .rar, .tar.gz, and other compressed files will not be accepted. 
l If a student's submission is not in a .py file, it will not be graded. 
¡ THIS WILL LEAD TO THE STUDENT RECEIVING A ZERO (0) ON THE ASSIGNMENT.
NOTE: Submitting the assignment on Canvas may result in either an error message or a 'spinning blue circle' on the 
submission page. This is the normal/ expected behavior.
l So long as the top of the page reads 'Submitted' in green text, there should not be a problem. 
l The student can email a Graduate TA/ UGTA to confirm the status of their submission. 
Grading Items
l (Due Date AND File Name) Was the assignment turned in by the due date, AND is the file named dungeonCrawl.py?
______ / 1 
l (Name In Script AND Delete First TODO AND Name In Output) Has the student typed in their name/ date/ assignment 
number at the top of the dungeonCrawl.py file, AND did the student delete the first 'TODO' comment in
dungeonCrawl.py such that the first thing in the file is their name/ date, AND Has the student added their name/ section 
number to the initial script output?: ______ / 1 
l ("p" Section Tasks) Has the student completed the "p" section tasks?: ______ / 6 
l ("i" Section Tasks) Has the student completed the "i" section tasks?: ______ / 1 
l ("q" Section Tasks) Has the student completed the "q" section tasks?: ______ / 1 
TOTAL ______ / 10
