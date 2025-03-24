# T11: The Legend of Tuna: Breath of the Catnip

## Instructions

Please replace each `**Replace This Text With Your Response**` with your answer.

___

## SECTION 1

1.a. First, discuss with your team and assign yourselves roles. Try to pick the role you’ve had the least experience in.

```
    |                 | Monday | Wednesday | Friday |
    |-----------------|--------|-----------|--------|
    | Driver          |        |           |        |
    | Navigator       |        |           |        |
    | Quality Control |        |           |        |
```

___

## SECTION 2

2.a. Look at the three Python files in the repository. Identify below all of the classes, and a brief description of
    what each one represents:

```
    **Replace This Text With Your Response**
```

2.b. Look more closely at the **t11_game.py** file. There are 8 lines; identify if they are 
    a) instance parameters
    b) method calls within the class
    c) method calls to another class or library

(Some are more than one answer!)

```
    self.size = 800, 600                              # **Replace This Text With Your Response**
    self.running = True                               # **Replace This Text With Your Response**
    pygame.init()                                     # **Replace This Text With Your Response**
    self.screen = pygame.display.set_mode(self.size)  # **Replace This Text With Your Response**
    self.clock = pygame.time.Clock()                  # **Replace This Text With Your Response**
    self.player = Player(self.size)                   # **Replace This Text With Your Response**
    self.good_npc = NPC(self.size)                    # **Replace This Text With Your Response**
    self.screen.fill('#9CBEBA')                       # **Replace This Text With Your Response**
```

2.c. Parse through the `run()` method of **t11_game.py**. In particular, note how the game handles 
    a) collisions between the player and NPC,
    b) moving the player and NPC around the screen, 
    c) redrawing the player and NPC after they move,
    d) how often the game updates the screen

In your own words, describe how the four items above are accomplished in the Game class:

```
    a) **Replace This Text With Your Response**
    b) **Replace This Text With Your Response**
    c) **Replace This Text With Your Response**
    d) **Replace This Text With Your Response**
```

_Return to the Google Doc to continue the assignment._

---

## SECTION 3

3.a: Take a look at the **t11_player.py** file. What class does the `Player` class inherit functionality from? 
     How do you know?

```
    **Replace This Text With Your Response**
```

3.b. Sprites need two attributes to function: A surface and a rectangle. The surface (implemented in a `Surface` 
     class inside **pygame**) represents the drawing that will be rendered to the screen. The rectangle 
     (implemented in the `Rect` class in **pygame**) represents the area where the surface will be drawn on the screen, 
     including its width, height, and position. Find the lines of code that implement these two ideas, 
     and explain what each line does. 

```
    **Replace This Text With Your Response**
```

3.c. The `Player` class has only one method so far. Parse that code and docstring, and describe what it does:

```
    **Replace This Text With Your Response**
```

3.d. Similarly, the `NPC` class in **t11_NPC.py** also inherits the `Sprite` class from **pygame**, 
     but it does a little more than our `Player` class. Compare the two classes, and identify/describe the differences:

```
    **Replace This Text With Your Response**
```

3.e. Of particular interest is how we keep the `NPC` on the screen. Describe how we're using 
    the `self.rect` attribute in the `get_direction()` method to keep the `NPC` visible.  

```
    **Replace This Text With Your Response**
```

_Return to the Google doc to continue the assignment._ 

---

## SECTION 4

Using **t11_NPC.py** as a starting point, create a new class called `Good_NPC` (you can do this in the **t11_NPC.py** 
file, or create a new file; your choice). Have the new class inherit from the `NPC` class that I gave you, 
including calling the parent class's initializer. Convert **t11_game.py** so that it spawns Taco Cat as a `Good_NPC` 
instead of an NPC. Debug any errors you get; the program should work, at this point. 

4.a. How hard was it to create the child class, given the parent?

```
    **Replace This Text With Your Response**
```

The parent class `NPC` currently holds attributes like the image used, which are actually more specific to 
`Good_NPC` now. Refactor the code so that you can indicate the image for Good_NPCs and Evil NPCs (coming next)
inside the child classes, instead of the parent class. There are multiple ways to accomplish this; discuss with your 
partner first how you would like to approach this problem. 

Next, implement another new class called `Bad_NPC` (again, you can do this in the **t11_NPC.py** 
file, or create a new file; your choice). Our bad NPC (Whiskers) is going to march around the screen in a different way
than our friend Taco Cat; he should move like a Boustrophedon, working his way across the entire screen, before 
moving up or down. Because this NPCs movement is significantly different from the Good NPCs movement, we should 
make a design choice. We could:
    a) keep the `movement` method in NPC, and override it inside `Bad_NPC` with a new method.
    b) remove `movement` from NPC, and implement separate `movement` functions in each child class.
    c) refactor `movement` in NPC, so it can handle both child class options.

4.b. Discuss with your partner your design choice above, including their pros and cons. Document your 
     choice and why: 

```
    **Replace This Text With Your Response**
```

Finally, we need to create our enemy object, Whiskers. Update **t11_game.py** to:
    a) spawn `whiskers` at the beginning of the game
    b) make `whiskers` move around the screen
    c) handle collisions between Tuna and Whiskers, which ends the game
    d) (optional) handle collisions between Taco Cat and Whiskers, which kills Whiskers and spawns a new evil NPC

---

## SECTION 5

5.a. Inheritance allows us to produce special cases of a class, extending their functionality. Describe
    what challenges you faced while implementing the child classes that extended the `NPC` class. 
    How did you overcome them?

```
    **Replace This Text With Your Response**
```