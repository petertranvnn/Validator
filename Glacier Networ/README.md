
### Thông tin
- Chuẩn bị: Ví metamask, BNB testnet trên OpBNB testnet
- Faucet BNB: https://www.bnbchain.org/en/testnet-faucet
- Brigde BNB testnet từ BNB sang OpBNB: https://opbnb-testnet-bridge.bnbchain.org
- Check Node status: https://testnet.nodes.glacier.io/status
- https://testnet.opbnbscan.com/

### Cấu hình tối thiểu
- CPU 1 Core
- Ram 2 GB
- Ổ cứng SSD 20 GB
- Hệ điều hành linux Ubuntu 22.04 trở lên

### Code chạy

1. Update

```
sudo apt-get update && sudo apt-get upgrade -y
```

2.

```
apt install screen
wget https://github.com/Glacier-Labs/node-bootstrap/releases/download/v0.0.2-beta/verifier_linux_amd64
```
3.
```
wget https://glacier-labs.github.io/node-bootstrap/config.yaml
```
4. mở nano
```
nano config.yaml
```
5. Edit nano
- Thay Private key ví trong “YourPrivateKey” bằng private ví của các bạn
- Sau đó nhấn tôt hợp phím
- Control+x
- Y
- Enter

6. Start Node
   
```
screen -S glacier-node

chmod +x verifier_linux_amd64

./verifier_linux_amd64
```
7. Check log
   
```
screen -R glacier-node

```
---------------------------------------------------------------------------------------
Update V0.03
```
docker run -d -e PRIVATE_KEY="YOUR_PRIVATE_KEY" --name glacier-verifier docker.io/glaciernetwork/glacier-verifier:v0.0.3
```

- sửa PRIVATE_KEY="YOUR_PRIVATE_KEY bằng Private ví bạn đang chạy

