# Try Out Development Containers: Python

[![Open in Dev Containers](https://img.shields.io/static/v1?label=Dev%20Containers&message=Open&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/microsoft/vscode-remote-try-python)

A **development container** is a running container with a well-defined tool/runtime stack and its prerequisites. You can try out development containers with **[GitHub Codespaces](https://github.com/features/codespaces)** or **[Visual Studio Code Dev Containers](https://aka.ms/vscode-remote/containers)**.

This is a sample project that lets you try out either option in a few easy steps. We have a variety of other [vscode-remote-try-*](https://github.com/search?q=org%3Amicrosoft+vscode-remote-try-&type=Repositories) sample projects, too.

> **Note:** If you already have a codespace or dev container, you can jump to the [Things to try](#things-to-try) section. 

## Setting up the development container

### GitHub Codespaces
Follow these steps to open this sample in a Codespace:
1. Click the **Code** drop-down menu.
2. Click on the **Codespaces** tab.
3. Click **Create codespace on main** .

For more information on creating your codespace, visit the [GitHub documentation](https://docs.github.com/en/free-pro-team@latest/github/developing-online-with-codespaces/creating-a-codespace#creating-a-codespace).

### VS Code Dev Containers

If you already have VS Code and Docker installed, you can click the badge above or [here](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/microsoft/vscode-remote-try-python) to get started. Clicking these links will cause VS Code to automatically install the Dev Containers extension if needed, clone the source code into a container volume, and spin up a dev container for use.

Follow these steps to open this sample in a container using the VS Code Dev Containers extension:

1. If this is your first time using a development container, please ensure your system meets the prerequisites (i.e. have Docker installed) in the [getting started steps](https://aka.ms/vscode-remote/containers/getting-started).

2. To use this repository, you can either open the repository in an isolated Docker volume:

    - Press <kbd>F1</kbd> and select the **Dev Containers: Try a Sample...** command.
    - Choose the "Python" sample, wait for the container to start, and try things out!
        > **Note:** Under the hood, this will use the **Dev Containers: Clone Repository in Container Volume...** command to clone the source code in a Docker volume instead of the local filesystem. [Volumes](https://docs.docker.com/storage/volumes/) are the preferred mechanism for persisting container data.   

   Or open a locally cloned copy of the code:

   - Clone this repository to your local filesystem.
   - Press <kbd>F1</kbd> and select the **Dev Containers: Open Folder in Container...** command.
   - Select the cloned copy of this folder, wait for the container to start, and try things out!

## Things to try

Once you have this sample opened, you'll be able to work with it like you would locally.

Some things to try:

1. **Edit:**
   - Open `app.py`
   - Try adding some code and check out the language features.
   - Make a spelling mistake and notice it is detected. The [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) extension was automatically installed because it is referenced in `.devcontainer/devcontainer.json`.
   - Also notice that utilities like `pylint` and the [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) extension are installed. Tools are installed in the `mcr.microsoft.com/devcontainers/python` image and Dev Container settings and metadata are automatically picked up from [image labels](https://containers.dev/implementors/reference/#labels).


2. **Terminal:** 
    - Press <kbd>ctrl</kbd>+<kbd>shift</kbd>+<kbd>\`</kbd> to open a terminal window.
    - Type `python -m flask run --port 9000 --no-debugger --no-reload` to run the app.
         - The terminal will say your app is `Running on http://127.0.0.1:9000/`. Click on the link in the terminal to view your app running in the browser.
    - Notice that the Python extension is already installed in the container since the `.devcontainer/devcontainer.json` lists `"ms-python.python"` as an extension to install automatically when the container is created.
    
      > **Tip:** If you use this container outside of VS Code via `docker run` with `-p 9000`, you may need to append `--host 0.0.0.0` to the command above. The `-p` option "publishes" the port rather than forwarding it. It therefore will not work if the application only listens to localhost. The `forwardPorts` property in `devcontainer.json` does not have this limitation, but you can use `appPort` property instead if you want to mirror the `docker run` behavior.

3. **Build, Run, and Debug:**
   - Open `app.py`
   - Add a breakpoint (e.g. on line 9).
   - Press <kbd>F5</kbd> to launch the app in the container.
   - Once the breakpoint is hit, try hovering over variables (e.g. the app variable on line 7), examining locals, and more.
   - Continue (<kbd>F5</kbd>). You can connect to the server in the container by either: 
      - Clicking on `Open in Browser` in the notification telling you: `Your service running on port 9000 is available`.
      - Clicking the globe icon in the 'Ports' view. The 'Ports' view gives you an organized table of your forwarded ports, and you can access it with the command **Ports: Focus on Ports View**.
   - Notice port 9000 in the 'Ports' view is labeled "Hello Remote World." In `devcontainer.json`, you can set `"portsAttributes"`, such as a label for your forwarded ports and the action to be taken when the port is autoforwarded.
   
   > **Note:** In Dev Containers, you can access your app at `http://localhost:9000` in a local browser. But in a browser-based Codespace, you must click the link from the notification or the `Ports` view so that the service handles port forwarding in the browser and generates the correct URL.

4. **Rebuild or update your container**

   You may want to make changes to your container, such as installing a different version of a software or forwarding a new port. You'll rebuild your container for your changes to take effect. 

   **Open browser automatically:** As an example change, let's update the `portsAttributes` in the `.devcontainer/devcontainer.json` file to open a browser when our port is automatically forwarded.
   
   - Open the `.devcontainer/devcontainer.json` file.
   - Modify the `"onAutoForward"` attribute in your `portsAttributes` from `"notify"` to `"openBrowser"`.
   - Press <kbd>F1</kbd> and select the **Dev Containers: Rebuild Container** or **Codespaces: Rebuild Container** command so the modifications are picked up.  

5. **Install Node.js using a Dev Container Feature:**
   - Press <kbd>F1</kbd> and select the **Dev Containers: Configure Container Features...** or **Codespaces: Configure Container Features...** command.
   - Type "node" in the text box at the top.
   - Check the check box next to "Node.js (via nvm) and yarn" (published by devcontainers) 
   - Click OK
   - Press <kbd>F1</kbd> and select the **Dev Containers: Rebuild Container** or **Codespaces: Rebuild Container** command so the modifications are picked up.
##Docker Manual Installation for VS Code Remote - Containers (vscode-remote-try-python)

This guide walks you through installing Docker on Ubuntu and using it with VS Code's Remote - Containers extension, specifically with the vscode-remote-try-python template.

Prerequisites

Ubuntu 24.04 or later

A user with sudo privileges

Visual Studio Code installed with the Remote - Containers extension

🧱 Step 1: Uninstall Old Docker Versions (if any)

Before installing a fresh version of Docker, remove any old versions:

sudo apt remove docker docker.io containerd runc

🧱 Step 2: Install Required Dependencies

Install required dependencies for Docker installation:

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

🧱 Step 3: Add Docker’s Official GPG Key

Add Docker’s official GPG key to ensure the authenticity of packages:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

🧱 Step 4: Add Docker’s Official Repository

Add Docker’s official APT repository:

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

🧱 Step 5: Update the Package Index

Update your package list to include Docker’s repository:

sudo apt update

🧱 Step 6: Install Docker Engine, CLI, and Containerd

Install Docker Engine, Docker CLI, and Containerd:

sudo apt install docker-ce docker-ce-cli containerd.io -y

🧱 Step 7: Enable and Start Docker Service

Enable Docker to start on boot and start the service:

sudo systemctl enable docker
sudo systemctl start docker

🧱 Step 8: Verify Installation

Confirm that Docker is installed correctly by checking the version:

docker --version


You should see an output like:

Docker version 20.10.7, build f0df350

🧱 Step 9: (Optional) Run Docker Without sudo

If you prefer to run Docker commands without needing sudo:

sudo usermod -aG docker $USER


After running this, log out and log back in (or reboot your system).

🧑‍💻 Step 10: Using VS Code Remote - Containers

Install Remote - Containers Extension: In VS Code, install the Remote - Containers extension
.

Clone the vscode-remote-try-python repository (or any other repo you want to work with):

git clone https://github.com/microsoft/vscode-remote-try-python.git
cd vscode-remote-try-python


Open VS Code: Inside your project folder, launch VS Code:

code .


Reopen in Container: In the bottom-left corner of VS Code, click the "><" Remote button and select “Reopen in Container”. VS Code will build the Docker container and connect to your Python environment inside the container.

Troubleshooting Tips

Docker Command Not Found: Ensure the Docker service is running with sudo systemctl status docker.

Build Failures in VS Code: Check the logs inside VS Code's terminal and make sure your Docker version is compatible with the Remote - Containers extension.

Further Resources

Docker Documentation

VS Code Remote Containers Documentation

vscode-remote-try-python GitHub Repository
### More samples

- [Tweeter App - Python and Django](https://github.com/Microsoft/python-sample-tweeterapp)

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## License

Copyright © Microsoft Corporation All rights reserved.<br />
Licensed under the MIT License. See LICENSE in the project root for license information.

