CẤU HÌNH
- CPU: 6 core
- RAM: 4Gb
- SSD 100Gb
- OS: Ubuntu 22.04
- Sever: Contabo
  
### Thông tin
- Faucet Arbitrum ETH Sepolia
https://faucet.quicknode.com/arbitrum/sepolia
  
- Faucet Privasea DeepSea Beta tokens
  https://deepsea-beta.privasea.ai/deepSeaFaucet


1. Update

```
sudo apt-get update && sudo apt-get upgrade -y
```

2. Cài Docker

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
sudo apt-get install docker.io -y
```

```
sudo apt update
```

```
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

```
sudo docker --version
```

```
sudo systemctl start docker
```

```
sudo systemctl enable docker
```


3. Pull docker mirroring
```
docker pull privasea/acceleration-node-beta:latest
```

4. Tạo thư mục privasea

```
mkdir -p ~/privasea/config && cd ~/privasea
```

5. Lấy keystore
```
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
Đặt mật khẩu

6. Chuyển keystore vào thư mục privasea
```
mv $HOME/privasea/config/UTC--* $HOME/privasea/config/wallet_keystore
```

7.
- Truy cập vào [Privanetix Dashboard](https://deepsea-beta.privasea.ai/privanetixNode)
- Kết nối ví chính và thiết lập node 

8. Run node
```
KEYSTORE_PASSWORD=<Mật Khẩu> && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" -e KEYSTORE_PASSWORD=$KEYSTORE_PASSWORD privasea/acceleration-node-beta:latest
```
Note: Nhớ thay <Mật Khẩu> bằng mật khẩu đã đặt cho keystore phía trên

9. Check log
```
docker logs -f <eb723c38e3e6283f6c9d50512828408bd6df2fbba22d1991daa459778d3e73bc>
```
Note: Thay <eb723c38e3e6283f6c9d50512828408bd6df2fbba22d1991daa459778d3e73bc> bằng khóa node của bạn

10. Dừng node
```
docker ps -q --filter "ancestor=privasea/acceleration-node-beta:latest" | xargs --no-run-if-empty docker stop
```

```
docker ps | grep privasea/acceleration-node-beta:latest
```



