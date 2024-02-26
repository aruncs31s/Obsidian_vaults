### Food Generation
Notes :
1. Food Generation Should be random 
2. 
###### Steps
- 
- 
#WholeCode 
```python
import random
import time

import pygame

pygame.init()
white = (255, 255, 255)
red = (255, 0, 0)
black = (0, 0, 0)
blue = (0, 255, 0)

WINDOW_WIDTH = 800
WINDOW_HEIGHT = 800

window = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT))
pygame.display.set_caption("Snake Game")
game_over = False


snake_size = 10
snake_speed = 10
x = 300
y = 300
x_change = 0
y_change = 0

clock = pygame.time.Clock()

font_style = pygame.font.SysFont("default", 50)


def message(msg, color):
    mesg = font_style.render(msg, True, color)
    window.blit(mesg, [WINDOW_WIDTH / 2 - 50, WINDOW_HEIGHT / 2 - 50])


foodx = round(random.randrange(0, WINDOW_WIDTH - snake_size) / 10) * 10
foody = round(random.randrange(0, WINDOW_WIDTH - snake_size) / 10) * 10

snake_speed = 30
snake_size = 10


while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
            message("Quiting", red)
            pygame.display.update()
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_q:
                game_over = True
            if event.key == pygame.K_LEFT:
                x_change = -snake_size
                y_change = 0
            elif event.key == pygame.K_RIGHT:
                x_change = snake_size
                y_change = 0
            elif event.key == pygame.K_DOWN:
                x_change = 0
                y_change = snake_size
            elif event.key == pygame.K_UP:
                x_change = 0
                y_change = -snake_size

    if x >= WINDOW_WIDTH or x < 0 or y >= WINDOW_HEIGHT or y < 0:
        game_over = True
    x += x_change
    y += y_change

    # Background

    window.fill(black)
    # message("Game Over", red)
    pygame.draw.rect(window, blue, [foodx, foody, snake_size, snake_size])
    pygame.draw.rect(window, white, [x, y, snake_size, snake_size])
    pygame.display.update()
    if x == foodx and y == foody:
        print("Good")
    clock.tick(snake_speed)
message("You lost", red)
pygame.display.update()
time.sleep(9)
# Control Snake speed
pygame.quit()
quit()

```

#BreakDown 


