---
layout: post
title: A Project in Modern C++
tags: cpp coding project
categories: demo
---

# digital-rain-25-cpp
A Project in Modern C++ cpp coding project
--
The Digital Rain Project is a modern C++ project that visually represents falling raindrops,

## Software Design, Architechture & test

I went with the design of object-oriented code for this project. I chose object-oriented code because
it promotes modularity and reusability, letting me group related data and functions together in classes. 
Additionally, using constructors ensures that each object is initialized properly, enhancing reliability.
Constructors allow for setting default values and establishing the initial state of an object, which is crucial for preventing errors.
This approach also simplifies debugging and testing.

The first thing i attempted was to print Hello vertically, this code snippet :
![image](https://github.com/user-attachments/assets/04a8f32e-c1a9-47d1-806d-033253242f8c)


  By being able to print hello veritcally going down my screen it gave me confidence that i can use
  letters and numbers to visually simulate digital rain. Here is an example of me printing random 
  numbers vertically. 
![image](https://github.com/user-attachments/assets/09ddf3cf-f5a2-40d1-83ce-12be4e05bb0a)

  After being able to print out charachters and number vertically, i choose to go with using ASCII charachters on the tabe within the range of 33 - 126,
  which is a mix of numbers, upper and lowercase charachters and symbols, this diversity allows for a visually engaging representation of digital rain 
 
  ![image](https://github.com/user-attachments/assets/e9bb2d22-d4a6-44f9-a9fc-e82d9940317c)
 
  The available symbols from the ASCII table :
  ![image](https://github.com/user-attachments/assets/6f049fc2-a59a-4600-8002-72eea201ac4f)

  After implemening the ASCII table to my project, the next solution was to be able to print out the range of characters randomly.
  To achieve this, I utilized the C++ random library, which provides tools for generating random numbers.

  I set up a random number generator using std::mt19937 and std::uniform_int_distribution<> to ensure that each character printed was selected from the specified 
  ASCII range, each 
  time my rain simulation was running. 

  To vertically print, i was using the function gotoxy, positioning each character vertically down the console window, this was to create the illusion of falling 
  rain drops.
  I also implemented an animation loop that would constantly update the positions of characters, by clearing the screen and re-printing characters 
  in their new positions
  this achievd a smooth visual transition.

  I have a function called TestRandomNumberGenerator. In this test, it generates 1,000 random values to test the X and Y coordinates. The function 
  is also wrapped in a try-catch block that will handle any exceptions. If any generated value falls outside the expected range, an error message is 
  printed to the console.

  Code Snippet of TestRandomNumberGenerator:
  ![image](https://github.com/user-attachments/assets/da50c063-526b-40a2-8979-bc6afdf69d27)

## Algorithms
I am using algorithms in several places with in my code, The first algorithm i am going to talk about is
: ![image](https://github.com/user-attachments/assets/bcf3c05b-2794-4197-89d3-ebf4d1c30b08)

This code snippet is of my Random Number Generation algorithm, this algorithm ensures that
each and every raindrop is unique and will behave unpredicatably, making for a realistic digital 
rain effect.

std::random_device rd;

std::mt19937 eng(rd());

This part of the code is responsible for seeding and initalizing the random number generator.

std::uniform_int_distribution<> distrX(0, SCREEN_WIDTH - 1);

std::uniform_int_distribution<> distrY(0, SCREEN_HEIGHT - 1);

This part of the code generates a random X & Y for the raindrop.

std::uniform_int_distribution<> distrSpeed(1, 3);

This part of the code assigns a random speed to each raindrop, ensuring that different raindrops fall at different speeds.

std::uniform_int_distribution<> distrChar(ASCII_CHAR_MIN, ASCII_CHAR_MAX);

This part of the code selects a random ASCII character for each raindrop within the range of 33 - 126. Each character is chosen randomly, creating an ever
changing visual.

The algorithm ensures that each raindrop appears at a random position, falls at a different speed, and displays a 
ASCII character. This algorithm enhances the visual of the digital rain.

![image](https://github.com/user-attachments/assets/f243a52a-63a7-4e1c-bf29-e5f6d9e4b16a)

The Digitalrain::updateRain() algorithm simulates falling raindrops on the screen. 
It loops through each raindrop, clears its previous position, and moves it down by its speed. 

If a raindrop reaches the bottom of the screen, it will then reset to the top with a random position and speed.

The Digitalrain::StartRain() function begins the animation by first clearing the screen. Then, it enters an infinite loop where updateRain() is called 
repeatedly, and a 50-millisecond delay is added using Sleep(50) to control the update speed, creating a pleasant rain effect on the screen.


## Problem Solving
 One of the problems I was previously experincing was a fickering issue when running my simulation of digital rain, I wanted to improve transitions, to resolve 
 this issue i implemented Vectors. Snippet of old code :
 
 ![image](https://github.com/user-attachments/assets/76a8fbca-afb7-4c92-9f79-6afd25b7549e)

 This code was only updating one column at a time, meaning the rest of the screen was static between updates.
 You could also see a kind of visual blink when this code ran each time : system("cls")). This approach was wrong as it was clearing the whole screen, which
 was resulting in flickering.

 ![image](https://github.com/user-attachments/assets/6940365e-2792-4b72-a31a-692001a2f7c2)

 By switching to a vector-based approach which stores a dynamic collection of RainDrop objects., I was able to update all active raindrops simultaneously. This 
 allowed for a much smoother transitionsmand eliminated the need to clear the screen entirely each time. 
 Since vector’s are dynamic this allowed me to handle multiple raindrops more efficiently, creating a much more apealing visual.
 
 This change significantly reduced the flickering and improved the overall performance and visual quality of the simulation.

## Modern C++ insight & reflection
  Previously i was using srand but that is not the correct practice of a modern
  C++ programmer, so i instead decided to use the <random> library, I avoided to use srand() because
  it's outdated, has poor randomness and is not thread safe, these are all features i want to avoid as a programmer.

  Another guideline I followed was that a modern C++ programmer would include constructors and destructors in the project, even if they aren't strictly required.

  Another practice I followed to was including return statements in the code, even when they aren't necessary. It’s considered good practice in C++ to 
  write return statements, as it improves readability and maintainability.

  I also kept my Main.cpp as simple and tidy as possible allowing for easy readability and naviagtion throughout the project

## DigitalRain image
Image of my digital rain project : 
![image](https://github.com/user-attachments/assets/c54e1a61-13da-4280-9fcd-28213220c0ee)

<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/DigitalRain.jpg" width="400" height="300">
