# Layeredge Node Setup


# INSTALL GOLANG
        Curl -OL https://go.dev/dl/go1.23.0.linux-amd64.tar.gz
        sudo tar -C /usr/local -xvf go1.16.7.linux-amd64.tar.gz
        sudo nano ~/.profile
        add the following information to the end of your file: export PATH=$PATH:/usr/local/go/bin
        
# INSTALL RUSTUP
        Install Rust curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
        Choose 1
        source "$HOME/.cargo/env"
        rustc -V
        go version

# INSTALL DOCKER
        # Add Docker's official GPG key:
        
        sudo apt-get update
        sudo apt-get install ca-certificates curl
        sudo install -m 0755 -d /etc/apt/keyrings
        sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
        sudo chmod a+r /etc/apt/keyrings/docker.asc

        
        # Add the repository to Apt sources:
        
        echo \
          "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
          $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
          sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        sudo apt-get update

# INSTALL SCREEN & GIT & TOOLCHAIN
        apt-getinstall screen && git-all -y && curl -L https://risczero.com/install | bash && rzup install

# CONFIGURE ENVIRONMENT VARIABLES

        GRPC_URL=34.31.74.109:9090
        CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
        ZK_PROVER_URL=http://127.0.0.1:3001
        API_REQUEST_TIMEOUT=100
        POINTS_API=https://light-node.layeredge.io
        PRIVATE_KEY='burn-private-key'

# START THE MERKLE SERVICE
        cd risc0-merkle-service
        cargo build && cargo run

# RUN LAYEREDGE LIGHT NODE
        Screen -S go Then Type go build
        Open New Terminal Then Type Screen -S edge
        ./light-node
        Copy your Public key then paste on https://dashboard.layeredge.io/
        Code: U7b0EDwb
