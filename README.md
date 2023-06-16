# Documentation ( 0.1.3 )

<aside>
💡 ******************************Quick Access: | [Game Objects](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [User Interface](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Support Classes](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Support Functions](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Physics](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Entity](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [StaticTile](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [MovingTile](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [AnimatedTile](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Light](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Button](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [Animator](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [clamp()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [import_folder()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [import_csv_layout()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [import_cut_graphics()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [draw_text()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [get_image()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [play_sound()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [scale_images()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) | [text_line_wrap()](https://www.notion.so/Documentation-0-1-3-40543d6137f84918bd900931ec93e02d?pvs=21) |*

</aside>

---

## BLACKFORGE2
  *********************A Framework/Libray For Making 2D Game Development Easier*********************

> ****************I want to help people both interested in game development in general and experienced pygame programmers.****************
> 

---

*BLACKFORGE2 provides you with a lot of useful Classes and methods that can help speed up the development process all while being efficient, performant, and simple to understand.*

---

<aside>
💡 You can access the quick guide [here](https://www.notion.so/Quick-Guide-2fd62b3bdc244e01941ea100b79eceac?pvs=21) to get an idea of how this library was intended to be used.

</aside>

---

## GAME OBJECTS

## Class: Physics()

### Parameters:

- None

### Methods:

- **`apply_gravity(self, entity, gravity_value: float, delta_time: float)**:`
Applies gravity to the given entity by updating its velocity and position based on the gravity value and delta time.
- **`horizontal_movement_collision(self, entity, collision_tiles: pygame.sprite.Group)**:`
Handles collision detection and response for horizontal movement of the entity.
Updates the entity's position and sets collision flags.
- **`vertical_movement_collision(self, entity, collision_tiles: pygame.sprite.Group)**:`
Handles collision detection and response for vertical movement of the entity.
Updates the entity's position and sets collision flags.

## Class: Entity(pygame.sprite.Sprite)

### Parameters:

- **`size:` int**:
The size of the entity.
- **p`osition:` tuple**:
The initial position of the entity.
- **`speed:` int**:
The speed of the entity.
- **`groups:` list**:
The groups to which the entity belongs.

### Methods:

- **`draw(self, surface: pygame.Surface)**:`
Draws the entity on the given surface.
- **`update(self)**:`
Updates the entity.

## Class: StaticTile(pygame.sprite.Sprite)

### Parameters:

- **`position:` tuple**:
The initial position of the tile.
- **`groups:` list**:
The groups to which the tile belongs.
- **`surface:` pygame.Surface**:
The surface of the tile.

### Methods:

- **`update(self, world_shift)**:`
Updates the tile's position based on the world shift.

## Class: MovingTile(StaticTile)

### Parameters:

- **`pos:` tuple**:
The initial position of the tile.
- **`groups:` list**:
The groups to which the tile belongs.
- **`direction:` str**:
The movement direction of the tile ('up', 'down', 'left', 'right').
- **`speed`: int**:
The movement speed of the tile (pixels per frame).
- **`delta_time:` float**:
The time difference between frames.
- **`surface:` pygame.Surface**:
The surface of the tile.

### Methods:

- **`move(self, constraints: list)**:`
Moves the tile based on its direction and speed, and reverses direction when colliding with constraints.

## Class: AnimatedTile(StaticTile)

### Parameters:

- **`size:` int**:
The size of the tile.
- **`x:` int**:
The initial x position of the tile.
- **`y:` int**:
The initial y position of the tile.
- **`path:` str**:
The path to the folder containing the animation frames.

### Methods:

- **`animate(self)**:`
Advances the animation frame index and updates the tile's image.
- **`update(self)**:`
Updates the tile's animation frame.

## Class: Light()

### Parameters:

- **`radius:` int**:
The radius of the light.
- **`color:` str**:
The color of the light.
- **`intensity:` float**:
The intensity of the light.
- **`screen_width:` int**:
The width of the screen.
- **`screen_height:` int**:
The height of the screen.
- **`world_brightness:` int**:
The brightness of the world.
- **`manual_pos: tuple` (optional)**:
The manual position of the light.

### Methods:

- **`generate_glow(self, glow: int, radius: int) -> pygame.Surface**:`
Generates a surface for the light glow effect.
- **`world_light(self)**:`
Creates the overlay with the world brightness.
- **```````apply_lighting(self, surface: pygame.Surface, light_layer: pygame.Surface, light_source_list=None)**:`
Applies lighting effects to the given surface based on the light source positions.

---

## USER INTERFACE

## Class: Button()

### Parameters:

- `game`: The main game instance.
- `text` (str): The text displayed on the button.
- `position` (tuple): The position of the button on the screen.
- `function`: The function associated with the button.
- `base` (tuple or str): The base image or rectangle of the button.
- `hovered` (tuple or str): The image or rectangle of the button when hovered.
- `base_color` (tuple): The base color of the button.
- `hover_color` (tuple): The color of the button when hovered.
- `text_color` (tuple): The color of the button's text.
- `text_size` (int): The size of the button's text.
- `hovered_pos` (tuple or None): The position of the button when hovered. Defaults to `None`.
- `id` (None or int): The identifier of the button. Defaults to `None`.

### Methods:

- `update(event: pygame.event) -> None`: Updates the button's state based on the mouse position and events.
- `draw() -> None`: Draws the button on the screen.
- `draw_rect(rect: pygame.Rect, color: str) -> None`: Draws a rectangle on the button's surface.
- `draw_image(image: pygame.Surface, color: str) -> None`: Draws an image on the button's surface.

---

## SUPPORT CLASSES

### Class: Animator()

### Parameters:

- `game`: The main game instance.
- `animation` (list): The list of frames in the animation.
- `frame_duration`: The duration of each frame in milliseconds.
- `loop` (bool): Indicates whether the animation should loop. Defaults to `False`.

### Methods:

- `update(dt: float)`: Updates the animation based on the elapsed time.
- `reset()`: Resets the animation to its initial state.

---

## SUPPORT FUNCTIONS

### Function: clamp

### Parameters:

- `num` (int): The number to clamp.
- `min_value` (int): The minimum value.
- `max_value` (int): The maximum value.

Returns the clamped value within the specified range.

### Function: import_folder

### Parameters:

- `path` (str): The path to the folder containing images.

Returns a list of surfaces loaded from the images in the folder.

### Function: import_csv_layout

### Parameters:

- `path` (str): The path to the CSV layout file.

Returns a list representing the terrain map imported from the CSV file.

### Function: import_cut_graphics

### Parameters:

- `path` (str): The path to the image containing the graphics.
- `tile_size` (int): The size of each tile in pixels.

Returns a list of cut tiles extracted from the image based on the tile size.

### Function: draw_text

### Parameters:

- `surface` (pygame.Surface): The surface to draw the text on.
- `text` (str): The text to display.
- `pos` (tuple): The position of the text on the surface.
- `size` (int): The size of the text. Defaults to `30`.
- `color` (tuple): The color of the text. Defaults to `(255, 255, 255)`.
- `bg_color` (None or tuple): The background color behind the text. Defaults to `None`.

Draws the specified text on the surface at the given position.

### Function: get_image

### Parameters:

- `path` (str): The path to the image file.

Returns the image loaded from the specified path.

### Function: play_sound

### Parameters:

- `path` (str): The path to the sound file.
- `stop` (None, True, or False): Determines the behavior of the sound. Defaults to `None`.

Plays the specified sound file. If `stop` is `True`, stops the sound. If `stop` is `False`, plays the sound repeatedly.

### Function: scale_images

### Parameters:

- `images` (list): The list of images to scale.
- `size` (tuple): The target size of the scaled images.

Returns a list of images scaled to the specified size.

### Function: text_line_wrap

### Parameters:

- `surface` (pygame.Surface): The surface to draw the wrapped text on.
- `text` (str): The text to wrap.
- `color` (str): The color of the text.
- `rect` (pygame.Rect): The rectangle defining the bounds of the wrapped text.
- `font` (pygame.Font): The font used for rendering the text.
- `aa` (bool): Indicates whether to use anti-aliasing. Defaults to `False`.
- `bkg` (None or tuple): The background color behind the text. Defaults to `None`.

Wraps the text to fit within the specified rectangle and renders it on the surface.
