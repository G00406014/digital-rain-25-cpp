# digital-rain-25-cpp


A Project in Modern C++ cpp coding project
--
The Digital Rain Project is a modern C++ project that visually represents falling raindrops,
//think about adding a try catch, exexution 

## Software Design, Architechture & test
- Design
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

Another algorithm which 

## Algorithms Development
- algorithms
## Problem Solving
- issues
## Modern C++ insight & reflection
- removing Srand()
## DigitalRain image
![image](https://github.com/user-attachments/assets/c54e1a61-13da-4280-9fcd-28213220c0ee)
//<img src="https://raw.githubusercontent.com/G00406014/digital-rain-25-cpp/main/docs/assets/images/DigitalRainDev1.png" width="400" height="300">
