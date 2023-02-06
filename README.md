# UTF-8 terminal for Windows

This proccess goal is to being able to develop with [**Elixir**](https://elixir-lang.org/) programming language on [**Windows**](https://www.microsoft.com) operating systems implementing a terminal that can correctly display characters encoded for **Unicode UTF-8**.

1. Install ***Visual Studio Code*** on your system. The installation can be done following the documentation in this link: [`https://code.visualstudio.com/Download`](https://code.visualstudio.com/Download)

1. Install on ***Visual Studio Code*** application the [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extension.

1. Open a ***PowerShell*** terminal and run:

    ```powershell
    wsl --install
    ```

    Some motherboards BIOS may not have *Secure Virtual Machine* (SVM) enabled by default. To enable virtualization, consult the documentation matching the motherboard model and BIOS version in order to enable it.

    Once the system virtualization has been properly configured, the installation can be completed. If this is the case, [Ubuntu](https://ubuntu.com/) will have been installed by default in WSL, the terminal will ask us to create a user with username and password, creating an user completes the installation.

1. It is necesary to install a few libraries for ***Ubuntu***. Open the recently created ***Ubuntu*** terminal and run:

    ```bash
    sudo apt update && apt upgrade
    sudo apt-get install \
      inotify-tools \
      libssl-dev \
      make \
      automake \
      autoconf \
      libncurses5-dev \
      gcc \
      g++ \
      unzip
    ```

1. Install ***ASDF*** version manager:

    ```bash
    git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.11.1
    echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
    echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc # optional
    source ~/.bashrc
    ```

1. Add to ***ASDF*** the Erlang and Elixir plugins, install both latest version and set those as global target versions:

    ```bash
    asdf plugin-add erlang
    asdf install erlang 25.0.4
    asdf global erlang 25.0.4

    asdf plugin-add elixir
    asdf install elixir 1.14.0-otp-25
    asdf global elixir 1.14.0-otp-25
    ```

1. Install ***Phoenix*** by running:

    ```bash
    mix local.hex
    mix archive.install hex phx_new
    ```

1. Install ***PostgreSQL*** in ***Ubuntu***:

    <https://wiki.postgresql.org/wiki/Detailed_installation_guides>
