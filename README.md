# Tetris_Game



License:
This script is distributed under the GNU General Public License (GPL) version 3 or later.

Class Block:
    - Description: This class represents a Tetris block and handles its movement, rotation, and collision detection.
    
    Constructor (__init__):
        - Parameters:
            - shape: List of block data containing [X, Y] coordinates of building blocks.
            - x: X coordinate of the first Tetris shape block.
            - y: Y coordinate of the first Tetris shape block.
            - screen: The screen on which the block is drawn.
            - color: The color of each shape block in RGB notation.
            - rotate_en: Boolean to enable or disable block rotation.

        - Initializes the Tetris block with the given parameters.
        - Converts the shape data to Rect objects for drawing.
        - Handles block movement and rotation.
    
    draw():
        - Description: Draws the Tetris block on the screen.
    
    get_rotated(x, y):
        - Description: Computes new coordinates based on the rotation angle.
        - Parameters:
            - x: The X coordinate to be transformed.
            - y: The Y coordinate to be transformed.
        - Returns a tuple with new (X, Y) coordinates after rotation.
    
    move(x, y):
        - Description: Moves all elements of the block using the given offset (x, y).
    
    remove_blocks(y):
        - Description: Removes blocks on the Y coordinate and moves blocks above down by one step.
        - Parameters:
            - y: Y coordinate to remove blocks above.
    
    has_blocks():
        - Description: Returns True if the block contains shape blocks, False otherwise.
    
    rotate():
        - Description: Rotates the block by 90 degrees if rotation is enabled.
    
    _update():
        - Description: Updates the position of all shape blocks based on movement and rotation.
    
    backup():
        - Description: Creates a backup of the current block configuration.
    
    restore():
        - Description: Restores the previous block configuration from the backup.
    
    check_collision(rect_list):
        - Description: Checks if the block collides with any other block in the provided list of Rect objects.
        - Parameters:
            - rect_list: List of Rect objects for collision detection.
        - Returns True if collision occurs, False otherwise.



from pygame.locals import *

# Configuration of building shape block
# Width of the shape block
BWIDTH     = 20
# Height of the shape block
BHEIGHT    = 20
# Width of the line around the block
MESH_WIDTH = 1

# Configuration of the player board
# Board line height
BOARD_HEIGHT     = 7
# Margin of upper line (for score)
BOARD_UP_MARGIN  = 40
# Margins around all lines
BOARD_MARGIN     = 2

# Color declarations in the RGB notation
WHITE    = (255,255,255)
RED      = (255,0,0)
GREEN    = (0,255,0)
BLUE     = (0,0,255)
ORANGE   = (255,69,0)
GOLD     = (255,125,0)
PURPLE   = (128,0,128)
CYAN     = (0,255,255) 
BLACK    = (0,0,0)

# Timing constraints
# Time for the generation of TIME_MOVE_EVENT (ms)
MOVE_TICK          = 1000
# Allocated number for the move down event
TIMER_MOVE_EVENT   = USEREVENT+1
# Speed up ratio of the game (integer values)
GAME_SPEEDUP_RATIO = 1.5
# Score LEVEL - first threshold of the score
SCORE_LEVEL        = 2000
# Score level ratio
SCORE_LEVEL_RATIO  = 2 

# Configuration of score
# Number of points for one building block
POINT_VALUE       = 100
# Margin of the SCORE string
POINT_MARGIN      = 10

# Font size for all strings (score, pause, game over)
FONT_SIZE           = 25



Tetris Class

The Tetris class implements the core logic of a Tetris game. It manages the game board, Tetris blocks, player actions, and scoring.

Constructor: __init__(self, bx, by)

- Initializes a new instance of the Tetris game.
- Parameters:
  - bx: Number of blocks in the X-axis.
  - by: Number of blocks in the Y-axis.

Attributes:

- resx (int): Width of the game board in pixels.
- resy (int): Height of the game board in pixels.
- board_up, board_down, board_left, board_right (pygame.Rect): Rectangular objects representing the borders of the game board.
- blk_list (list): List of Tetris blocks in the game.
- start_x (int): Starting X-coordinate for new Tetris blocks.
- start_y (int): Starting Y-coordinate for new Tetris blocks.
- block_data (tuple): Data defining Tetris block shapes, colors, and rotation settings.
- blocks_in_line (int): Number of blocks in each row of the game board.
- blocks_in_pile (int): Number of blocks in each column of the game board.
- score (int): Current player score.
- speed (float): Current game speed.
- score_level (int): Score threshold to increase game speed.

Methods:

- apply_action(self):
  - Processes user input to control the game.
  - Handles actions such as moving blocks, rotating, and pausing.

- pause(self):
  - Pauses the game and displays a pause message.
  - Resumes the game when the "p" key is pressed.

- set_move_timer(self):
  - Adjusts the move timer based on the current game speed.
  - Controls the frequency of Tetris block movement.

- run(self):
  - Initializes the game, sets up the game window, and starts the game loop.
  - Handles user input and game logic within the loop.
  - Displays the game over screen when the game ends.

- print_status_line(self):
  - Prints the current score and game speed on the screen.

- print_game_over(self):
  - Displays the game over message and waits for user input to exit the game.

- print_text(self, str_lst, x, y):
  - Prints a list of strings on the screen at the specified coordinates.

- print_center(self, str_list):
  - Centers a list of strings on the screen.

- block_colides(self):
  - Checks if the active Tetris block collides with other blocks or game borders.
  - Returns True if a collision is detected.

- game_logic(self):
  - Implements the main game logic.
  - Detects collisions, block insertions, and filled lines.

- detect_line(self):
  - Detects and removes filled lines from the game board.
  - Increases the player's score accordingly.

- remove_line(self, y):
  - Removes a filled line from the game board.
  - Shifts blocks above the removed line downward.

- get_blocks_in_line(self, y):
  - Counts the number of shape blocks on a specified Y-coordinate.

- draw_board(self):
  - Draws the white borders of the game board.

- get_block(self):
  - Generates a new Tetris block and adds it to the game if needed.

- draw_game(self):
  - Renders the game by clearing the screen, drawing the game board, and rendering Tetris blocks.

Main Execution: if __name__ == "__main__":

- Initializes an instance of the Tetris game with a specific number of blocks in the X and Y axes (16 blocks wide and 30 blocks high).
- Calls the run method to start the game.

This class encapsulates the functionality required to run a Tetris game, including user interaction, scoring, and block manipulation.


Thanx to the Auther🏆😘
