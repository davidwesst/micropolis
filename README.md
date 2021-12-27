 # Modern Micropolis (Working Title)
 Modern Micropolis (or MMicropolis for short) is a modernization of the original Micropolis game (a.k.a. SimCity) and source code released by Don Hopkins [(Reference)](https://www.donhopkins.com/home/micropolis/). This is a _work-in-progress_ project.

 For the original README included in the project, see _README.original_ in the root project directory.

 ## Development Setup

 The MMicropolis repository is a self-contained development project that uses [Visual Studio Code](https://code.visualstudio.com/) and [DevContainers](https://code.visualstudio.com/docs/remote/containers) to handle the configuration and setup of a new environment. If you cannot install Docker locally, [GitHub Codespaces](https://code.visualstudio.com/docs/remote/codespaces) provides a paid-hosting option for DevContainers.

 ### Build
 
1. Clone the respository to your local machine.
2. Open the folder in Visual Studio Code.
   - The [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extension should be installed to allow for development with DevContainers.
3. From the command palette, select _Remote-Containers: Open Folder in Container_.
4. Verify all is working by running `cd src && make all` from the terminal.

### Common Tasks (Build, Rebuild, Clean, Run)

All common tasks included in the `./src/makefile` have been added as VSCode [Tasks](https://code.visualstudio.com/Docs/editor/tasks). See the `./vscode/tasks.json` for details.

## Running the Game

Being a desktop application mean that Micropolis runs on the "desktop" inside the docker container not on the host machine. There are two ways to interact with the running game while testing or debugging.

### Web Browser (noVNC)

The devcontainer exposes port 6080, where you can open `localhost:6080` and use password `vscode` if hosted locally or through whatever port forwarding address is provided by Codespaces.

### VNC Viewer (Locally Hosted Only)

The devcontainer exposes port 5091 which any VNC Viewer like [this one](https://www.realvnc.com/en/connect/download/viewer/) from Real VNC can connect to. Use the address `localhost:5901` with password `vscode`.

**NOTE: This method does appear to work with Codespaces dev environments.** 

## Debugging the Game

A debug launch configuration has been added to `./vscode/launch.json` that attaches VSCode to the GDB installed in the devcontainer enviornment. See the documentation about [Debugging in VSCode](https://code.visualstudio.com/Docs/editor/debugging) for details. On a successful launch, the debugger will break on start.

Refer to the _Running the Game_ section to interact and test the game with the debugger attached.
