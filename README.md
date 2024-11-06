
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
- **Visual Studio Code**: Install with the Microsoft C/C++ extension and the CMake Tools extension.
- **JUCE**: Download JUCE and ensure it is available on your system.
- **CMake**: Install CMake and add it to your system PATH.
- **Compiler**:
  - **Windows**: Download Visual Studio and install the **Desktop Development with C++** workload.
  - **macOS/Linux**: Install Xcode Command Line Tools or Clang.

## Setting up the JUCE Paths

### Option 1: Using an environmental variable (Reccomended)

*Note: Replace `/path/to/JUCE` with the actual path to your JUCE directory.*

### macOS/Linux
1. Open your terminal.

2. Determine your shell type:
   ```bash
   echo $SHELL
   ```
   *You'll likely see something like `/bin/zsh`*

3. Edit your shell configuration file (e.g., `.bashrc`, `.zshrc`, or `.bash_profile`):
   ```bash
   nano ~/.bashrc  # or ~/.zshrc or ~/.bash_profile
   ```

4. Add the following lines ot set `JUCE_DIR` and `JUCE_MODULES_PATH`:
   ```bash
   export JUCE_DIR="/path/to/JUCE"
   export JUCE_MODULES_PATH="/path/to/juce/modules"
   ```
*Do not add spaces to after the export command, adding spaces will result in the path not being found*
*If you already have exisitng code in the file do not change those just add the directory to the bottom*

5. Save and close file: 
   In `nano` press `CTRL + X`, then `Y` to confirm saving then `ENTER` to confirm file name.

6. Run:
   ```bash
   source ~/.bashrc  # or source ~/.zshrc
   ```
*This command reloads your shell configuration so the new variable is immediately available.*

### Windows
1. Open **"Edit the system environment variables"** from the Start menu.
   - Press the **Windows Key** or click the **Start** button.
   - Type `environment variable` in the search bar.
   - Select **Edit the system environment variables** from the search results.

2. Click **"Environment Variables"**.

3. Under **"User variables"**, add a new variable:
   - **Name**: `JUCE_MODULES_PATH`
   - **Value**: `C:\path\to\juce\modules`

4. Click OK to save.

#### Option 2: Manually Updating the Path
1. Open `.vscode/c_cpp_properties.json`.

2. Replace `${env:JUCE_MODULES_PATH}` with your full JUCE modules path:
   - **macOS/Linux**: `/path/to/juce/modules/**`
   - **Windows**: `C:/path/to/juce/modules/**`

## Generating `JuceLibraryCode` with Projucer

The `JuceLibraryCode`folder and `JuceHeader.h` are generated using the  projucer
1. Open the Projucer (found in the JUCE directory).
2. Open the .jucer project file located in the project directory.
3. Verify the necessary JUCE modules are added under the Modules section.
4. Click "Save Project" or "Save and Open in IDE" to generate or update the JuceLibraryCode folder.
5. Commit the JuceLibraryCode folder to version control, so all team members have access to it
*Step 5 is optional because the JuceLibraryCode file is excluded from commits because each time we build we should use the projucer first to get the necessary files*

## Building the Project with Cmake

### macOS/Linux
1. Open a terminal and navigate to the project directory:
   ```bash
   cd /path/to/team8_project
   ```
2. Create a build directory and navigate into it:
   ```bash
   mkdir build
   cd build
   ```
3. Run CMake to configure the project:
   ```bash
   cmake .. -D JUCE_DIR=$JUCE_DIR -D CMAKE_BUILD_TYPE=Debug
   ```
4. Build the project:
   ```bash
   cmake --build . --config Debug
   ```
### Windows

1. Open Command Prompt or Developer Command Prompt.
2. Navigate to the project directory:
   ```cmd
   cd C:\path\to\team8_project
   ```
3. Create and navigate to the build directory:
   ```cmd
   mkdir build
   cd build
   ```
4. Run CMake to configure the project:
   ```cmd
   cmake .. -G "Visual Studio 17 2022" -D JUCE_DIR=%JUCE_DIR%
   ```
5. Build the project:
   ```cmd
   cmake --build . --config Debug
   ```
### Selecting up VS Code
1. Open **VS Code** and ensure CMake Tools extension is installed.

2. In the bottom right corner, click on the IntelliSense configuration (e.g., "Mac" or "Win32").

3. Open the **Command Palette** (`Ctrl + Shift + P`) and select **Cmake: Configure**

4. Choose the appropriate CMake kit:
   - **macOS**: select Clang. 
   - **Windows**: Select the correct Visual Studio version (e.g. "Visual Studio 17, 2022"). 

5. Set Build Configuration:
   - Open the Command Palette again and choose **CMake: Set Build Type**.
   - Select Debug or Release based on your needs.
   
6. Build:
   - Use CMake: Build from the Command Palette.

### Troubleshooting
- Ensure your environment variable is set correctly.
- On macOS/Linux, reload your shell with `source ~/.bashrc`.
- On Windows, you may need to restart VS Code or your computer.
- JuceHeader.h Not Found:
   - Ensure JuceLibraryCode is generated using the Projucer and that JuceHeader.h exists.
   - Make sure JUCE_DIR and JUCE_MODULES_PATH environment variables are correctly set.
- CMake Errors:
   - Verify cmake.cmakePath in VS Code settings points to the correct CMake executable path.
   - Run cmake --version in the terminal to confirm CMake is installed.


# Guidelines 

## Adding New Source Files
When you add new `.cpp` or `.h` files to the project, make sure to update `CMakeLists.txt` to include these files in the `target_sources()` section:
```cmake
target_sources(team8_project
    PRIVATE
        Source/YourNewFile.cpp
        Source/YourNewFile.h
)
```
## Pulling the Latest Changes
To Update your local repository:
   ```bash
   git pull origin main
   ```

## Stashing Local Changes (if necessary)
If you have uncommited changes, you can stash them (when want fetch new changes):
   ```bash
   git stash
   git pull origin main
   git stash apply 
   ```

## Branching Workflow for Each Effect Team

To help each team work independently on their specific effects, follow this branching workflow:

### Creating and Working on a New Branch

1. **Clone the Repository (If Not Done Already)**:
   - First, clone the repository if you haven’t already:
     ```bash
     git clone https://github.com/efrosty24/JUICE-Project.git
     ```

2. **Create a New Branch for Your Effect**:
   - Use a descriptive branch name, like `effect-graphic-eq` or `effect-distortion`.
   - Create and switch to a new branch:
     ```bash
     git checkout -b effect-graphic-eq
     ```
   - Replace `effect-graphic-eq` with the name of your specific effect branch.

3. **Push the New Branch to GitHub**:
   - Push the new branch to the remote repository so others can see it:
     ```bash
     git push -u origin effect-graphic-eq
     ```
   - The `-u` flag sets up tracking so future pushes on this branch only require `git push`.

4. **Work on Your Branch**:
   - Make changes to files in your branch. When ready to save progress, commit the changes:
     ```bash
     git add .
     git commit -m "Implement initial version of Graphic EQ effect"
     ```

5. **Push Local Changes to the Remote Branch**:
   - Sync changes to the remote branch on GitHub:
     ```bash
     git push
     ```
   - Since tracking is set up, `git push` will push changes to the same branch on GitHub.

6. **Stay Up-to-Date with `main` (Optional)**:
   - To stay current with changes in `main`, periodically merge `main` into your feature branch:
     ```bash
     git checkout effect-graphic-eq
     git pull origin main
     ```
   - Resolve any merge conflicts, then commit the merge.

---

### Merging Your Branch Back into `main`

1. **Open a Pull Request (PR)**:
   - Once the effect is complete, open a pull request on GitHub to merge your branch into `main`.
   - In GitHub, go to **Pull Requests** and click **New pull request**.
   - Select your feature branch (e.g., `effect-graphic-eq`) as the source and `main` as the target, then create the pull request.

2. **Code Review and Merge**:
   - After reviewing the code, merge the branch into `main`.
   - Once merged, delete the feature branch on GitHub to keep the repository organized.

---

### Summary for Team Members

1. **Create a Branch**: `git checkout -b effect-name`
2. **Push the Branch**: `git push -u origin effect-name`
3. **Work and Commit**: `git add .` and `git commit -m "Message"`
4. **Push Changes**: `git push`
5. **Open a Pull Request**: Once complete, open a PR to merge into `main`.

This workflow keeps each effect isolated for easier development and integration.
