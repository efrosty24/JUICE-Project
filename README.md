
# CodeCoogs Team 8 Github Repository

## What is our team project?

We are going to be making an effect rack plugin that is compatible across multiple DAWs.
Our team is going to learn many skills such as Object-Oriented Programming, C++, UI/UX, Git/GitHub, and many more skills!


## Types of *Effects* we are going to be building 

- Graphic EQ
- Distortion
- Reverb
- Delay

## Setting up the JUCE_DIR
Before building the project, make sure the JUCE_DIR variable is updated to the path of your local JUCE installation directory

- Before proceeding make sure you have downloaded and configured Cmake on your local machine.
- Rely on generative AI as needed because this process varies from mahcine to machine.

### Option 1: Set up JUCE_DIR as an Environment Variable

'''bash'''
> export JUCE_DIR= /path/to/JUCE

In the code above change the the "/path/to/JUCE" as the path to your JUCE download folder.

For example on my mac my directory for JUCE is /Users/evanf/JUCE, so I would use that as my "path/to/JUCE"

### Option 2: Pass JUCE_DIR as a CMake Argument 
'''bash'''
> cmake -B build -S . -D JUCE_DIR=/path/to/JUCE

Again change the "/path/to/JUCE" as the download path to JUCE on your machine.

Then you want to execute this with
'''bash'''
> cmake --build build 

Whenever you want to build the project. 
