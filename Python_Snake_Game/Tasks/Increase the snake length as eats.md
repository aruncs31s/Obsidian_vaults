#### Increase the snake length as it eats the food

#WholeCode 

```python
# Time = 2:33 AM 24.02.2024
import random
import time

import pygame

# from snake_temp_5 import WINDOW_HEIGHT, WINDOW_WIDTH

pygame.init()
# Define Window Size
WINDOW_WIDTH = 1360
WINDOW_HEIGHT = 760

# Define Colors
WHITE = (255, 255, 255)
RED = (255, 0, 0)
BLACK = (0, 0, 0)
BLUE = (0, 0, 255)
YELLOW = (255, 255, 102)
GREEN = (0, 255, 0)

# Defining snake properties

snake_size = 50
snake_speed = 15


window = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT))
pygame.display.set_caption("Snake Game")
clock = pygame.time.Clock()

# Defining fonts
font_style = pygame.font.SysFont("bahnschrift", 25)
score_font = pygame.font.SysFont("comicsansms", 35)


def our_snake(snake_size, snake_List):
    for k in snake_List:
        # pygame.draw.rect(window, BLACK, [k[0], k[1], snake_size, snake_size])
        pygame.draw.circle(
            window,
            BLACK,
            (k[0] + snake_size // 2, k[1] + snake_size // 2),
            snake_size // 2,
        )


def message(msg, color):
    mesg = font_style.render(msg, True, color)
    window.blit(mesg, [WINDOW_WIDTH / 2 - 50, WINDOW_HEIGHT / 2 - 50])


def gameLoop():
    game_over = False
    game_close = False

    snake_List = []
    Length_of_snake = 1
    x = WINDOW_WIDTH / 2
    y = WINDOW_HEIGHT / 2
    x_change = 0
    y_change = 0

    foodx = round(random.randrange(0, WINDOW_WIDTH - snake_size) / 20) * 20
    foody = round(random.randrange(0, WINDOW_WIDTH - snake_size) / 20) * 20

    while not game_over:
        while game_close == True:
            window.fill(BLUE)
            message("You Lost", RED)

            pygame.display.update()
            for event in pygame.event.get():
                print("hi")
                if event.type == pygame.QUIT:
                    game_over = True
        for event in pygame.event.get():
            if event.type == pygame.KEYDOWN:
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_LEFT:
                        x_change = -snake_size
                        y_change = 0
                        print("hi")
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
            game_close = True
        x += x_change
        y += y_change
        window.fill(BLUE)
        pygame.draw.rect(window, GREEN, [foodx, foody, snake_size, snake_size])
        snake_Head = []
        snake_Head.append(x)
        snake_Head.append(y)
        snake_List.append(snake_Head)
        if len(snake_List) > Length_of_snake:
            del snake_List[0]
        for k in snake_List[:-1]:
            if k == snake_Head:
                game_close = True
        our_snake(snake_size, snake_List)

        pygame.display.update()
        if (x == foodx or x - snake_size / 2 == foodx) and (
            y == foody or y - snake_size / 2 == foody
        ):
            foodx = round(random.randrange(0, WINDOW_WIDTH - snake_size) / 10.0) * 10.0
            foody = round(random.randrange(0, WINDOW_HEIGHT - snake_size) / 11.0) * 10.0
            Length_of_snake += 1

        clock.tick(snake_speed)

    pygame.quit()
    quit()


gameLoop()

```

#BreakDown 

