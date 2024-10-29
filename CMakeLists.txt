# Minimum CMake version required
cmake_minimum_required(VERSION 3.15)

# Project name and version
project(team8_project VERSION 0.1.0)

# Path to JUCE library
#set(JUCE_DIR "/Users/evanf/JUCE")
if(NOT DEFINED JUCE_DIR)
    message(FATAL_ERROR "JUCE_DIR is not set. Please set JUCE_DIR as an environment variable or pass it as a CMake argument.")
endif()


# Add the JUCE library
add_subdirectory(${JUCE_DIR} JUCE)

# Define the JUCE plugin
juce_add_plugin(team8_project
    COMPANY_NAME "TeamJuice"
    PLUGIN_NAME "Team8 Project Plugin"
    VERSION "0.1.0"
    FORMATS VST3 AU Standalone # Define the plugin formats (VST3, AU, etc.)
    PRODUCT_NAME "Team8 Project Plugin"
    BUNDLE_ID "com.TeamJuice.team8_project"
)

# Add source files for the project
target_sources(team8_project
    PRIVATE
        Source/PluginProcessor.cpp
        Source/PluginProcessor.h
        Source/PluginEditor.cpp
        Source/PluginEditor.h
)

# Link JUCE modules to the project
target_link_libraries(team8_project
    PRIVATE
        juce::juce_audio_utils
        juce::juce_dsp
        juce::juce_audio_processors
        juce::juce_audio_basics
        juce::juce_gui_basics
)

# Set the C++ standard
set_property(TARGET team8_project PROPERTY CXX_STANDARD 17)
