# T11: The Legend of Tuna: Breath of the Catnip

## Instructions

Please replace each `**Replace This Text With Your Response**` with your answer.

___

## SECTION 1
#
1.a. First, discuss with your team and assign yourselves roles. Try to pick the role you’ve had the least experience in.

```
    |                 | Monday | Wednesday | Friday |
    |-----------------|--------|-----------|---------|
    | Driver          | ANT    | ARBY                | DAVID  |
    | Navigator       | DAVID  | ARBY//DAVID = *     | *      |
    | Quality Control | ARBY   | DAVID//ARBY = *     | *      |
```

___

## SECTION 2

2.a. Look at the three Python files in the repository. 
    Identify below all of the classes, and a brief description of
    what each one represents:

```
In the files: player.py, game.py, and NPC.py

    Classes:
       Player # Represents the character in game AND handles the movement of the player. 
       NPC # Represents the NPC in game AND handles the movement of the NPC.
       Game # Imports the classes from the other files. Game class for handling the game logic. 
            - What is the game logic?
```

2.b. Look more closely at the **t11_game.py** file. 
There are 8 lines; identify if they are 
    a) instance parameters, defined as: a type of input that allows for the creation of object instances? I.e. Instantiation. 
    b) method calls within the class, defined as:
    c) method calls to another class or library, defined as: 

(Some are more than one answer!)

```
    self.size = 800, 600                              # This creates the window and resolution. Is it [a,b,c]? - a | Instance paramter
    self.running = True                               # a
    pygame.init()                                     # c
    self.screen = pygame.display.set_mode(self.size)  # a, c
    self.clock = pygame.time.Clock()                  # a, c
    self.player = Player(self.size)                   # a, c
    self.good_npc = NPC(self.size)                    # a, c
    self.screen.fill('#9CBEBA')                       # b, c
```

2.c. Parse through the `run()` method of **t11_game.py**. In particular, note how the game handles 
    a) collisions between the player and NPC,
    b) moving the player and NPC around the screen, 
    c) redrawing the player and NPC after they move,
    d) how often the game updates the screen

In your own words, describe how the four items above are accomplished in the Game class:

```
    a) Line 52 checks for collision between tuna and tacocat. It is first set to false so that way when the sprites collide
    it will return True and mean that they found each other and print out the text intended below.
    b) Line 59 and 60, so tuna is going to wherever the key is pressed. Their movements are called from "movement" methods
    from different classes. It's just the names of the methods that are the same.
    c) Line 56 allows for the program to erase objects and not leave any traces.
    d) Line 65, because for each second it will reset 50 times.
```

_Return to the Google Doc to continue the assignment._

---

## SECTION 3

3.a: Take a look at the **t11_player.py** file. What class does the `Player` class inherit functionality from? 
     How do you know?

```
    It inherits from pygame as seen in line 22: Class Player(pygame.sprite.Sprite):.
```

3.b. Sprites need two attributes to function: A surface and a rectangle. The surface (implemented in a `Surface` 
     class inside **pygame**) represents the drawing that will be rendered to the screen. The rectangle 
     (implemented in the `Rect` class in **pygame**) represents the area where the surface will be drawn on the screen, 
     including its width, height, and position. Find the lines of code that implement these two ideas, 
     and explain what each line does. 

```
    From t11_NPC we get surface from line 34, and from t11_player line 32 - it loads the image from the png loaded in the 
    program, and then convert_alpha is used to convert surfaces to the same pixel format as used by the screen.
    From t11_NPC we get rectangle from line 36, and from t11_player line 34 - it manages the positioning of the surfaces
    and checks for collisions.
```

3.c. The `Player` class has only one method so far. Parse that code and docstring, and describe what it does:

```
    if keys[pygame.K_UP]: - if the up key is pressed
        self.rect.move_ip(0, -3) - it gets the current position of the rectangle and moves it by the unit defined inside
                                    the parentheses
    the same applies for the codes below it if the up key isn't pressed, the down would be pressed
    There are two if statements which check for up and down, or right and left.
```

3.d. Similarly, the `NPC` class in **t11_NPC.py** also inherits the `Sprite` class from **pygame**, 
     but it does a little more than our `Player` class. Compare the two classes, and identify/describe the differences:

```
    The `NPC` class is more autonomous, it moves on its own and includes logic to keep itself within screen bounds by 
    `get_direction()`. It also randomly changes direction. The `Player` class, on the other hand, is controlled 
    entirely by user input through key presses and does not contain any screen-bound checking logic—it assumes the 
    player will stay within bounds. Also, the `NPC` class uses a `path` attribute to determine direction, while the 
    `Player` class checks real-time keyboard inputs to move.

```

3.e. Of particular interest is how we keep the `NPC` on the screen. Describe how we're using 
    the `self.rect` attribute in the `get_direction()` method to keep the `NPC` visible.  

```
    The `get_direction()` method checks if the NPC’s rectangle (self.rect) goes out of screen bounds. If so, it 
    updates the `path` attribute to reverse or change direction, for example if it hits the bottom of the screen, 
    it moves north). This prevents the NPC from moving off-screen and ensures it stays visible by adjusting 
    movement before drawing.

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
    ** The good NPC was easy to implement but we had some troubles getting the movement in the Bad NPC**
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
    Sure! Here's the answer written in your voice:

---

We decided to go with **option (a)** — keeping the `movement` method in the `NPC` class and overriding 
it in `Bad_NPC`. I like this approach because it lets me reuse code from the parent class, but still 
lets Whiskers have his own unique movement. It also keeps things organized and avoids repeating too 
much code. One downside is that the base class might have methods that not every child uses, but I 
think that’s okay since overriding gives us the flexibility we need.
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
    One challenge we faced was getting Whiskers to move differently from Taco Cat while still using the 
    shared `NPC` class. His boustrophedon movement needed custom logic, so we overrode the `movement` and 
    `get_direction` methods in `Bad_NPC`. We fixed issues like him not showing up or moving by adjusting 
    his position and carefully testing the logic.
```