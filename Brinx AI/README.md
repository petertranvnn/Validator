
Note: Nguồn code và hướng dẫn coppy từ nodesync

1. Update

```
sudo apt-get update && sudo apt-get upgrade -y
```

2. Cài đặt docker
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```

3. Pull Worker

```
docker pull admier/brinxai_nodes-worker:latest
```

4/  Run Worker

```
git clone https://github.com/admier1/BrinxAI-Worker-Nodes
cd BrinxAI-Worker-Nodes
chmod +x install_ubuntu.sh
./install_ubuntu.sh
```
5/ Đăng ký tài khoản và login 
- Link: https://workers.brinxai.com/register.php?ref=d45334ca
- Sau khi dăng nhập vào click vào Add Node và điền các thông tin vào
- xong rồi thì click tiếp "Manually Turn On Models" chọn cấu hình phù hợp để chạy.
- Coppy lệnh rồi paste vào terminal nếu hợp lệ thì chạy được
- chờ 15 - 30 phút vào xem đã chạy thành công chưa


