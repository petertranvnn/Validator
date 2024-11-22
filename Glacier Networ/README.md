
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
wget https://github.com/Glacier-Labs/node-bootstrap/releases/download/v0.0.1-beta/verifier_linux_amd64
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

chmod +x verifier_linux_amd64

./verifier_linux_amd64
```



