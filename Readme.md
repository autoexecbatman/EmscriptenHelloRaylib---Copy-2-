# Emscripten Raylib Projects

## About

This is a "Starter" repo for Raylib projects. Web builds are automaticly triggered via Github actions and Deployed to Github Pages.

Libraries are Pre-Compiled for:
 - Visual Studio 2022
 - Emscripten

## Creating a new Project
1. Duplicate the `HelloRaylib` from the `projects` folder.
2. Rename the folder to match your project name.
3. Edit the `CMakeLists.txt` file in your new project folder.
    ```CMake
    project("<your_project_name>")
    ```
4. Edit `CMakeLists.txt` in the **root directory** to include the new project.
    ```CMake
    # Include sub-projects
    # ====================
    add_subdirectory ("projects/HelloRaylib")
    add_subdirectory ("projects/<your_project_name>")
    # ====================
    ```

## Building on windows
1. Create a folder for the Visual Studio files.
 - `mkdir vs`
2. Navigate to the folder.
 - `cd vs`
3. Open a powershell window in the folder.(or another shell)
4. Use cmake to build the solution
 - `cmake .. -G "Visual Studio 17 2022"`

## Building for web (locally)
**this step is optional**

To build the project locally you will need to install `docker for windows` https://hub.docker.com/editions/community/docker-ce-desktop-windows/

1. make sure `docker desktop` is running
2. double click on `windows_docker_build_web.bat` <br/>
this will compile your project with the emscripten toolchain
3. If no errors have occured - Your game will be available in the `bin/Emscripten/<your_project_name>/` folder
4. You will need to serve the generated files via a local webserver
 - Navigate to emscripten build folder
  - `cd bin/Emscripten/<your_project_name>/`
 - open powershell (make sure to setup emscripten)
  - `emrun <your_project_name>.html`

## Automated Build and Deploy to GHPages
This repo contains a github action that will automaticly build and publish your projects to the gh-pages branch.

To view your published projects, Github Pages will need to be enabled via your repository settings.

[Link to a sample project on GHPages](https://autoexecbatman.github.io/EmscriptenHelloRaylib---Copy-2-/Pong/Pong.html)
