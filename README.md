# BLACKFORGE2
 A framework for developing 2d games with python+pygame.


# Simple Platformer With BLACKFORGE2

- This is meant to show you some attributes, classes and functions provided by BLACKFORGE2. There are many more tools included to help you out with making your game. Go to definition on the BLACKFORGE2 import and check out some of the code to learn more about them. I will be creating documentation soon.-

- First we get our imports ready and our project settings
---
```python
from BLACKFORGE2 import *

""" Settings """
FPS = 60
SCREEN_SIZE = (1000,800)
GRAVITY = 0.62
```
- The development branch of pygame *pygame-ce* is installed when you install BLACKFORGE2.
If you are experiencing issues/conflicts, it is reccomended to delete pygame by running the following command: ``` pip uninstall pygame ```
---
- First lets create a simple Player class
Within this Player class we will use the Physics class, and the Entity class along with their attributes to get our player set up quick and clean.
---
```python
class Player(Entity):
    def __init__(self, game, size:int, position:tuple, speed:int, group:pygame.sprite.Group()):
        super().__init__(size, position, speed, group)
        self.game = game  # passing an instance of your main game class can give you access to other classes without imports e.g(self.game.level.level_width)
        self.image.fill([255,0,255]) # the Entity() class has a default image attribute which is just a pygame surface
        self.jump_force = -13  # the force upwards the player has when jumping
        # go to definition on the Entity class to see what other useful attributes it has

    def move(self):
        keys = pygame.key.get_pressed()

        if keys[pygame.K_d]:
            self.velocity.x = self.speed  # the velocity attribute is used to control the speed the player will move in a certain direction
        elif keys[pygame.K_a]:
            self.velocity.x = -self.speed
        else:
            self.velocity.x = 0
        
        # the Entity class has atttributes to verify where a collision is happening.
        if keys[pygame.K_SPACE] and self.collide_bottom:  # here we can implement a jump by checking the key pressed and the player's bottom collision attribute
            self.velocity.y = self.jump_force
    
    def update(self, terrain):  # pass the sprite group containing sprites you want the player to collide with for the collision methods to check
        self.move()  # call the players move method which alters its velocity
        self.rect.x += self.velocity.x  # move the player's rect according to its velocity (this is done for the y direction on any Entity() that calls the apply_gravity() method.)
        # the Entity class has a physics attribute by default which comes with gravity application, and 2d collision checks
        self.physics.horizontal_movement_collision(self, terrain)  # for the collision checks, you pass the entity to perform the checks on (as the Physics class can be used alone) and the sprites to check collisions with
        self.physics.apply_gravity(self, GRAVITY)  # for gravity application you pass the entity to apply gravity to as well as the gravity constant of your game
        self.physics.vertical_movement_collision(self, terrain)

```
