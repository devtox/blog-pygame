---
layout: post
title: Python Dispay images with PyGame 
categories:
- General
---

The following are some brief instructions on how to display images with PyGame.The first thing you need to do is create a PyGame display. 

You can do this by calling the pygame.display.set_mode() function. This function takes two arguments: the width and height of the display in pixels. For example, to create a 400x300 pixel display, you would call:

```python
pygame.display.set_mode((400, 300))
```

## how to load images

Once you have created your PyGame display, you can load images into it using the pygame.image.load() function. This function takes one argument: the path to the image file you want to load (typically something like 'my-image-file.png'). 

For example, if you have an image file named 'player-sprite.png' in your current directory, you could load it into your PyGame display like so:

```python
pygame.display.set_mode((400, 300))
...
player_image = pygame.image.load('player-sprite.png')
```
Once you have loaded an image with pygame.image.load(), you can display it on your PyGame display by calling the blit() function on your display surface and passing it the image and x/y coordinates of where you want to draw the top-left corner of the image:

```python
display_surface.blit(player_image, (0, 0))
```

You can also use the pygame.transform module to do things like rotate or scale images before blitting them to your display:

```python
rotated_image = pygame.transform.rotate(player_image, 45)
scaled_image = pygame.transform.scale(player_image, (100, 200))
```
The pygame.transform module has a number of built-in functions to implement flipping, rotating and deflating of images.

## display images

PyGame can load images in a variety of formats, including JPG and PNG. This makes it easy to use PyGame to display pictures stored in these popular formats.

The following example loads an image. Image files are loaded with the pygame.image.load() function. This function returns a Surface which is the image itself. It consits of several steps, the first step is to load the pygame module and create a window.

The code below creates a game window with width and height set to 640×480. It initializes Python using the method *pygame.init()*. 

```python
import sys
import pygame

pygame.init()
size=width,height=640,480
screen=pygame.display.set_mode(size)
```
Now we will put a picture fill in this window. You can load an image with *pygame.image.load* with the parameter containing the filename or the path+filename. Then get the rect and draw it on the screen with *screen.blit*. 

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
img=pygame.image.load("1.jpg")

# get rectangular area
imgrect=img.get_rect()

while True:
    for event in pygame.event.get():
         if event.type == pygame.KEYDOWN:
             sys.exit()

    # fill screen
    screen.fill(color)	
    
    # draw image
    screen.blit(img,imgrect)
    
    # flip image
    pygame.display.flip()		
pygame.quit()
```

The code loops using the while True loop. The call *pygame.event.get()* can get the event queue, used to iterate through the events, and then determine the event type according to the type property. Event handling is similar to the GUI, into event.type is equal to pygame.QUIT means the detection of the close window. The event *pygame.KEYDOWN* means the keyboard press event, *pygame.MOUSEBUTTONDUWN* means the mouse press event, etc.

![pygame load image](/images/pygame-display-image.png)

## scale image

The following image is large, and so you can scale it. In the example below we use *pygame.transform.scale(surface,(width,heigth))*. In this call parameter 1 is a surface containing the image to be used, the second parameter is a tuple of the image size after scaling, it returns a surface of the scaled image. Because it returns a new scaled image, you need to store its output.

We added the function to our program and the result is as follows:

```python
img=pygame.image.load("1.jpg")
img=pygame.transform.scale(img,size)
imgrect=img.get_rect() # Get the rectangular area
```

Finally we can do this:

```python
import sys
import pygame

img_=pygame.image.load("1.jpg")
img_rect=img_.get_rect()
size=(int(img_rect[2]/3),int(img_rect[3]/3))
img_=pygame.transform.scale(img_,size)

pygame.init()
screen=pygame.display.set_mode(size)
color=(0,0,0)
img_=pygame.transform.scale(img_,size)
# img_rect= (img_.get_rect())
# pygame.init()
# size=width,height=700,600
# screen=pygame.display.set_mode(size)
# color=(0,0,0)

while True:
    for event in pygame.event.get():
         if event.type == pygame.KEYDOWN:
             sys.exit()
    screen.fill(color)
    screen.blit(img_,img_rect)
    pygame.display.flip()
pygame.quit()
```

![pygame scale image](/images/pygame-scale-image.png)

That way, the image is scaled in the window.

