---
title: "Python et les beaux boulons : fenêtres fluides, standard de code..."
date: 2018-05-30 19:30
---

```python
import pygame

if __name__ == '__main__':
# Initialize  the stuff
    pygame.init()
    pygame.display.set_caption('Color crisis')
    # sets the window size
    screen = pygame.display.set_mode((750, 400))
    screen.fill((255, 255, 255))
    surface = pygame.display.get_surface()
    color = [0, 0, 250]
    for red in range(255):
        for green in range(255):
            # Allow bagless display
            pygame.display.flip()
            # draw circle as psychadelic blue sunset
            # width cannot be greater than radius 600, 460 
            pygame.draw.circle(surface, color, (20, 10), 500, 460)
            color[1] = red
            color[0] = green
            # Updated display without bag
            pygame.display.flip()
    
    for event in pygame.event.get(pygame.QUIT):
        exit(0)
```
