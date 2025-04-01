---
layout: post
title: A Project in Modern C++
tags: cpp coding project
categories: demo
---

# A Project in Modern C++ Digital Rain coding project

The Digital Rain Project is a modern C++ project that visually represents falling digital raindrops.
The raindrops are made up of several symbols, characters, and numbers. I've made it so that the rain
is random and unpredictable and that each raindrop varies in shape and size. Throughout this project, 
I followed object-oriented programming principles and applied practices and techniques that I have learnt in this module.

## Software Design, Architechture & test

I went with the design of object-oriented code for this project. I chose object-oriented code because
it keeps the code organized and reusable. I also use constructors and destructors which ensures that each object is initialized properly.
Constructors help by setting default values and defining the object's state. This makes debugging and testing easier.

The first thing I attempted was to print Hello vertically.
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/Startercode.jpg" width="500" height="400">


  By being able to print hello veritcally going down my screen it gave me confidence that I can use
  letters and numbers to visually simulate digital rain. Here is an example of me printing random 
  numbers vertically. 
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/NumberCode.jpg" width="500" height="400">

  After being able to print out characters and numbers vertically, I chose to use ASCII symbols within the range of 33 to 126, which includes numbers, uppercase 
  and lowercase letters, and various symbols. This diverse character set enhances the visual appeal of the digital rain effect.
 
 <img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/ASCII.jpg" width="350" height="175">
 
  The available symbols from the ASCII table.
  
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/ASCIITable.jpg" width="600" height="400">

  After implemening the ASCII table to my project, the next solution was to be able to print out the range of characters randomly.
  To achieve this, I utilized the C++ random library, which provides tools for generating random numbers.

  I set up a random number generator using std::mt19937 and std::uniform_int_distribution<> to ensure that each character printed was selected from the specified 
  ASCII range, each time my rain simulation was running. 

  To vertically print, I was using the function gotoxy, positioning each character vertically down the console window, this was to create the illusion of falling 
  rain drops.
  I also implemented an animation loop that would constantly update the positions of characters, by clearing the screen and re-printing characters 
  in their new positions. This achievd a smooth visual transition.

  I have a function called TestRandomNumberGenerator, which ChatGPT helped me to design, OpenAI, "ChatGPT," OpenAI, Mar. 2025. [Online]. Available: 
  https://openai.com/chatgpt. In this test, it generates 1,000 random values to test 
  the X and Y coordinates. The function 
  is also wrapped in a try-catch block that will handle any exceptions. If any generated value falls outside the expected range, an error message is 
  printed to the console.

  Code Snippet of TestRandomNumberGenerator:
  <img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/TestRandomNumberGenerator.jpg" width="800" height="800">

## Algorithms
I am using algorithms in several places with in my code, The first algorithm I am going to talk about is the TestRandomNumberGenerator.
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/Algorithmimage1.jpg" width="800" height="400">

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
ASCII character. This algorithm enhances the visual of the digital rain. Mathematically, this algorithm relies on random number generation to ensure each 
raindrop’s position, speed, and character are unique, and the continuous fall of each raindrop is determined by the speed variable.
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/Algorithmimage2.jpg" width="800" height="700">

The Digitalrain::updateRain() algorithm simulates falling raindrops on the screen. 
It loops through each raindrop, clears its previous position, and moves it down by its speed. 

If a raindrop reaches the bottom of the screen, it will then reset to the top with a random position and speed.

The Digitalrain::StartRain() function begins the animation by first clearing the screen. Then, it enters an infinite loop where updateRain() is called 
repeatedly, and a 50-millisecond delay is added using Sleep(50) to control the update speed, creating a pleasant rain effect on the screen.


## Problem Solving
 One of the problems I was previously experincing was a flickering issue when running my simulation of digital rain. I wanted to improve transitions, to resolve 
 this issue i implemented Vectors. Snippet of old code :
 
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/ProblemSolvingimage1.jpg" width="800" height="400">

 This code was only updating one column at a time, meaning the rest of the screen was static between updates.
 You could also see a kind of visual blink when this code ran each time : system("cls")). This approach was wrong as it was clearing the whole screen, which
 was resulting in flickering.

 
<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/ProblemSolvingImage2.jpg" width="800" height="400">


 By switching to a vector-based approach which stores a dynamic collection of RainDrop objects., I was able to update all active raindrops simultaneously. This 
 allowed for a much smoother transitions and eliminated the need to clear the screen entirely each time. 
 Since vector’s are dynamic this allowed me to handle multiple raindrops more efficiently, creating a much more apealing visual.
 
 This change significantly reduced the flickering and improved the overall performance and visual quality of the simulation.

## Modern C++ insight & reflection
  Previously i was using srand() but that is not the correct practice of a modern
  C++ programmer, so i instead decided to use the random library, I avoided using srand() because
  it's outdated, has poor randomness and is not thread safe, these are all features i want to avoid as a programmer.

  Another guideline I followed was that a modern C++ programmer would include constructors and destructors in the project, even if they aren't strictly required.

  Another practice I followed to was including return statements in the code, even when they aren't necessary. It’s considered good practice in C++ to 
  write return statements, as it improves readability and maintainability.

  I also kept my Main.cpp as simple and tidy as possible, allowing for easy readability and navigation throughout the project.

   Reflecting on the project, I gained many valuable lessons from this module and project that, I will carry forward into my future career in industry.
  Throughout the project I put a strong emphasis on writing clean, well structured code and implied good coding practice styles and techniques in my 
  project.
  I beleive that applying these practice will help me become a better modern C++ programmer. 

## DigitalRain image
Image of my digital rain project : 


<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/Rain2.jpg" width="600" height="300">


Gif of my digital rain project : 


<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/Rain.gif" width="600" height="300">


