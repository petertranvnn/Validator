### Phần mềm yêu cầu

- [Docker](https://docs.docker.com/desktop/)
- [Python 3](https://www.python.org/downloads/)

### Cấu hình phần cứng

Cấu hình khuyến nghị:
- Ram 16 GB
- CPU 4 Core
- Ổ cứng SSD 200 GB
  
Cấu hình tối thiểu có thể chạy:
- Ram 8 GB
- CPU 4 core
- Ổ cứng SSD 160 GB

- Hệ điều hành linux Ubintu 20.04 trở lên

### Code chạy

1. Chạy lệnh Update

```
sudo apt-get update && sudo apt-get upgrade -y
```

2. Cài đặt thư viện
```
sudo apt install curl build-essential git screen jq pkg-config libssl-dev libclang-dev ca-certificates gnupg lsb-release -y
```

2. Cài đặt docker

```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpgchmod a+r /etc/apt/keyrings/docker.gpg
```

3/

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
4/

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y
```

5/

```
git clone https://github.com/conduitxyz/node.gitclone https://github.com/conduitxyz/node.git
```

6/

```
cd node
./download-config.py zora-mainnet-0
```

7/

```
export CONDUIT_NETWORK=zora-mainnet-0
cp .env.example .env
nano .env
```

8/ 
**Chỗ này đặt khóa Alchemy API vào
OP_NODE_L1_ETH_RPC=http://khoa_Alchemy_API

9/bắt đầu chạy

```
screen -S loglog
docker compose up --build--build
```

