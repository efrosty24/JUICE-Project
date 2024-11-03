
# CodeCoogs Team 8 Github Repository

## What is our team project?

We are going to be making an effect rack plugin that is compatible across multiple DAWs.

Our team is going to learn many skills such as Object-Oriented Programming, C++, UI/UX, Git/GitHub, and many more skills!


## Types of *Effects* we are going to be building 

- Graphic EQ
- Distortion
- Reverb
- Delay

# Project Setup

### Prerequisites
- Make sure you have Visual Studio Code installed, along with the Microsoft C/C++ extension.
- Ensure JUCE is downloaded and available on your system.
- Make sure you have downloaded and configured CMake on your local machine.
- Rely on generative AI as needed because this process varies from machine to machine.

## Setting up the JUCE_DIR
Before building the project, make sure the JUCE_DIR variable is updated to the path of your local JUCE installation directory
### Option 1: Set up JUCE_DIR as an Environment Variable
```bash
    export JUCE_DIR= /path/to/JUCE
```
*Note: In the code above change the the "/path/to/JUCE" as the path to your JUCE download folder. Maintain the quotations around the path.*

*For example on a Mac, it could look like /Users/evanf/JUCE*

### Option 2: Pass JUCE_DIR as a CMake Argument 
```bash
    cmake -B build -S . -D JUCE_DIR=/path/to/JUCE
```
*Again change the "/path/to/JUCE" as the download path to JUCE on your machine.*

Then you want to execute this with
```bash
    cmake --build build 
```
Run this command whenever you want to build the project. You should always run this command whenever you make any changes to the source code, as it configures the builiding of the project.

## Setting up the JUCE Modules Path

### Option 1: Using an environmental variable (Reccomended)

*Note: Use the actual path to your JUCE modules folder as /path/to/juce/modules in the instructions below. Keep the quotation marks around the path*

1. **macOS/Linux**
- Open your terminal.
- Edit your shell configuration file (e.g., `.bashrc`, `.zshrc`, or `.bash_profile`):
   ```bash
   nano ~/.bashrc  # or ~/.zshrc or ~/.bash_profile
   ```
- Add the following line:
   ```bash
   export JUCE_MODULES_PATH="/path/to/juce/modules"
   ```
- Save the file and run:
   ```bash
   source ~/.bashrc  # or source ~/.zshrc
   ```
*This command reloads your shell configuration so the new variable is immediately available.*

2. **Windows**
- Open **"Edit the system environment variables"** from the Start menu.
- Click **"Environment Variables"**.
- Under **"User variables"**, add a new variable:
   - **Name**: `JUCE_MODULES_PATH`
   - **Value**: `C:\path\to\juce\modules`
- Click OK to save.

#### Option 2: Manually Updating the Path
1. Open `.vscode/c_cpp_properties.json`.
2. Replace `${env:JUCE_MODULES_PATH}` with your full JUCE modules path:
   - **macOS/Linux**: `/path/to/juce/modules/**`
   - **Windows**: `C:/path/to/juce/modules/**`

### Selecting the Correct Configuration in VS Code
1. Open VS Code.
2. In the bottom right corner, click on the IntelliSense configuration (e.g., "Mac" or "Win32").
3. Select the appropriate configuration for your operating system.

### Troubleshooting
- Ensure your environment variable is set correctly.
- On macOS/Linux, reload your shell with `source ~/.bashrc`.
- On Windows, you may need to restart VS Code or your computer.

# Guidelines 

### Adding New Source Files
When you add new `.cpp` or `.h` files to the project, make sure to update `CMakeLists.txt` to include these files in the `target_sources()` section:
```cmake
target_sources(team8_project
    PRIVATE
        Source/YourNewFile.cpp
        Source/YourNewFile.h
)
```
When you commit specify what changes were done concisely and if you did add any source files
