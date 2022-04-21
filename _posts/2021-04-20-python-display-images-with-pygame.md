---
layout: post
title: Python Dispay images with PyGame 
categories:
- General
---

The following are some brief instructions on how to display images with PyGame.The first thing you need to do is create a PyGame display. You can do this by calling the pygame.display.set_mode() function. This function takes two arguments: the width and height of the display in pixels. For example, to create a 400x300 pixel display, you would call:

```python
pygame.display.set_mode((400, 300))
```

Once you have created your PyGame display, you can load images into it using the pygame.image.load() function. This function takes one argument: the path to the image file you want to load (typically something like 'my-image-file.png'). For example, if you have an image file named 'player-sprite.png' in your current directory, you could load it into your PyGame display like so:pygame.display.set_mode((400, 300))

```python
player_image = pygame.image.load('player-sprite.png')
```

Once you have loaded an image with pygame.image.load(), you can display it on your PyGame display by calling the blit() function on your display surface and passing it the image and x/y coordinates of where you want to draw the top-left corner of the image:

```python
display_surface.blit(player_image, (0, 0))
```

## display images

The pygame.transform module has a number of built-in functions to implement flipping, rotating and deflating of images.
Create a game window with width and height set to 640×480

```python
import sys
import pygame

pygame.init()
size=width,height=640,480
screen=pygame.display.set_mode(size)
```

Now we will put a picture fill in this window.

```python
import sys
import pygame

# initialize pygame
pygame.init()	

# set window properties					
size=width,height=700,600 

# create window
screen=pygame.display.set_mode(size)

# set fill color
color=(0,0,0) 	

# load image
charlotte=pygame.image.load("1.jpg")

# get rectangular area
charlotterect=charlotte.get_rect()

while True:
    for event in pygame.event.get():
         if event.type == pygame.KEYDOWN:
             sys.exit()

    # fill screen
    screen.fill(color)	
    
    # draw image
    screen.blit(charlotte,charlotterect)
    
    # flip image
    pygame.display.flip()		
pygame.quit()
```

The code in while True in the figure, pygame.event.get() can get the event queue, use for...in to iterate through the events, and then determine the event type according to the type property, here the event handling is similar to the GUI, into event.type is equal to pygame.QUIT means the detection of the close window KEYDOWN means the keyboard press event, pygame.MOUSEBUTTONDUWN means the mouse press event, etc.

The following is the image we intend to insert, it is 1920 x 1080, and our window is 700 x 600, so we intend to shrink it a bit and add it in.

Here we need to use pygame.transform.scale(surface,(width,heigth)), parameter 1 is a surface containing the image to be used, the second parameter is a tuple of the image size after scaling, it returns a surface of the scaled image
 We added the function to our program and the result is as follows

```python
charlotte=pygame.image.load("1.jpg")
charlotte=pygame.transform.scale(charlotte,size)
charlotterect=charlotte.get_rect() # Get the rectangular area
```

Finally we can do this:

```python
import sys
import pygame

charlotte=pygame.image.load("1.jpg")
charlotterect=charlotte.get_rect()
size=(int(charlotterect[2]/3),int(charlotterect[3]/3))
charlotte=pygame.transform.scale(charlotte,size)

pygame.init()								
screen=pygame.display.set_mode(size)	
color=(0,0,0)									
charlotte=pygame.transform.scale(charlotte,size)
# charlotterect= (charlotte.get_rect()) 
# pygame.init()
# size=width,height=700,600
# screen=pygame.display.set_mode(size)
# color=(0,0,0)

while True:
    for event in pygame.event.get():
         if event.type == pygame.KEYDOWN:
             sys.exit()
    screen.fill(color)
    screen.blit(charlotte,charlotterect)
    pygame.display.flip()
pygame.quit()
```
