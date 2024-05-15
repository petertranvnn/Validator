### Phần mềm yêu cầu

- [Docker](https://docs.docker.com/desktop/)
- [Python 3](https://www.python.org/downloads/)

### Cấu hình phần cứng

Cấu hình khuyến nghị:
- Ram 16 GB
- CPU 4 Core
- Ổ cứng SSD 1T
  
Cấu hình tối thiểu:
- Ram 4 GB
- CPU 8 core
- Ổ cứng SSD 400 GB

- Hệ điều hành linux Ubintu 20.04 trở lên

### Code chạy

1. Update

```
sudo apt-get update && sudo apt-get upgrade -y
```

2. Cài đặt
```
sudo apt install curl git wget htop tmux build-essential jq make lz4 gcc unzip -y
```

2. coppy paste

```
cd $HOME
VER="1.21.3"
wget "https://golang.org/dl/go$VER.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$VER.linux-amd64.tar.gz"
rm "go$VER.linux-amd64.tar.gz"
[ ! -f ~/.bash_profile ] && touch ~/.bash_profile
echo "export PATH=$PATH:/usr/local/go/bin:~/go/bin" >> ~/.bash_profile
source $HOME/.bash_profile
[ ! -d ~/go/bin ] && mkdir -p ~/go/bin
```

3/ Coppy từng lệnh 

```
git clone https://github.com/initia-labs/initia
cd initia
git checkout v0.2.11
make build
```
4/

```
mkdir -p $HOME/.initia/cosmovisor/genesis/bin
mv /root/initia/build/initiad $HOME/.initia/cosmovisor/genesis/bin/
```

5/

```
sudo ln -s $HOME/.initia/cosmovisor/genesis $HOME/.initia/cosmovisor/current -f
sudo ln -s $HOME/.initia/cosmovisor/current/bin/initiad /usr/local/bin/initiad -f
```

6/

```
go install cosmossdk.io/tools/cosmovisor/cmd/cosmovisor@v1.5.0
```

7/

```
sudo tee /etc/systemd/system/initiad.service > /dev/null << EOF
[Unit]
Description=initia node service
After=network-online.target

[Service]
User=$USER
ExecStart=$(which cosmovisor) run start
Restart=on-failure
RestartSec=10
LimitNOFILE=65535
Environment="DAEMON_HOME=$HOME/.initia"
Environment="DAEMON_NAME=initiad"
Environment="UNSAFE_SKIP_BACKUP=true"
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:$HOME/.initia/cosmovisor/current/bin"

[Install]
WantedBy=multi-user.target
EOF
```

8/ 
```
sudo systemctl daemon-reload
sudo systemctl enable initiad.service
```

9/bắt đầu chạy

```
sudo systemctl daemon-reload
sudo systemctl enable initiad.service
```

