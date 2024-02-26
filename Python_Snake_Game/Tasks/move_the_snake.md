---
id: move_the_snake
aliases: []
tags: []
---

## Moving the Snake
Prerequisites : [[create_the_snake]]

#WholeCode

```python
import pygame

pygame.init()
white = (255, 255, 255)
red = (255, 0, 0)
black = (0, 0, 0)

window = pygame.display.set_mode((800, 500))
pygame.display.set_caption("Snake Game")
game_over = False

x = 300
y = 300
x_change = 0
y_change = 0
clock = pygame.time.Clock()
while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                x_change = -10
                y_change = 0
            elif event.key == pygame.K_RIGHT:
                x_change = 10
                y_change = 0
            elif event.key == pygame.K_DOWN:
                x_change = 0
                y_change = 10
            elif event.key == pygame.K_UP:
                x_change = 0
                y_change = -10

    x += x_change
    y += y_change
    window.fill(black)

    pygame.draw.rect(window, white, [x, y, 10, 10])
    pygame.display.update()

    # Control Snake speed
    clock.tick(30)
pygame.quit()
quit()

```

#BreakDown
Note : *Here we're using pygame.event.get() method to get all the keystrokes*

1. 
```python
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                x_change = -10
                y_change = 0
            elif event.key == pygame.K_RIGHT:
                x_change = 10
                y_change = 0
            elif event.key == pygame.K_DOWN:
                x_change = 0
                y_change = 10
            elif event.key == pygame.K_UP:
                x_change = 0
                y_change = -10

    x += x_change
    y += y_change
```
*This segment in the code block is corresponding to the movement of snake*

- If we want to make it dynamic we can replace the -10 and +10 increments in the code with `snake_size` 
	- so after doing that the code will look like this 
		```python
import pygame

pygame.init()
white = (255, 255, 255)
red = (255, 0, 0)
black = (0, 0, 0)

window = pygame.display.set_mode((800, 500))
pygame.display.set_caption("Snake Game")
game_over = False

### Snake Properties
snake_size = 10 


x = 300
y = 300
x_change = 0
y_change = 0
clock = pygame.time.Clock()
while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.KEYDOWN:
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

    x += x_change
    y += y_change
    window.fill(black)

    pygame.draw.rect(window, white, [x, y, 10, 10])
    pygame.display.update()

    # Control Snake speed
    clock.tick(30)
pygame.quit()
quit()

		
```

- We can also the value provided inside `clock.tick()` to control the speed
	- So after doing that the code will look like the following
	```python 
	snake_speed = 30
	.
	.
	.
	clock.tick(snake_speed)
```

