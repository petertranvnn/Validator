
### Thông tin
- CHuẩn bị: ảnh lòng bàn tay, ảnh selfie, Ví Nillion (Keplr, leap)
- Link: https://verifier.nillion.com/verifier
- Faucet: https://faucet.testnet.nillion.com/

### Phần mềm yêu cầu

- [Docker](https://docs.docker.com/desktop/)


### Cấu hình phần cứng
- CPU 2 Core
- Ram 4 GB
- Ổ cứng SSD 40 GB
- Hệ điều hành linux Ubintu 22.04 trở lên

### Code chạy

1. Update

```
sudo apt-get update && sudo apt-get upgrade -y
```

2. Cài đặt docker

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt-get update
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y
```

Kiểm tra version Docker
```
docker --version
```

3/ Cài đặt node Nillion

```
docker pull nillion/verifier:v1.0.1
```
```
mkdir -p nillion/verifier
```
```
docker run -v ./nillion/verifier:/var/tmp nillion/verifier:v1.0.1 initialise
```

4/ Coppy account id & Public Key paste vào trang verify của Nillion

5/ Vào trang Faucet, Faucet NIL testnet vào địa chỉ ví (là cái account id vừa mới lấy trong terminal)

6/ Cuối cùng chạy lệnh này
```
docker run -v ./nillion/verifier:/var/tmp nillion/verifier:v1.0.1 verify --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com"
```




