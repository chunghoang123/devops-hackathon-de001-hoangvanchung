DevOps Hackathon - De 001: 

1. Thong tin sinh vien
Ho va ten: Hoang Van Chung
Ma sinh vien: B24DTCN085
Lop: CNTT1
Tai khoan Linux: hoangvanchung-cntt1
GitHub: chunghoang123
Email: chungss7890@gmail.com
Cong Nginx: 8081
Repo: https://github.com/chunghoang123/devops-hackathon-de001-hoangvanchung

2. Moi truong trien khai
He dieu hanh: Ubuntu 24.04.5 LTS
Nginx: nginx/1.24.0 (Ubuntu), xem bang lenh nginx -v
Git: git version 2.43.0, xem bang lenh git --version
Noi chay: Server lab, card enp9s0, IP 192.168.0.103
IP may chu: 192.168.0.103, lay bang lenh hostname -I
Web root: /var/www/devops-hackathon-de001-hoangvanchung/src

3. Cau truc du an
devops-hackathon-de001-hoangvanchung/
src/index.html
nginx/hoangvanchung-cntt1.conf
.gitignore
README.md
Ghi chu: bo qua thu muc screenshots theo lua chon ca nhan, chap nhan mat diem anh minh chung.

4. Cau hinh Nginx
PORT = 8081 cho ca IPv4 va IPv6, khong dung cong 80 de tranh xung dot server chung.
SERVER_NAME = 192.168.0.103 la IP may chu, khong dung domain nen khong can DNS.
WEB_ROOT = /var/www/devops-hackathon-de001-hoangvanchung/src, tro dung vao src de khong lo README, nginx, .git.
INDEX_FILE = index.html la file mac dinh khi truy cap /.
TEN_TAI_KHOAN = hoangvanchung-cntt1 dung dat ten file log rieng access va error.
ALLOW_DIRECTIVE = allow all; cho phep moi request tu ben ngoai.
File kich hoat: /etc/nginx/sites-available/hoangvanchung-cntt1.conf symlink sang /etc/nginx/sites-enabled/, da go default.

5. Tuong lua UFW
Chay lenh: sudo ufw allow 22/tcp truoc khi bat UFW.
Chay lenh: sudo ufw allow 8081/tcp cho cong website.
Chay lenh: sudo ufw --force enable roi kiem tra sudo ufw status verbose.
Ket qua: Status active, co 22/tcp ALLOW IN Anywhere, 8081/tcp ALLOW IN Anywhere kem dong (v6).
Ghi chu: 80/tcp va 8082/tcp la rule co san cua server chung, giu nguyen.

6. Cac buoc trien khai
Buoc 1 tao user: sudo useradd -m -s /bin/bash hoangvanchung-cntt1, sudo usermod -aG sudo hoangvanchung-cntt1, sudo passwd hoangvanchung-cntt1, su - hoangvanchung-cntt1, id, whoami.
Buoc 2 cai dat: sudo apt update, sudo apt install -y nginx git ufw curl, sudo systemctl enable --now nginx, systemctl status nginx, git config user.name chunghoang123, git config user.email chungss7890@gmail.com.
Buoc 3 clone: sudo mkdir -p /var/www, sudo git clone https://github.com/chunghoang123/devops-hackathon-de001-hoangvanchung.git /var/www/devops-hackathon-de001-hoangvanchung, sudo chown -R hoangvanchung-cntt1, find chmod 755 cho thu muc va 644 cho file.
Buoc 4 nginx: sudo cp nginx conf vao sites-available, sudo ln -sf sang sites-enabled, sudo rm -f sites-enabled/default, sudo nginx -t, sudo systemctl reload nginx, curl -I http://192.168.0.103:8081.
Buoc 5 ufw: sudo ufw allow 22/tcp, sudo ufw allow 8081/tcp, sudo ufw --force enable, sudo ufw status verbose.

7. Kiem tra va minh chung
Mo trinh duyet http://192.168.0.103:8081 thay trang cua sinh vien la dat.
Ghi chu: bo qua anh minh chung screenshots theo lua chon ca nhan.

8. Quy trinh cap nhat website
May ca nhan them dong Cap nhat lan 2 - [ngay gio] vao src/index.html roi commit va push.
May chu chay cd /var/www/devops-hackathon-de001-hoangvanchung roi git pull, khong can reload Nginx.
Kiem tra curl -s http://192.168.0.103:8081 thay noi dung moi la dat.

9. Su co gap phai va cach khac phuc
Trung cong: doi sang cong tren 8080 con trong, sua ca listen, UFW, README.
403 Forbidden: sai root hoac sai owner, chay lai chown va 755 644.
nginx -t fail: kiem tra dau cham phay va ngoac, kiem tra server_name la IP.
