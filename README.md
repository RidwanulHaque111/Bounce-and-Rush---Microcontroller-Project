# Bounce and Rush

In this project, we have recreated the classic offline Chrome dinosaur game with our unique twist. This single-player game involves guiding a character through a side-scrolling landscape, avoiding obstacles to achieve a higher score. The primary goal is to attain the highest score possible.

## Introduction
"Bounce and Rush" is controlled by an ATMEGA32 micro-controller, which interacts with various hardware components. It also displays the real-time score. Game speed and difficulty level increases with player's score.

## Components
- 2-4 Decoder (74HC139)
- 4-16 Decoder (74HC154)
- ATMEGA32 Microcontroller
- 2x16 LCD Module (LM016L)
- 8x8 LED Matrix (x6)
- Resistor 300 ohm
- SPST Push Button (x2)

## Working Principle
The game is controlled by an ATMEGA32 micro-controller, which interacts with various hardware components. Two SPST push buttons are utilized for player control: one for jumping and the other for restarting the game. The player and obstacles are represented on six 8x8 LED matrices. The score is displayed consistently on an LCD module. If the player avoids obstacles, the score increases, but if a collision occurs, the game can be restarted using one of the buttons.

## Algorithm
* Start, and LED display shows the score.
* If the jump button is pressed, the dinosaur will jump.
* As the score increases, the difficulty level rises.
* If the player is hit by an obstacle, display 'GAME OVER.'
* If the restart button is pressed, the game will restart.

## Handling 6 LED Matrices
Implementing code to navigate objects through multiple LED matrices presented challenges. Initially, we attempted to create obstacles by selecting a single column and multiple rows. However, as we increased the number of LED matrices, moving the object became problematic. To address this, we selected only a single dot at a time, and we used 2x4 decoders to enable 4x16 decoders, connecting them to the LED matrices.


## LCD and Delay
Ensuring smooth transitions of obstacles and the dinosaur required managing delays. Connecting an LCD display impacted the delay, and efforts were made to keep it as low as possible (1ms) for smooth LED blinking. Challenges persisted in achieving optimal smoothness.

## Collision
Collision detection was implemented based on any part of the dinosaur hitting an obstacle.

## LCD
The score is dynamically updated on the LCD, refreshing a specific part after the previously printed string ('SCORE: ').

## Decoder
Four 2x4 decoders were used to control eight 4x16 decoders. Ports 0-3 of ATMEGA32 controlled the 4x16 decoders, while the last 4 bits controlled the 2x4 decoders and enabled them.

