# Bitrix24 Self-hosted Installation on CentOS 7 - Apache 2.4.34 + PHP 8.2 + MySQL 8.0

> Runbook ghi lại quá trình dựng máy lab/VM CentOS 7 để làm baseline cho backup/restore và migration Bitrix24 sang AlmaLinux 9.

## 1. Mục tiêu và kiến trúc

```text
Internet
   |
   v
Nginx :80 / :443
   |
   v
Apache 2.4.34 :8888
   |
   v
PHP 8.2.20 (mod_php / libphp.so)
   |
   v
/home/bitrix/www
   |
   v
MySQL 8.0.46
```

## 2. Thông số baseline đã xác nhận

| Thành phần | Giá trị |
|---|---|
| OS | CentOS 7.9.2009 |
| Kernel | 3.10.0-1160.105.1.el7.x86_64 |
| Apache hệ thống cũ | 2.4.6 |
| Apache mục tiêu | 2.4.34 (httpd24) |
| PHP | 8.2.20 |
| PHP SAPI | Apache 2.0 Handler |
| MySQL | 8.0.46 |
| DB | sitemanager |
| DB user | bitrix0 |
| Web source | /home/bitrix/www |
| Apache upstream | 127.0.0.1:8888 |
| Nginx | :80 / :443 |

## 3. Apache 2.4.6 vs 2.4.34

Trên máy có hai binary:

```text
/usr/sbin/httpd
    -> Apache 2.4.6 (CentOS)

/opt/rh/httpd24/root/usr/sbin/httpd
    -> Apache 2.4.34 (Red Hat)
```

Vì vậy `httpd -v` vẫn có thể trả Apache 2.4.6 dù Apache 2.4.34 đang phục vụ Bitrix ở port 8888.

Kiểm tra Apache mục tiêu:

```bash
/opt/rh/httpd24/root/usr/sbin/httpd -v
```

## 4. Dừng Apache cũ trước khi chuyển

```bash
systemctl stop httpd
systemctl stop httpd-scale
```

Xác nhận:

```bash
ps -ef | grep '[h]ttpd'
ss -lntp | grep -E ':8888|:9887'
```

Không cần xóa package Apache 2.4.6 chỉ để đổi version.

## 5. Apache 2.4.34 cho Bitrix

File cấu hình:

```text
/opt/rh/httpd24/root/etc/httpd/conf/httpd-bitrix.conf
```

Các thành phần cốt lõi:

```apache
ServerRoot "/opt/rh/httpd24/root/etc/httpd"
Listen 127.0.0.1:8888
PidFile "/var/run/httpd24/httpd.pid"
ServerName bitrix.review360.id.vn

LoadModule mpm_prefork_module modules/mod_mpm_prefork.so
LoadModule unixd_module modules/mod_unixd.so
LoadModule php_module /usr/lib64/httpd/modules/libphp.so
LoadModule authz_core_module modules/mod_authz_core.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule access_compat_module modules/mod_access_compat.so
LoadModule dir_module modules/mod_dir.so
LoadModule mime_module modules/mod_mime.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule env_module modules/mod_env.so
LoadModule headers_module modules/mod_headers.so
LoadModule log_config_module modules/mod_log_config.so

User bitrix
Group bitrix

DocumentRoot "/home/bitrix/www"

<Directory "/home/bitrix/www">
    AllowOverride All
    Require all granted
    Options FollowSymLinks
    DirectoryIndex index.php index.html
</Directory>

<FilesMatch "\.php$">
    SetHandler application/x-httpd-php
</FilesMatch>

ErrorLog "/var/log/httpd24/error_log"
CustomLog "/var/log/httpd24/access_log" combined

ServerTokens Full
ServerSignature Off
```

### 5.1. PID directory

Lỗi đã gặp:

```text
AH00099: could not create /var/run/httpd24/httpd.pid
AH00100: could not log pid to file /var/run/httpd24/httpd.pid
```

Khắc phục:

```bash
mkdir -p /var/run/httpd24
chown bitrix:bitrix /var/run/httpd24
chmod 755 /var/run/httpd24
```

Test:

```bash
/opt/rh/httpd24/root/usr/sbin/httpd \
  -f /opt/rh/httpd24/root/etc/httpd/conf/httpd-bitrix.conf \
  -t
```

## 6. Các lỗi Apache đã gặp

### 6.1. `mod_unixd`

```text
AH00136: Server MUST relinquish startup privileges before accepting connections.
Please ensure mod_unixd or other system security module is loaded.
```

Thêm:

```apache
LoadModule unixd_module modules/mod_unixd.so
```

### 6.2. Thiếu `mime.types`

```text
AH01597: could not open mime types config file /opt/rh/httpd24/root/etc/httpd/conf/mime.types
```

Nếu config trỏ tới file không tồn tại, bổ sung/điều chỉnh MIME types trước khi start.

### 6.3. Port 8888 bị chiếm

```text
Address already in use
AH00072: make_sock: could not bind to address 127.0.0.1:8888
```

Kiểm tra process giữ port và stop Apache cũ trước khi start Apache 2.4.34.

## 7. PHP 8.2.20

PHP dùng `/etc/php.ini`.

Đã xác nhận:

```text
PHP Version      8.2.20
Server API       Apache 2.0 Handler
Loaded Config    /etc/php.ini
mysqli           loaded
```

Bitrix installer yêu cầu `short_open_tag = On`.

```bash
grep -n "^short_open_tag" /etc/php.ini
curl -s http://127.0.0.1:8888/phpinfo.php | grep -i -A2 "short_open_tag"
```

## 8. MySQL 8.0.46

Kiểm tra:

```bash
mysql -uroot -p -e "SELECT VERSION();"
```

Trong lab, data directory mới được khởi tạo bằng:

```bash
mysqld --initialize-insecure --user=mysql --datadir=/var/lib/mysql
systemctl start mysqld
```

Không chạy `--initialize` lặp lại trên data directory có dữ liệu.

### 8.1. Socket

Có hai path từng xuất hiện:

```text
/var/lib/mysqld/mysqld.sock
/var/lib/mysql/mysql.sock
```

Kiểm tra:

```bash
mysql --print-defaults
cat /root/.my.cnf
grep -RniE 'password|socket' /etc/my.cnf /etc/my.cnf.d/ 2>/dev/null
```

### 8.2. Database/user

```sql
CREATE DATABASE sitemanager CHARACTER SET utf8 COLLATE utf8_unicode_ci;
CREATE USER 'bitrix0'@'localhost' IDENTIFIED BY 'CHANGE_ME';
GRANT ALL PRIVILEGES ON sitemanager.* TO 'bitrix0'@'localhost';
FLUSH PRIVILEGES;
```

Kiểm tra:

```bash
mysql -ubitrix0 -p -hlocalhost sitemanager -e "SELECT VERSION();"
mysql -ubitrix0 -p -h127.0.0.1 sitemanager -e "SELECT VERSION();"
```

## 9. Kết nối PHP -> MySQL

Khi PHP dùng `localhost` đã gặp `mysqli_sql_exception: Permission denied`, trong khi TCP `127.0.0.1:3306` hoạt động.

Test TCP:

```php
<?php
mysqli_report(MYSQLI_REPORT_OFF);
$conn = mysqli_connect('127.0.0.1', 'bitrix0', 'CHANGE_ME', 'sitemanager', 3306);
if (!$conn) { die("MYSQL ERROR: " . mysqli_connect_error()); }
echo "MYSQL OK<br>";
echo "VERSION: " . mysqli_get_server_info($conn);
```

Kết quả baseline:

```text
HTTP/1.1 200 OK
MYSQL OK
VERSION: 8.0.46
```

Với lab này, khi socket `localhost` bị từ chối, dùng `127.0.0.1` trong Bitrix DB connection.

## 10. `.settings.php` và source installer

Source mới có:

```text
/home/bitrix/www/index.php
/home/bitrix/www/install.config
/home/bitrix/www/bitrix/modules/...
```

`index.php` gọi `bitrix/modules/main/install/wizard/wizard.php`, chứng minh đây là installer mới.

Database `sitemanager` lúc đầu không có table là bình thường. Không tự tạo `b_option`, `b_user`, v.v.

Ownership đã chuẩn hóa:

```bash
chown bitrix:bitrix /home/bitrix/www/bitrix/.settings.php
chmod 660 /home/bitrix/www/bitrix/.settings.php
```

## 11. Kiểm tra Apache + PHP

```bash
curl -I http://127.0.0.1:8888/
curl -s http://127.0.0.1:8888/phpinfo.php | grep -E 'PHP Version|Server API|Loaded Configuration File'
```

Kết quả đã đạt:

```text
HTTP/1.1 200 OK
Server: Apache/2.4.34 (Red Hat) PHP/8.2.20
X-Powered-By: PHP/8.2.20
```

## 12. Nginx -> Apache

Nginx giữ `:80` và `:443`. Apache giữ `127.0.0.1:8888`.

```bash
curl -I http://127.0.0.1:8888/
curl -k -I https://bitrix.review360.id.vn/
```

Kết quả public đã đạt HTTP 200 qua Nginx.

## 13. Bitrix Installer

Installer đã đi qua:

1. License agreement
2. Product Registration
3. System Installation
4. System Update
5. Bitrix24 Configuration

System Update đã xử lý nhiều module và progress đã chạy tới 59% trong phiên test.

### 13.1. Active Directory Settings

Wizard có các trường Server:port, Administrative Login, Administrative Password, Tree Root (base DN). Nếu VM không dùng AD, không nhập thông tin giả. Thử bỏ trống và tiếp tục; nếu wizard bắt buộc thì xác định dependency của solution/flow đang chọn.

## 14. Troubleshooting - `The script encountered an error and will be aborted`

Khi browser chỉ hiện thông báo chung, đọc:

```bash
tail -100 /var/log/php/exceptions.log
tail -100 /var/log/httpd24/error_log
```

### 14.1. `b_option` chưa tồn tại

```text
Table 'sitemanager.b_option' doesn't exist
```

Nếu đây là installer mới thì database schema chưa hoàn chỉnh; không tự tạo table.

### 14.2. PHP/MySQL socket

```text
Mysql connect error [localhost]: (2002) Permission denied
```

Đã xác nhận PHP web kết nối được khi dùng `127.0.0.1` TCP. Đổi DB host của Bitrix sang `127.0.0.1` khi cần.

### 14.3. `urlrewrite.php` không có

```text
script '/home/bitrix/www/bitrix/urlrewrite.php' not found or unable to stat
```

Với source installer mới, không tự tạo file này.

### 14.4. PHP test trả HTTP 500

```text
HTTP/1.0 500 Internal Server Error
```

Đọc Apache error log để lấy `PHP Fatal error`.

## 15. MySQL remote access - lab/admin

Nếu cần listen từ mạng:

```ini
[mysqld]
bind-address = 0.0.0.0
port = 3306
```

Kiểm tra:

```bash
mysql -uroot -p -e "SHOW VARIABLES LIKE 'bind_address';"
mysql -uroot -p -e "SHOW VARIABLES LIKE 'port';"
ss -lntp | grep 3306
ss -lntp4 | grep 3306
```

Baseline đã xác nhận `bind_address = *` và `port = 3306`.

Máy không có `firewall-cmd`; firewall là `iptables`. Kiểm tra:

```bash
systemctl status iptables
iptables -L INPUT -n --line-numbers
```

Trong lab, INPUT policy là ACCEPT và có rule ACCEPT rộng, nên không cần cài `firewalld` chỉ để mở 3306.

Không nên duy trì `root@'%'` trên production. Dùng user riêng và giới hạn source IP/VLAN.

## 16. Verification checklist

### OS
- [ ] CentOS 7 baseline captured
- [ ] Kernel captured
- [ ] Hostname/IP documented
- [ ] Time/NTP checked

### Apache
- [ ] Apache 2.4.34 binary path documented
- [ ] `-t` = `Syntax OK`
- [ ] `mod_unixd` loaded
- [ ] `mod_prefork` loaded
- [ ] PHP module loaded
- [ ] `/var/run/httpd24` exists
- [ ] `127.0.0.1:8888` listening

### PHP
- [ ] PHP 8.2.20
- [ ] `short_open_tag=On`
- [ ] `mysqli` loaded
- [ ] `/etc/php.ini` verified
- [ ] Web SAPI verified

### MySQL
- [ ] MySQL 8.0.46 running
- [ ] Port 3306
- [ ] bind-address verified
- [ ] sitemanager exists
- [ ] bitrix0 exists
- [ ] CLI connection works
- [ ] PHP web connection works
- [ ] Socket/TCP behavior documented

### Bitrix
- [ ] Installer source present
- [ ] `install.config` present
- [ ] `.settings.php` ownership checked
- [ ] Compatibility checks pass
- [ ] System Update completes
- [ ] Administrator account created
- [ ] Solution installed
- [ ] Final login tested

### Nginx
- [ ] :80 listening
- [ ] :443 listening
- [ ] proxy to 127.0.0.1:8888
- [ ] public HTTPS returns HTTP 200

## 17. Evidence commands

```bash
cat /etc/centos-release
uname -r
/opt/rh/httpd24/root/usr/sbin/httpd -v
php -v
mysql -uroot -p -e "SELECT VERSION();"
ss -lntp | grep -E ':80|:443|:8888|:3306'
ps -ef | grep '[h]ttpd'
curl -I http://127.0.0.1:8888/
curl -k -I https://bitrix.review360.id.vn/
mysql -uroot -p -e "SHOW DATABASES;"
mysql -ubitrix0 -p -h127.0.0.1 sitemanager -e "SHOW TABLES;"
```

## 18. Baseline for CentOS 7 -> AlmaLinux 9

Only after Bitrix installation is complete:

```text
1. Freeze baseline
2. Backup application source
3. Backup database
4. Record versions/configuration
5. Record ownership/permissions
6. Record Nginx/Apache/PHP/MySQL topology
7. Restore into target
8. Validate DB connectivity
9. Validate web stack
10. Validate Bitrix files/modules
11. Validate cron/agents
12. Functional test
13. Cutover plan
```

Phân biệt rõ installer-new VM, installed Bitrix VM và migration source.

## 19. Security cleanup

Sau khi lab hoàn tất, xóa:

```text
/home/bitrix/www/phpinfo.php
/home/bitrix/www/dbtest.php
```

Rotate các password đã dùng trong troubleshooting nếu cần. Không commit credential vào Git.

---

**Status:** Web stack và troubleshooting path đã được kiểm chứng trong lab CentOS 7. Production hardening và migration sang AlmaLinux 9 cần được revalidate theo đúng Bitrix edition/version và target stack.