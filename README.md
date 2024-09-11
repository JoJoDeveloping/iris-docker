# iris-docker
Docker container based on [4ever2's au-fsv](https://github.com/4ever2/au-fsv22) docker container.
The container can be used for easy cross-platform Coq/Iris development using Visual Studio Code.
The container configuration will automatically install the VsCoq extension for Visual Studio Code and configure Coq-related settings.

The precise software used in this image can be found in `src/Dockerfile`.

## Setup
1) [Install Docker](https://www.docker.com/get-started/)
2) Make sure Docker is running
3) [Install Visual Studio Code](https://code.visualstudio.com/Download)
4) [Install Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
5) Copy the `.devcontainer` folder to the root of your project folder

After following the above instructions open your project in Visual Studio Code and run the `>Dev Containers: Open Folder in Container` command.
If the instructions are followed correctly Visual Studio Code should also automatically suggest opening the repository in container mode when the project is loaded.

## System requirements
See [here](https://code.visualstudio.com/docs/remote/containers#_system-requirements)

## Known problems
### VSCode shows `Docker returned an error`
Make sure that Docker is installed and running.

### The `Dev Containers: Reopen in Container` command is not recognized by VSCode
You need to have the Remote - Containers extension VSCode extension installed and enabled.
See [here](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) for instructions on how to install it.

### Running `Dev Containers: Reopen in Container` cannot find the container
Make sure you copied the `.devcontainer` folder to your project's root folder and that it includes the `devcontainer.json` file.

### `Cannot find a physical path bound to logical path X with prefix Y` when importing a file
* Make sure that the Coq files have been compiled. Run `make` to compile the project files.
* If the `_CoqProject` files are not located in the project root folder you need to either
  * Move the files to the root project folder
  * Or add the line `"coq.coqProjectRoot": "PATH_TO_COQPROJECT"` (in `.devcontainer/devcontainer.json` to point to the directory where `_CoqProject` is located. Restarting the docker container is required after this step.

### Problems on Apple Silicon
Run `docker pull --platform linux/amd64 <the docker link>` to force the `x86` version of the Docker container to be installed.
This should then trick Docker into using some kind of emulation, and the software should work natively.

### pull rate limit hit
Docker Hub rate limits pulls of images for free accounts to 200 per six hours.
If this limit is hit you might get one of the following errors and have to wait until the rate limit resets.
* `ERROR: toomanyrequests: Too Many Requests`
* `You have reached your pull rate limit. You may increase the limit by authenticating and upgrading: https://www.docker.com/increase-rate-limits`

